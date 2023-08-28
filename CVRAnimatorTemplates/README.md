# CVR Animator Templates
A set of templates for basic animator tasks in cvr.

## Usage
### Simple
For just adding expressions and uploading, barely any customization.
1. Select the template you want to use.
2. Copy the template's override controller ({Template Name}Override.overrideController) somewhere.
3. Select your copy and fill the slots with any animations you want to change.
4. Drag your copy to the `Animation Overrides` field in your avatar's `CVR Avatar` component.
5. Drag your copy to the `Override Controller` field under the `Advanced Settings` section in your avatar's `CVR Avatar` component.
6. Add advanced settings corresponding to your selected template(see template descriptions below)
7. Upload and use.

### Advanced
This is for adding onto the templates and requires some more stuff.

1. Select the template you want to use.
2. Drag the template's controller to the `Base Animator` field under the `Advanced Settings` section of your avatar's `CVR Avatar` component.
3. Drag the template's coresponding override controller ({Template Name}Override) to the `Override Controller` field under the `Advanced Settings` section of your avatar's `CVR Avatar` component.
4. Add the advanced settings corresponding to your selected template(see template descriptions below).
5. Add additional advanced settings for other avatar features.
6. Press the `CreateAnimator` button at the bottom of the `Advanced Settings` section then press `Attach Created Override to Avatar`.
7. Your generated animators will be in `{Unity Project Path}\Assets\AdvancedSettings.Generated\{AvatarName}_AAS` (`{AvatarName}_aas.controller` and `{AvatarName}_aas_overrides.overrideController` )
8. Select the Override Controller and fill the animations with whatever you want to replace.
9. Further modifications should be done in the generated controller.
7. Once its all done, upload and use.

## Available Templates
### Expressive
Expressive templates are for adding basic gesture based expressions to your avatars.

There are two.
- `ExpressiveBlend`
	+ Adds left and right hand expressions in a single layer using direct blendtrees.
	+ Simplest and most performant.
	+ No control over transitions.
- `ExpressiveTraditional`
	+ Adds left and right hand expressions each in a seperate layer using transitions from `Any State`.
	+ Open hand and Fist gestures handled as a blendtree for blending between shapes(manual eye close, tounge stick out, etc...)
	+ Less effecient than ExpressiveBlend but offers more control.

Animations to replace in the override controllers are `Expr{Hand}{Gesture}`(So the animation on a right handed finger gun is `ExprRightGun`) Neither adds any aditional advanced settings.

### Scaling
Scaling templates are for adding scaling to an avatar to make it grow bigger or smaller.

There are four.
- `ScalingBlendTree`
	+ Most effecient and simple. Uses a single layer and blend tree.
	+ Needs the following AdvancedSettings
		* `AvatarScale`: Preferably a Slider but an Input Single is also usable.
	+ The override contoller allows you to replace the following animations
		* `ScaleMax`: The largest scale of the gameobject(usually the avatar)
		* `ScaleMin`: The smallest scale of the gameobject(usually the avatar)
		* `ScaleStandard`: The standard, default, or average scale of the gameobject(usually the avatar)
	+ `AvatarScale` is from 0 to 1 where 0 is smallest, 1 is largest, and 0.5 is standard.
- `ScalingBlendTreeTouchToggle`
	+ Like `ScalingBlendTree` but adds support for a toggle for touch triggers on the avatar(for scaling by touching your wrist for example.)
	+ Needs the following AdvancedSettings
		* `AvatarScale`: Preferably a Slider but an Input Single is also usable.
		* `TouchToggle`: Use a game object toggle for this.
	+ The override contoller allows you to replace the following animations
		* `ScaleMax`: The largest scale of the gameobject(usually the avatar)
		* `ScaleMin`: The smallest scale of the gameobject(usually the avatar)
		* `ScaleStandard`: The standard, default, or average scale of the gameobject(usually the avatar)
		* `TouchTogglesOn`: Animation enabling the touch toggles. This template assumes they are disabled on upload.
	+ `AvatarScale` is from 0 to 1 where 0 is smallest, 1 is largest, and 0.5 is standard.
- `ScalingMotionTime`
	+ Scales the avatar using a single animation and motion time.
	+ Needs the following AdvancedSettings
		* `AvatarScale`: Preferably a Slider but an Input Single is also usable.
	+ The override contoller allows you to replace the following animations
		* `ScaleCombined` An animation with at least two keyframes with the smallest and largest scales. A third in the middle is suggested for an "Average" scale.
	+ `AvatarScale` determines the avatar's scale by acting as `ScaleCombined`'s Motion time.
		* The "time" in the animation is determined by the remainder of the setting divided by 1
		* So a value of .5, 1.5, and 2.5 are all read as .5 or half way through the animation.
		* As well 1 is read as 0.
		* 0 is the first key frame, almost 1 is the last keyframe, and other values are between.
		* This means increasing/decreasing the scale with touch triggers can make the scale "loop".
		* Google the modulo operator idk.
- `ScalingMotionTimeTouchToggle`
	+ Like `ScalingMotionTime` but adds support for a toggle for touch triggers on the avatar(for scaling by touching your wrist for example.)
	+ Needs the following AdvancedSettings
		* `AvatarScale`: Preferably a Slider but an Input Single is also usable.
		* `TouchToggle`: Use a game object toggle for this.
	+ The override contoller allows you to replace the following animations
		* `ScaleCombined` An animation with at least two keyframes with the smallest and largest scales. A third in the middle is suggested for an "Average" scale.
		* `TouchTogglesOn`: Animation enabling the touch toggles.
		* `TouchTogglesOff`: Animation disabling the touch toggles. 
	+ `AvatarScale` determines the avatar's scale by acting as `ScaleCombined`'s Motion time.
		* The "time" in the animation is determined by the remainder of the setting divided by 1
		* So a value of .5, 1.5, and 2.5 are all read as .5 or half way through the animation.
		* As well 1 is read as 0.
		* 0 is the first key frame, almost 1 is the last keyframe, and other values are between.
		* This means increasing/decreasing the scale with touch triggers can make the scale "loop".
		* Google the modulo operator idk.
