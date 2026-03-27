## 7.2.3.xxxxx MM DD YYYY [xxxxx]

## NEW
#### Notecard syntax highlighting
- fix: new rule colors are now generated randomly and distinct from other colors in the set
- fix: remove set/rule button now properly removes the selected set/rule
- added `Random` color button next to rule color swatch
- added ability to save/load pre-defined colors with the `Defined colors` button

#### Misc
- changed Linux default install path from `/opt/firestorm/` and `$HOME/firestorm` to `/opt/aero` and `$HOME/aero`
- parcel/region-only object culling is now based on root prim position, instead of individual child prim positions
  this makes it so objects with child prims outside of the current region/parcel are still properly rendered

something about new cloning feature/ghosting thing
something about rlv commands for cloning
something about slua script syntax highlighting 
something about other stuff i forgot

## BUG FIXES


## 7.2.3.80476 Mar 12 2025 [ccfcaf3d90]

## NEW
#### Texture Explorer
- now keeps track of recent particle systems detected, up to 120s history
- if live particle system is not found on the object, pull from recent particle systems history

#### Animation Explorer
- increase `MAX_ANIMATIONS` from 100 to 400
- increase history window from 60s to 120s

#### Particle Editor
- add `AEROParticleEditorHistoryMax` debug setting to control max undo history depth
- add undo/redo functionality, history size based on `AEROParticleEditorHistoryMax`
- add randomize button to randomize particle editor settings
- add randomization settings to adjust randomization value ranges, with load/save XML preset options
- change import/export functionality from XML to inventory LSL scripts

#### Notecard Syntax Highlighting
- notecards can now have syntax highlighted based on regex rules that match the notecard's name
- rules are grouped into "syntax sets", each with a name pattenr a a list of colorizing rules
- managed via `Preferences > Aero > Notecard syntax`
- special rule names `_BACKGROUND_`, `_FOREGROUND_`, `_SELECTED_`, `_CURSOR_` override the notecard editor's colors instead of matching patterns

#### Upstream changes
merged with the latest firestorm upstream changes:
- UI: Add option to automatically group IM tabs by type like group IMs, conferences and 1 on 1 IMs
- UI: `FIRE-33859` - Add +/- and reset buttons to hover height slider
- UI: Update viewer-fonts (emoji) to use DejaVu 2.37 (was 2.30)
- Poser: add modified-date column, add column headers, allow column-sorting
- Audio: Update Fmod to 2.03.12

#### Misc
- added Aero tab to `Help > About Firestorm` for aero-specific info
- `World > Environment > Save to Inventory` now saves settings with the actual name of the setting
   description is saved as `REGION_NAME @ x,y,z`
- outfit gallery can now be set to only show outfits with preview images

## BUG FIXES
- fixed debug setting controls disappearing AGAIN
- fix debug settings floater regression without breaking bottom toolbar
  
## 7.2.3.80362 Feb 25 2026 [d6569f7ed2]

## NEW
##### Appearance/Outfits Panel
- add `Show in Main View` to outfit gallery context menu, will show the selected outfit in the `Outfits` tab
- add `Show in Gallery` to the outfits context menu, will show the selected outfit in the `Outfit Gallery` tab
 - add `Scroll to Current Outfit` to both sort menus, scrolls to the currently worn outfit in the current tab
- add `Random Outfit Filter` button to the floater, next to the `Random Outfit` button, to quickly change the `AERORandomOutfitFilter` setting

##### Asset Management
- all wearables can now be opened and inspected (read-only if no-mod)
- add `Recreate Wearable` to inventory context menu to quickly re-create wearables
- add texture swatch submenu with `Open` and `Copy UUID` options
 `Copy UUID` or `Copy Asset UUID` buttons now post nearby chat messages: `AssetType> UUID: <uuid>`
 
##### World Map
- add `Copy Pos (G)` button to copy target positions' global coords (<xxxxx,yyyyy,zzzz>)
- add `Copy Pos (R)` button to copy target posisiton's relative-to-avatar coords
- add `Copy Pos (S)` button to copy target position's relative-to-sim-corner 
- merge region name and advanced into (agent count, maturity rating) into a single line and use short labels

##### Parcel/About Land
- add `Custom` landing point button, allowing the ability to specific a custom landing point, event outside the parcel/region
- note: appears to be limited to +/- 512m from the region's corner (0,0,

##### Misc
- new debug setting `AEROShowTextAllocFails` (default: false) to hide the USELESS on-screen texture allocation error counts

