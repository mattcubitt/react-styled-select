
[![Issues](https://img.shields.io/github/issues/agutoli/react-styled-select.svg)](https://github.com/agutoli/react-styled-select/issues) [![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://www.npmjs.com/package/react-styled-select)
[![Build Status](https://travis-ci.org/agutoli/react-styled-select.svg?branch=master)](https://travis-ci.org/agutoli/react-styled-select)
[![NPM](https://img.shields.io/npm/v/react-styled-select.svg)](https://www.npmjs.com/package/react-styled-select)



react-styled-select
============
### ATTENTION: Work in Progress (sorry about that!)

This project was built with [styled-components](https://github.com/styled-components/styled-components) and is a "rethink" of the awesome project [react-select](https://github.com/JedWatson/react-select). But what the differences between [react-select](https://github.com/JedWatson/react-select) and this project?

* Lightweight!
* It don`t force you to load any external css.
* Works with css-modules concept and not with global class names. Here has a good discussion about this problem ([here](https://github.com/oliviertassinari/a-journey-toward-better-style)).
* [CSS Variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_variables): Very easy to customize for your need.
* [Shadow DOM](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Shadow_DOM): If you has or had problems with input fields globally stylized you can "encapsulate" your component using this awesome feature.

## Installation

`npm install react-styled-select --save`

## Demo

[http://agutoli.github.io/](http://agutoli.github.io/)

## Example Usage

    import React from 'react'
    import Select from 'react-styled-select'

    class MyComp extends React.Component {
      render() {
        const options = [
          { label: "One", value: 1},
          { label: "Two", value: 2},
        ]
        return (
          <Select
            options={options}
            onOpen={myOpenFunc}
            onChange={myChangeFunc}
            classes={{
              selectValue: 'my-custom-value',
              selectArrow: 'my-custom-arrow'
            }}
          />
        )
      }
    }



## Opptions

| Property | Type | Default | Description
:---|:---|:---|:---
| `classes` | object | `undefined` | You can specify `className` for each element. Possible values: `selectArrow`, `selectArrowZone`, `selectClear`, `selectClearZone`, `selectControl`, `selectInput`, `selectInputField`, `selectMenu`, `selectMenuOuter`, `selectMultiValueWrapper`, `selectOption`, `selectPlaceholder`, `selectValue`, `selectValueLabel`
|`clearable` | bool | `false` | should it be possible to reset value
|`searchable`| bool | `true` | whether to enable searching feature or not
|`placeholder`| string | `Select...` | The short hint is displayed in the input field before the user enters a value
| `loadOptions` | function | `undefined` | function that returns a promise or calls a callback with the options: `function(input, [callback])`
| `className` | string | `undefined` | Root element className
| `value` | any | `undefined` | If you want to specify a pre selected value
| `options` | array | `[]` | List of values. Ex. <br> `[{"label": "Foo", value: "foo"}]`
|`onOpen`| function | `undefined` | It calls when open outer menu
|`onChange`| function | `undefined` | It calls when change selected value
|`onValueClick`| function | `undefined` | It calls when click over a option value
|`onInputClear`|function| `undefined` | It calls when input is cleared
|`valueRenderer`|function| `undefined` | function which returns a custom way to render the value selected function (option) {}
|`optionRenderer`|function| `undefined` | function which returns a custom way to render the options in the menu (option) {}

## Async options (NEW)

Very similar with `react-select` API.

    var getOptions = function(input, callback) {
      setTimeout(function() {
        callback(null, {
          options: [
            { value: 'one', label: 'One' },
            { value: 'two', label: 'Two' }
          ]
        });
      }, 500);
    };

    <Select.Async
        loadOptions={getOptions}
    />

## Custom appearance with CSS Variebles

#### Multi Select (NEW)
![](https://image.ibb.co/h69O2Q/print_multi_select.png)

#### Default
![](https://image.ibb.co/bC4i7k/Captura_de_Tela_2017_06_27_a_s_03_18_09.png)

#### Customized
![](https://image.ibb.co/bSei7k/Captura_de_Tela_2017_06_27_a_s_03_17_59.png)

* Your react file ex. `MyForm.jsx`

```javascript
class MyForm extends React.Component {
  render() {
    return(){
      <Select className="dark-theme" options={[...]} />
    }
  }
}
```

* Your project CSS file ex. `mysite.css`

```css
.dark-theme {
  --styled-select-placeholder__color: #999;
  --styled-select__color: white;
  --styled-select__background-color: #555;
  --styled-select__border-color: black;
  --styled-select__border-width: 3px;
  --styled-select__border-radius: 5px;

  --styled-select-menu-outer__margin: 10px 0 0 0;
  --styled-select-menu-outer__padding: 0;
  --styled-select-menu-outer__background-color: #555;
  --styled-select-menu-outer__border-color: black;
  --styled-select-menu-outer__border-style: solid;
  --styled-select-menu-outer__border-width: 3px;

  --styled-select-option__background-color: #444;

  --styled-select-option__color--focused: #eee;
  --styled-select-option__background-color--focused: #333;

  --styled-select-option__color--selected: #eee;
  --styled-select-option__background-color--selected: #444;
}
```

## Available CSS variables

<pre>
--styled-<b>select</b>__color: #777;
--styled-<b>select</b>__background-color: #fff;
--styled-<b>select</b>__border-radius: 2px;
--styled-<b>select</b>__border-style: solid;
--styled-<b>select</b>__border-width: 1px;
--styled-<b>select-arrow</b>__size: 8;
--styled-<b>select-arrow</b>__color: #9b9ba5;
--styled-<b>select-clear</b>__color: #999;
--styled-<b>select-clear</b>__font-size: 14px;
--styled-<b>select-control</b>__min-height: 36px;
--styled-<b>select-control</b>__border-color: #dcdce3;
--styled-<b>select-control</b>__border-color--focused: #40a3f5;
--styled-<b>select-input</b>__height: 23px;
--styled-<b>select-input</b>__padding: 0;
--styled-<b>select-input</b>__line-height: 23px;
--styled-<b>select-menu</b>__max-height: 198px;
--styled-<b>select-menu-outer</b>__max-height: 200px;
--styled-<b>select-menu-outer</b>__background-color: #fff;
--styled-<b>select-menu-outer</b>__border-color: #f0f0f5;
--styled-<b>select-menu-outer</b>__border-radius: 2px;
--styled-<b>select-menu-outer</b>__border-style: solid;
--styled-<b>select-menu-outer</b>__border-width: 1px;
--styled-<b>select-menu-outer</b>__box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
--styled-<b>select-menu-outer</b>__margin: 5px 0 0 0;
--styled-<b>select-menu-outer</b>__padding: 0;
--styled-<b>select-no-results</b>__color: #999;
--styled-<b>select-no-results</b>__padding: 8px 10px;
--styled-<b>select-no-results</b>__font-size: 14px;
--styled-<b>select-no-results</b>__font-family: Tahoma, Helvetica, Arial, sans-serif;
--styled-<b>select-option</b>__font-family: Tahoma, Helvetica, Arial, sans-serif;
--styled-<b>select-option</b>__color--focused: #333;
--styled-<b>select-option</b>__color--selected: #333;
--styled-<b>select-option</b>__background-color: #fff;
--styled-<b>select-option</b>__background-color--focused: #f0f0f5;
--styled-<b>select-option</b>__background-color--selected: #ddd;
--styled-<b>select-placeholder</b>__padding: 0 10px;
--styled-<b>select-placeholder</b>__color: #d2d2d9;
--styled-<b>select-placeholder</b>__font-family: Tahoma, Helvetica, Arial, sans-serif;
--styled-<b>select-placeholder</b>__font-size: 12px;
--styled-<b>select-placeholder</b>__line-height: 34px;
--styled-<b>select-value</b>__color: Tahoma, Helvetica, Arial, sans-serif;
--styled-<b>select-value</b>__line-height: 34px;
--styled-<b>select-value</b>__max-width: 100%;
--styled-<b>select-value</b>__overflow: hidden;
--styled-<b>select-value</b>__padding: 0 5px;
--styled-<b>select-value</b>__text-overflow: ellipsis;
--styled-<b>select-value</b>__white-space: nowrap;
--styled-<b>select-value-label</b>__padding: 1px 6px;
--styled-<b>select-value-label</b>__font-family: Tahoma, Helvetica, Arial, sans-serif;
--styled-<b>select-value-icon</b>__background-color: transparent;
--styled-<b>select-value-icon</b>__background-color--hover: rgba(0, 0, 0, 0.1);
--styled-<b>select-value-icon</b>__font-family: arial;
--styled-<b>select-value-icon</b>__padding: 1px 5px;
--styled-<b>select-multi-value</b>__font-size: 0.9em;
--styled-<b>select-multi-value</b>__line-height: 1.4;
--styled-<b>select-multi-value</b>__margin: 2px 5px 2px 0;
--styled-<b>select-multi-value</b>__background-color: #eee;
--styled-<b>select-multi-value</b>__border: 1px solid #aaa;
--styled-<b>select-multi-value</b>__border--hover: 1px solid #777;
--styled-<b>select-multi-value</b>__border-radius: 3px;
--styled-<b>select-multi-value</b>__box-shadow: rgba(0,0,0,0.2) 0px 0px 3px;
--styled-<b>select-multi-value-wrapper</b>__padding: 3px 0 3px 5px;
</pre>

## Inspiration
This project was based on [react-select](https://github.com/JedWatson/react-select).

## License

The MIT License (MIT)

Copyright (c) 2017 Bruno Agutoli

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
