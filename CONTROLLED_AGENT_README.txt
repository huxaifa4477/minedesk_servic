MineDesk / RustDesk - Controlled Side (Employee Agent)
======================================================

Changes applied:
1. No tray icon on Windows (completely disabled)
2. No main UI window on Windows (headless)
3. Permanent password only (cannot be changed after set)
4. Approve mode = password only (no confirmation popups / click-to-accept)
5. Remote printer disabled
6. ID change disabled

HOW TO BUILD (on Windows machine with Rust + dependencies)
----------------------------------------------------------
This project needs the full RustDesk build environment (Rust, vcpkg, Flutter or Sciter, etc.).

See official docs:
https://rustdesk.com/docs/en/dev/build/

Typical Flutter Windows build (simplified):
  python build.py --flutter --hwcodec

Or follow the CI workflow in .github/workflows/flutter-build.yml

HOW TO INSTALL & RUN AS SERVICE
-------------------------------
After you have the .exe (e.g. rustdesk.exe or minedesk.exe):

1. Run as Administrator once to install the service:
     rustdesk.exe --install

   Or:
     rustdesk.exe --install-service

2. Set permanent password (Administrator, only once):
     rustdesk.exe --password YOUR_STRONG_PASSWORD

3. Get the ID:
     rustdesk.exe --get-id

   Note the ID down. Manager will use: ID + permanent password.

4. Service starts automatically with Windows.
   No window, no tray will appear.

5. From manager PC use normal RustDesk client:
   - Enter the ID
   - Enter the permanent password
   - Connect (full control + screen)

NOTES
-----
- Permanent password cannot be changed from UI or later (locked by design).
- No approval dialog will appear on employee PC.
- Public RustDesk servers are used by default (no self-host needed).
- Only the controlled (employee) side is modified. Manager uses stock client.

