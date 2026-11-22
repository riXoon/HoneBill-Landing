# Motion and 3D

## Pick the technique

- Use CSS transitions or keyframes for simple interface feedback and loops. Consider the Web Animations API for imperative playback and use the project's animation library for coordinated timelines or scroll sequences. Introduce a dependency when the orchestration or rendering benefit justifies its cost.
- For a fixed camera and no viewer interaction, compare an optimized still or video with runtime 3D. Use CSS perspective for simple depth effects. Use Three.js, or the project's existing renderer such as React Three Fiber, when real geometry, lighting, model animation, or camera interaction is required.
- Define each effect by its trigger, start and end states, duration, easing, replay behavior, and reduced-motion equivalent. Favor transform and opacity animations where practical and profile effects that trigger layout, paint large surfaces, or apply expensive filters.

## Preserve input and accessibility

- Respect `prefers-reduced-motion` in CSS and JavaScript. Stop decorative loops and remove parallax or camera travel in this mode. Preserve state changes and show the content in a readable static state.
- Keep native scrolling and keyboard navigation usable. Keep content visible if an animation never starts. For interactive graphics, provide keyboard and touch access through labeled DOM controls where needed. Give users a way to pause moving content where applicable.
- Use compositor-friendly or browser-scheduled updates where suitable. Keep frame-by-frame values out of component-wide reactive state. Cancel owned timelines, observers, listeners, and frame loops when the feature unmounts.

## Budget and lifecycle for runtime 3D

- Establish camera composition and the poster at representative sizes before tuning the scene. Reserve the canvas region with stable dimensions and keep essential text, links, and controls in HTML. Show the poster while loading and when the renderer is unavailable, initialization fails, or the graphics context is lost. Recover on context restoration where supported.
- Split renderer and model code from the critical path where the stack allows. Warm up on approach or intent where that helps, and render on demand for static scenes. Suspend ongoing rendering when the scene is offscreen or the document is hidden. Keep decorative canvas layers from intercepting normal page gestures.
- Profile on representative devices or with available throttling. Tune device-pixel ratio, geometry, texture dimensions, draw calls, shadows, and postprocessing based on measurements. Consider compressed glTF geometry or textures where supported, including their decoder cost. Use lower quality tiers when needed and keep visual continuity with the poster.
- Resize the render buffer and update camera projection with the scene container. Release owned geometry, materials, textures, render targets, and renderer resources as appropriate, preserving shared assets used elsewhere. Check repeated mount and unmount, resize, rotation, and fallback behavior.
