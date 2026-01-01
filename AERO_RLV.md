

## camera/view

### `@setcam_target:<uuid>=n|y`
sets the camera target to a specific object or avatar UUID
when active, the camera will continously focus on the specified target

| param | desc |
|-----------|-------------|
| `<uuid>` | UUID of the object or avatar to target |


## outfits

### `@randomoutfit[:pattern]=force`
randomly selects and wears an outfit from the user's inventory, optionally filters outfits by a regex pattern

| param | desc |
|-----------|-------------|
| `pattern` | (optional) regular expression pattern to filter outfit names |


### `@outfitcount[:pattern]=<channel>`
returns the count of outfits matching an optional regex pattern

| param | desc |
|-----------|-------------|
| `pattern` | (optional) regular expression pattern to filter outfits |
| `channel` | channel number to send the reply |


### `@outfitlist:<start>/<count>[/pattern]=<channel>`
returns a list of outfit names optionally filtered by regex

| param | desc |
|-----------|-------------|
| `start` | starting index (0-based) |
| `count` | number of outfits to return |
| `pattern` | (optional) regular expression pattern to filter outfits |
| `channel` | channel to send the reply on |


### `@outfitpreview:<name>=<channel>`
returns the thumbnail UUID of a specified outfit

| param | desc |
|-----------|-------------|
| `name` | name of the outfit |
| `channel` | channel to send the reply on |


### `@outfitcontents:<name>=<channel>`
returns a list of item UUIDs in the specified outfit

| param | desc |
|-----------|-------------|
| `name` | name of the outfit |
| `channel` | channel to send the reply on |


### `@outfitreplace:<name>=force`
replaces the current outfit with the specified outfit

| param | desc |
|-----------|-------------|
| `name` | name of the outfit to wear |


### `@outfitadd:<name>=force`
adds items from the specified outfit to the current outfit

| param | desc |
|-----------|-------------|
| `name` | name of the outfit to add |


### `@outfitremove[:name]=force`
removes the specified outfit's items from your current worn items

| param | desc |
|-----------|-------------|
| `outfitname` | name of the outfit to remove |


### `@outfitsetimage:<name>;<uuid>=force`
sets the thumbnail image for the specified outfit

| param | desc |
|-----------|-------------|
| `name` | name of the outfit |
| `uuid` | UUID of the texture to use as thumbnail |


### `@outfitname=<channel>`
sends the name of the currently worn outfit to the specified channel

| param | desc |
|-----------|-------------|
| `channel` | channel to send the reply on |


## chat/comms

### `@sendlocalchat:<type>;<channel>;<message>=force`
forces the avatar to send a local chat message of a specified type on a specified channel

| param | desc |
|-----------|-------------|
| `type` | chat type: `say`, `whisper`, or `shout` |
| `channel` | channel number |
| `message` | message to send |


### `@sendim:<target>;<message>=force`
forces the avatar to send an instant message to a specified avatar

| param | desc |
|-----------|-------------|
| `target` | UUID of the target avatar |
| `message` | message to send |


### `@starttyping=force`
forces the avatar to start the typing animation/indicator in locl chat


### `@stoptyping=force`
forces the avatar to stop the typing animation/indicator in local chat


## snapshots

### `@takesnapshot[:outputpath;x/y/z;x/y/z;rebuild;delay]=force`
takes a snapshot with optional camera positioning and output path

| param | desc |
|-----------|-------------|
| `outputpath` | (optional) file path to save the snapshot |
| `x/y/z` | (optional) camera position coordinates |
| `x/y/z` | (optional) camera look-at coordinates |
| `rebuild` | (optional) 1 to rebuild scene, 0 otherwise (idk if this even works)|
| `delay` | (optional) delay in seconds before taking snapshot (0-10) |


### `@takesnapshot_size:width;height=force`
sets the size for snapshots, can be specified as width;height or just width (maintains aspect ratio)

| param | desc |
|-----------|-------------|
| `width` | width in pixels |
| `height` | (optional) height in pixels |


## uploads

### `@uploadthumbnail:<path>=<channel>`
uploads an image file as a thumbnail (free) and sends the UUID to the specified channel.

| param | desc |
|-----------|-------------|
| `path` | file path to the image |
| `channel` | channel to send the reply on |


### `@uploadasset:<path>=<channel>`
uploads an asset file (script, notecard, etc.) to inventory
note: requires premium plus account, to prevent L$ usage

| param | desc |
|-----------|-------------|
| `path` | file path to the asset |
| `channel` | channel to send the reply on |


## script

### `@getscriptlines:<start>;<end>;<linetype>;<maxlength>=<channel>`
retrieves lines from the currently focused script editor and sends them to the specified channel

| param | desc |
|-----------|-------------|
| `start` | number of lines before the current line (relative) |
| `end` | number of lines after the current line (relative) |
| `linetype` | line numbering method: `abs` (absolute), `rel` (relative), or `none` |
| `maxlength` | maximum length of the returned text, `0` for no limit |
| `channel` | channel to send the reply on |


## avatar

### `@resetskeleton[:target]=force`
resets the skeleton/ for a specified avatar or all avatars

| param | desc |
|-----------|-------------|
| `target` | (optional) `self` for your avatar, `all` for all nearby avatars, or specific avatar UUID |


### `@replaceprofiletext:<search>;<replace>=force`
replaces text in the user's profile with specified search and replace patterns

| param | desc |
|-----------|-------------|
| `search` | text pattern to search for |
| `replace` | text to replace with |


### `@camerashake:<intensity>;<duration>;<frequency>=force`
applies a camera shake effect

