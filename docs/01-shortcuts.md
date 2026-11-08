# Shortcuts and interactions

Checked against official references on 2026-11-08. Mappings below are **DOCUMENTED** defaults unless specifically marked otherwise; the Paint/Notepad legacy app-source gap is identified below. Their execution on this Zenbook is **UNKNOWN** unless historical evidence is identified. No destructive shortcuts were exercised. `Win` means the Windows-logo key; `+` means keys held together. Remapping, Fn mode, app focus, keyboard layout and policy can change behavior.

## Start, shell, search and system

Source: [Microsoft Windows shortcut reference][windows]. These are concise factual mappings, grouped by context.

| Shortcut | Action | Behavior | Conditions | Source |
|---|---|---|---|---|
| Win / Ctrl+Esc | Start | Toggle menu | Shell | [MS][windows] |
| Win+S / Win+Q | Search | Focus search | Win+Q instead invokes Click to Do on eligible Copilot+ PCs; results depend on indexing/cloud policy | [MS][windows], [AI keys][aikeys] |
| Win+E | Explorer | Open file browser | Shell | [MS][windows] |
| Win+R | Run | Enter program/path/URI | Execution permissions still apply | [MS][windows] |
| Win+I | Settings | Open app | Page availability varies | [MS][windows] |
| Win+X | Quick Link | Administrative shortcut menu | Same as Start right-click | [MS][windows] |
| Win+A | Quick Settings | Connectivity/audio/display controls | Windows 11; differs from Win10 | [MS][access] |
| Win+N | Notifications | Open notifications/calendar | Notification policy applies | [MS][windows] |
| Win+W | Widgets | Open board | Web Experience/account/network affect content | [MS][windows] |
| Win+L | Lock | Lock session | Authentication required to return | [MS][windows] |
| Ctrl+Alt+Delete | Security screen | Lock/sign out/Task Manager options | Secure desktop; differs over RDP | [MS][windows] |
| Ctrl+Shift+Esc | Task Manager | Open process monitor | Some details need elevation | [MS][windows] |
| Win+Pause | About | Open system information page | Pause may need Fn | [MS][windows] |
| Win+F | Feedback | Launch Feedback Hub | App/account availability | [MS][windows] |
| Win+Ctrl+Q | Quick Assist | Remote-help app | Network and consent needed | [MS][windows] |
| Win+K | Cast | Discover wireless displays | Miracast hardware/receiver required | [MS][windows] |
| Win+P | Project | Choose display topology | Duplicate/extend/PC/second only | [MS][windows] |
| Win+Alt+B | HDR | Toggle HDR | Supported display/graphics and software | [MS][windows] |
| Win+Ctrl+Shift+B | Display recovery | Request display-stack recovery | Brief blank/beep possible; not a hardware diagnosis | [MS][windows] |
| Win+C / Copilot key | Copilot/search | Configurable launch target | Installed app, policy and current build; see AI catalog | [MS][windows] |
| Win+J | Recall | Open Recall | Eligible supported PC and rollout; not generic Windows | [MS][windows] |

## Window management and virtual desktops

| Shortcut | Action | Behavior | Conditions | Source |
|---|---|---|---|---|
| Alt+Tab / Alt+Shift+Tab | Switch window | Forward/backward | Hold Alt for picker | [MS][windows] |
| Ctrl+Alt+Tab | Persistent picker | Choose with arrows/Enter | Picker remains after release | [MS][windows] |
| Alt+Esc | Cycle | Open-order navigation | Desktop windows | [MS][windows] |
| Alt+F4 | Close | Close active window | Desktop with no window: power dialog | [MS][windows] |
| Alt+Space | Window menu | Move/size/minimize commands | App window supports menu | [MS][windows] |
| Win+D | Desktop | Hide/restore windows | Toggle | [MS][windows] |
| Win+, | Peek | Show desktop while held | Desktop shell | [MS][windows] |
| Win+M / Win+Shift+M | Minimize/restore | All windows / restore minimized | Window support varies | [MS][windows] |
| Win+Home | Isolate window | Minimize/restore others | Active desktop window | [MS][windows] |
| Win+Up / Win+Down | Maximize/minimize | Down can restore first | Current window state matters | [MS][windows] |
| Win+Left / Win+Right | Snap | Place window to side | Snap enabled | [MS][windows] |
| Win+Z | Layout picker | Choose Snap layout | Display size/layout eligibility | [MS][windows] |
| Win+Alt+Up / Down | Half-screen Snap | Top/bottom | Supported Windows 11 layout | [MS][windows] |
| Win+Shift+Up | Stretch vertically | Keep width | Resizable desktop window | [MS][windows] |
| Win+Shift+Down | Restore | Undo stretch/maximize/Snap state | State dependent | [MS][windows] |
| Win+Shift+Left / Right | Move monitor | Send window to adjacent display | Multiple displays | [MS][windows] |
| Win+Tab | Task View | Windows and desktops overview | Shell | [MS][windows] |
| Win+Ctrl+D | New desktop | Create and switch | Virtual desktops | [MS][windows] |
| Win+Ctrl+Left / Right | Switch desktop | Adjacent desktop | At least two desktops | [MS][windows] |
| Win+Ctrl+F4 | Close desktop | Windows move to surviving desktop | Does not close each app | [MS][windows] |
| Win+Shift+Enter | Full screen | App-specific UWP full screen | Supported UWP app | [MS][windows] |

