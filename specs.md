# AgentHub Platform Specification

## Product and Technical Constraints

- AgentHub is a SaaS administration interface for companies to rent pre-configured AI agents and equip them with capabilities called skills.
- Build the frontend with semantic HTML, Tailwind CSS loaded from its CDN, and vanilla TypeScript; do not use a frontend framework.
- This deliverable is frontend-only: do not add backend services, API calls, authentication flows, or persistent server data. Use realistic hardcoded sample data and local interaction state.
- Provide six sections reachable from a persistent sidebar: Dashboard, User Management, Agent Management, Skills, Agent Contracts, and Error Log.
- Provide a top-bar theme toggle that switches the whole interface between light and dark mode using Tailwind `dark:` utilities. Keep the chosen mode while navigating between sections during the current page session.
- Ensure navigation, menus, expandable skill lists, dialogs, and theme controls are keyboard-operable, have accessible names, and expose appropriate focus states. Dialogs must identify themselves to assistive technology and support Escape to close.
- Use responsive layouts that remain usable on narrow screens. Keep tables readable by allowing horizontal overflow or an equivalent compact layout rather than clipping content.

## 1. Dashboard

- Show four metric cards in a responsive 2-by-2 grid on the dashboard: total revenue generated, total discount and coupon losses, number of active agents across all clients, and number of agents currently flagged as failing.
- Each metric card includes a distinct icon, a visible label, and a hardcoded formatted value; use a different accent color for each metric type and a subtle shadow.
- Place a full-width weekly activity chart placeholder beneath the cards, with a dashed border and a centered label; it must remain legible and full-width on mobile.
- Mark the Dashboard navigation item as the current section and provide a clear page title and supporting date/context label.

## 2. User Management

- Render a table of registered users with name, email, plan, and status columns, populated with hardcoded sample records.
- Include a per-row vertical-ellipsis action button that opens a compact dropdown containing at least “View detail” and “Delete”.
- Selecting “View detail” opens an overlay modal containing the selected user's full record; close it with a labeled close button, backdrop click, or Escape.
- Selecting “Delete” must present a confirmation step before removing that user from the visible in-memory list; canceling leaves the record unchanged.

## 3. Agent Management

- List registered agents with agent name, owner, current status (active, inactive, or failing), and associated skills.
- Hide each agent's skill list by default; an accessible expand control reveals the complete list with a smooth transition and updates its expanded/collapsed state for assistive technology.
- Give each agent a row action dropdown with “Configure” and “Delete”; “Configure” opens a modal that displays that agent's system prompt.
- Require confirmation before removing an agent from the visible in-memory list, and show status with text as well as color so it is not conveyed by color alone.

## 4. Skills

- Present a catalog of available skills, each with a name, short description, and count of agents that currently have the skill enabled.
- Include an in-panel explanation that a skill is an attachable agent capability, such as web browsing, document reading, or calendar management.
- Provide a per-skill action dropdown with “View detail” and “Delete”; the detail view shows the skill's full description and enabled-agent count.
- Require confirmation before deleting a skill from the visible in-memory catalog, and ensure the catalog adapts to narrow screens.

## 5. Agent Contracts

- Show active and past rental contracts in a table with client, rented agent, contracted skills, contract dates, and total amount paid.
- Provide a per-row action dropdown with “View detail” and open a modal for the selected contract.
- The contract detail modal includes the complete contract breakdown, including an itemized list of contracted skills and each skill's individual price, plus the total paid.
- Distinguish active and past contracts with readable status text and make all contract data available without relying on hover.

## 6. Error Log

- List hardcoded agent execution errors with timestamp, agent name, error type, and a short description.
- Categorize each error with color-coded severity/type badges while retaining readable text labels for accessibility.
- Provide a per-entry action dropdown with “View detail” and “Mark as resolved”. The detail modal shows the full error trace for the selected entry.
- Marking an entry resolved updates its visible state in memory and communicates the resolved status without removing the log entry.

## Shared Interaction and Presentation

- Sidebar navigation changes the visible section without a page reload and remains available across all sections; indicate the active destination.
- All row action dropdowns open and close predictably, close on Escape or outside click, and avoid being clipped by responsive containers.
- Modal overlays close using their labeled close control, backdrop click, and Escape; keep keyboard focus within an open modal and return focus to its trigger when dismissed.
- Theme switching applies consistently to navigation, top bar, page content, tables, dropdowns, and dialogs, with sufficient contrast in both modes.

## Prototype Completion Criteria

### Navigation & Layout (3 criteria)

1. **Sidebar Navigation**: Clicking each of the six sidebar items (Dashboard, User Management, Agent Management, Skills, Agent Contracts, Error Log) changes the visible section without a page reload.
2. **Active Indicator**: The currently active section is visually marked in the sidebar navigation with distinct styling or highlighting.
3. **Persistent Navigation**: The sidebar remains visible and fully functional when navigating between all six sections.

### Theme Toggle (2 criteria)

