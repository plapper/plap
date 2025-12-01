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
