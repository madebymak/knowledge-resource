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