## BUG FIXES
-  restore `Hover Height` and `Tex Refresh` to the `Appearance` submenu, in the pie menu
- fix control buttons/input being missing from the Debug Settings floater
- removed the empty unused `Advanced > AERO` submenu
- `Shift+Click` on object faces with materials no longer opens all textures, instead just opens the material editor window
- increased space between spaces and text in top level menus

[PREVIOUS CHANGES/VERSIONS](https://github.com/plapper/plap/blob/main/CHANGELOG.md)

## 7.2.3.80353 Feb 9 2026 [a42c1abe0d]

- Bug fixes:
    - fixed issue where far clipping plane would be set to the current draw distance, instead of constant 1024
    - fixed issue where nametag would show `--- ---` for friends with "Remove Display Name" enabled but not in a contact 
    
- UI Changes:
    - allow exporting RAW terrain files by generating them locally from terrain height data in `Region/Estate > Terrain` (WIP: importing)
    - allow users to export terrain and water as glTF file in `Region/Estate > Terrain floater`
    - `Shift+Click` on an object face opens texture floaters (and material editor if using PBR)
    - color picker in the build menu can now be opened all for objects, (read-only on non-modifiable objects)
    - copy buttons in the build menu are now enabled for all objects
    - allow using emojis in estate messages
    - debug settings floater now supports regex search and resizing the settings list horizontally
    - add new target/anchor tab to cameratools floater
    - add new targetr/anchor controls to phototools floater
      Phototools (Alt+P) > Cam > Target/Anchor tab (bottom)

- Camera Changes:
    - added `AERORenderNearClip` setting: min distance from camera at which objects are rendered, closer objects are are "clipped"
    - added `AERORenderMaxFarPlane` setting: max distance from the camera at which objects are render, further objects are "clipped"
    - lowered `MIN_NEAR_PLANE` constant from 0.1f to 0.001f to allow smaller near clip values
    - automatically adjust far clip to maintain 10000:1 depth ratio to combat z-fighting when near clip is set very low

- Misc Changes:
    - increase avatar picker page size from 100 to 1000 for better results
    - remove distance limit check for the poser model list
    - poser model list now shows object names instead of UUIDs
    - removed map privilege notifs
    - added support for exporting bone translations to BVH files
    - **EXPERIMENTAL [game_control](https://wiki.secondlife.com/wiki/Game_control) support, untested on Windows**


### RLV changes
view [AERO_RLV.md](https://github.com/plapper/plap/blob/main/AERO_RLV.md) for full documentation

- new friend management RLV commnads:
  * `@friend_get:<uuid>=<channel>` - get friend information
  * `@friend_map:<uuid>=<channel>` - get friend map location
  * `@friend_set:<uuid>;<online_rights>;<map_rights>;<edit_rights>=<channel>` - set friend rights
  * `@friend_add:<uuid>=force` - add friend
  * `@friend_remove:<uuid>[;force]=force` - remove friend
  * `@friend_feed[:<uuid>]=<channel>` - subscribe to friend status updates
   - location initially will return `0` if the friend's location is not
  cached. this allows the LSL script to know to retry. if `-1` is return,
  then it means you dont have map privileges, the friend is offline, or
  the location is unknown.
- add `@setcam_anchor` command that anchors camera to static global pos/object position
    - `@setcam_anchor:<x/y/z>;<strength>=force` - static global pos
    - `@setcame_anchor:<uuid>/<bone>;<strength>=force `- object position pos
    - `@setcam_anchor:none=force `- clears the anchor
- add `thirdperson` parameter to `@setcam_target:<uuid>[;<thirdperson>]=force`
   - when `thirdperson` is 1, target tracking also applies to 3rd person view

#### RLV HMC:
- fixed issue where buttons would not work if the HMC was being updated repeatedly
- replaced text-based alignment padding with proper alignment spacer
- added animated image tag support `{ia:uuid;width;height;mode;columns;rows;start;frames;fps}`
- no longer capture cursor focus when opened
- added minimize button, scrollbar control
- consolidate `@hudmsg_xbtn` and `@hudmsg_resize` into: `@hudmsg_btns:<ident>;<close>;<resize>;<minify>;<scrollbar>=force`
- make floaters immune to Ctrl+W and Ctrl+Shift+W
- add passthrough as 6th parameter to @hudmsg_btns command
    - format: `@hudmsg_btns:<ident>;<close>;<resize>;<minify>;<scrollbar>;<passthrough>=force`
    - when `passthrough` is 1, all mouseclicks pass through the window, including dragging

[PREVIOUS CHANGES/VERSIONS](https://github.com/plapper/plap/blob/main/CHANGELOG.md)

## 7.2.3.80275 Jan 1 2026 [7ff308bb44]
- merged with the latest firestorm upstream changes to include:
    - omnifilter (block chat, dialogs, teleport offers, friendship, etc. based on content rather than just owner or sender)
    - poser translation manipulators (drag arrows to reposition bones)
    - pinning/unpinning groups in the people and contacts floater
    - chat spheres (Ctrl-Shift-N, display spheres to visualize chat ranges)
    - fix for ctrl+backspace and ctrl+delete not updating visually
- anim explorer now keeps track of anims in the background, displaying all anims played within the last 60 seconds as well as currently playing anims
- moved aero tokens window from debug menu to help menu, no longer need to enable debug menu to access it
- removed my implementation of the poser translation manipulators (due to it being added in upstream firestorm)
- reattaching via outfit now re-attaches to previous attachment point instead of defaulting to chest
- removed dual token auth system (access token + feature token) with token system using level-based permissions (0-4)
    - level 0: login only
    - level 1: level 0 + access to level 1 features (tester)
    - level 2: level 1 + access to level 2 features (debugger)
    - level 3: level 2 + access to level 3 features (dev)
    - level 4: access to ALL features (admin)

#### RLV changes
view [AERO_RLV.md](https://github.com/plapper/plap/blob/main/AERO_RLV.md) for full documentation
- **NEW**
    - `@avataranim_list:<target>;<type>=<channel>`
    - `@sendim:<target>;<message>=force`
    - hud message console system `@hudmsg_*`
- simplify `@avatarrotation` RLV command to use z-axis only
- `@sendsay` `@sendshout` `@sendwhisper` unified into: `@sendlocalchat:<type>;<channel>;<message>=force`
- refactored the following commands into proper syntax:
    - `@outfitname`
    - `@uploadthumbnail`
    - `@uploadasset`
    - `@resetskeleton`
    - `@takesnapshot`
- `@avataranim` is split into:
    - `@avataranim_start:<target>;<anim>;<priority>;<loop>;<local>=force`
    - `@avataranim_stop:<target>;<anim>=force`
  
## 7.2.2.79741 Dec 1 2025 [6122e09]
#### new features
- **TEMPORARY/EXPERIMENTAL** SLua support
- this adds the ability to write and compile SLua support in the script editor
- choose "SLua" from the drop-down menu in the script editor and save your script
- this will be removed/replaced at a later date when Firestorm implements it properly
- this adapted from the Linden viewer which is also in a very beta stage and inherits it's issues
    - syntax highlight for SLua is broken - use an external editor
    - the websocket stuff for vscode is broken
    - requires the Firestorm preprocessor to disabled
    - SLua only compiles in [SLua regions](https://maps.secondlife.com/secondlife/SLua%20Beta%20Void/32/32/23)
  
#### bug fixes
- exporting rigged .dae now exports joint positions properly

## 7.2.2.79738 Nov 23 2025 [bc2890d]
#### bug fixes
- fix anim preview priority handling and add metadata description update
  - fix priority spinner defaulting to 0 when anim data isn't loaded
  - spinner is blank and disabled until anim data loads
  - "Play Locally" skips priority override when data isn't loaded,
    using anim's baked-in priority instead
  - UI automatically updates when anim data finished loading

- implement "Update description with metadata" button in the anim preview floater
  - generates metadata description in the same format as upload:
    
  `priority:X, length:Y, loop:Z, easein:A, easeout:B, frames:C, fps:D, joints:E, deform:F`

## 7.2.2.79736 Nov 21 2025 [9272eeb]
#### bug fixes
- fix pie menu items/ordering

### 7.2.2.79735 Nov 21 2025 [4366236]
#### bug fixes
- fix for blinn-phong texture transform inputs always being disabled  in the build menu
- support for file metadata descriptions for uploading via @uploadasset and for uploading PBR materials
- add optional 'delay' parameter to @takesnapshot

## 7.2.2.79734 Nov 19 2025 [b6f92f941d]
- new: clipboard keytool - press ctrl-shift-k with a UUID in your keyboard to view/open it
   - supports agents, textures, sounds, animations, gtlf materials(?)
   - displays small window showing progress
   - note: only works if you own the asset (except for agents)
- new: enhanced animation explorer
   - moved anim preview to left side and made larger + higher res
   - added "show bones" options, green bones are bones being animated by the selected anim
- new: custom login page with update notification
- new: user auth system. only authorized users may login (press Ctrl-Alt-K)
- new: import/export wearables
- new: add enhanced dae/oxp import/export features, supports exporting rigged mesh
   - RIGGED MESH EXPORT REQUIRES YOU TO: OWN THE MESH, BE THE CREATOR, AND THE MESH MUST BE FULL PERM.
- new: add poser translation manipulators
- refactor: @takesnapshot command renders the scene offscreen, removing the need to use LSL to move the camera
   -`\@takesnapshot:<outputpath>;<position>;<lookat>=force`
- fix: - build menu UI improvements:
    - object tab: display all values as read-only instead of hiding them
    - features tab: display all values as read-only instead of hiding them
    - textures tab: display all values as read-only instead of blanking entire panel
    - COPY butttons for pos/size/rot always enabled
- fix: AEROAnimTimeFactor now works in the quick prefs window
- fix: "Reset to default folders" now works for scripts/notecards
- fix: allow derendering own attachments regardless of RLV
- fix: make windows desktop shortcut creation option in installer

## 7.2.2.79670 Nov 1 2025 [fb449c8]
- refactor: rename `AEROExperiments` to `AERODebugging`
   - this name is more inline with what these features are meant for
- fix: actual fix for [FIRE-33977](https://jira.firestormviewer.org/browse/FIRE-33977)
- fix: `Copy Lists` functionality fixes
  - now grabs the proper UUIDs
  - paired lists now ignore `AEROCopyListThreshold` and always to name,uuid pairs on separate lines
- new: add AERO debugging feature tab 
- new: add `Unlocked Poser` and `Save Environment to Inventory` to AERO debugging tab
- new: merges with latest [upstream changes](https://github.com/FirestormViewer/phoenix-firestorm/compare/0d2477c...b1026c6)
- new: add option to allow uploading pre-encoded ogg files
  - enable via `Preferences > Aero > Debugging > Allow pre-encoded OGG sound uploads`
- new: add file metadata to descriptions when uploading
   - adds `AEROUploadMetadataDesc` setting to set item description to various metadata when uploading:
     - images: `dimensions:WIDTHxHEIGHT`
     - sounds: `duration:SECONDS`
     - animations: `priority, duration, looped, ease_in/out, total_frames, frames_per_second, joint_count, has_translations`
- new: add `Mass Delete` functionality to inventory folder context menu
  - bulk deletion of landmarks/notecards/scripts with confirmation dialog
  - multi-layer protection for exclusions:
    - skips favorited items
    - recursive parent hierarchy protection for system folders, protected folders, and favorited folders
    - also exclude these folders from showing the mass delete context menu items
   
## 7.2.2.79508 Oct. 24 2025 [f177582]
 - note: version number decreased due to dropping/squashing a few commits
 - new: added support for specifying default upload folder for scripts and notecards
 - new: moves all the "Create X" inventory context menu items to a submenu: `Create New`
 - new: Aero preferences tab for various aero settings and new rlv command documentation
 - new: add ability to save the current environment settings to inventory; `World > Environment > Save to Inventory`
 - fix: `AERO3pmOffset` is now properly updates when adjusting
 - fix: Copy Lists functionality now gets the current UUIDs for animations
 - fix: HUD objects no longer get clipped by inworld objects when zooming in very close
 - fix: HUD objects no longer get derendered when `AEROParcelOnlyObjects` is true
 - fix: possible fix for [FIRE-33977](https://jira.firestormviewer.org/browse/FIRE-33977)

 ### 7.2.2.79507 Oct. 18 2025 [f7a36ec]
 - fix: issue with incorrect chat log file naming
 - fix: `Copy Lists` submenu not appearing
 - new: show notification when a friend grants/revokes map rights
 - new: show notification when a friend removes you
 - new: experimental `AERORegionOnlyObjects` debug setting - only render objects that are in your current region
 - new: experimental `AEROParcelOnlyObjects` debug setting - only render objects that are in your current parcel
 - fix: @uploadasset now only works with premium plus users, to prevent unapproved L$ spending
 
## 7.2.2.79506 Oct. 16 2025 (hot fix) [dd6a7c4]
 - move `Reattach` to the `Appearance` submenu in the pie menu
 - add `Copy Lists` to copy multiple names or UUIDS or both into a list of code list
    
## 7.2.2.79505 Oct. 16 2025 [bbe98f2]
- new: import/export particle presets locally, .xml format
- new: added script/text file upload support
- new: rlv `@uploadthumbnail:<path>;<channel>=force` - upload free 256px thumbnail and print UUID on given channel
- new: rlv `@uploadasset:<path>=force` - uploads asset to your inventory (WARNING: SKIPS PAYMENT CONFIRMATION)
- new: rlv `@outfitsetimage:<name>=force` - set the thumbnail of the specified outfit
- new: rlv `@outfitname:<channel>=force` - retrive the name of the currently worn outfit
- new: rlv `@resetskeleton=force` - reset your avatar's skeleton
- new: rlv `@getscriptlines:<start>;<end>;<linetype>;<maxlength>=force` - get currently open script lines/nearby lines
- new: rlv `@replaceprofiletext:<search>;<replace>=force` - replace certain strings in your profile
- new: rlv `@camerashake:<duration>;<frequency>;<amplitude>=force` - customizable camera shake command
- new: outfit marking features in context menu (this is mainly for outfit management/filtering)
- new: add ability to IM yourself via the Comms menu or right clicking your avatar -> Community
- refactor: shorten debug setting names for better readability
    - `AEROAnimationTimeFactor` -> `AEROAnimTimeFactor`
    - `AEROFieldOfViewHotkeyMult` -> `AEROFOVHotkeyMult`
    - `AEROLindenBalanceOffset` -> `AEROBalanceOffset`
    - `AEROPoserAvPositionInOut` -> `AEROPoserLimitX`
    - `AEROPoserAvPositionLeftRight` -> `AEROPoserLimitY`
    - `AEROPoserAvPositionUpDown` -> `AEROPoserLimitZ`
    - `AERORandomizeOutfitFilter` -> `AERORandomOutfitFilter`
    - `AEROThirdPersonMouselookOffset` -> `AERO3pmOffset`
    - `AEROUploadWithExtension` -> `AEROUploadExt`
    - `AEROThirdPersonMouselookZoomAmount` -> AERO3pmZoomAmt
- fix: `@setcam_target` now uses standard rlv modifier/format: `@setcam_target:<uuid>=y/n`
- fix: `New Note` button no longer forces the inventory to open

## 7.2.2.79401 Oct. 3 2025 [bbe98f2]
- new: visual indicators to object contents for disabled scripts
- new: rlv command @randomoutfit[:<pattern>]=force
- new: target lock-on with rlv command @setcam_target:<uuid|none>=force
- new: Ctrl+Scroll for left/right cam adjust in 3rd person mouselook 
- new: Shift+Scroll for up/down cam adjust in 3rd person mouselook 
- new: add script actions to object contents context menu (start, stop, reset, recompile, delete, open)
- fix: possible fix for conflict between disabling camera contraints + camera push through prims
- fix: restore AudioLevelDopple debug setting
- new: outfit management RLV commands:
    - `@outfitcount[:<pattern>]=channel` - get the number of numbers available that match pattern
    - `@outfitlist:start/count[/pattern]=channel` - get paginated line-seperated list of outfits that match pattern
    - `@outputpreview:<name>=channel` - get thumbnail UUID of outfit (blank if no thumbnail set)
    - `@outfitcontents:<name>=channel` - return list of items in the specified outfit
    - `@outfitadd:<name>=force` - add outfit contents to currently worn (vs replacing)
    - `@outfitrepalce:<name>=force` - replace currentl worn outfit with specific outfit
    - `@sendwhisper:<channel>/<message>=force` - whisper a message on specified channel
    - `@sendsay:<channel>/<message>=force` - say a message on specified channel
    - `@sendshout:<channel>/<message>=force` - shout a message on specified channel
    - `@starttyping=force, @stoptyping=force` - start/stop the typing state
    - `@takesnapshot_size:<width>[x<height]=force` - set snapshot size
    - `@takesnapshot[:<outputpath>]=force` - take snapshot and save to optional specified path


## 7.2.2.79354 Sept. 28 2022 [7f47cf6]
- anim speed slider in phototools + `AEROAnimationTimeFactor` debug setting
- AEROFieldOfViewHotkeyMult to adjust fov change amount when using Ctrl+0/9
- add "reattach" functionality to detach and quickly re-attach objects
- debug setting `AEROReattachDelay`, delay to wait before reattaching objects
- debug setting `AEROReattachTimeout`, timeout to give up on reattaching objects
- add "New Note" button to object inventory to create a notecard inside the selected object
- add "Random Outfit" to outfit window to select a random outfit
- debug setting `AERORandomizeOutfitFilter`, only outfits matching this pattern will be considered for random selection
- added visual indicator to object inventory for disabled scripts
- disabled script names are red and striked through

## 7.2.2.79322 Sept. 18 2022 [be5ebfd]
- allow posing other avatars and avatar in other regions
- enhanced sound explorer/sound preview floater (ambient sound button, copy UUID, etc)
- new debug setting `AEROShowDialogChannels` to show channels in script dialogs
- customizable slider ranges for the viewer poser (`AEROPoserAvPosition*` debug settings)
