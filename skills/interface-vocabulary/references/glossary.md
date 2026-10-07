# Interface glossary

Use these terms as a shared vocabulary, not as rigid standards. Product teams and design systems sometimes use different names; describe the behavior when the label is ambiguous.

## UI components and patterns

- **Modal dialog:** a focused task or decision presented above the current page, usually making the background unavailable until dismissed or completed.
- **Popover:** contextual content positioned in relation to a trigger; it may contain interactive controls.
- **Tooltip:** brief, non-interactive help attached to an element, commonly shown on hover or focus.
- **Drawer / sheet:** a panel that enters from a viewport edge, often while the current page remains visible.
- **Toast / snackbar:** a temporary status message that does not interrupt the current task. Some systems reserve “snackbar” for messages with an action.
- **Badge:** a compact label or status marker associated with content or a control.
- **Chip:** a compact token, often interactive, used for a filter, selection, or category. “Tag” and “pill” can describe similar appearances; behavior clarifies the distinction.
- **Disclosure:** a control that shows or hides associated content. An **accordion** is usually a group of disclosures.
- **Command palette:** a searchable overlay for invoking commands or navigating by keyboard.
- **Skeleton:** a placeholder that approximates the shape of content while it loads. A **shimmer** is an optional animated highlight, not the skeleton itself.
- **Empty state:** the interface shown when a collection or view has no content, often explaining why and what action is available.
- **Progress indicator:** feedback that an operation is underway; may be determinate (known progress) or indeterminate.

## Layout and composition

- **Stack:** elements arranged along one axis with consistent spacing.
- **Cluster:** related inline items grouped together and allowed to wrap as space changes.
- **Split layout:** adjacent regions with distinct roles, such as content and a sidebar.
- **Overlay:** content layered above other content rather than occupying its normal place in document flow.
- **Sticky element:** an element that stays near a viewport edge while its container scrolls, then follows the container boundary.
- **Responsive breakpoint:** a viewport or container threshold at which layout or styles change.
- **Progressive disclosure:** showing the information or controls needed now while keeping secondary detail available when requested.
- **Visual hierarchy:** the arrangement of emphasis that communicates relative importance and reading order.

## Motion: entrances and exits

- **Fade in / fade out:** appear or disappear by changing opacity.
- **Slide in / slide out:** enter or leave by moving along an axis.
- **Scale in:** grow from a smaller size as an element appears, often paired with a fade.
- **Pop in:** appear with a small overshoot or bounce.
- **Reveal:** gradually uncover content, often with a mask or clip path.
- **Enter / exit:** the motion an element plays when added to or removed from the interface.

## Motion: timing and sequencing

- **Keyframes:** defined points in an animation that specify property values at particular times.
- **Interpolation / tween:** the calculation of in-between values from a start and end state.
- **Stagger:** animate items in a group one after another with short offsets.
- **Orchestration:** coordinate the timing and order of multiple animations.
- **Delay:** time between an animation being triggered and starting.
- **Duration:** the time an animation takes to complete.
- **Fill mode:** whether an animation applies its initial or final styles outside its active interval.
- **Stepped animation:** motion that changes in discrete jumps instead of continuous interpolation.

## Motion: transforms and spatial effects

- **Translate:** move an element along an axis.
- **Scale:** make an element larger or smaller.
- **Rotate:** turn an element around an origin point.
- **Skew:** slant an element by shifting one side relative to the other.
- **3D tilt / flip:** rotate an element in three-dimensional space to suggest depth or a turn-over.
- **Perspective:** the strength of depth distortion in a 3D transform.
- **Transform origin:** the anchor point around which an element scales or rotates.
- **Origin-aware animation:** motion that appears to grow from or return to a related point, such as a popover's trigger.
- **Parallax:** foreground and background move at different rates to suggest depth.

## Motion: state and view transitions

- **Crossfade:** one visual fades out as another fades in over the same area.
- **Continuity transition:** connect before and after states so the user can follow what changed.
- **Morph:** one shape or visual element smoothly changes into another.
- **Shared-element transition:** an element appears to move and transform between layouts or views.
- **Layout animation:** elements animate between positions or sizes when the layout changes.
- **Accordion / collapse animation:** a section expands or contracts to show or hide content.
- **Direction-aware transition:** navigation direction is reflected in the direction content enters or leaves.
- **Page transition:** motion between pages or routes.
- **View transition:** a browser-supported transition between document or UI states, optionally connecting shared elements.

## Motion: interaction and feedback

