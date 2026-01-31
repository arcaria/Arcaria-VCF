# Changelog

All notable changes to this project will be documented in this file.

## v0.0.10

- **New Feature: X/Y/Z Plot System**:
  - Added a comprehensive X/Y/Z Plot system to the sidebar.
  - Supports iterating over any parameter (Steps, CFG, Model, etc.).
  - **Prompt S/R** (Search/Replace): Iterate over prompts by replacing specific text.
  - **Negative Prompt S/R**: Iterate over negative prompts search/replace.
  - **Wildcard Expansion**: Automatically expands wildcards (e.g. `__colors__`) into all their values when used in a Plot Axis.
  - **Batch Generation**: Generates combinations and submits them as a batch to the queue.
  - **Job Details**: Updated to show "Original Prompt" vs "Final Prompt" and specific plot settings for each job.
- **Wildcard Manager Improvements**:
  - Fixed "undefined items" bug in the dashboard dropdown.
  - Improved Wildcard parsing to correctly handle Prefixes and Suffixes during Plot expansion.
- **UI/UX**:
  - Added "X/Y/Z Plot" toggle and configuration panel to the sidebar.
  - Improved Job Details modal metadata display.

## v0.0.9 (Wildcards & UI Polish)

### Added

- **Wildcard System**:
  - **Manager**: Full CRUD interface for creating and managing wildcard lists (e.g., `__colors__`).
  - **Click-Outside**: Picker and Modals now support click-outside-to-close for faster workflows.
  - **Recursion**: Parser now supports nested wildcards (e.g., a wildcard value that contains another wildcard).
  - **Prefix/Suffix**: Checkboxes to auto-wrap wildcard values (e.g., `(value)` or `value,`).
  - **Quick Insert**: Dropdown menu in the Prompt area to quickly insert available wildcards.
- **UI Improvements**:
  - **Split-Pane Managers**: Preset and Style managers now use a consistent split-pane layout (List on left, Editor on right).
  - **In-Modal Editing**: Presets can now be edited directly within the Manager using the dynamic FormEngine.
  - **Scroll Fixes**: Fixed double scrollbars in all managers; content now scrolls internally while header/footer stay fixed.

### Removed

- **Redundant Buttons**: Removed "Save Current Settings" from main sidebar (use "Copy Current" in Preset Manager) and "Manage" from Wildcard dropdown.

### Improved

- **Visuals**: Updated Wildcard "Quick Apply" icon to a terminal style (`>_`).
- **Performance**: Optimized list rendering for large wildcard collections.

## v0.0.8 (Gallery Modal & Refinements)

### Added

- **Gallery Refinements**:
  - **Tree-Based Loading**: Switched to GitHub Tree API for recursive scanning of all folders. Significantly faster for large repos and enables global sorting.
  - **Date Navigator**: Replaced simple dropdown with a Date Navigator (< > buttons) and a Quick Select popover with search.
  - **Stats**: Added global image usage counters (Total / In View).
  - **Smart Date Persistence**: The gallery now remembers your date selection while navigating.
- **Gallery Modal**:
  - **Sidecar Metadata**: Automatically detects and loads `image.json` if it exists next to the image.
  - **Detail View**: Clicking a card opens a modal with a large preview and full metadata (prompt, model, params).
  - **Reuse Settings**: "Use This" button in the modal restores all generation parameters from the image metadata back to the form.
  - **Download**: Direct download support from the modal.

### Improved

- **Pagination**: Moved pagination controls to the top of the gallery for easier access.
- **Visuals**: Enhanced "Glass" styling for all gallery elements.

## v0.0.7 (Gallery Overhaul)

### Added

- **Gallery Pagination**: Implemented optimized client-side pagination for gallery grids.
- **Improved Loading State**: Visual spinner for better UX during GitHub API calls.
- **Format Support**: Gallery now supports `.webp`, `.jpg`, and `.png`.
- **Enhanced Interactions**:
  - **Direct Open**: Opens full-resolution image in new tab.
  - **Download Button**: Download image with original filename.

### Fixed

- **Private Repo Access**: Fixed broken images for Private Repositories using "Blob Fetching" strategy.
- **v6 Regression**: Fixed `clearBtn` reference error.

## v0.0.6 (Fixes)

### Fixed

- **Discord Thread Persistence**: Logic updated to use Local Time instead of UTC for daily threads. This prevents thread duplication/mismatch when dates shift in different timezones. Also improved error logging for webhook responses.
- **Webhook URL Hygiene**: Added automatic sanitization of Discord Webhook URLs. If a user pastes a URL containing an existing `thread_id` or `wait` parameter, it is now stripped before applying Smart Thread logic, preventing accidental renaming of old threads.

