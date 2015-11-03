# Snippet #

 - Generate Radial progress bar without external libruaries or plugins
 
 ![Example](http://content.screencast.com/users/michael.grabovsk/folders/Snagit/media/2896d6c0-99b4-4e7a-a2d8-2fca2dbbbf42/11.03.2015-23.44.png)

**HTML***
``` html
  <div class="svg radial-progress">
    <svg height="10em" width="10em">
      <circle class="radial-progress__background" r="" cx="5em" cy="5em" fill="transparent" stroke-dasharray="0em" stroke-dashoffset="0em"></circle>
      <circle class="radial-progress__cover" r="" cx="5em" cy="5em" fill="transparent" stroke-dasharray="0em" stroke-dashoffset="0"></circle>
      <circle class="radial-progress__center" r="" cx="5em" cy="5em" fill="transparent" stroke-dasharray="0em" stroke-dashoffset="0em"></circle>
      <text class="radial-progress__text-percent" x="4.1em" y="-4.5em" text-anchor="middle">57%</text>
      <text class="radial-progress__text-desc" x="0" y="-6.5em" text-anchor="middle">
        <tspan x="6.8em" dy="1em">emissions</tspan>
        <tspan x="6.6em" dy="1.3em">avoided</tspan>        
      </text>
    </svg>
  </div>
```

**SCSS**
``` scss
circle {
  stroke-width: 1.2em;
  fill: transparent;
  transform: rotate(0.1deg);
}

.radial-progress {
  position: relative;
  display: inline-block;
  transform: rotate(270deg);

  &__background {
    stroke: orange;
  }
  &__cover {
    stroke: white;
    stroke-width: 2.1em;
    border: 12px solid red;
  }
  &__center {
    fill: white;
  }
  &__text-percent {
    fill: blue;
    transform: rotate(90deg);
    font-weight: bold;
    font-family: Arial;
    font-size: 20px;
  }
  &__text-desc {
    fill: gray;
    transform: rotate(90deg);
    font-weight: bold;
    font-family: Arial;
    font-size: 12px;
    width: 140px;
  }
}
```

**Javascript**
``` js
window.onload = function () {
  var radius = 3.2;
  var currentCount = 57; // set percent
  
  var circumference = 2 * radius * Math.PI;
  var offset = -(circumference / 100) * currentCount + 'em';
  
  Array.prototype.forEach.call(document.querySelectorAll('circle'), function (el) {
    el.setAttribute('stroke-dasharray', circumference + 'em');
    el.setAttribute('r', radius + 'em');
  });
  
  document.querySelector('.radial-progress__background').setAttribute('r', (radius - 0.04 + 'em'));
  document.querySelector('.radial-progress__center').setAttribute('r', (radius + 0.01 + 'em'));
  document.querySelector('.radial-progress__cover').setAttribute('stroke-dashoffset', offset);
}; 
```

[CodePen Demo](http://codepen.io/mgrabovskyi/pen/YyjRXd)
