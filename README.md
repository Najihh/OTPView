# OTPView
[![](https://jitpack.io/v/Najihh/OTPView.svg)](https://jitpack.io/#Najihh/OTPView)

 Heavily customizable OTP or Pin View. **Note**:OTPView is still in early stages

## Description

OTPView is meant to be a highly customizable OTP / Pin View for android. It supports customization for text styling, background styling, and dimensional styling. It defines the view as 4 segments:
* The Highlighted Item
* The Empty Item
* The filled Item
* The error Item

Each type can be customized separately, with the empty item being the default.

The OTPView also supports some android standards such as `android:inputType`, `android:importantForAutofill` and `android:autofillHints` so you can easily set options like numbers/string, allcaps, etc.

## Install

```
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}

dependencies {
    implementation 'com.github.Najihh:OTPView:0.1.1'
}
```


![IMG](/images/example.png)

## Attributes

| Attribute | Format | Description | Default |
|-----------|--------|-------------|---------|
| otp_itemCount | integer | The length of the input | 1 |
| otp_showCursor | boolean | Should show cursor | false |
| otp_itemWidth | dimension | width of each item | 44dp |
| otp_itemHeight | dimension | height of each item | 44dp |
| otp_cursorColor | color | color of the cursor | Black |
| otp_underscoreCursor (Experimental) | boolean | if true will show '_' instead of '|' for the cursor | false |
| otp_customCursor | drawable | custom drawable for the cursor, overrides otp_underscoreCursor | null |
| otp_allcaps | boolean | all caps(if fails set input type) | false |
| otp_marginBetween | dimension | margin between each item horizontally | 8dp |
| otp_isPassword | boolean | sets previously entered items as hidden | false |
|  |  |  |  |
| otp_textSize | dimension | The text size of items past the cursor | 14dp |
| otp_textColor | integer | The text color of items past the cursor | Black |
| otp_backgroundImage | reference | The background image of items past the cursor | N/A |
| otp_Font | reference | The font of items past the cursor | N/A |
|  |  |  |  |
| otp_highlightedTextSize | dimension |  The text size of the highlighted item | otp_textSize |
| otp_highlightedTextColor | integer | The text color of the highlighted item | otp_textColor |
| otp_highlightedBackgroundImage | reference | The background image of the highlighted item | otp_backgroundImage |
| otp_highlightedFont | reference | The font of the highlighted item | otp_Font |
|  |  |  |  |
| otp_filledTextSize | dimension | The text size of items before the cursor | otp_textSize |
| otp_filledTextColor | integer | The text color of items before the cursor | otp_textColor |
| otp_filledBackgroundImage | reference | The background image of items before the cursor| otp_backgroundImage |
| otp_filledFont | reference | The font of items before the cursor | otp_Font |
|  |  |  |  |
| otp_errorTextSize | dimension | The text size of items before the cursor when error state | otp_textSize |
| otp_errorTextColor | integer | The text color of items before the cursor when error state | otp_textColor |
| otp_errorBackgroundImage | reference | The background image of items before the cursor when error state | otp_backgroundImage |
| otp_errorFont | reference | The font of items before the cursor when error state | otp_Font |

## API
* `fun showError()` - call error state view
* `fun hideError()` - hide error state view

* `fun setOnFinishListener(func: (String) -> Unit)` - Simple listener callback for when all items have been filled
```
otp_view.setOnFinishListener {
    Toast.makeText(this,it,Toast.LENGTH_LONG).show()
}
```
* `fun setOnCharacterUpdatedListener(func: (Boolean) -> Unit)` - listener callback for when a character was updated. Returns whether or not it was filled.

* `fun setText(str:String)` - Fills in as much of the text into the items as possible, with one character for each item. Overflow characters are discarded.
* `fun clearText(showKeyboard: Boolean)` - Clears all the text, also has the option to hide or show the keyboard on the first item.

* `fun copyText(showKeyboard: Boolean)` - Copies text from OTP View.
* `fun pasteText(showKeyboard: Boolean)` - Pastes text from OTP View, paste menu item should be overridden from Activity.

* `fun fitToWidth(width: Int)` - Fits the entire view to the width entered. Made so that you can dynamically resize the view.
* `fun isFilled(): Boolean` - Returns whether or not all the fields have been filled.
* `fun getStringFromFields(): String` - Returns the string from the view.
* `override fun setEnabled(enabled: Boolean)` - Allows you to disable the view as you normally would.
