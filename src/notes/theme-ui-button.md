---
title: Custom inclusive/accessible Theme UI Button
date: 2021-11-11
tags:
  - react
  - typescript
  - a11y
---

This button component extends Theme UI's `Button` and add some more props/functionality. It takes all standard `<button>` attributes e.g. `disabled`, `type` etc etc **AND** also Theme UI's props like `variant` and `sx`. It is based on the guidelines at https://css-tricks.com/making-disabled-buttons-more-inclusive/

## Usage

```tsx
<Button>Click me</Button>
<Button type="submit">Click me</Button>
<Button disabled>Click me</Button>
<Button onClick={() => console.log('clicked')}>Click me</Button>
```

### With loading state

```tsx
<Button isLoading={true}>Click me</Button>
```

### Inclusive/accessible disabled state

Using the guidelines from https://css-tricks.com/making-disabled-buttons-more-inclusive/, this button will show a simple tooltip if the form state is not ready. Instead of passing `disabled=true` to the button, use the `isDisabled` & `disabledText` props.

```tsx
<Button
  isDisabled={true}
  disabledText="You must select a meeting for all trainees"
>
  Request meetings
</Button>
```

### Icon buttons

If you need an icon button, do not use this `Button` component. Instead, use the `IconButton` component from `theme-ui`, like so:

```tsx
import { IconButton } from 'theme-ui'
import { IconPicker } from '../components'
;<IconButton>
  <IconPicker icon="exclamation" />
</IconButton>
```

## Source code

```tsx
import React, { forwardRef } from 'react'
import {
  Box,
  Button as ThemeUIButton,
  ButtonProps as ThemeUIButtonProps,
} from 'theme-ui'

export interface ButtonProps extends ThemeUIButtonProps {
  isLoading?: boolean
  isDisabled?: boolean
  disabledText?: string
}

export const Button = forwardRef<HTMLButtonElement, ButtonProps>(
  (
    {
      sx,
      isLoading,
      children,
      onClick,
      isDisabled,
      disabledText,
      disabled,
      ...rest
    },
    ref
  ): JSX.Element => {
    return (
      <ThemeUIButton
        sx={{
          position: 'relative',
          display: 'inline-flex',
          alignItems: 'center',
          ...sx,
          cursor: isLoading ? 'wait' : isDisabled ? 'not-allowed' : 'pointer',
          '&:hover .tooltipBox,&:focus-within .tooltipBox': {
            opacity: 1,
            visibility: 'visible',
            transition: 'opacity 250ms',
          },
          '&:hover .tooltipBox:hover &': {
            transition: 'opacity 250ms 500ms',
          },
        }}
        ref={ref}
        disabled={disabled}
        onClick={(event) => {
          if (isLoading || isDisabled) {
            event.preventDefault()
          } else {
            onClick?.(event)
          }
        }}
        {...rest}
        aria-disabled={isDisabled ? 'true' : 'false'}
        aria-describedby="disabledReason"
      >
        <Box
          as="span"
          sx={{
            visibility: isLoading ? 'hidden' : 'visible',
          }}
        >
          {children}
        </Box>
        {isLoading && (
          <Box
            sx={{
              position: 'absolute',
              top: '50%',
              left: '50%',
              transform: 'translate(-50%, -50%)',
              color: 'currentColor',
              pointerEvents: 'none',
              visibility: isLoading ? 'visible' : 'hidden',
            }}
          >
            🤔
          </Box>
        )}
        {isDisabled && disabledText ? (
          <Box
            role="tooltip"
            className="tooltipBox"
            id="disabledReason"
            sx={{
              position: 'absolute',
              bottom: '100%',
              left: '50%',
              transform: 'translateX(-50%)',
              width: 'max-content',
              pb: 2,
              opacity: 0,
              visibility: 'hidden',
              transition: 'opacity 250ms, visibility 1ms 250ms',
            }}
          >
            <Box
              as="span"
              className="tooltipItself"
              sx={{
                display: 'block',
                bg: '#e2e8f0',
                color: '#64748b',
                px: 2,
                py: 1,
                fontSize: 1,
                borderRadius: 'default',
                textAlign: 'center',
                WebkitFontSmoothing: 'initial',
                MozOsxFontSmoothing: 'initial',
              }}
            >
              {disabledText}
            </Box>
          </Box>
        ) : null}
      </ThemeUIButton>
    )
  }
)
```
