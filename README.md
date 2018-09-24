# Sass Helpers

[![npm version](http://img.shields.io/npm/v/@ederssouza/sass-helpers.svg)](https://npmjs.org/package/@ederssouza/sass-helpers)

Functions, mixins and placeholders for speed up your development process.

## Installation

```bash
npm install @ederssouza/sass-helpers --save-dev
```

## How to use

Import the global `index.scss` file in your project.

```scss
@import '~@ederssouza/sass-helpers';
```

## Mixins
See [mixins.scss](https://github.com/ederssouza/sass-helpers/blob/master/src/_mixins.scss).

### CSS3 animation

#### scss
```scss
.icon {
  width: 100px;
  height: 100px;
  background-color: red;
  @include animation(changeBg 4s);
}

@include keyframes(changeBg) {
  from {background-color: red;}
  to {background-color: yellow;}
}
```

#### css compiled
```css
.icon {
  width: 100px;
  height: 100px;
  background-color: red;
  -webkit-animation: changeBg 4s;
  -moz-animation: changeBg 4s;
  animation: changeBg 4s;
}

@-webkit-keyframes changeBg {
  from {
    background-color: red;
  }
  to {
    background-color: yellow;
  }
}

@-moz-keyframes changeBg {
  from {
    background-color: red;
  }
  to {
    background-color: yellow;
  }
}

@keyframes changeBg {
  from {
    background-color: red;
  }
  to {
    background-color: yellow;
  }
}
```

### CSS3 background-size

#### scss
```scss
.container {
  @include background-size(cover);
}
```

#### css compiled
```css
.container {
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
}
```

### CSS3 border-radius

#### scss
```scss
.container {
  @include border-radius(4px);
}
```

#### css compiled
```css
.container {
  -webkit-border-radius: 4px;
  -moz-border-radius: 4px;
  border-radius: 4px;
}
```

### CSS3 box-shadow

#### scss
```scss
.container {
  @include box-shadow(1px 1px 2px rgba(#000, .8));
}
```

#### css compiled
```css
.container {
  -webkit-box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.8);
  -moz-box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.8);
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.8);
}
```

### CSS3 @font-face

#### scss
```scss
$fonts-dir: '../fonts';

@include font-face('Roboto', 'roboto', 'regular');
```

#### css compiled
```css
@font-face {
  font-family: "Roboto";
  src: url("../fonts/regular/roboto.eot");
  src: url("../fonts/regular/roboto.eot?#iefix") format("embedded-opentype"), url("../fonts/regular/roboto.woff") format("woff"), url("../fonts/regular/roboto.ttf") format("truetype"), url("../fonts/regular/roboto.svg#Roboto") format("svg");
}
```

### CSS3 linear-gradient

#### scss
```scss
.container {
  @include linear-gradient(red, orange);
}
```

#### css compiled
```css
.container {
  background: orange;
  background: -moz-linear-gradient(top, red 0%, orange 100%);
  background: -webkit-gradient(linear, left top, left bottom, color-stop(0%, red), color-stop(100%, orange));
  background: -webkit-linear-gradient(top, red 0%, orange 100%);
  background: -o-linear-gradient(top, red 0%, orange 100%);
  background: linear-gradient(to bottom, red 0%, orange 100%);
}
```

### opacity

#### scss
```scss
.container {
  @include opacity(.5);
}
```

#### css compiled
```css
.container {
  opacity: 0.5;
  filter: alpha(opacity=50);
}
```

### CSS3 placeholder input

#### scss
```scss
input, textarea {

  @include placeholder {
    font-style:italic;
  }
}
```

#### css compiled
```css
input::-webkit-input-placeholder, textarea::-webkit-input-placeholder {
  font-style: italic;
}

input::-moz-placeholder, textarea::-moz-placeholder {
  font-style: italic;
}

input:-moz-placeholder, textarea:-moz-placeholder {
  font-style: italic;
}

input:-ms-input-placeholder, textarea:-ms-input-placeholder {
  font-style: italic;
}
```

### tab-size

#### scss
```scss
pre {
  @include tab-size(2);
}
```

#### css compiled
```css
pre {
  -webkit-tab-size: 2;
  -moz-tab-size: 2;
  -o-tab-size: 2;
  tab-size: 2;
}
```

### CSS3 transform

#### scss
```scss
.icon {
  @include transform(scale(1.5));
}
```

#### css compiled
```css
.icon {
  -webkit-transform: scale(1.5);
  -moz-transform: scale(1.5);
  -ms-transform: scale(1.5);
  transform: scale(1.5);
}

```

### CSS3 transition

#### scss
```scss
button {
  background-color: #fff;
  @include transition(background-color .26s);

  &:hover {
    background-color: #333;
  }
}
```

#### css compiled
```css
button {
  background-color: #fff;
  -webkit-transition: background-color 0.26s;
  -moz-transition: background-color 0.26s;
  -o-transition: background-color 0.26s;
  transition: background-color 0.26s;
}

button:hover {
  background-color: #333;
}
```

## Helpers

### center-vertical

#### scss
```scss
.icon {
  height: 100px;
  width: 100px;
  @include center-vertical;
}
```

#### css compiled
```css
.icon {
  height: 100px;
  width: 100px;
  left: 50%;
  position: absolute;
  top: 50%;
  -webkit-transform: translate(-50%, -50%);
  -moz-transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}
```

### sprite

#### scss
```scss
$img-dir: '../img';

.icon {
  @include sprite('sprite-icon.png', '0 50px', 50px, 50px);
}
```

#### css compiled
```css
.icon {
  background-image: url("../img/sprite-icon.png");
  background-position: "0 50px";
  height: 50px;
  width: 50px;
}
```

## Functions
See [functions.scss](https://github.com/ederssouza/sass-helpers/blob/master/src/_functions.scss).


### Convert px to em

#### scss
```scss
$browser-context: 16;

.container {
  font-size: em(14)
}
```

#### css compiled
```css
.container {
  font-size: 0.875em;
}
```

## Placeholders
See [placeholders.scss](https://github.com/ederssouza/sass-helpers/blob/master/src/_placeholders.scss).


### center-block

#### scss
```scss
.container {
  @extend %center-block;
}
```

#### css compiled
```css
.container {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
```

### clearfix

#### scss
```scss
.container {
  @extend %clearfix;
}
```

#### css compiled
```css
.container:before,
.container:after {
  clear: both;
  content: "";
  display: block;
}
```

## License

[MIT License](http://ederssouza.mit-license.org/) &copy; Eder Sampaio