| param | desc |
|-----------|-------------|
| `intensity` | shake intensity |
| `duration` | duration in seconds |
| `frequency` | frequency of shake |


### `@scaleavatar:<uuid>;<scale>=force`
scales an avatar to the specified size

| param | desc |
|-----------|-------------|
| `uuid` | UUID of the avatar to scale |
| `scale` | scale multiplier, `0` for normal scale |


### `@avatarposition:<agent>;<x/y/z>;<anchor_uuid>;<update>=force`
sets or overrides the position of an avatar, with optional anchor to position relative to another object/avatar

| param | desc |
|-----------|-------------|
| `agent` | UUID of the avatar |
| `x/y/z` | position coordinates |
| `anchor_uuid`  | (optional) UUID of anchor object/avatar |
| `update`  | (optional) `0` to not update, `1` to update continously |


### `@avatarrotation:<agent>;<yaw>;<anchor_uuid>;<update>=force`
sets or overrides the rotation of an avatar, with optional anchor to rotate relative to another object/avatar

| param | desc |
|-----------|-------------|
| `agent` | UUID of the avatar |
| `yaw` | rotation in radians |
| `anchor_uuid`  | (optional) UUID of anchor object |
| `update` | (optional) update frequency |


### `@avataranim_start:<target>;<anim>;<priority>;<loop>;<local>=force`
starts an animation on the specified avatar

| param | desc |
|-----------|-------------|
| `target` | UUID of the avatar |
| `anim` | UUID of the animation |
| `priority` | animation priority |
| `loop` | `1` to loop, `0` to play once |
| `local` | `1` for local-only, `0` to play normally (user avatar only) |


### `@avataranim_stop:<target>;<anim>=force`
stops an animation on the specified avatar

| param | desc |
|-----------|-------------|
| `target` | UUID of the avatar |
| `anim` | UUID of the animation, or `all` to stop all |


### `@avataranim_list:<target>;<type>=<channel>`
lists active animations on the specified avatar

| param | desc |
|-----------|-------------|
| `target` | UUID of the avatar |
| `type` | type filter: <br/>`0` for all <br/>`1` for RLV-started only <br/>`2` for non-RLV only <br/>or object uuid for anims played by a specific object |
| `channel` | channel to send the reply on |

## hud message console
### `@hudmsg_update:<identifier>;<action>;<contents>=force`
updates the content of the specified console, if console does not exist, a new one is created

| param | desc |
|-----------|-------------|
| identifier | used to identify which console to affect |
| action | `0` to **replace** with new content<br/> `1` to **append** new content <br/> `2` to **prepend** new content
| contents | message content which supports various tags:<br/><br/>`{c:color}...{cr}` - sets text color, format: `R,G,B` or hex `RRGGBB` format <br/> `{i:uuid;width;height}` - displays an image with specific width and height <br/> `{al:left\|right\|center}` - align the current line <br/>`{ad:left\|right\|center}` - align the entire message <br/>`{b:width;height;channel;message}` - display a button with specific width/height, click sends the message on the channel<br/>`{ib:icon;width;height;channel;message}` - display an icon button with specific width and height, click sends the message on the channel

  
## `@hudmsg_read:<identifier>=<channel>`
retrieve the contents of the specified console, and send it via local chat on the specified channel

| param | desc |
|-----------|-------------|
| identifier | used to identify which console to affect |
| channel | the channel to send the reply on
  

## `@hudmsg_pos:<identifier>;<x>;<y>=force`
set the postion of the specified console

| param | desc |
|-----------|-------------|
| identifier | used to identify which console to affect |
| x | the position of the console on the horizontal axis |
| y | the position of the console on the vertical axis |


## `@hudmsg_size:<identifier>;<width>;<height>=force`
set the size of the specified console

| param | desc |
|-----------|-------------|
| identifier | used to identify which console to affect |
| width | width of the console
| height | height of the console |

## `@hudmsg_dur:<identifier>;<duration>=force`
set the duration that the specified console will be visible
| param | desc |
|-----------|-------------|
| identifier | used to identify which console to affect |
| duration | duration, in second, that the window will be visible<br/> use `0` to make permanently visible |
  

## `@hudmsg_vis:<identifier>;<visibility>=force`
change the visibility of the specified console

| param | desc |
|-----------|-------------|
| identifier | used to identify which console to affect |
| visibility | `0` to hide the window<br/> `1` to show the window  
  

## `@hudmsg_bg:<identifier>;<opacity>;<color>=force`
change the background of the specified console
  
| param | desc |
|-----------|-------------|
| identifier | used to identify which console to affect |
| opacity | value between `0.0` transparent and `1.0` opaque |
| color | format: `R/G/B` where each value is between `0.0` and `1.0`
  

## `@hudmsg_xbtn:<identifier>;<visible>=force`
make the window uncloseable (close button is hidden) or closeable (close button is visible)

| param | desc |
|-----------|-------------|
| identifier | used to identify which console to affect |
| visible | `0` close button is hidden<br/> `1` close button is visible
  

## `@hudmsg_resize:<identifier>;<resizeable>=force`
enable or disable the resize grip for the specified console

| param | desc |
|-----------|-------------|
|identifier | used to identify which console to affect |
| resizeable |  `0`  not resizeable (resize handles are hidden) <br/> `1` resizeable (resize handles are visible) |

  

## `@hudmsg_clear[:identifier]=force`
clear all consoles or a specific one, this removes the window itself, it's text, images, etc.

| param | desc |
|-----------|-------------|
| identifier | (optional) used to indentify which console to affect |
