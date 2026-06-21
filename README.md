[![Static Badge](https://img.shields.io/badge/Godot%20Engine-4.7.stable-blue?style=plastic&logo=godotengine)](https://godotengine.org/)
[![License](https://img.shields.io/github/license/dragonforge-dev/dragonforge-input-map-action?logo=mit)](https://github.com/dragonforge-dev/dragonforge-input-map-action/blob/main/LICENSE)
[![GitHub release badge](https://badgen.net/github/release/dragonforge-dev/dragonforge-input-map-action/latest)](https://github.com/dragonforge-dev/dragonforge-input-map-action/releases/latest)
[![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/dragonforge-dev/dragonforge-input-map-action)](https://img.shields.io/github/languages/code-size/dragonforge-dev/dragonforge-input-map-action)

# Dragonforge Input Map Action <img src="/addons/dragonforge_input_map_action/assets/textures/icons/input_map_action.svg" width="32" alt="Input Map Action Icon"/>
Helper class to create and add actions when a plugin is activated, and likewise remove actions when the plugin is deactivated.

# Version 1.0.1
For use with **Godot 4.7.stable** and later.

# Installation Instructions
1. Copy the `dragonforge_input_map_action/` folder from the `addons` folder into your project's `addons` folder.
2. Save your project.

# Usage Instructions
This is meant to be used in an editor plugin to add actions to the Input Map. What follows is an example,
```
@tool
extends EditorPlugin
const AUTOLOAD_CAMERA_2D_SIGNAL_BUS = "Camera2DSignalBus"
const MOVE_UP = "move_up"
const MOVE_DOWN = "move_down"
const MOVE_LEFT = "move_left"
const MOVE_RIGHT = "move_left"
const JUMP = "jump"
const FIRE = "fire"


func _enable_plugin() -> void:
	InputMapAction.add(MOVE_UP, InputMapAction.joy_axis(JOY_AXIS_LEFT_Y, InputMapAction.AXIS_UP), InputMapAction.key(KEY_UP), InputMapAction.key(KEY_W))
	InputMapAction.add(MOVE_DOWN, InputMapAction.joy_axis(JOY_AXIS_LEFT_Y, InputMapAction.AXIS_DOWN), InputMapAction.key(KEY_DOWN), InputMapAction.key(KEY_S))
	InputMapAction.add(MOVE_LEFT, InputMapAction.joy_axis(JOY_AXIS_LEFT_X, InputMapAction.AXIS_LEFT), InputMapAction.key(KEY_LEFT), InputMapAction.key(KEY_A))
	InputMapAction.add(MOVE_RIGHT, InputMapAction.joy_axis(JOY_AXIS_LEFT_X, InputMapAction.AXIS_RIGHT), InputMapAction.key(KEY_RIGHT), InputMapAction.key(KEY_D))
	InputMapAction.add(JUMP, InputMapAction.joy_button(JOY_BUTTON_A), InputMapAction.mouse_button(MOUSE_BUTTON_RIGHT), InputMapAction.key(KEY_SPACE))
	InputMapAction.add(FIRE, InputMapAction.joy_axis(JOY_AXIS_TRIGGER_RIGHT), InputMapAction.mouse_button(MOUSE_BUTTON_LEFT), InputMapAction.key(KEY_CTRL))
	print_rich("[color=yellow][b]WARNING[/b][/color]: Project must be reloaded for InputMap changes to appear. [color=ivory][b]Project -> Reload Current Project[/b][/color]")
	EditorInterface.restart_editor()

func _disable_plugin() -> void:
	InputMapAction.remove(MOVE_UP)
	InputMapAction.remove(MOVE_DOWN)
	InputMapAction.remove(MOVE_LEFT)
	InputMapAction.remove(MOVE_RIGHT)
	InputMapAction.remove(JUMP)
	InputMapAction.remove(FIRE)
	print_rich("[color=yellow][b]WARNING[/b][/color]: Project must be reloaded for InputMap changes to appear. [color=ivory][b]Project -> Reload Current Project[/b][/color]")
	EditorInterface.restart_editor()
```

# Class Descriptions
## InputMapAction <img src="/addons/dragonforge_input_map_action/assets/textures/icons/input_map_action.svg" width="32" alt="Input Map Action Icon"/>
<img src="/assets/textures/docs/doc_screen_shot_1.png" alt="Screenshot of in-editor docs."/>
<img src="/assets/textures/docs/doc_screen_shot_2.png" alt="Screenshot of in-editor docs."/>

### Constants
- `AXIS_UP = -1`
- `AXIS_DOWN = 1`
- `AXIS_LEFT = -1`
- `AXIS_RIGHT = 1`

### Public Functions
- `static func joy_axis(input: JoyAxis, direction: int = 0, device: int = -1) -> InputEventJoypadMotion` Returns an [InputEventJoypadMotion] event. Valid [param input] values are in [enum @GlobalScope.JoyAxis]. Valid [param direction] values are [member AXIS_UP], [member AXIS_DOWN], [member AXIS_LEFT], and [member AXIS_RIGHT]. [param device] indicates which gamepad device this action listens to and defaults to -1 (all gamepad devices).
- `static func joy_button(input: JoyButton, device: int = -1) -> InputEventJoypadButton` Returns an [InputEventJoypadButton] event. Valid [param input] values are in [enum @GlobalScope.JoyButton]. [param device] indicates which gamepad device this action listens to and defaults to -1 (all gamepad devices).
- `static func key(input: Key) -> InputEventKey` Returns an [InputEventKey] event. Valid [param input] values are in [enum @GlobalScope.Key].
- `static func mouse_button(input: MouseButton, device: int = -1) -> InputEventMouseButton` Returns an [InputEventMouseButton] event. Valid [param input] values are in [enum @GlobalScope.MouseButton]. [param device] indicates which pointer device this action listens to and defaults to -1 (all pointer devices).
- `static func add(action: StringName, ...events: Array) -> void` Adds [param action] to the [InputMap]. The [param events] argument accepts [float], [InputEventJoypadButton], [InputEventJoypadMotion], [InputEventKey], and [InputEventMouseButton]. It will ignore everything else. If a [float] is provided, the deadzone for the controller will be set to that value. Supported [InputEvent]s can be passed by using the functions [method joy_axis], [method joy_button], [method key], and [method mouse_button]. Alternately, they can be created manually and passed in.

# Credits

## Icons
- [Input Latin Uppercase](https://www.svgrepo.com/svg/396692/input-latin-uppercase) by googlefonts (Apache)
