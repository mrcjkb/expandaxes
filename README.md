# expandaxes


> [![Maintenance](https://img.shields.io/badge/Maintained%3F-no-red.svg)](https://bitbucket.org/lbesson/ansi-colors)
>
> __NOTE:__
>
> Since I no longer use Matlab, I cannot actively maintain this model.
> I will gladly accept PRs, as long as I can review them without Matlab.


More reliable implementation of the option "expand axes to fill figure" in the Export Setup... settings. 

Works with multiple subplots and usually does not distort objects such as colorbars.

This function attempts to automatically remove white space in figures by expanding the axes objects to fill the figure.
The available option in the "export setup" figure menu sometimes distorts the axes and often does not work at all if there is more than one axes or a colorbar. 
The common fix is to manually change the position of each axes, which can be a tedious process. 
This function attempts to automate the process while keeping the syntax as simple as possible. 
It automatically removes the white space of most figures with multiple subplots, superimpozed axes objects and colorbars without distorting the axes.


## Syntax

```matlab
expandaxes(h);
expandaxes(h, fHor, fVer); % For manual adjustment of the distance between subplots
```

### Input arguments

* `h`:    Figure handle
* `fHor`: Factor for the distance between subplots in horizontal direction (Default: `1`)
* `fVer`: Factor for the distance between subplots in vertical direction (Default: `1`)

### Hints
* General rule of thumb for the order of execution when calling expandaxes:
  - Set objects, FontSizes, etc.
  - Call expandaxes
  - Other manipulations of axes and colorbar positions
* By setting `h.SizeChangedFcn = expandaxes(gcf, fHor, fVer)`, this function can be called with exery resize of the figure h.
