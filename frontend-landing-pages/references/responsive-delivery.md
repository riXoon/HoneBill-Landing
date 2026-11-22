# Responsive delivery and verification

## Layout and accessibility

- Start with a readable narrow layout and add breakpoints at content pressure points or where the supplied frames change composition. Constrain content widths, use flexible tracks and wrapping, and keep spacing and type ramps aligned with design tokens. Diagnose the source of overflow before applying clipping.
- Check the page at reference widths, a narrow phone width around 320 CSS pixels, intermediate widths, and a wide viewport. Check long text, text scaling, and mobile menu behavior. Preserve reading and focus order when rearranging content. Account for safe-area insets when fixed controls reach screen edges.
- Exercise navigation, calls to action, forms, and any drawer or carousel with touch and keyboard where applicable. Check visible focus, focus restoration for modal controls, meaningful accessible names and alt text, sufficient contrast, usable touch targets, and form loading, success, and error states.

## Performance and page delivery

- Identify the likely Largest Contentful Paint element. Keep critical HTML visible on first render where the stack supports it. Serve the hero image in the initial markup when practical, with suitable responsive sizes and priority. Reserve image and media dimensions. Defer genuinely noncritical media, scripts, and interactive effects.
- Use existing build support for responsive image formats, compression, font subsetting, or caching where appropriate. Load the font weights the design uses, choose sensible fallbacks, and preload only assets that need early discovery. Check how font and media loading affect line wrapping and layout shifts.
- Preserve site metadata conventions. Where relevant, set page title, description, and social preview, and verify crawlable content and working links for public pages. Follow the site's existing handling for forms, metadata, and analytics.
- In a production build when available, inspect the mobile waterfall, layout shifts, and main-thread work during interactions. Measure or investigate LCP, CLS, and interaction responsiveness using the project's tools. Compare against an existing baseline or agreed budget. Treat local runs as lab diagnostics and reserve field claims for real-user data.

## Browser review

- Capture the main view and changed sections at desktop and mobile widths. Look for unintended overflow, clipped artwork, sticky elements covering focused controls, and layout shifts while fonts and media load.
- Check reduced motion, touch input, keyboard navigation, and a slow connection when tools allow. For 3D, also test loading or renderer failure while confirming that the primary action and relevant content still work.
- Use the repository's relevant build, lint, typecheck, and tests. Inspect the browser console and network for errors caused by the change. Report the viewports, input modes, or performance conditions actually exercised when they matter to the result.
