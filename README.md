## Welcome to my collection of tech recipes

### How to build an epaper / eink weather / calendar display

#### Shopping list
* [Display](https://www.welectron.com/Waveshare-13380-75inch-e-Paper-B)
* [Raspberry](https://www.welectron.com/Raspberry-Pi-Zero-WH-mit-verloeteter-Stiftleiste)
* [Case](https://www.welectron.com/Raspberry-Pi-Zero-Gehaeuse)
* [Keyboard Adapter](https://www.welectron.com/USB-20-OTG-Adapter)
* [Power Supply](https://www.welectron.com/Goobay-46600-Steckernetzteil-microUSB-5V-1A)

#### Wiring / Driver installation
* [Waveshare: "Hardware/Software setup >> Raspberry Pi"](https://www.waveshare.com/wiki/7.5inch_e-Paper_HAT_(B))

#### Software preparations
* [OpenWeather API Key](https://openweathermap.org/appid)
* Google Calendar iCal URL ![PrivateICal](data:image/jpeg;base64,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)

#### Software installation
* [Inky Calendar](https://github.com/aceisace/Inky-Calendar)



### How to choose a license
[Overwiew](https://choosealicense.com/appendix/)

### How to edit this page
By [editor on GitHub](https://github.com/ingmar424242/tech/edit/master/README.md).

### How to show this page in HTML
[Link](https://ingmar424242.github.io/tech/).
