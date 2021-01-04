# Eslint Notes

## Setup Eslint
- setup package.json if needed with `npm init`
- install to eslint to local folder with `npm install eslint --save-dev`
- setup eslint file with `npxeslint --init`
- use airbnb style and set format to be JSON

<br>

## Sample .eslintrc.json
```
{
    "env": {
        "browser": true,
        "es2021": true,
        "jquery": true // turns jQuery on
    },
    "extends": [
        "airbnb-base"
    ],
    "parserOptions": {
        "ecmaVersion": 12
    },
    "rules": {
        "indent": ["error", 4] // sets indent to 4
        "linebreak-style": 0 // turns off LF vs CRLF
    }
}
```
<br>

## Eslint Disable
- place at beginning of file you don't want checked

```
/* eslint-disable */

    // code you don't want linted

/* eslint-enable */

    // rest of the code
```
<br>

## Ignore next line
```
// eslint-disable-next-line
```