## Taskbar and notifications

| Shortcut | Action | Behavior | Conditions | Source |
|---|---|---|---|---|
| Win+T / Win+Shift+T | Taskbar focus | Next/previous app | Enter activates | [MS][windows] |
| Win+B | Tray focus | First notification-area icon | Arrow keys navigate | [MS][windows] |
| Win+number | Pinned app | Open or activate position | Ordered taskbar positions | [MS][windows] |
| Win+Shift+number | New instance | Launch pinned app again | Multi-instance support | [MS][windows] |
| Win+Ctrl+number | Last window | Last active window of pinned app | Running app | [MS][windows] |
| Win+Alt+number | Jump List | Open pinned app's task list | App supplies entries | [MS][windows] |
| Win+Ctrl+Shift+number | Elevated launch | New administrator instance | UAC consent and app support | [MS][windows] |
| Shift+taskbar click | New instance | Launch app again | App dependent | [MS][windows] |
| Ctrl+Shift+taskbar click | Elevated launch | Administrator instance | UAC | [MS][windows] |
| Shift+taskbar right-click | Window menu | Per-window/group controls | Target context matters | [MS][windows] |
| Ctrl+grouped taskbar click | Cycle group | Switch group's windows | Group has multiple windows | [MS][windows] |
| Alt+Shift+Arrow | Reorder taskbar | Move focused icon | Keyboard focus on taskbar icon | [MS][windows] |
| Win+Alt+Enter | Taskbar settings | Open settings | Taskbar item focused | [MS][windows] |
| Win+Alt+D | Clock/calendar | Show/hide | Shell | [MS][windows] |
| Win+Shift+V | Notification focus | Cycle notifications | Active notification context | [MS][windows] |

## Capture, recording, clipboard, input and media

| Shortcut | Action | Behavior | Conditions | Source |
|---|---|---|---|---|
| Win+Shift+S | Snip | Select capture area | Snipping Tool/version settings | [MS][windows] |
| Print Screen | Snip or screenshot | Mapping configurable | Accessibility > Keyboard; Fn on compact keyboards | [MS][windows] |
| Alt+Print Screen | Window screenshot | Copy active window | Clipboard | [MS][windows] |
| Win+Print Screen | Full screenshot | Save image | Pictures/Screenshots path can be redirected | [MS][windows] |
| Win+Shift+R | Region recording | Open Snipping recording selection | Recent Snipping Tool; earlier builds vary | [MS][windows] |
| Win+G | Game Bar | Overlay | Installed/enabled Game Bar | [MS][windows] |
| Win+Alt+R | Recording toggle | App/game recording | Game Bar capture-compatible app | [Xbox][gamebar] |
| Win+Alt+G | Recent capture | Save recent gameplay | Background capture enabled beforehand | [Xbox][gamebar] |
| Win+Alt+Print Screen | Game screenshot | Save game/app capture | Game Bar capture context | [Xbox][gamebar] |
| Win+Alt+M | Capture microphone | Toggle recording mic | During Game Bar capture | [Xbox][gamebar] |
| Win+V | Clipboard history | Choose retained item | Opt-in; sync separate; not inspected here | [MS][windows] |
| Win+. / Win+; | Emoji/symbols | Picker | Panel varies by language/build | [MS][windows] |
| Win+H | Voice typing | Speech to focused text | Mic, online service and language support | [MS][access] |
| Win+Alt+H | Voice typing focus | Focus dictation UI | Voice typing open | [MS][access] |
| Win+Space / Win+Shift+Space | Input switch | Forward/back through layouts | Multiple installed input methods | [MS][windows] |
| Win+Ctrl+Space | Previous input | Restore prior input method | Input-method context | [MS][windows] |
| Ctrl+Shift | Keyboard layout | Configured layout switch | Multiple layouts; advanced setting can remap | [MS][windows] |
| Ctrl+Space | Chinese IME | Toggle IME | Relevant Chinese IME | [MS][windows] |
| Win+/ | IME reconversion | Reconvert selection | Supporting IME | [MS][windows] |
| Win+Ctrl+V | Audio outputs | Output, mixer and spatial controls | Recent Windows 11 | [MS][windows] |
| Win+Alt+K | Microphone mute | Supported communications app | App exposes system mute integration | [MS][windows] |
| Hardware media keys | Playback/volume | Play/pause, track, volume, mute | Keyboard and app media-session support | [ASUS][asuskeys] |

