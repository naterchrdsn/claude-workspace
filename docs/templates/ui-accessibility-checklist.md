# UI Accessibility Checklist

## Fundamentals

- [ ] Semantic HTML elements used appropriately
- [ ] Page has a single h1 and logical heading order
- [ ] Form inputs have associated labels
- [ ] Color contrast meets WCAG 2.1 AA
- [ ] Focus states are visible and consistent

## Keyboard Navigation

- [ ] All interactive elements are reachable via keyboard
- [ ] Tab order follows visual order
- [ ] No keyboard traps
- [ ] Skip-to-content link is present (if needed)

## Screen Readers

- [ ] Images have descriptive alt text
- [ ] ARIA labels used only when necessary
- [ ] ARIA roles are correct and minimal
- [ ] Status messages use aria-live when appropriate

## Forms and Validation

- [ ] Error messages are announced to screen readers
- [ ] Required fields are clearly indicated
- [ ] Inline validation is accessible

## Media and Motion

- [ ] Captions provided for videos
- [ ] Animations respect prefers-reduced-motion
- [ ] Audio controls are accessible

## Testing

- [ ] Tested with keyboard only
- [ ] Tested with screen reader
- [ ] Tested at 200% zoom
- [ ] Tested with reduced motion

## Notes

- Known issues:
- Follow-up actions:
