---
title: "modUser.getSettings"
_old_id: "1344"
_old_uri: "2.x/developing-in-modx/other-development-resources/class-reference/moduser/moduser.getsettings"
---

## modUser::getSettings

Gets all user settings in array format.

## Syntax

API Doc: [http://api.modx.com/revolution/2.2/db\_core\_model\_modx\_moduser.class.html#%5CmodUser::getSettings()](http://api.modx.com/revolution/2.2/db_core_model_modx_moduser.class.html#%5CmodUser::getSettings())

``` php 
array getSettings ()
```

## Example

Get all the User Settings for this User.

``` php 
$settings = $user->getSettings();
```

## See Also

- [modUser](developing-in-modx/other-development-resources/class-reference/moduser "modUser")
- [Settings](administering-your-site/settings "Settings")