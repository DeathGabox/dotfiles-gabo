Esta cosa si que estuvo complicada, casi me gana pero soy mejor
Instalar dependencias
yay -S redshift-minimal

> Crear script de ejecucion
```
mkdir -p /home/$USER/.bin/
micro /home/$USER/.bin/redshift_autostart

#!bin/bash
sleep 8
exec /usr/bin/redshift -v
```

> Crear redshift.service (User)

Ruta: /home/$USER/.config/systemd/user/redshift.service

NOTE: XAUTORITY se cambia segun el OUTPUT de `echo $XAUTHORITY`
```
[Unit]
Description=Redshift
Documentation=http://jonls.dk/redshift/

[Service]
Environment="DISPLAY=:0" "XAUTHORITY=/run/user/1000/.emptty-xauth"
ExecStart=/home/deathgabox/.bin/start_redshift
RestartSec=15

[Install]
WantedBy=default.target
```
> Crea un config file
RUTA: /home/$USER/.config/redshift/redshift.conf
```
; Global settings for redshift
[redshift]
; Set the day and night screen temperatures
temp-day=3000
temp-night=2000

; Disable the smooth fade between temperatures when Redshift starts and stops.
; 0 will cause an immediate change between screen temperatures.
; 1 will gradually apply the new screen temperature over a couple of seconds.
fade=1

; Solar elevation thresholds.
; By default, Redshift will use the current elevation of the sun to determine
; whether it is daytime, night or in transition (dawn/dusk). When the sun is
; above the degrees specified with elevation-high it is considered daytime and
; below elevation-low it is considered night.
;elevation-high=3
;elevation-low=-6

; Custom dawn/dusk intervals.
; Instead of using the solar elevation, the time intervals of dawn and dusk
; can be specified manually. The times must be specified as HH:MM in 24-hour
; format.
;dawn-time=6:00-7:45
;dusk-time=18:35-20:15

; Set the screen brightness. Default is 1.0.
;brightness=0.9
; It is also possible to use different settings for day and night
; since version 1.8.
brightness-day=0.9
brightness-night=0.7
; Set the screen gamma (for all colors, or each color channel
; individually)
;gamma=0.9
;gamma=0.8:0.7:0.8
; This can also be set individually for day and night since
; version 1.10.
;gamma-day=0.8:0.7:0.8
;gamma-night=0.6

; Set the location-provider: 'geoclue2', 'manual'
; type 'redshift -l list' to see possible values.
; The location provider settings are in a different section.
location-provider=manual

; Set the adjustment-method: 'randr', 'vidmode'
; type 'redshift -m list' to see all possible values.
; 'randr' is the preferred method, 'vidmode' is an older API.
; but works in some cases when 'randr' does not.
; The adjustment method settings are in a different section.
adjustment-method=randr

; Configuration of the location-provider:
; type 'redshift -l PROVIDER:help' to see the settings.
; ex: 'redshift -l manual:help'
; Keep in mind that longitudes west of Greenwich (e.g. the Americas)
; are negative numbers.
[manual]
lat=-33.30
lon=-70.9

; Configuration of the adjustment-method
; type 'redshift -m METHOD:help' to see the settings.
; ex: 'redshift -m randr:help'
; In this example, randr is configured to adjust only screen 0.
; Note that the numbering starts from 0, so this is actually the first screen.
; If this option is not specified, Redshift will try to adjust _all_ screens.
[randr]
screen=0
```