- **Hover effect:** a visual response while a pointer is over an element.
- **Press / tap feedback:** a visual response to activation, such as a subtle scale or color change.
- **Hold to confirm:** progress or feedback advances while a control is held, often for deliberate actions.
- **Drag:** move an element by grabbing and moving it, sometimes carrying momentum after release.
- **Drag to reorder:** move an item within a collection while other items shift to make room.
- **Swipe to dismiss:** drag an element away to dismiss it.
- **Rubber-banding:** resistance and rebound when a dragged or scrolled element passes a boundary.
- **Shake / wiggle:** brief side-to-side motion used to signal an error or rejected input.
- **Ripple:** a circle expands from an activation point as feedback.

## Motion: easing and spring terms

- **Easing:** how an animation's speed changes over time.
- **Ease-out:** starts quickly and settles near the end; often useful for an entrance or response.
- **Ease-in:** starts slowly and accelerates; can make a response feel delayed if overused.
- **Ease-in-out:** accelerates and then decelerates; often suits movement between two on-screen positions.
- **Linear:** constant speed; common for continuous progress or looping motion.
- **Cubic Bézier:** a curve used to define custom timing and easing.
- **Asymmetric easing:** easing whose acceleration and deceleration are not mirror images.
- **Spring:** motion model that settles toward a target using spring-like dynamics instead of only a fixed-duration curve.
- **Stiffness / tension:** how strongly a spring pulls toward its target; higher values tend to feel faster.
- **Damping:** how quickly spring oscillation settles; lower damping usually means more bounce.
- **Mass:** how heavy a spring-driven element feels; greater mass tends to slow its response.
- **Bounce:** overshoot and oscillation around a target.
- **Perceptual duration:** how long motion appears to take before it feels settled, even if small movement continues.
- **Momentum:** continued movement that carries speed from a preceding gesture or motion.
- **Velocity:** speed and direction of movement at a point in time; can carry through an interrupted gesture or spring.
- **Interruptible animation:** motion that can be redirected or reversed before it finishes.

## Motion: loops and ambient effects

- **Marquee:** content that scrolls continuously in a loop.
- **Loop:** an animation that repeats a set number of times or indefinitely.
- **Alternate / yoyo:** a loop that plays forward and then reverses on the next iteration.
- **Orbit:** an element follows a circular path around another point or element.
- **Pulse:** a repeating change in scale, opacity, or another property that draws attention.
- **Float:** subtle repeating drift that suggests lightness.
- **Idle animation:** ambient motion while an element waits for interaction.

## Visual effects and content treatments

- **Blur:** soften visual detail with a filter or surface effect.
- **Clip path:** hide parts of an element at a defined geometric boundary, usually with a hard edge.
- **Mask:** use a shape or gradient to control which parts of an element are visible, including soft edges.
- **Before / after slider:** draggable divider that reveals different portions of two overlaid images for comparison.
- **Line drawing:** progressively reveal an SVG or stroked path as if it were being drawn.
- **Text morph:** animate text characters or shapes as the displayed text changes.
- **Number ticker:** animate digits as a value changes or counts toward a target.
- **Tabular numbers:** fixed-width numerals that prevent columns of changing numbers from shifting.
- **Typewriter:** reveal text one character at a time to imitate typing.

## Motion performance terms

- **Frame rate (FPS):** number of frames displayed per second.
- **Jank:** visible stutter or uneven motion, often caused by missed frame deadlines.
- **Dropped frame:** a frame that was not drawn in time.
- **Compositing:** browser work that combines rendered layers; some changes can be handled without recalculating layout or repainting the full page.
- **`will-change`:** a CSS hint that a property may change; use sparingly and in response to a real rendering need.
- **Layout thrashing:** repeated reads and writes that force the browser to recalculate layout during rendering, potentially causing jank.
- **Hardware acceleration:** informal term for browser/GPU-assisted rendering work; it does not guarantee an animation is fast.

## Motion principles

- **Purposeful animation:** motion that communicates feedback, state, spatial relationships, or explanation rather than serving as decoration alone.
- **Anticipation:** a small preparatory movement that signals an action is about to happen.
- **Follow-through:** secondary movement that continues briefly after the main movement to suggest weight or flexibility.
- **Squash and stretch:** deformation used to suggest speed, impact, weight, or flexibility.
- **Perceived performance:** how responsive an interface feels, which can differ from its measured speed.
- **Frequency of use:** how often someone encounters an interaction; repeated interactions generally need less delay and visual fuss.
- **Spatial consistency:** preserving a sense of where an element came from or went during a state change.
- **Reduced motion:** adapting nonessential movement when a person requests reduced motion through their system preference.
