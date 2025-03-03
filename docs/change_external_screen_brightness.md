# Change the brightness of the external screen from Terminal (on Linux) with xrandr

When you attach an external display to an Ubuntu laptop, the keyboard command only changes the brighness on the build-in screen. In order to change the brightness of the external screen (and avoid being blinded by white windows) follow the steps below: 

## Find list of screens

`xrandr -q | grep " connected"`

## usually 1st item is laptop screen

`eDP-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm`
`DP-1-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 597mm x 336mm`

## set the brightness to (for example) 0.63
`xrandr --output DP-1-1 --brightness 0.63`

# Change brightness for Wayland (does not support xrandr) 

## The infor below can be found [here](https://fostips.com/ddcbc-gtk-control-brightness-ddc-ci-monitors/)

ddcutil needs to be installed : 

` sudo apt install ddcutil`

and granted user access :

`sudo gpasswd --add $USER i2c`

Then `ddcutil detect` will show the displays (default laptop display is untouchable, the external monitor is usually display 1)

Find the feature code that is controlling the brightness:

`ddcutil --display 1 capabilities |grep Brightness`

example output: `Feature: 10 (Brightness)`

So to change it to 5 for example:  

`ddcutil --display 1 setvcp 10 5`

