<img width="550" height="313" alt="Preview" src="https://github.com/user-attachments/assets/c0e100e2-2f23-4aed-818e-bdf44792ed56" />
# Glitch Screensaver

A Windows screensaver that plays a GIF with randomized, never-repeating glitch effects: block cut & relocate, row/pixel displacement, color inversion, channel shift, CRT scanlines, resolution-loss pixelation, and rare "no signal" static bursts.

## Quick Install (use your own GIF)

1. Delete `glitch.gif`.
2. Add whatever GIF you want to this folder — no need to rename it.
3. Run `Install.exe`.

Done. `Install.exe` self-elevates via UAC, installs the screensaver, and picks up your GIF automatically — whatever it's named, no renaming to `glitch.gif` required. Keep just one GIF in the folder so there's no ambiguity about which one gets installed.

## What each file is

| File | Purpose |
|---|---|
| `GlitchScreensaver.scr` | The compiled screensaver itself. |
| `Install.exe` | One-click installer — copies the `.scr` to `C:\Windows\System32` (required for it to show up in the Windows screensaver dropdown), copies your GIF + `GlitchSettings.ps1` to `C:\Program Files\GlitchScreensaver`, and registers a normal Windows uninstaller in Apps & Features. |
| `GlitchSettings.ps1` | Settings GUI — sliders and toggles for every glitch effect, an overall glitch % slider, and Save/Preview/Cancel buttons. Also opens automatically if you click "Settings..." in the Windows screen saver control panel. |
| `Program.cs` | Source code for `GlitchScreensaver.scr`, in case you want to rebuild it (e.g. after editing an effect). Build command is in the header comment of the file. |
| `glitch.gif` | The default GIF that plays. Replace with any GIF you like (see Quick Install above). |

## After installing

- **Change settings:**  Right-click desktop → Personalize → Lock screen → Screen saver settings (or search "Change screen saver" in the Start menu) → choose **Settings...*, Adjust sliders/toggles, hit **Preview** to test full-screen, then **Save**. No reinstall or rebuild needed — it just rewrites a settings file that the `.scr` reads on startup.
- **Set as your screensaver:** Right-click desktop → Personalize → Lock screen → Screen saver settings (or search "Change screen saver" in the Start menu) → choose **GlitchScreensaver** from the dropdown.
- **Uninstall:** Settings → Apps → Installed apps → find **GlitchScreensaver** → Uninstall. It's a normal Windows uninstall, nothing to hunt for manually.

## Swapping the GIF later

If you want to change the GIF after you've already installed, you'll first need to uninstall the previously installed screensaver with Settings → Apps → Installed apps → find **GlitchScreensaver** → Uninstall & put the new one in this folder (replacing the old), then run `Install.exe` again.

## Notes

- `Install.exe` only installs the already-built `GlitchScreensaver.scr` — it doesn't compile `Program.cs`. You only need to touch `Program.cs` if you're changing the effect code itself.
- Settings are stored per-user in `%LOCALAPPDATA%\GlitchScreensaver\glitch.settings.ini`, so they save fine without admin rights even though the `.scr` lives in System32.
