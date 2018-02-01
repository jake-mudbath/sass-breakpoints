# sass-breakpoints

SASS mixins for named breakpoints.

- Named breakpoints improve readability and maintainability
- Customisable breakpoints allow you to target whatever devices you want
- Breakpoints are set in `em` and scale with the user's base font-size

## Installation

    npm install --save mb-sass-breakpoints

## Usage

    $ sass-composer example/example.scss -o compiled.css

SCSS: `example/settings.scss`

    //these are the default settings if not specified by the user
    $breakpoints: (
      'xs': 0px,
      'sm': 480px,
      'md': 640px,
      'lg': 800px,
      'xl': 960px,
    );

SCSS: `example/example.scss`

    @import "./settings";
    @import "sass-breakpoint";
    
    @include breakpoint('sm') {           //from `sm` (>=0px)
      body {
        background-color: red;
      }
    }
    
    @include breakpoint('md', 'lg') {     //from `md` to `lg - 1px` (>=768px to <1024px)
      body {
        background-color: green;
      }
    }
    
    @include breakpoint('lg') {           //from `lg` (>=1024px)
      body {
        background-color: blue;
      }
    }
    
CSS: `compiled.scss`
        
    @media (min-width: 35.5em) {
      body {
        background-color: red; } }
    
    @media (min-width: 48em) and (max-width: 62.6875em) {
      body {
        background-color: green; } }
    
    @media (min-width: 62.75em) {
      body {
        background-color: blue; } }

## API
    
### breakpoint($from, $to: null)

    @include breakpoint('xs') {           //>=0px
      body { color: red; }
    }
    
    @include breakpoint('sm, 'md') {      //>=568px but <768px
      body { color: blue; }
    }
 
### breakpoint-lt($to)

    @include breakpoint-lt('md') {        //<768px
      body { color: red; }
    }

### breakpoint-lte($to)

    @include breakpoint-lte('md') {       //<=768px
      body { color: red; }
    }

### breakpoint-gt($from)

    @include breakpoint-gt('md') {        //>768px
      body { color: red; }
    }

### breakpoint-lte($to)

    @include breakpoint-gte('md') {       //>=768px
      body { color: red; }
    }

### breakpoint-between($from, $to)
    
    @include breakpoint-between('sm', 'md') { //>568px but <768px
      body { color: red; }
    }

## License

The MIT License (MIT)

Copyright (c) 2015 James Newell