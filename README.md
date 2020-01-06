# Figma Plugin DS Svelte

WORK IN PROGRESS—This is a version of the Figma Plugin DS specifically for use in creating Figma Plugins. I decided to create this because Svelte seems like a great lightweight approach well suited for creating Figma plugins, and also simplifies the developer experience over using the vanilla JS Figma Plugin DS that I created with easier markup.

You can also get started with [Figsvelte](https://github.com/thomas-lowry/figsvelte), a boilerplate for Figma plugins that already has this library setup as a dependency.

## Installation

To install into your own Svelte project.
`npm -D figma-plugin-ds-svelte`

## Usage

```javascript
//import the global css which includes Figma color, spacing, and type vars
//also includes a basic set of utility classes
import { GlobalCSS } from 'figma-plugin-ds-svelte';

//import the desired components
import { Button, Input, SelectMenu } from 'figma-plugin-ds-svelte';
```


## Components

### Button
```javascript
import { Button } from 'figma-plugin-ds-svelte';
```
```html
<Button on:click={funcName}>Label</Button>
<Button on:click={funcName} variant="secondary">Label</Button>
<Button on:click={funcName} variant="secondary" destructive>Label</Button>
<Button on:click={funcName} disabled>Label</Button>
```
**Props**

| Prop           | Type    | Options/notes                                               |
|:---------------|:--------|:------------------------------------------------------------|
| `variant`      | String  | Default: `"primary"`, Options: `"secondary"`, `"tertiary"`  |
| `disabled`     | Boolean | Default: `false`                                            |
| `desctructive` | Boolean | Default: `false`                                            |


### Checkbox
```javascript
import { Checkbox } from 'figma-plugin-ds-svelte';
```
```html
<Checkbox>Label</Checkbox>
<Checkbox checked>Label</Checkbox>
<Checkbox disabled>Label</Checkbox>
```
**Props**

| Prop       | Type    | Options/notes                                                                            |
|:-----------|:--------|:-----------------------------------------------------------------------------------------|
| `value`    | String  | Define checkbox value here.                                                              |
| `checked`  | Boolean | Default: `false`; You can bind the value when checked to a var. `bind:checked={varName}` |
| `disabled` | Boolean | Default: `false`  
