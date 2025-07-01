# ExperDisco

**File:** `overviewjourneynew-canvas.component.ts`  
**Location:** `src/app/modules/engage/canvas-new/overviewjourneynew-canvas/`

======================================================================================================================

## Overview

- `OverviewjourneynewCanvasComponent` is an Angular component that:
    - Provides a dashboard and management interface for marketing journeys (campaigns).
    - Displays journey statistics and key metrics.
    - Supports filtering, searching, and tagging of journeys.
    - Offers actions such as edit, duplicate, delete, stop, and sunset for journeys.
    - Visualizes journey revenue data using charts.
    - Integrates with services for API calls, notifications, and routing.

======================================================================================================================

## Component Metadata

- **Selector:** `app-overviewjourneynew-canvas`
- **Template:** `overviewjourneynew-canvas.component.html`
- **Style:** `overviewjourneynew-canvas.component.css`
- **Imports:**  
  - Angular: `CommonModule`, `FormsModule`, `NgClass`, `DecimalPipe`, `DatePipe`, `RouterLink`
  - Third-party: `NgSelectModule`, `NgxDaterangepickerBootstrapDirective`, `NgxPaginationModule`
  - Charting: `Chart.js`
  - Date libraries: `dayjs`, `moment`
  - Notifications: `ToastrService`
  - API: `ApiService`

======================================================================================================================

## Key Properties

### State & UI

- `list`, `overview`: Toggles between list and overview views.
- `all`, `running`, `stopped`, `sunset`, `draft`, `deleted`: Flags for journey status cards.
- `search`, `isSearched`, `filtertags`, `isfiltertags`: Search and filter state.
- `p`, `JPageDataObj`, `JLastPage`, `JPageCount`, `journeyItemCount`: Pagination and data caching.
- `cardNavigator`: Tracks which status card is active.
- `modalAction`: Stores modal dialog configuration for confirmation actions.
- `showCalendarInput`, `myDateRange`, `pickerDirective`: Date range picker state.

### Journey Data

- `mytemplates`: List of journey templates (campaigns).
- `journeyCampaignName`: Stores the currently selected journey for actions.
- `tags`, `tagsList`, `tagsList1`, `DisplayFirstTag`, `firstTag`, `newTags`: Tag management.
- `allocated_type`, `portArray`: Port/channel allocation for journeys.

### Metrics & Statistics

- `metrics`: Array of key metrics (users engaged, campaigns, conversions, revenue).
- `userengagedcount`, `totalcampaigns`, `totalconversion`, `totalrevenue`: Overall metrics.
- Channel-specific metrics:  
  - Push: `pushuserengagevalue`, `pushcampaignsvalue`, `pushconversionvalue`, `pushrevenuevalue`, etc.
  - SMS, Email, InApp, Onsite, WebPush: Similar properties for each channel.

### Charting

- `chartLabels`, `overallRevenue`, `journeyRevenue`, `myChart`: Chart.js data and instance.
- `averageOverallRevenue`, `averageJourneyRevenue`, `averagePercentage`: Calculated averages for display.

======================================================================================================================

## Lifecycle Hooks

- **ngOnInit:**  
  - Reads query parameters for filtering and navigation.
  - Initializes the view (list or overview) and fetches initial data.
  - Sets up date and tag state.

======================================================================================================================

## Major Functionalities

### 1. **Journey Listing & Pagination**
- Fetches journey templates with support for search, filters, tags, and pagination.
- Caches paginated data for performance.
- Supports status-based navigation (all, running, stopped, sunset, draft, deleted).

### 2. **Journey Actions**
- **Edit:** Navigates to the journey creation page for editing.
- **Duplicate:** Duplicates a journey and updates the list.
- **Delete:** Deletes a journey after confirmation.
- **Stop/Sunset:** Changes the status of a journey (stop or sunset) after confirmation.

### 3. **Tag Management**
- Fetches, displays, adds, and removes tags for journeys.
- Supports saving new tags and updating journey tags via API.

### 4. **Search & Filtering**
- Supports searching by journey ID or name.
- Filters journeys by tags and status.
- Integrates with a date range picker for time-based filtering.

### 5. **Overview Dashboard**
- Displays overall and channel-specific metrics.
- Loads and visualizes journey revenue data using Chart.js.
- Calculates and displays averages and percentages.

### 6. **Chart Visualization**
- Renders a line chart of journey revenue as a percentage of overall revenue.
- Supports downloading the chart as an image.
- Adds a benchmark line to the chart for comparison.

### 7. **Modal Dialogs**
- Handles confirmation modals for delete, stop, and sunset actions using Bootstrap modals.

======================================================================================================================

## Key Methods
 _________________________________________________________________________________________________________________________
| Method                                  | Description                                                                   |
|-----------------------------------------|-------------------------------------------------------------------------------|
| `getJourneyTemplates()`                 | Fetches paginated journey templates based on page number and various filters. |
| `navigator(text)`                       | Switches between overview and list views.                                     |
| `cardnavigator(text)`                   | Switches b/w status (e.g., all, running,etc) and fetches corresponding data.  |
| `deleteJourney(template)`               | Deletes a journey after confirmation.                                         |
| `editJourney(template)`                 | Navigates to the journey editing page.                                        |
| `duplicateJourney(template)`            | Duplicates a journey and updates the list.                                    |
| `changeStatusJourney(template, status)` | Changes the status of a journey (e.g., stop, sunset).                         |
| `stopjourney(template, status)`         | Stops a journey and updates its status.                                       |
| `fetchTags(journey_id)`                 | Fetches tags associated with a specific journey.                              |
| `saveTag()`                             | Saves new or updated tags for a journey.                                      |
| `getJourneyOverview()`                  | Loads overall and channel-specific metrics for the dashboard.                 |
| `getJourneyRevenueData()`               | Loads revenue data for chart visualization based on the selected date range.  |
| `createLineChart()`                     | Renders the revenue line chart using Chart.js.                                |
| `calculateAverage()`                    | Calculates averages for revenue and other metrics.                            |
| `onDateRangeSelection()`                | Handles selection of a date range for filtering data.                         |
| `clearDate()`                           | Clears the selected date range filter.                                        |
| `toggleCalender(event?)`                | Toggles the visibility of the date range picker.                              |
| `openConfirmationModal()`               | Opens a dialog for confirmation before performing actions like delete, sunset |

======================================================================================================================

## Usage Example

```html
<app-overviewjourneynew-canvas></app-overviewjourneynew-canvas>
```

======================================================================================================================

## Notes

- The component is highly interactive and stateful, designed for a dashboard/admin interface.
- Integrates deeply with backend APIs for journeys, tags, and revenue data.
- Uses Chart.js for advanced charting and visualization.
- Supports advanced filtering, searching, and tag management for large-scale campaign operations.
- Designed for marketing automation and campaign management use cases.

======================================================================================================================

## Related Files
 __________________________________________________________________________________________________________
| File/Library                               | Purpose/Usage                                               |
|--------------------------------------------|-------------------------------------------------------------|
| `overviewjourneynew-canvas.component.html` | Template for rendering the dashboard and list UI.           |
| `api.service.ts`                           | Handles backend API calls for journeys, tags, and revenue.  |
| `ngx-daterangepicker-bootstrap`            | Provides date range picker integration.                     |
| `chart.js`                                 | Used for chart rendering and visualization.                 |

======================================================================================================================
