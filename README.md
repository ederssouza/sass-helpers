# Sass Helpers

## Mixins
See [_mixins.scss](https://github.com/ederssouza/sass-helpers/blob/master/scss/core/_mixins.scss).

### CSS3

#### animation

```scss
@mixin animation($str) {
  -webkit-animation: #{$str};
     -moz-animation: #{$str};
          animation: #{$str};
}

@mixin keyframes($animation-name) {
  @-webkit-keyframes #{$animation-name} {
    @content;
  }
  @-moz-keyframes #{$animation-name} {
    @content;
  }
  @keyframes #{$animation-name} {
    @content;
  }
}
```

#### background-size

```scss
@mixin background-size($size) {
  -webkit-background-size: $size;
     -moz-background-size: $size;
       -o-background-size: $size;
          background-size: $size;
}
```

#### border-radius

```scss
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
          border-radius: $radius;
}
```

#### box-shadow

```scss
@mixin box-shadow($args...) {
  -webkit-box-shadow: $args;
     -moz-box-shadow: $args;
          box-shadow: $args;
}
```

#### font-face

```scss
@mixin font-face($style-name, $file, $family, $category:'') {
  $filepath: $fonts-dir + '/' + $family + '/' + $file;
  @font-face {
    font-family: '#{$style-name}';
    src: url($filepath + '.eot');
    src: url($filepath + '.eot?#iefix') format('embedded-opentype'),
         url($filepath + '.woff') format('woff'),
         url($filepath + '.ttf')  format('truetype'),
         url($filepath + '.svg#' + $style-name + '') format('svg');
  }
  %#{$style-name} {
    font: {
      @if $category != '' {
        family: '#{$style-name}', #{$category};
      } @else {
        family: '#{$style-name}';
        weight: normal;
      }
    }
  }
}
```

#### linear-gradient

```scss
@mixin linear-gradient($from, $to) {
  background: $to;
	background: -moz-linear-gradient(top, $from 0%, $to 100%);
	background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,$from), color-stop(100%,$to));
	background: -webkit-linear-gradient(top, $from 0%,$to 100%);
	background: -o-linear-gradient(top, $from 0%,$to 100%);
	background: linear-gradient(to bottom, $from 0%,$to 100%);
}
```

#### opacity

```scss
@mixin opacity($opacity) {
  opacity: $opacity;
  $opacity-ie: $opacity * 100;
  filter: alpha(opacity = $opacity-ie);
}
```

#### tab-size

```scss
@mixin tab-size($size) {
  -webkit-tab-size: #{$size};
     -moz-tab-size: #{$size};
       -o-tab-size: #{$size};
          tab-size: #{$size};
}
```

#### transform

```scss
@mixin transform($args...) {
  -webkit-transform: #{$args};
     -moz-transform: #{$args};
      -ms-transform: #{$args};
          transform: #{$args};
}
```

#### transition

```scss
@mixin transition($args...) {
  -webkit-transition: $args;
     -moz-transition: $args;
       -o-transition: $args;
          transition: $args;
}
```

### Helpers

#### center-vertical

```scss
@mixin center-vertical($position: absolute) {
  left: 50%;
  position: $position;
  top: 50%;
  @include transform(translate(-50%, -50%));
}
```

#### sprite

```scss
@mixin sprite($file, $position, $width, $height) {
  background-image: url($img-dir + '/' + $file);
  background-position: $position;
  height: $height;
  width: $width;
}
```

## Functions
See [_functions.scss](https://github.com/ederssouza/sass-helpers/blob/master/scss/core/_functions.scss).


### Convert px to em

```scss
@function em($pixels, $context: $browser-context) {
  @return ($pixels / $context) * 1em;
}
```

## Placeholders
See [_placeholders.scss](https://github.com/ederssouza/sass-helpers/blob/master/scss/core/_placeholders.scss).

#### placeholder input

```scss
%placeholder {
  &.placeholder { @content; }
  &::-webkit-input-placeholder { @content; }
  &::-moz-placeholder { @content; }
  &:-moz-placeholder { @content; }
  &:-ms-input-placeholder { @content; }
}
```

#### center-block

```scss
%center-block {
  display: block;
  margin: {
    left:  auto;
    right:  auto;
  }
}
```

#### clearfix

```scss
%clearfix {

  &:before,
  &:after {
    clear: both;
    content: "";
    display: block;
  }
}
```

## License

[MIT License](http://ederssouza.mit-license.org/) &copy; Eder Sampaio