## Editing and dialogs

| Shortcut | Action | Behavior | Conditions | Source |
|---|---|---|---|---|
| Ctrl+C / Ctrl+Insert | Copy | Selected content | Focused app allows copying | [MS][windows] |
| Ctrl+X | Cut | Move selection to clipboard | Editable content | [MS][windows] |
| Ctrl+V / Shift+Insert | Paste | Insert clipboard | Format/app rules apply | [MS][windows] |
| Ctrl+Shift+V | Plain paste | Remove formatting | Only supporting apps | [MS][windows] |
| Ctrl+Z / Ctrl+Y | Undo/redo | Edit history | App-specific undo scope | [MS][windows] |
| Ctrl+A | Select all | Current text/list | Focus dependent | [MS][windows] |
| Ctrl+Left / Right | Word navigation | Previous/next word | Text input | [MS][windows] |
| Ctrl+Up / Down | Paragraph navigation | Previous/next paragraph | Editor dependent | [MS][windows] |
| Home / End | Line navigation | Line start/end | Editor/list dependent | [MS][windows] |
| Ctrl+Home / End | Document navigation | Start/end | Focused document | [MS][windows] |
| Shift+Arrow / Home / End | Select | Extend text/item selection | Focus dependent | [MS][windows] |
| Ctrl+Shift+Left / Right | Select words | Extend by word | Text input | [MS][windows] |
| Backspace / Delete | Delete | Before/after cursor | Editable text; Explorer differs | [MS][windows] |
| Tab / Shift+Tab | Focus | Forward/backward control | Dialog or settings | [MS][windows] |
| Ctrl+Tab / Ctrl+Shift+Tab | Tabs | Next/previous | Tabbed dialog/app | [MS][windows] |
| Alt+underlined letter | Access key | Invoke labeled command | Locale-specific mnemonic | [MS][windows] |
| Space | Toggle | Checkbox/button | Focused control | [MS][windows] |
| Enter / Esc | Accept/cancel | Default action/dismiss | Dialog dependent | [MS][windows] |
| F4 | Expand list | Show list choices | Dialog drop-down focus | [MS][windows] |
| F6 | Regions | Cycle pane/control groups | App dependent | [MS][windows] |
| F10 | Menu | Activate menu bar | Traditional menu app | [MS][windows] |
| Shift+F10 / Menu key | Context menu | Keyboard right-click | Focused item | [MS][windows] |
| Ctrl+F4 | Close document | Leave host app open | MDI/tabbed app dependent | [MS][windows] |

## File Explorer and file operations

