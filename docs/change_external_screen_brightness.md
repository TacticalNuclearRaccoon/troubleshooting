# Change the brightness of the external screen from Terminal (on Linux)

When you attach an external display to an Ubuntu laptop, the keyboard command only changes the brighness on the build-in screen. In order to change the brightness of the external screen (and avoid being blinded by white windows) follow the steps below: 

## Find list of screens

`xrandr -q | grep " connected"`

## usually 1st item is laptop screen

`eDP-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm`
`DP-1-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 597mm x 336mm`

## set the brightness to (for example) 0.63
`xrandr --output DP-1-1 --brightness 0.63`
