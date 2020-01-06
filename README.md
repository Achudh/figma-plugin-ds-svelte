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
_All components can accept class props to add global or utility classes to each component_

---

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
| `on:click`     | Func    | Assign a function to run on click. Ex: `on:click={funcName}`|
| `variant`      | String  | Default: `"primary"`, Options: `"secondary"`, `"tertiary"`  |
| `disabled`     | Boolean | Default: `false`                                            |
| `desctructive` | Boolean | Default: `false`                                            |

---

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
| `disabled` | Boolean | Default: `false`                                                                         |

---

### Disclosure
```javascript
import { Disclosure, DisclosureItem } from 'figma-plugin-ds-svelte';
```
```html
<Disclosure>
  <DisclosureItem title="Item 1" open>Content here</DisclosureItem>
  <DisclosureItem title="Item 2">Content here</DisclosureItem>
  <DisclosureItem title="Item 3">Content here</DisclosureItem>
</Disclosure>
```
**Props**

| Prop    | Type    | Options/notes                                                     |
|:--------|:--------|:------------------------------------------------------------------|
| `title` | String  | Title of disclosure item                                          |
| `open`  | Boolean | Default: `false`; Only one disclosure item can be opened at once. |

---

### Icon
```javascript
//You need to import the icon component + whatever icons you want to use,
//pass the names of your icon modules to the iconName prop in the Icon component
import { Icon, IconName } from 'figma-plugin-ds-svelte';

//You can also import your own svg icon (32x32) and pass it to the icon component
import SvgName from './src/directory/image.svg';

//Example
import { Icon, IconVisible, IconSpinner } from 'figma-plugin-ds-svelte';
```
```html
<Icon iconName={IconVisible} color="black"/>
<Icon iconName={IconSpinner} color="blue" spin/>
<Icon iconText="W" color="blue"/>
```
**Props**

| Prop       | Type    | Options/notes                                                                                |
|:-----------|:--------|:---------------------------------------------------------------------------------------------|
| `iconName` | Var     | Pass an imported SVG to this prop. `iconName={IconImport}`                                   |
| `iconText` | String  | Pass a text character to use instead of an icon. Ex: width and height inputs `iconText="W"`  |
| `color`    | String  | Pass the name of any Figma color var to this prop. `color="blue"`                            |
| `spin`     | Boolean | Default: `false`; This will rotate the icon in an endless loop.                              |

---

### Input
```javascript
import { Input } from 'figma-plugin-ds-svelte';
```
```html
<Input value="Value"/>
<Input value="Value" disabled/>
<Input placeholder="Enter some info..."/>

<!-- You can also pass Icon props to use the icon component inside the input -->
<Input iconName={IconName} />
<Input iconName={IconSpinner} spin placeholder="Fetching data..." />

<!-- Force borders on the input -->
<Input value="Value" borders/>
```
**Props**

| Prop          | Type    | Options/notes                                                      |
|:--------------|:--------|:-------------------------------------------------------------------|
| `on:change`   | Func    | Funtion to execute on change. Ex: `on:change={funcName}`           |
| `value`       | String  | Value that will get populated by user or specify predefined value. |
| `placeholder` | String  | Placeholder text.                                                  |
| `borders`     | Boolean | Default: `false`; Force a border on the input field.               |
| `disabled`    | Boolean | Default: `false`                                                   |
| `iconName`    | Var     | _See Icon component for usage._                                    |
| `iconText`    | String  | _See Icon component for usage._                                    |
| `spin`        | Boolean | _See Icon component for usage._                                    |

---

### Label + Section
```javascript
import { Label, SectionHeader } from 'figma-plugin-ds-svelte';
```
```html
<Label>Label name</Label>
<Section>Section name</Section>
```

---

### Onboarding Tip
```javascript
import { OnboardingTip } from 'figma-plugin-ds-svelte';
```
```html
<OnboardingTip iconName={IconStyles}>
  Tip text goes here
</OnboardingTip>
```
**Props**

| Prop       | Type    | Options/notes                   |
|:-----------|:--------|:--------------------------------|
| `iconName` | Var     | _See Icon component for usage._ |
| `iconText` | String  | _See Icon component for usage._ |
| `spin`     | Boolean | _See Icon component for usage._ |

---

### Radio Button
```javascript
import { Radio } from 'figma-plugin-ds-svelte';

//use bind:group, with a var to create a radio group and store the value of selected item
//set value if this var to same value as radio item to set initial selection
var radioValue;
```
```html
<Radio bind:group={radioValue} value="a">Label</Radio>
<Radio bind:group={radioValue} value="b">Label</Radio>
```
**Props**

| Prop       | Type    | Options/notes                                             |
|:-----------|:--------|:----------------------------------------------------------|
| `on:change`| Func    | Funtion to execute on change. Ex: `on:change={funcName}`  |
| `group`    | Var     | Pass name of var to store selected item from radio group. |
| `value`    | String  | Value of radio item.                                      |
| `disabled` | Boolean | Default: `false`                                          |

---

### Select Menu
```javascript
import { SelectMenu } from 'figma-plugin-ds-svelte';

//You will need to pass and bind an array of menu items to this
//Note: it is up to you to sort this array however you want
let menuItemArray = [
  { 'value': 'item1', 'label': 'Menu item 1', 'group': null, 'selected': false },
  { 'value': 'item2', 'label': 'Menu item 2 ', 'group': null, 'selected': false }
];

//use bind:value, with a var bind the data of the selected item
var selectedItem;
```
```html
<SelectMenu bind:menuItems={menuItemArray} bind:value={selectedItem}/>
```
**Props**

| Prop              | Type    | Options/notes                                                                                                                            |
|-------------------|---------|------------------------------------------------------------------------------------------------------------------------------------------|
| `on:change`       | Func    | Function to execute on change. Ex: `on:change={funcName}`                                                                                |
| `menuItems`       | Var     | Pass in array of menu item objects. See example above for format.  If you want to use option groups, update the group keys to a string.  |
| `value`           | Var     | Bind the value of the selected item to a var. Example: `bind:value={selectedItem}`                                                       |
| `placeholder`     | String  | Override default placeholder text with a string when there is no item selected.                                                          |
| `showGroupLabels` | Boolean | Default: `false`; If you are using option groups, this will show the group labels.                                                       |
| `disabled`        | Boolean | Default: `false`                                                                                                                         |
| `macOSBlink`      | Boolean | Default: `false`; Easter egg, old school Mac OS triple blink on select.                                                                  |
| `iconName`        | Var     | _See Icon component for usage._                                                                                                          |
| `iconText`        | String  | _See Icon component for usage._                                                                                                          |

---

## Tokens

**Color**

**Type**

**Shadows**

**Border Radius**

**Sizes**