| Shortcut | Action | Behavior | Conditions | Source |
|---|---|---|---|---|
| Ctrl+N / Ctrl+T | New window/tab | Open browser context | Tabs require recent Explorer | [MS][windows] |
| Ctrl+W | Close tab/window | Window closes on final tab | Explorer | [MS][windows] |
| Ctrl+Tab / Ctrl+Shift+Tab | Switch tabs | Next/previous | Multiple tabs | [MS][windows] |
| Ctrl+1…9 | Numbered tab | Select position | Explorer version | [MS][windows] |
| Ctrl+L / Alt+D / F4 | Address | Focus editable path | Can accept paths/URIs | [MS][windows] |
| Ctrl+E / Ctrl+F / F3 | Search | Search current location | Indexing/location affects results | [MS][windows] |
| Alt+Left / Backspace | Back | Previous location | Navigation history | [MS][windows] |
| Alt+Right | Forward | Next history location | After Back | [MS][windows] |
| Alt+Up | Parent | Open parent folder | Filesystem/namespace context | [MS][windows] |
| Ctrl+Shift+N | New folder | Create folder | Write access required | [MS][windows] |
| F2 | Rename | Edit item name | Write access required | [MS][windows] |
| Alt+Enter | Properties | Item metadata dialog | Selected item | [MS][windows] |
| Alt+P / Alt+Shift+P | Panes | Preview/details | Preview handlers vary | [MS][windows] |
| Ctrl+Shift+1…9 | View | Change layout | Explorer supported views | [MS][windows] |
| Ctrl+wheel | Icon sizing | Adjust view scale | Pointer over file view | [MS][windows] |
| Ctrl+numpad + | Column sizing | Fit columns | Details view; numeric keypad | [MS][windows] |
| Ctrl+Shift+E | Navigation tree | Expand parent folders | Navigation pane | [MS][windows] |
| Left / Right | Tree navigation | Collapse/expand | Tree focus | [MS][windows] |
| Home / End | List navigation | First/last | File view | [MS][windows] |
| Shift+Arrow | Range selection | Extend selected items | File view | [MS][windows] |
| Ctrl+Arrow, Space | Separate selection | Move focus, toggle item | File view | [MS][windows] |
| Delete / Ctrl+D | Recycle | Send item to Recycle Bin | Some network/removable locations bypass bin | [MS][windows] |
| Shift+Delete | Permanent delete | Bypass Recycle Bin | Destructive; documented only | [MS][windows] |
| F5 / Ctrl+R | Refresh | Reload location | Explorer | [MS][windows] |
| F11 | Full screen | Toggle window presentation | Explorer | [MS][windows] |
| Ctrl+drag | Copy | Force copy on drop | Source/destination access | [MS][windows] |
| Shift+drag | Move | Force move on drop | Destructive to source location | [MS][windows] |
| Alt+drag | Shortcut | Create .lnk | Destination write access | [MS][windows] |
| Shift+right-click | Legacy menu | Show more options directly | Windows 11 Explorer | [MS][windows] |

## Accessibility

| Shortcut | Action | Behavior | Conditions | Source |
|---|---|---|---|---|
| Win+U | Accessibility | Open settings | Shell | [MS][access] |
| Win+Ctrl+Enter | Narrator | Start/stop screen reader | Shortcut enabled | [MS][windows] |
| Win+Ctrl+N | Narrator settings | Open options | Shell | [MS][access] |
| Win+Ctrl+O | On-screen keyboard | Toggle keyboard | Distinct from touch keyboard | [MS][access] |
| Win+plus / minus | Magnifier | Zoom in/out | Plus starts Magnifier | [MS][windows] |
| Win+Esc | Magnifier exit | Close magnification | Magnifier active | [MS][windows] |
| Win+Ctrl+C | Color filters | Toggle configured filter | Shortcut enabled in settings | [MS][access] |
| Left Alt+Left Shift+Print Screen | Contrast | Toggle contrast mode | Shortcut policy/prompt | [MS][access] |
| Shift five times | Sticky Keys | Toggle modifier latching | Shortcut enabled | [MS][access] |
| Right Shift eight seconds | Filter Keys | Toggle repeat filtering | Shortcut enabled | [MS][access] |
| Num Lock five seconds | Toggle Keys | Toggle key-state sounds | Shortcut enabled | [MS][access] |
| Left Alt+Left Shift+Num Lock | Mouse Keys | Numeric keypad pointer | Shortcut enabled | [MS][access] |
| Win+Ctrl+L | Live captions | Open captioning | Language model availability | [MS][captions] |

Older references list Win+Ctrl+S for Windows Speech Recognition. Microsoft dates its replacement by voice access to September 2024 on Windows 11 22H2 and later; treat this as a historical mapping, not a guaranteed modern activation path. [Replacement notice][wsr]

## Mouse, touchpad, touchscreen and Snap interactions

