# Dragonforge Input Map Action

Helper class to create and add actions when a plugin is activated, and likewise remove actions when the plugin is deactivated. [br] [br] Plugin Example Code: [codeblock] @tool extends EditorPlugin

 const AUTOLOAD_CAMERA_2D_SIGNAL_BUS = "Camera2DSignalBus" const MOVE_UP = "move_up" const MOVE_DOWN = "move_down" const MOVE_LEFT = "move_left" const MOVE_RIGHT = "move_left" const JUMP = "jump" const FIRE = "fire"



 func _enable_plugin() -> void: Action.add(MOVE_UP, Action.joy_axis(JOY_AXIS_LEFT_Y, Action.AXIS_UP), Action.key(KEY_UP), Action.key(KEY_W)) Action.add(MOVE_DOWN, Action.joy_axis(JOY_AXIS_LEFT_Y, Action.AXIS_DOWN), Action.key(KEY_DOWN), Action.key(KEY_S)) Action.add(MOVE_LEFT, Action.joy_axis(JOY_AXIS_LEFT_X, Action.AXIS_LEFT), Action.key(KEY_LEFT), Action.key(KEY_A)) Action.add(MOVE_RIGHT, Action.joy_axis(JOY_AXIS_LEFT_X, Action.AXIS_RIGHT), Action.key(KEY_RIGHT), Action.key(KEY_D)) Action.add(JUMP, Action.joy_button(JOY_BUTTON_A), Action.mouse_button(MOUSE_BUTTON_RIGHT), Action.key(KEY_SPACE)) Action.add(FIRE, Action.joy_axis(JOY_AXIS_TRIGGER_RIGHT), Action.mouse_button(MOUSE_BUTTON_LEFT), Action.key(KEY_CTRL)) print_rich("[color=yellow][b]WARNING[/b][/color]: Project must be reloaded for InputMap changes to appear. [color=ivory][b]Project -> Reload Current Project[/b][/color]") EditorInterface.restart_editor()



 func _disable_plugin() -> void: Action.remove(MOVE_UP) Action.remove(MOVE_DOWN) Action.remove(MOVE_LEFT) Action.remove(MOVE_RIGHT) Action.remove(JUMP) Action.remove(FIRE) print_rich("[color=yellow][b]WARNING[/b][/color]: Project must be reloaded for InputMap changes to appear. [color=ivory][b]Project -> Reload Current Project[/b][/color]") EditorInterface.restart_editor() [/codeblock]

## Table of contents

### Functions

|Name|Type|Default|
|:-|:-|:-|
|[joy_axis](#joy_axis)|`JoyAxis`|-|
|[joy_button](#joy_button)|`JoyButton`|-|
|[key](#key)|`Key`|-|
|[mouse_button](#mouse_button)|`MouseButton`|-|
|[add](#add)|`StringName`|-|
|[remove](#remove)|`StringName`|-|

## Functions

### joy_axis

```gdscript
static func joy_axis(input: JoyAxis, direction: int = 0, device: int = -1) -> InputEventJoypadMotion
```

Returns an [InputEventJoypadMotion] event. Valid [param input] values are in [enum @GlobalScope.JoyAxis]. Valid [param direction] values are [member AXIS_UP], [member AXIS_DOWN], [member AXIS_LEFT], and [member AXIS_RIGHT]. [param device] indicates which gamepad device this action listens to and defaults to -1 (all gamepad devices).

**Returns**: `InputEventJoypadMotion`

#### Parameters

|Name|Type|Default|
|:-|:-|:-|
|`input`|`JoyAxis`|-|
|`direction`|`int`|`0`|
|`device`|`int`|`-1`|

### joy_button

```gdscript
static func joy_button(input: JoyButton, device: int = -1) -> InputEventJoypadButton
```

Returns an [InputEventJoypadButton] event. Valid [param input] values are in [enum @GlobalScope.JoyButton]. [param device] indicates which gamepad device this action listens to and defaults to -1 (all gamepad devices).

**Returns**: `InputEventJoypadButton`

#### Parameters

|Name|Type|Default|
|:-|:-|:-|
|`input`|`JoyButton`|-|
|`device`|`int`|`-1`|

### key

```gdscript
static func key(input: Key) -> InputEventKey
```

Returns an [InputEventKey] event. Valid [param input] values are in [enum @GlobalScope.Key].

**Returns**: `InputEventKey`

#### Parameters

|Name|Type|Default|
|:-|:-|:-|
|`input`|`Key`|-|

### mouse_button

```gdscript
static func mouse_button(input: MouseButton, device: int = -1) -> InputEventMouseButton
```

Returns an [InputEventMouseButton] event. Valid [param input] values are in [enum @GlobalScope.MouseButton]. [param device] indicates which pointer device this action listens to and defaults to -1 (all pointer devices).

**Returns**: `InputEventMouseButton`

#### Parameters

|Name|Type|Default|
|:-|:-|:-|
|`input`|`MouseButton`|-|
|`device`|`int`|`-1`|

### add

```gdscript
static func add(action: StringName, ...events: Array) -> void
```

Adds [param action] to the [InputMap]. The [param events] argument accepts [float], [InputEventJoypadButton], [InputEventJoypadMotion], [InputEventKey], and [InputEventMouseButton]. It will ignore everything else. [br][br] If a [float] is provided, the deadzone for the controller will be set to that value. [br][br] Supported [InputEvent]s can be passed by using the functions [method joy_axis], [method joy_button], [method key], and [method mouse_button]. Alternately, they can be created manually and passed in.

 [codeblock] const MOVE_UP = "move_up"

 Action.add(MOVE_UP, Action.joy_axis(JOY_AXIS_LEFT_Y, Action.AXIS_UP), Action.key(KEY_UP), Action.key(KEY_W)) [/codeblock]

#### Parameters

|Name|Type|Default|
|:-|:-|:-|
|`action`|`StringName`|-|
|`...events`|`Array`|-|

### remove

```gdscript
static func remove(action: StringName) -> void
```

Removes an action and all associated [InputEvent]s from the [InputMap].

 [codeblock] const MOVE_UP = "move_up"

 Action.remove(MOVE_UP) [/codeblock]

#### Parameters

|Name|Type|Default|
|:-|:-|:-|
|`action`|`StringName`|-|

## 📝 Licenses

- Documentation ([GDScriptify](https://github.com/hiulit/GDScriptify)): [MIT License](/LICENSE_GDSCRIPTIFY.txt).

---

Powered by [GDScriptify](https://github.com/hiulit/GDScriptify).
