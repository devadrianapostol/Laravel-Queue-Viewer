##Laravel Queue Viewer

A PhpStorm plugin for inspecting Laravel queue contents directly in a tool window. Fetches jobs asynchronously to keep the UI responsive—perfect for debugging without blocking your flow.
Features

Dynamic Queue Selection: Dropdown populated from your project's queues (e.g., via jobs table).
Job Table: Columns for ID, Queue, Class, Attempts, Created At, and Payload Preview (truncated JSON for quick scans).
Async Loading: PHP execution runs in background threads; status updates keep you informed.
Auto-Setup: Injects a view-queue.php script on first use (adds to .gitignore if needed).
Laravel Detection: Only activates in projects with artisan.

Assumes database driver; extend for Redis in the script.
Installation

Build the plugin: Run ./gradlew build in the project root.
Install in PhpStorm: Preferences > Plugins > Gear Icon > Install Plugin from Disk > Select build/distributions/*.zip.
Restart PhpStorm.
Open: View > Tool Windows > Laravel Queue (or menu: View > Open Laravel Queue).

Usage

Open the tool window—queues load automatically.
Select a queue from the dropdown; jobs populate the table async.
Refresh button reloads everything.
Payload previews show arg snippets—click rows for full inspection? (Future idea.)

Example output:

ID,Queue,Class,Attempts,Created At,Payload Preview
1,default,App\SendEmailJob,0,2025-11-24 10:00,"{""email"":""user@example.com"",...}"

Screenshots
(Add your own: Tool window with dropdown and table)
Development

Kotlin + IntelliJ SDK (PhpStorm edition).
Key files: LaravelQueueToolWindowFactory.kt (UI/logic), view-queue.php (injected backend).
Test: ./gradlew runIde in sandbox.
Extend: Add delete buttons or Redis support in script.

License
MIT – fork away.
