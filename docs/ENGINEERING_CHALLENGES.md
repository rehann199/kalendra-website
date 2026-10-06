# Engineering Challenges

Each entry states a problem, the approach taken in the site and the outcome or remaining trade-off. All descriptions come from reading the source and from the live site.

## 1. Making a conversation feel live without a video

- **Problem:** show the product's central idea, talking to a calendar, on a page with no real app to embed.
- **Approach:** a reusable bubble component takes position, delay, colours and one or more messages. After its delay, each bubble shows an animated voice-waveform, fades the bars out, expands into a bubble and types its text. Six instances run on staggered delays, and a shared loop duration resets all of them together every 35 seconds.
- **Outcome:** a scripted exchange (a request to clear Friday afternoon and Kalendra's reply) that is editable as plain data.
- **Trade-off:** timing is hard-coded per bubble, so adding a message means re-planning delays by hand.

## 2. One animation, two layouts

- **Problem:** absolutely positioned bubbles that look right on a wide desktop crush or overlap on a phone.
- **Approach:** two configurations of the same component, with different font sizes, widths and positions, chosen by a window-width check at 768 px. The background image is also swapped with `<picture>`.
- **Outcome:** a stacked, alternating left and right conversation on mobile that reads like a chat thread.
- **Trade-off:** JavaScript decides the layout, so the first paint depends on the initial width check.

## 3. A glass lens built from an SVG filter

- **Problem:** show a ticker of job titles with a refracting lens effect without canvas or WebGL.
- **Approach:** the ticker is DOM text moved by a `requestAnimationFrame` loop. A lens-shaped window applies an SVG turbulence and displacement filter to the text inside it, while text outside is blurred. Lens width, height, speed and font size change at the mobile breakpoint.
- **Outcome:** a distinctive effect that stays selectable, crisp text.
- **Trade-off:** SVG filters are costly on low-end devices, and the loop updates React state each frame.

## 4. Drawing integration lines from parameters

- **Problem:** connect the Kalendra logo to Google, Outlook and Zoom icons with smooth curves that animate in sequence, and keep it adjustable.
- **Approach:** Bezier path strings are computed from start point, segment lengths, control offsets and a scale factor. The logo itself transitions from a square to a pill by animating border radius, width and position values in state.
- **Outcome:** a self-playing diagram that loops; only a few numbers change between the desktop card and the mobile card.

## 5. Sending form data with no backend

- **Problem:** collect early-access requests without standing up a server.
- **Approach:** the browser SDK of an email-delivery service sends the entry. The component checks that its configuration is present, shows submitting and submitted states, locks after success and translates network failures into readable messages.
- **Trade-off:** there is no server-side validation, rate limiting or spam control, and the browser-side identifiers are public by design.

## 6. Linkable legal dialogs in a single page

- **Problem:** privacy and terms must be reachable by URL and from the footer, but the site has no router.
- **Approach:** the app derives dialog state from `location.hash` on load and on `hashchange`. Closing removes the hash with `history.pushState`. The dialogs set body scroll lock, close on Escape and have dialog roles and labels.
- **Outcome:** shareable links and working back and forward buttons.
