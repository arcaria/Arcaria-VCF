# Changelog

All notable changes to this project will be documented in this file.

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