Source: [Microsoft touch and precision-touchpad gestures][gestures], [Snap][snap]. Touchscreen entries are **UNKNOWN** for this machine: an OLED panel does not prove a touch digitizer.

| Interaction | Action | Behavior | Conditions | Source |
|---|---|---|---|---|
| Touchpad tap | Select | Primary click | Taps enabled | [MS][gestures] |
| Two-finger tap / lower-right press | Context | Secondary click | Touchpad configuration | [MS][gestures] |
| Two-finger slide | Scroll | Horizontal/vertical | App scroll surface | [MS][gestures] |
| Two-finger pinch/stretch | Zoom | Scale content | Supporting app | [MS][gestures] |
| Three-finger swipe up/down | Overview/desktop | Task View / desktop | Precision touchpad; customizable | [MS][gestures] |
| Three-finger swipe left/right | App switch | Previous/next window | Precision touchpad; customizable | [MS][gestures] |
| Four-finger swipe left/right | Desktops | Previous/next desktop | Precision touchpad; customizable | [MS][gestures] |
| Touch tap / hold | Select/context | Click / context menu | Touchscreen required | [MS][gestures] |
| Touch two-finger slide/pinch | Scroll/zoom | Content navigation | Touchscreen/app support | [MS][gestures] |
| Touch three-finger up/down | Overview/desktop | Task View / desktop | Three/four-finger gestures enabled | [MS][gestures] |
| Touch three-finger left/right | Last app | Switch app | Touchscreen gesture enabled | [MS][gestures] |
| Touch four-finger left/right | Desktop switch | Adjacent virtual desktop | Gesture enabled | [MS][gestures] |
| Touch right-edge / left-edge swipe | Notifications/widgets | Open side surfaces | Edge gestures enabled | [MS][gestures] |
| Hover maximize button | Snap layouts | Choose placement | Snap enabled; supported window | [MS][snap] |
| Drag title bar to edge/top | Snap/maximize | Position window | Snap settings and screen geometry | [MS][snap] |
| Drag title bar to top layout bar | Snap layout | Drop into layout | Windows 11 version/settings | [MS][snap] |

## Built-in application and terminal context

These defaults belong to applications; they are not universal global bindings. App versions can add/remove them. Sources: [legacy Windows app reference][apps], [Edge][edge], [Terminal][terminal]. **Source gap:** Microsoft's legacy app-reference URL now redirects to its generic Windows list. Paint/Notepad-specific mappings below are retained as legacy reference knowledge with **UNKNOWN current documentation verification and current execution**, rather than claimed as newly verified. Calculator mappings use Microsoft's open-source implementation/test documentation.

| Shortcut | Action | Behavior | Conditions | Source |
|---|---|---|---|---|
| Ctrl+N / Ctrl+O / Ctrl+S | Document lifecycle | New/open/save | Supporting editor, including Paint/Notepad; source-gap caveat above | [MS][apps] |
| Ctrl+Shift+S / F12 | Save as | Save with new location/name | App-dependent; classic Paint uses F12; source-gap caveat above | [MS][apps] |
| Ctrl+P | Print | Print dialog | Supporting app/printer or PDF output | [MS][apps] |
| Ctrl+F / Ctrl+H | Find/replace | Text search/edit | Notepad/editor context | [MS][apps] |
| Ctrl+G / F5 | Go to/date | Go to line / insert timestamp | Notepad context | [MS][apps] |
| Ctrl+E / Ctrl+W | Image properties/resize | Image operations | Paint context; differs in browsers | [MS][apps] |
| Ctrl+R / Ctrl+G | Ruler/grid | View aids | Paint context; not global Refresh | [MS][apps] |
| Alt+1 / Alt+2 / Alt+3 / Alt+4 / Alt+5 | Calculator mode | Standard/scientific/graphing/programmer/date | Calculator mode/version | [MS][calculator] |
| Ctrl+H | Calculator history | Open calculation history | Calculator, not editor Replace | [MS][calculator] |
| Ctrl+M | Calculator memory | Store current value in memory | Calculator; does not open memory panel | [MS][calculator] |
| Ctrl+T / Ctrl+W / Ctrl+Shift+T | Browser tabs | New/close/reopen | Edge | [MS][edge] |
| Ctrl+L / Ctrl+K | Browser focus | Address / search | Edge | [MS][edge] |
| Ctrl+Shift+N | InPrivate | Open private window | Edge policy; not Explorer New Folder | [MS][edge] |
| Ctrl+J / Ctrl+H / Ctrl+D | Browser tools | Downloads/history/favorite | Edge; personal contents not inspected | [MS][edge] |
| F9 / F11 / F12 | Reading/fullscreen/devtools | Browser surfaces | Edge; site/policy support | [MS][edge] |
| Ctrl+Shift+P | Command palette | Terminal actions | Windows Terminal | [MS][terminal] |
| Ctrl+Shift+T / Ctrl+Shift+W | Terminal tab/pane | New tab / close pane | Terminal, remappable | [MS][terminal] |
| Ctrl+Shift+C / Ctrl+Shift+V | Terminal copy/paste | Selection / clipboard | Shell may intercept other chords | [MS][terminal] |
| Ctrl+Tab / Ctrl+Shift+Tab | Terminal tabs | Next/previous | Terminal | [MS][terminal] |
| Alt+Shift+plus / minus | Terminal split | Vertical/horizontal pane | Terminal defaults | [MS][terminal] |
| Alt+Shift+D | Duplicate pane | Same profile | Terminal defaults | [MS][terminal] |
| Ctrl+M | Console Mark mode | Select console output | Classic conhost, not every terminal | [MS][windows] |
| Ctrl+C | Interrupt/copy | Interrupt command or copy selection | Console selection and shell context | [MS][windows] |
| Ctrl+Home / End | Console buffer | Buffer/history navigation | Mark mode and command text affect behavior | [MS][windows] |

