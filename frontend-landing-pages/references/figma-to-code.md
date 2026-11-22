# Figma-to-code

## Get usable design evidence

- Discover the configured Figma MCP tools. For the official server, load its `figma-design-to-code` guidance before `get_design_context`. Once the file key is known, start a file session with `create_session` and pass its returned ID to subsequent file tools as directed by the server.
- Identify the requested frame and related desktop, tablet, and mobile frames, variants, and prototype states. Resolve node-specific links according to the server's instructions. If the node is unclear, use available file metadata to locate it when supported, or request the specific frame link when ambiguity would materially change the work.
- Use `get_design_context` for the target frames and inspect its screenshot. Fetch a focused `get_screenshot` when the screenshot is missing or detail is too small. For a large frame that returns only metadata, inspect the relevant child sections. Use variables, Code Connect mappings, and motion context where available to resolve open implementation questions.
- Use the original assets from the design context and request asset exports for missing items. Save the files through the project's asset pipeline while the links work. Preserve SVGs for provided logos and icons where appropriate. Check that fonts and weights are available for web use. If MCP access fails, work from supplied frames, exports, and specs when possible, and identify any fidelity checks that remain open.

## Translate design intent into the repository

- Adapt generated reference code to the project's framework, component APIs, and tokens. Translate auto layout, hug/fill, and constraints into content-driven sizing, flexbox, or grid. Use absolute positioning for intentional overlays and artwork where appropriate.
- Match typeface, weight, line height, tracking, spacing, alignment, color, borders, and asset crops. Translate Figma states into semantic browser behavior. Keep live text and interactive controls in the DOM.
- Use supplied frames as anchors for responsive behavior. When only a desktop frame exists, infer narrow layouts from reading order, content priority, and constraints. Check image focal points and important calls to action at narrow widths. Document material assumptions.
- Treat static frames as composition references. For motion, inspect available prototype transitions and use the supplied duration, easing, and trigger where feasible. If a transition is unspecified, choose behavior that supports the design and disclose significant assumptions.
- Capture the implementation at the Figma frame widths after fonts and images settle. Compare equivalent states using side-by-side screenshots or overlays when available. Adjust structure and typography before minor offsets. Check browser rendering at intermediate widths and distinguish verified matches from remaining differences.
