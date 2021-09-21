# VScode Notes

## Side by Side Editing
- `crtl + \` to split screen

## Switching Panes
- use `ctrl + <number>` to switch between tabs

## Switching Split Panes
- use `cmd + <number>` to switch between split panes

## Sidebar
- `cmd + b` to toggle sidebar

## Copy Line Up/Down
- `shift + alt + up/down` to copy line up/down

## Move Line Up/Down
- `alt + up/down` to move line up/down
<br>

## Close Current Pane
- `cmd + w` to close current pane
<br>

## Import Path Shortcut
- reduce long relative import paths by mapping keywords
```
// create jsconfig.json in home directory
{
	"compilerOptions": {
		"baseUrl": "./",
		"paths": {
			"@components/*": ["components/*"],
			"@styles/*": ["styles/*"],
			"@libs/*": ["libs/*"],
		}
	}
}

// js file
import styles from '../../../styles/style.css'
// new way
import styles from '@styles';
```
<br>

## Focusing Explorer
- `cmd + 0` to focus on the explorer file panel
- navigate using up/down arrows and `enter` to view/open file
<br>

## Tab Through Open Files
- use `ctrl + TAB` to switch open tabs
- you can also use `ctrl + <number>` to switch to a ordered tabs list
<br>

## Open Terminal
```
- use ctrl + ` to open/close terminal
```
<br>

## Shortcut Color Selection
- you can type `--` instead of `var(...)` when using a declared CSS color variable
```
// CSS
:root {
	--primary-color: #FFF
}

.btn-class {
	background-color: var(--primary-color);

// alternative
	background-color: --primary-color;
}
```
<br>

## Sorting CSS Properties
- highlight lines, open command palette and search `Sort Lines Ascending/Descending`

```
// unsorted
.some-css-class {
	position: absolute;
	margin: 0;
	top: 0;
	left: 0;
	padding: 30px;
	height: 100%;
	width: 100%;
	display: flex;
	align-items: flex-end
}

// sorted ascending
.some-css-class {
	align-items: flex-end;
	display: flex;
	height: 100%;
	left: 0;
	margin: 0;
	padding: 30px;
	position: absolute;
	top: 0;
	width: 100%;
}
```
<br>

## Return to Previous Line
- use `alt + left arrow` to return to previous line afer scrolling away
<br>