## ASUS Fn and NumberPad boundary

| Shortcut/interaction | Action | Behavior | Conditions | Source |
|---|---|---|---|---|
| Fn+Esc | Function/hotkey mode | Swap top-row default | DOCUMENTED only for supporting models; historical MyASUS Fn-mode UI OBSERVED 2026-09-25 | [ASUS][asuskeys] |
| F1–F3 icon functions | Speaker mute/down/up | Audio hotkeys | Historical UM3406GA notes identify these; current physical check UNKNOWN | Private baseline + [ASUS][asuskeys] |
| F4 icon function | Keyboard light | Manual brightness control | Historical model notes; Fn requirement depends on mode | Private baseline |
| Other top-row icons | Brightness, touchpad, display, camera, MyASUS, snip | OEM actions | Generic ASUS examples are other models; exact UM3406GA F5–F12 map UNKNOWN | [ASUS][asuskeys] |
| NumberPad corner controls | Touchpad/numeric pad | Integrated numeric overlay | Historical NumberPad UI and filter stack AVAILABLE/CAPTURED; current corner gestures UNKNOWN | Private baseline |

No UX325/ROG keyboard map is presented as this UM3406GA's physical layout. A single physical photo/manual page and a harmless hotkey check can close that gap later.

[windows]: https://support.microsoft.com/en-us/accessibility/windows/keyboard-shortcuts-in-windows
[access]: https://support.microsoft.com/en-us/accessibility/windows/windows-keyboard-shortcuts-for-accessibility
[gestures]: https://support.microsoft.com/en-us/windows/hardware/input-devices/touch-gestures-for-windows
[apps]: https://support.microsoft.com/en-us/windows/keyboard-shortcuts-in-apps-139014e7-177b-d1f3-eb2e-7298b2599a34
[gamebar]: https://support.microsoft.com/en-us/accessibility/windows/use-a-screen-reader-to-record-your-screen-with-xbox-game-bar
[edge]: https://support.microsoft.com/en-us/edge/keyboard-shortcuts-in-microsoft-edge
[terminal]: https://learn.microsoft.com/en-us/windows/terminal/install
[captions]: https://support.microsoft.com/en-us/accessibility/windows/use-live-captions-to-better-understand-audio
[snap]: https://support.microsoft.com/en-us/windows/experience/snap-your-windows
[asuskeys]: https://www.asus.com/support/faq/1038312/
[aikeys]: https://support.microsoft.com/en-us/windows/ai/ai-features/keyboard-shortcuts-for-recall-and-click-to-do
[calculator]: https://github.com/microsoft/calculator/blob/main/docs/ManualTests.md
[wsr]: https://support.microsoft.com/en-us/windows/use-voice-recognition-in-windows-83ff75bd-63eb-0b6c-18d4-6fae94050571
