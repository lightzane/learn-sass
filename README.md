# learn-sass

Learning `SASS` (https://sass-lang.com/) to generate `CSS` stylesheets

```
npm i -D sass
```

# Getting Started

```
npm install
npm start
```

# Content

1. [Variables](#variables)
2. [Maps](#maps)
3. [Mixins](#mixins)

## Variables

```scss
$mac-red: #ff605c;
$mac-orange: #ffbd44;
$mac-green: #00ca4e;
```

## Maps

Are like enums.

`scss`

```scss
@use 'sass:map';

$font-weights: (
  'regular': 400,
  'medium': 500,
  'bold': 700,
);

.title {
  // need to add `@use 'sass:map'` in order to use map.get()
  font-weight: map.get($font-weights, 'bold');
}
```

`css`

```css
.title {
  font-weight: 700;
}
```

## Mixins

Are like functions/methods

`scss`

```scss
@mixin flex() {
  display: flex;
  justify-content: center;
  align-items: center;
}

@mixin square($size, $radius: 0) {
  width: $size;
  height: $size;

  @if $radius != 0 {
    border-radius: $radius;
  }
}

.d-flex {
  // mixin
  @include flex();
}

.avatar {
  // mixin with parameters
  @include square(100px);
}

.avatar-radius {
  @include square(100px, 4px);
}
```

`css`

```css
.d-flex {
  display: flex;
  justify-content: center;
  align-items: center;
}

.avatar {
  width: 100px;
  height: 100px;
}

.avatar-radius {
  width: 100px;
  height: 100px;
  border-radius: 4px;
}
```

## Others

### Extension

Using `@extend` is like calling a variable with a group of styles

`scss`

```scss
%extend-name {
  margin: 0;
  padding: 0;
}

.mac-green {
  @extend %extend-name;
  color: $mac-green;
}
```

`css`

```css
.mac-green {
  margin: 0;
  padding: 0;
}

.mac-green {
  color: #00ca4e;
}
```

### Looping

Using `@each` to loop in (i.e. looping in **maps**)

`scss`

```scss
$font-weights: (
  'regular': 400,
  'medium': 500,
  'bold': 700,
);

// maps ($font-weights) are like enums or key/value pair
@each $weight, $value in $font-weights {
  .text-#{$weight} {
    font-weight: $value;
  }
}
```

`css`

```css
.text-regular {
  font-weight: 400;
}

.text-medium {
  font-weight: 500;
}

.text-bold {
  font-weight: 700;
}
```