### Improved

- **Settings Overhaul**: Completely redesigned the Settings modal with a **Tabbed Interface** (General, Generation, Connections). Added **Manual Save Buttons** for configuration tabs to prevent accidental changes.
- **Connection Monitoring**: The app now periodically checks the connection to the AI Horde (every 30s) and updates the status indicator and User Kudos automatically. Includes a new **Heartbeat Interval** setting.
- **Auto-Update Check**: Added an automatic version checker that notifies users when a new version of the webapp is hosted/deployed.

## [v0.0.5] - Released - (Data Management & UI Polish)

- **Data Management System**:
  - **Export**: Full JSON backup of Settings, History, Presets, and Forms.
  - **Fine-grained Control**: Checkboxes to select specific data categories to export.
  - **Import**: Restore data from backup with safety warnings to prevent accidental overwrites.
  - **Critical Styling**: The Data Management section uses a distinct red theme to indicate sensitive operations (API Keys).
- **Settings UI**:
  - **Accordions**: Settings sections are now collapsible `<details>` groups for a cleaner interface.
  - **Validation**: Added confirmation dialogs for all destructive actions.

## [v0.0.4] - Released - (Settings Overhaul)

### Improved

- **Horde Manager Upgrade**: Added support for multiple API Keys.
- **API URL Manager**: Users can now configure custom Horde endpoints.
  - Added support for multiple Webhooks.
  - **Smart Threading**: Automatically creates daily threads in Forum Channels.
  - **Channel Types**: Explicit support for Text vs Forum channels.
- **GitHub Integration**: Added support for multiple Profiles (PAT/Repo pairs).
- **Edit Capability**: All settings (Keys, URLs, profiles) can now be edited in-place.
- **Dry Run Fix**: Generating with `dry_run: true` now correctly reports cost estimates without creating broken job entries.
- **UI Refresh**: Migrated Settings to a dedicated "Managers" architecture.

## [v0.0.3] - Released

### Fixed

- **Resume Tracking**: Fixed logic where "Resume" button would immediately switch back to "Error" status if no workers were available. It now forces "Waiting" status.
- **Queue Persistence**: Added QueueManager saving/loading from LocalStorage. The queue now survives page refreshes.
- **Private Data Storage**: Fixed bug where "User Only" fields (like Notes, API Keys) were not being saved to Job History.

### Improved

- **Discord Integration**:
  - Now sends a permanent Image Attachment (instead of temporary URL).
  - Attaches full Job Metadata as JSON.
  - Includes Rich Embed with generation parameters.
  - Logic improved to auto-use Form Notes or Personal Notes as the caption, only prompting if both are empty.
- **Queue UI**: Added live counters (badges) to the filter buttons (e.g. "Waiting 3").

## [v0.0.2] - Released

### Added

- **Pending Requests Module (Queue)**:
  - **Smart Queue List**: Optimized rendering with DOM-diffing (no flickering).
  - **State Filters**: Filter jobs by All, Waiting, Processing, Finished, or Error.
  - **Settings**: Configurable polling interval via settings modal.
  - **Resume Tracking**: Ability to force-resume tracking for jobs marked as "Error" (e.g. Impossible generation).
- **Job Details Modal**:
  - **Tabs**: "Overview" for main content, "Debug JSON" for raw API data inspection.
  - **Actions Toolbar**:
    - **Reuse Settings**: Restore prompts, model, and form parameters to the generator.
    - **Save Preset**: Save a job's configuration as a reusable preset.
    - **Download**: Direct image download.
    - **Cancel/Delete**: API Cancellation (DELETE Request) + Local removal.
  - **Personal Notes**: Text area to save private notes for each job (persisted to storage).
  - **Deep Linking**: Buttons to open Horde `check` and `status` endpoints in new tabs.

## [v0.0.1] - Released

### Added

- **Core Structure**: Single-file HTML application `antigravity_horde.html`.
- **Dynamic Form Engine**: Custom JSON-based form builder with live preview.
- **Generation**: AI Horde API integration with Queue/Polling system.
- **Managers**:
  - **Styles**: Create and apply prompt modifier presets.
  - **Presets**: Save full form states (model, sliders, prompts) and restore them.
- **Integrations**:
  - **GitHub**: Auto-upload images to private repo gallery.
  - **Discord**: Manual "Send to Discord" webhook integration.
- **UI/UX**:
  - **Glassmorphism**: Premium dark UI aesthetics.
  - **Notifications**: Custom non-blocking toast system.
  - **Dialogs**: Custom Promise-based modal dialogs replacing native alerts.
  - **Validation**: Smart inputs with character counting and Negative Prompt separation (`###`).