4. **Light/Dark Mode Switch**: The theme toggle button in the top bar switches the entire interface between light and dark modes using Tailwind `dark:` utilities.
5. **Theme Persistence**: The selected theme persists across navigation between sections during the current page session (does not reset when changing sections).

### Dashboard (4 criteria)

6. **Four Metric Cards Rendered**: All four metric cards display on the dashboard: total revenue, discount/coupon losses, active agents count, and failing agents count.
7. **Card Styling & Icons**: Each metric card has a distinct accent color, an icon, a visible label, and a hardcoded formatted value with subtle shadow.
8. **Chart Placeholder**: A full-width weekly activity chart placeholder with dashed border and centered label is visible below the metric cards.
9. **Dashboard Context**: The page displays a clear title (e.g., "Dashboard") and supporting date/context label.

### User Management Table & Actions (6 criteria)

10. **User Table Rendered**: The user table displays all columns (name, email, plan, status) with at least 3 hardcoded sample user records.
11. **Row Action Button**: Each user row has a vertical-ellipsis action button that opens a dropdown menu.
12. **View Detail Action**: Selecting "View detail" from the dropdown opens a modal overlay showing the selected user's full record.
13. **User Detail Modal Close**: The user detail modal closes when clicking the labeled close button, clicking the backdrop, or pressing Escape.
14. **Delete Confirmation**: Selecting "Delete" displays a confirmation dialog requiring explicit confirmation before removal.
15. **Delete Execution**: Confirming deletion removes the user from the visible in-memory list; canceling leaves the record unchanged.

### Agent Management Table & Expand/Collapse (6 criteria)

16. **Agent Table Rendered**: The agent table displays agent name, owner, status, and associated skills for at least 3 hardcoded agents.
17. **Status Text & Color**: Agent status (active, inactive, failing) is conveyed by both text label and color (not color alone).
18. **Skill List Collapsed by Default**: Each agent's skill list is hidden by default.
19. **Skill List Expand Control**: Each agent row has an accessible expand control that reveals the skill list with smooth transition.
20. **Skill List Accessibility**: The expand control updates its expanded/collapsed state for assistive technology (ARIA attributes).
21. **Configure Modal**: Selecting "Configure" from the agent action dropdown opens a modal displaying that agent's system prompt.
22. **Agent Delete Confirmation**: Selecting "Delete" displays a confirmation dialog before removing the agent from the in-memory list.

### Skills Catalog (3 criteria)

23. **Skills Displayed**: The skills section shows at least 3 skills with name, short description, and count of agents using that skill.
24. **Skill Info Panel**: An in-panel explanation appears stating that a skill is an attachable agent capability (e.g., web browsing, document reading).
25. **Skill Action Dropdown**: Each skill has an action dropdown with "View detail" and "Delete" options; "View detail" opens a modal with full description and agent count.

### Agent Contracts Table (3 criteria)

26. **Contracts Table Rendered**: The contracts table displays client, rented agent, contracted skills, contract dates, and total amount paid for at least 2 contracts.
27. **Contract Status Distinction**: Active and past contracts are visually and textually distinguished (status labels visible without hover).
28. **Contract Detail Modal**: Selecting "View detail" opens a modal with itemized skill breakdown, individual prices, and total amount paid.

### Error Log (3 criteria)

29. **Error List Rendered**: The error log displays at least 3 hardcoded errors with timestamp, agent name, error type, and short description.
30. **Severity Badges**: Each error is categorized with a color-coded severity/type badge that includes readable text label (not color alone).
31. **Error Resolution**: The "Mark as resolved" action updates the entry's visible state in memory and displays the resolved status without removing the log entry.

### Dropdowns (2 criteria)

32. **Dropdown Open/Close**: All row action dropdowns (User, Agent, Skill, Contract, Error Log) open predictably and close on Escape key or outside click.
33. **Dropdown Clipping Prevention**: Dropdowns avoid being clipped by responsive containers and remain fully visible on narrow screens.

### Modal Dialogs (3 criteria)

34. **Modal Close Methods**: All modal overlays close via labeled close button, backdrop click, or Escape key.
35. **Focus Management**: Keyboard focus remains within an open modal during interaction.
36. **Focus Return**: When a modal is dismissed, focus returns to its trigger button.

### Responsive Design (2 criteria)

37. **Mobile Table Readability**: Tables remain readable on narrow screens (≤480px) via horizontal overflow, compact layout, or equivalent approach without content clipping.
38. **Mobile Chart Legibility**: The dashboard chart placeholder remains legible and full-width on mobile screens.

### Accessibility (2 criteria)

39. **Keyboard Operability**: All interactive elements (navigation, buttons, menus, dropdowns, dialogs, theme toggle) are fully keyboard-operable with visible focus states.
40. **Dialog Accessibility**: Modals identify themselves to assistive technology with appropriate ARIA attributes (role, labelledby).

### Contrast & Theming (1 criterion)

41. **Theme Contrast**: Text and UI elements maintain sufficient contrast in both light and dark modes per WCAG AA standards.
