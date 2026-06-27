# shadcn/ui Component Guide: UI/UX & Accessibility Best Practices

This guide outlines design systems, use cases, visual patterns, and accessibility (a11y) considerations for every major component in the shadcn/ui ecosystem.

---

## Table of Contents

1. [Layout & Navigation](#1-layout--navigation)
   - [Sidebar](#sidebar)
   - [Navigation Menu](#navigation-menu)
   - [Tabs](#tabs)
   - [Breadcrumb](#breadcrumb)
   - [Pagination](#pagination)
   - [Scroll Area](#scroll-area)
   - [Resizable](#resizable)
   - [Separator](#separator)
   - [Aspect Ratio](#aspect-ratio)
   - [Collapsible](#collapsible)
2. [Forms & Inputs](#2-forms--inputs)
   - [Form](#form)
   - [Button](#button)
   - [Input](#input)
   - [Input OTP](#input-otp)
   - [Textarea](#textarea)
   - [Select](#select)
   - [Combobox](#combobox)
   - [Checkbox](#checkbox)
   - [Radio Group](#radio-group)
   - [Switch](#switch)
   - [Slider](#slider)
   - [Label](#label)
   - [Toggle & Toggle Group](#toggle--toggle-group)
3. [Overlays & Dialogs](#3-overlays--dialogs)
   - [Dialog](#dialog)
   - [Alert Dialog](#alert-dialog)
   - [Sheet](#sheet)
   - [Drawer](#drawer)
   - [Popover](#popover)
   - [Tooltip](#tooltip)
   - [Hover Card](#hover-card)
   - [Dropdown Menu](#dropdown-menu)
   - [Context Menu](#context-menu)
   - [Menubar](#menubar)
4. [Data Display & Feedback](#4-data-display--feedback)
   - [Card](#card)
   - [Table](#table)
   - [Chart](#chart)
   - [Calendar](#calendar)
   - [Avatar](#avatar)
   - [Badge](#badge)
   - [Progress](#progress)
   - [Skeleton](#skeleton)
   - [Alert](#alert)
   - [Sonner / Toast](#sonner--toast)

---

## 1. Layout & Navigation

### Sidebar
* **Description**: A multi-layout side panel for navigation, dashboard widgets, and global controls.
* **Use Cases**: Admin dashboards, primary application navigation, collapsible side toolbars.
* **UI/UX Best Practices**:
  - Keep it collapsible on desktop to maximize screen space for core work.
  - Include clear visual indicators of the active page.
  - Implement smooth collapse transitions and clear tooltips for icons when collapsed.
* **Dos & Don'ts**:
  - **Do**: Convert to a slide-over sheet drawer on mobile layouts.
  - **Don't**: Clutter the panel with deep multi-level navigation lists; stick to 1 or 2 levels.
* **Accessibility (a11y)**: Focus states must be highly visible. Toggles must indicate `aria-expanded` state.

### Navigation Menu
* **Description**: A collection of links and dropdown lists for primary application navigation.
* **Use Cases**: E-commerce megamenus, primary website header menus.
* **UI/UX Best Practices**:
  - Group related links logically and keep dropdown menu items to a manageable number (under 8 items per section).
  - Use visual hierarchies (e.g., icons, headings, bold labels) inside dropdowns to make items self-describing.
* **Dos & Don'ts**:
  - **Do**: Add a slight hover delay (e.g., 150ms) to dropdown transitions to prevent menus from disappearing/triggering too aggressively.
  - **Don't**: Hide primary links inside hamburger menus on large desktop views.
* **Accessibility (a11y)**: Supports keyboard navigation via `Tab`, `ArrowKeys`, `Enter`, `Space`, and `Escape`.

### Tabs
* **Description**: A set of layered sections of content (tab panels) where only one panel is visible at a time.
* **Use Cases**: Switching views within a single context (e.g., profile settings, charts vs. table views) without changing page URL.
* **UI/UX Best Practices**:
  - Keep tabs in a single horizontal row. If you need vertical tabs, style them differently or use a sidebar.
  - Use short, clear labels (1-2 words). Avoid icons alone unless they are universally recognizable.
* **Dos & Don'ts**:
  - **Do**: Keep tab panel heights consistent to avoid page jumping when users switch tabs.
  - **Don't**: Use tabs for sequential steps or progress flows (e.g., checkouts)—use a Step/Wizard interface instead.
* **Accessibility (a11y)**: Keyboard navigation must support `ArrowLeft` / `ArrowRight` to transition focus between tabs.

### Breadcrumb
* **Description**: A navigation aid that shows the user's current location in a hierarchical trail.
* **Use Cases**: Nested directory structures, multi-level file systems, and deep category structures.
* **UI/UX Best Practices**:
  - Place breadcrumbs at the top left of the main content container, below the header.
  - The last item (current page) should be plain text (not clickable) and visually distinct (e.g., slightly bolder or darker text).
* **Dos & Don'ts**:
  - **Do**: Truncate long link names with an ellipsis (`...`) if the trail is too long.
  - **Don't**: Use breadcrumbs on flat websites with shallow hierarchies.
* **Accessibility (a11y)**: Wrap in `<nav aria-label="Breadcrumb">` and ensure the last item has `aria-current="page"`.

### Pagination
* **Description**: Navigational interface to split large data sets into multiple pages.
* **Use Cases**: Search results, product grid lists, page-based data tables.
* **UI/UX Best Practices**:
  - Always show "Previous" and "Next" indicators.
  - Highlight the active page button clearly with distinct background colors.
  - Provide links to first and last pages if the total pages count is large.
* **Dos & Don'ts**:
  - **Do**: Ensure target button click sizes are at least 44x44px for touchscreens.
  - **Don't**: Use pagination if infinite scrolling or virtual lists fit the content paradigm better (e.g., social media feeds).
* **Accessibility (a11y)**: Use descriptive labels like `aria-label="Goto page 3"`.

### Scroll Area
* **Description**: Custom, cross-browser scrollbar container.
* **Use Cases**: Sidebar menus, custom selects, dashboard widget panels, code snippets.
* **UI/UX Best Practices**:
  - Keep scrollbars subtle and slim to avoid visual noise.
  - Fade scrollbars out when the cursor is not hover-interacting with the container.
* **Dos & Don'ts**:
  - **Do**: Match scroll track color with the background color to maintain visual minimalism.
  - **Don't**: Nest multiple scrollable containers inside one another—it confuses page scrolls.
* **Accessibility (a11y)**: Ensure keyboard arrow keys scroll the container when it has focus.

### Resizable
* **Description**: A layout panel builder that allows users to drag and resize adjacent panels.
* **Use Cases**: Code workspaces, data panels, dashboard grid customizers.
* **UI/UX Best Practices**:
  - Provide clear drag-handle visual bars (lines, dots).
  - Define minimum and maximum scale constraints so panels cannot be resized to unusable widths.
  - Preserve user layouts using `localStorage`.
* **Dos & Don'ts**:
  - **Do**: Change the cursor style to `col-resize` or `row-resize` on handle hover.
  - **Don't**: Allow panels to overlap or disappear completely without an explicit toggle.
* **Accessibility (a11y)**: Ensure drag handles are keyboard focusable and can be resized with arrow keys.

### Separator
* **Description**: A simple dividing line to visually separate content blocks.
* **Use Cases**: Splitting headers from content, dividing menu sections, vertical link groups.
* **UI/UX Best Practices**:
  - Keep separators extremely light and low-contrast (e.g., using `border-muted`) so they do not compete with text.
* **Dos & Don'ts**:
  - **Do**: Use appropriate margins/padding to let layout elements breathe naturally.
  - **Don't**: Overuse separators; empty white space is often a better divider.
* **Accessibility (a11y)**: Add `role="separator"` and match `aria-orientation`.

### Aspect Ratio
* **Description**: A container that locks its contents to a specific aspect ratio, scaling fluidly.
* **Use Cases**: Video player panels, photo gallery grids, product card thumbnails.
* **UI/UX Best Practices**:
  - Match common aspect ratios (16:9 for video, 4:3 or 3:2 for photographs, 1:1 for square items).
  - Use skeleton loading states to reserve spaces before the media fully loads.
* **Dos & Don'ts**:
  - **Do**: Apply tailwind classes like `object-cover` to prevent media distortion.
  - **Don't**: Force non-proportional crops on user images that contain text.
* **Accessibility (a11y)**: Retain correct alt text definitions for images/videos loaded inside the aspect ratio wrapper.

### Collapsible
* **Description**: An interactive component that toggles the visibility of content.
* **Use Cases**: "Show More/Less" content blocks, secondary details in lists.
* **UI/UX Best Practices**:
  - Keep the trigger action label clear (e.g., "Show details").
  - Animate height transition smoothly.
* **Dos & Don'ts**:
  - **Do**: Keep the trigger button in a predictable place after content expands.
  - **Don't**: Use to hide information critical to completing the main workflow.
* **Accessibility (a11y)**: Manage `aria-expanded` and `aria-controls` programmatically.

---

## 2. Forms & Inputs

### Form
* **Description**: Form layout and wrapper component integrated with `react-hook-form` and `zod` validation schemas.
* **Use Cases**: Registration pages, checkout screens, configuration settings.
* **UI/UX Best Practices**:
  - Show error messages inline, directly below the invalid input field.
  - Group related fields (e.g., personal details vs. billing info) inside distinct sections or cards.
  - Highlight fields containing errors with a red border (`border-destructive`).
* **Dos & Don'ts**:
  - **Do**: Auto-focus the first empty input field when appropriate (e.g., on login pages).
  - **Don't**: Disable submit buttons without explaining why; it's better to allow submission and show validation errors.
* **Accessibility (a11y)**: Screen readers must announce inline errors immediately using `aria-describedby` links.

### Button
* **Description**: Clickable actions.
* **Use Cases**: Submitting forms, triggers, cancel actions.
* **UI/UX Best Practices**:
  - Establish a strong visual hierarchy: Primary (solid), Secondary (muted), Outline, Ghost, and Destructive (red).
  - Use clear, action-oriented verbs for button labels (e.g., "Save changes", "Send invoice", "Delete").
  - Center icons inside buttons next to text or align them on the outer edge depending on visual preference.
* **Dos & Don'ts**:
  - **Do**: Show a spinner and disable the button during API submissions to prevent double clicks.
  - **Don't**: Put multiple primary buttons next to each other; there should only be one main call-to-action per section.
* **Accessibility (a11y)**: Must have a minimum clickable area of 44x44px. Icon-only buttons must have an `aria-label` attribute.

### Input
* **Description**: Text input field.
* **Use Cases**: Usernames, search fields, passwords, numbers, email inputs.
* **UI/UX Best Practices**:
  - Choose the correct `type` attribute (e.g., `type="email"`, `type="password"`, `type="number"`) to enable mobile keyboard optimizations.
  - Ensure focus rings are thick and clearly visible (e.g., `ring-ring` focus outlines).
* **Dos & Don'ts**:
  - **Do**: Provide helper text beneath the input for complex requirements (e.g., "Password must be 8+ characters").
  - **Don't**: Use placeholders as labels—once the user types, the placeholder disappears, leaving them without context.
* **Accessibility (a11y)**: Connect labels to inputs using matching `id` and `htmlFor`.

### Input OTP
* **Description**: Segmented field input for one-time passwords and verification codes.
* **Use Cases**: Two-factor authentication (2FA) verification, security codes.
* **UI/UX Best Practices**:
  - Automatically focus the first character cell on page load.
  - Allow users to copy and paste the entire verification code; split it into slots programmatically.
  - Show a clear cursor blinking indicator inside the active slot.
* **Dos & Don'ts**:
  - **Do**: Group codes visually (e.g. 3 slots - separator line - 3 slots for 6-digit codes) to make readability easier.
  - **Don't**: Block paste commands.
* **Accessibility (a11y)**: Direct focus changes automatically as the user types; read the whole code to screen readers.

### Textarea
* **Description**: Multiline text inputs.
* **Use Cases**: Comments, feedback reviews, descriptions.
* **UI/UX Best Practices**:
  - Set a reasonable default vertical height (e.g., `min-h-[100px]`).
  - Restrict sizing to vertical only (`resize-y`) to prevent users from breaking page container layouts.
* **Dos & Don'ts**:
  - **Do**: Provide a character count indicator below when character limits apply.
  - **Don't**: Let the input auto-grow infinitely if it risks pushing primary footers off screen.
* **Accessibility (a11y)**: Ensure keyboard focus outlines match standard Inputs.

### Select
* **Description**: Popover selection dropdown list.
* **Use Cases**: Choice grids, country selectors, sorting configurations.
* **UI/UX Best Practices**:
  - Use instead of Radio Groups when options exceed 5.
  - Display the currently selected value clearly inside the collapsed select button trigger.
  - Add search filtering inside the select popover if the list is long (see Combobox).
* **Dos & Don'ts**:
  - **Do**: Include a clean placeholder (e.g., "Select a category...").
  - **Don't**: Use a select if a simple boolean Switch or Checkbox is more appropriate.
* **Accessibility (a11y)**: Uses Radix primitives supporting arrow key selection, loops, and search typing.

### Combobox
* **Description**: Floating panel combining popover dropdowns with command text searches.
* **Use Cases**: Tagging systems, timezone picks, country selectors.
* **UI/UX Best Practices**:
  - Filter list choices instantly on typing.
  - Show a "No results found" placeholder state.
  - Highlight matched strings within the results list.
* **Dos & Don'ts**:
  - **Do**: Allow keyboard users to navigate selections with `ArrowDown`/`ArrowUp` and select with `Enter`.
  - **Don't**: Hide scrollbars on results lists with more than 8 options.
* **Accessibility (a11y)**: Set appropriate role labels mapping to input autocomplete systems.

### Checkbox
* **Description**: Form control to select one or multiple items.
* **Use Cases**: Multi-selection filters, agreements, list updates.
* **UI/UX Best Practices**:
  - Always place the checkbox box on the left of its text label.
  - Ensure the clickable area includes both the checkbox and the label.
* **Dos & Don'ts**:
  - **Do**: Support indeterminate states when handling parent/child checkbox structures.
  - **Don't**: Use checkboxes if the selection is mutually exclusive—use Radio Groups instead.
* **Accessibility (a11y)**: Supports keyboard spacebar checks.

### Radio Group
* **Description**: Mutually exclusive single-choice controls.
* **Use Cases**: Payment methods, subscription tiers.
* **UI/UX Best Practices**:
  - Select one option by default to avoid empty forms.
  - List items vertically to make rapid scanning easier.
* **Dos & Don'ts**:
  - **Do**: Use when options are few (under 5); if you have more, use a Select.
  - **Don't**: Place radio buttons horizontally if it risks text wrapping on mobile screens.
* **Accessibility (a11y)**: Wrap inside `role="radiogroup"` with a clear description header.

### Switch
* **Description**: Binary slider toggles.
* **Use Cases**: Dark mode toggling, notification alerts settings.
* **UI/UX Best Practices**:
  - The toggle changes state instantly without requiring a "Save" action.
  - Use clear text labels that accurately indicate states.
* **Dos & Don'ts**:
  - **Do**: Use standard active colors (e.g. green or blue) to show "On".
  - **Don't**: Use switch inside multi-step forms where actions are not immediate—use checkboxes instead.
* **Accessibility (a11y)**: Focus indicator must wrap around the switch thumb.

### Slider
* **Description**: Selection track for numeric values or ranges.
* **Use Cases**: Pricing filters, video timelines, audio volume controls.
* **UI/UX Best Practices**:
  - Show numeric value updates dynamically next to or above the slider handle.
  - Style the slider handle to be large enough for finger touchpoints on mobile screens.
* **Dos & Don'ts**:
  - **Do**: Implement step parameters (e.g. increments of 5 or 10) where applicable.
  - **Don't**: Use sliders for precise inputs (e.g. entering birth year)—provide text inputs instead.
* **Accessibility (a11y)**: Supports keyboard arrow key shifts.

### Label
* **Description**: Text label linked directly to input fields.
* **Use Cases**: Headers of inputs, select dropdowns, toggles.
* **UI/UX Best Practices**:
  - Place directly above the input fields.
  - Indicate required fields visually (e.g., red asterisk `*` or writing `(Optional)`).
* **Dos & Don'ts**:
  - **Do**: Match labels font weight with visual headings hierarchy.
  - **Don't**: Put long description paragraphs inside label components.
* **Accessibility (a11y)**: Bind to inputs via matching `id` and `htmlFor`.

### Toggle & Toggle Group
* **Description**: Push-button binary controls.
* **Use Cases**: Font settings (Bold, Italic, Underline), visual style changes.
* **UI/UX Best Practices**:
  - Toggle states must look visibly different when "pressed" (darker background/shadow).
  - Use simple icons inside individual toggles rather than text.
* **Dos & Don'ts**:
  - **Do**: Group similar toggles within a unified container.
  - **Don't**: Use a toggle if it leads to routing changes—use buttons or links instead.
* **Accessibility (a11y)**: Use `aria-pressed` to indicate selection state.

---

## 3. Overlays & Dialogs

### Dialog
* **Description**: Center-aligned modal window overlaying the user interface.
* **Use Cases**: Creating entries, settings windows, detailed views.
* **UI/UX Best Practices**:
  - Use a semi-transparent dark backdrop overlay (`backdrop-blur` or black overlay) to focus user attention on the modal.
  - Place a clear "Close" icon (usually cross `X` icon) in the top-right corner.
  - Set maximum height and handle overflow content with scroll bars.
* **Dos & Don'ts**:
  - **Do**: Allow closing by clicking on the overlay backdrop or hitting `Esc`.
  - **Don't**: Open modals on top of other modals.
* **Accessibility (a11y)**: Modal dialogs must trap focus inside the modal until dismissed.

### Alert Dialog
* **Description**: Modal dialog that interrupts the user workflow for confirmations.
* **Use Cases**: Deleting data, canceling accounts, discarding changes.
* **UI/UX Best Practices**:
  - Use specific button text (e.g. "Delete Permanently" instead of "Yes").
  - Highlight warning actions in warning colors (red background for destructive buttons).
* **Dos & Don'ts**:
  - **Do**: Auto-focus the "Cancel" action to prevent accidental deletions.
  - **Don't**: Allow dismissals on clicking the backdrop overlay.
* **Accessibility (a11y)**: Uses `role="alertdialog"`.

### Sheet
* **Description**: Slide-out pane from the edges (usually right or left) of the screen.
* **Use Cases**: Cart previews, advanced filters panels, mobile menus.
* **UI/UX Best Practices**:
  - Use standard sizes (e.g. 400px width on desktop) to show complex sidebar layout structures.
  - Animate panels sliding in from the right for content details, or left for navigation menus.
* **Dos & Don'ts**:
  - **Do**: Fade background with an overlay to create clear visual hierarchy.
  - **Don't**: Put long forms with multi-step workflows inside a sheet; use a full page.
* **Accessibility (a11y)**: Traps keyboard focus and closes on pressing `Escape`.

### Drawer
* **Description**: Mobile-optimized slide-over overlay from the bottom.
* **Use Cases**: Mobile menus, quick action triggers.
* **UI/UX Best Practices**:
  - Show a small bar handle at the top indicating drag-dismiss actions.
  - Convert to centered dialogs on desktop view sizes.
* **Dos & Don'ts**:
  - **Do**: Support swipe gestures to dismiss the drawer.
  - **Don't**: Add complex horizontal scrolling elements inside the drawer.
* **Accessibility (a11y)**: Ensure focus is managed properly and overlays match dialog key accessibility constraints.

### Popover
* **Description**: Contextual overlay box floating relative to a trigger element.
* **Use Cases**: Date pickers, inline forms, settings details.
* **UI/UX Best Practices**:
  - Position dynamically to avoid going off screen edges (use Radix Auto-positioning).
  - Keep triggers clear (usually an icon or subtle button).
* **Dos & Don'ts**:
  - **Do**: Close the popover when clicking anywhere outside of its container.
  - **Don't**: Mix up Popovers with Tooltips—Popovers hold interactive elements, while Tooltips are for static text labels.
* **Accessibility (a11y)**: Ensure triggers state their expanded state to screen readers.

### Tooltip
* **Description**: Small text bubble clarifying the function of an icon or button.
* **Use Cases**: Icon buttons (e.g. plus button, edit button), glossary definitions.
* **UI/UX Best Practices**:
  - Keep text limited to short phrases (1-5 words).
  - Show on hover AND on keyboard focus.
* **Dos & Don'ts**:
  - **Do**: Use tooltips for icon-only actions.
  - **Don't**: Place interactive links or buttons inside tooltips.
* **Accessibility (a11y)**: Must use `role="tooltip"` and associate with triggers using `aria-describedby`.

### Hover Card
* **Description**: Popover preview triggered by hovering over an anchor link.
* **Use Cases**: User profile preview on hover of username, link preview cards.
* **UI/UX Best Practices**:
  - Apply a brief hover delay (e.g. 300ms) to prevent cards from popping up during rapid cursor movements.
  - Do not require users to input data inside a hover card.
* **Dos & Don'ts**:
  - **Do**: Fade out smoothly when mouse leaves the trigger or card area.
  - **Don't**: Use on mobile interfaces since hover states do not exist on touch screens.
* **Accessibility (a11y)**: Screen readers must read card info, or the trigger must link directly to the full page.

### Dropdown Menu
* **Description**: List of choices/actions toggled by click of a trigger.
* **Use Cases**: User profile menus, action lists, sorting filters.
* **UI/UX Best Practices**:
  - Order items by popularity; place destructive actions at the bottom in red text.
  - Align dropdown edges with trigger boundaries.
* **Dos & Don'ts**:
  - **Do**: Add icons next to menu items to speed up scan readability.
  - **Don't**: Open dropdowns on hover on desktop; click triggers are much more intentional.
* **Accessibility (a11y)**: Supports arrow keys navigation and matching focus tracking.

### Context Menu
* **Description**: Popover menu activated by a mouse right-click.
* **Use Cases**: Custom actions in tables, image downloads, file manager options.
* **UI/UX Best Practices**:
  - Limit to desktop layouts—touch devices must use long-press equivalents or menu buttons.
  - Style items cleanly with keyboard shortcut hints right-aligned.
* **Dos & Don'ts**:
  - **Do**: Provide separator lines to group related actions.
  - **Don't**: Make actions *only* accessible via context menu—provide an alternate accessible route.
* **Accessibility (a11y)**: Accessible via standard keyboard shortcut combinations.

### Menubar
* **Description**: A horizontal menu bar that displays dropdown lists, modeled after desktop application menus.
* **Use Cases**: Complex file editors, dashboard managers.
* **UI/UX Best Practices**:
  - Use simple labels (File, Edit, View).
  - Open submenus instantly on hover once the bar is active.
* **Dos & Don'ts**:
  - **Do**: Keep visual spacing consistent between categories.
  - **Don't**: Wrap the bar into multiple rows; keep it single-row.
* **Accessibility (a11y)**: Supports keyboard arrow key shifts.

---

## 4. Data Display & Feedback

### Card
* **Description**: Content container with structured headers, body paragraphs, and footer components.
* **Use Cases**: Dashboard summaries, product lists, blog posts, item grids.
* **UI/UX Best Practices**:
  - Maintain consistent grid spacing and internal padding (usually `p-6`).
  - Ensure cards have clean visual distinction (use subtle borders or shadow offsets).
* **Dos & Don'ts**:
  - **Do**: Group primary buttons in the card footer aligned to the right or left consistently.
  - **Don't**: Nest cards within cards unless strictly required for nested layouts.
* **Accessibility (a11y)**: If the whole card is clickable, use a single primary link element and ensure focus outlines cover the card area properly.

### Table
* **Description**: Tabular layout structure for structured data rows.
* **Use Cases**: Transactional databases, admin logs, price plans.
* **UI/UX Best Practices**:
  - Align text columns to the left, numbers to the right, and actions/status indicators to the center or right.
  - Implement sticky headers for vertical scrolling of large tables.
  - Provide clear column sorting headers.
* **Dos & Don'ts**:
  - **Do**: Implement hover rows highlight to help visual scanning across long rows.
  - **Don't**: Cram too many columns; allow columns toggle selection or horizontal scrolls.
* **Accessibility (a11y)**: Use correct table elements (`<thead>`, `<tbody>`, `<th>` with matching scopes).

### Chart
* **Description**: Data visualization panels (integrated with recharts styling).
* **Use Cases**: Dashboard analytics, trend graphs, sales metrics.
* **UI/UX Best Practices**:
  - Use accessible, high-contrast color palettes.
  - Include rich tooltips showing data value details on hover.
* **Dos & Don'ts**:
  - **Do**: Provide a text table fallback of the chart data for screen readers.
  - **Don't**: Rely entirely on color to distinguish lines—use dotted/dashed patterns.
* **Accessibility (a11y)**: Ensure SVGs contain `<title>` tags and aria-labels.

### Calendar
* **Description**: Graphic date picker panel.
* **Use Cases**: Booking platforms, date range selects, event schedule selectors.
* **UI/UX Best Practices**:
  - Clearly highlight current date and the active selection range.
  - Disable invalid dates to prevent user click mistakes.
* **Dos & Don'ts**:
  - **Do**: Use standard abbreviation for weekdays (M, T, W, etc.).
  - **Don't**: Use it for birthday input dates—typing the date in a text field is much faster.
* **Accessibility (a11y)**: Keyboard navigation must navigate grid cells via arrows.

### Avatar
* **Description**: Rounded profile graphic with fallback textual initials.
* **Use Cases**: User profiles, team member lists, author blocks.
* **UI/UX Best Practices**:
  - Use text initials as fallback if the image fails to load or load is delayed.
  - Color code fallback avatars to create distinct identity groups.
* **Dos & Don'ts**:
  - **Do**: Ensure correct alt attributes for the profile image.
  - **Don't**: Render pixelated image scales; use appropriate crop dimensions.
* **Accessibility (a11y)**: Images should have empty `alt` tag if decoration, or descriptive `alt="User Name"` if functional.

### Badge
* **Description**: Tiny visual indicators or label pills.
* **Use Cases**: Status states (e.g. Active, Pending, Error), tag categories, new updates count.
* **UI/UX Best Practices**:
  - Use subtle color schemes (light backgrounds with darker text) instead of super bright colors.
  - Keep character limits very short (1-2 words).
* **Dos & Don'ts**:
  - **Do**: Ensure badges don't look like clickable buttons unless they function as filters.
  - **Don't**: Put critical functional inputs inside badges.
* **Accessibility (a11y)**: If badges represent status, ensure screen readers hear the status context clearly.

### Progress
* **Description**: Horizontal visual loading bar.
* **Use Cases**: File uploads, step wizards, profile completion status.
* **UI/UX Best Practices**:
  - Animate progress indicators to reassure users that the system is active.
  - Include numeric status percentage representation nearby.
* **Dos & Don'ts**:
  - **Do**: Match bar color to completion states (e.g., green for successful finishes).
  - **Don't**: Use progress bars for unknown long-duration loadings—use a spinner/skeleton.
* **Accessibility (a11y)**: Update attributes like `aria-valuenow`, `aria-valuemin`, and `aria-valuemax` in real-time.

### Skeleton
* **Description**: Muted animated placeholder shapes representing loading content layout.
* **Use Cases**: Content containers, list feeds, cards loading states.
* **UI/UX Best Practices**:
  - Match the skeleton shapes to the actual layout containers (e.g. circle for avatars, block for headers).
  - Apply a pulsing animation loop (`animate-pulse`) to show background loading.
* **Dos & Don'ts**:
  - **Do**: Replace the skeleton with the loaded components instantly once data arrives.
  - **Don't**: Keep skeletons flashing infinitely if a loading error occurs—show error notices.
* **Accessibility (a11y)**: Label skeleton container with `aria-busy="true"` and `aria-live="polite"`.

### Alert
* **Description**: A non-blocking banner used to present important, timely information to the user.
* **Use Cases**: Providing contextual feedback (e.g., success, warning, info, error states).
* **UI/UX Best Practices**:
  - Use color-coded states matching the severity (e.g., red for errors, amber/yellow for warnings, green for success, blue for info).
  - Include a relevant icon on the left (e.g., warning triangle, error circle, info bubble, checkmark) to aid visual scanning.
* **Dos & Don'ts**:
  - **Do**: Place alerts near the relevant context or at the top of the main container.
  - **Don't**: Use an Alert if the user must explicitly acknowledge the error before continuing; use an *Alert Dialog* instead.
* **Accessibility (a11y)**: Use `role="alert"` for high-priority alerts (error/warning) and `role="status"` for info or success messages.

### Sonner / Toast
* **Description**: Temporary banner notifications that pop up at screen edges.
* **Use Cases**: Action confirmations (e.g., "Item added to cart", "Message Sent").
* **UI/UX Best Practices**:
  - Provide action links inside toast notifications (e.g., "Undo").
  - Auto-dismiss after 3-5 seconds.
  - Place at the top-right or bottom-right consistently.
* **Dos & Don'ts**:
  - **Do**: Limit concurrent visible toasts to 3 to prevent notification spam.
  - **Don't**: Put critical settings or error descriptions inside toasts—toasts dismiss too fast for study.
* **Accessibility (a11y)**: Ensure toast alerts do not hijack keyboard focus unless user action is required.
