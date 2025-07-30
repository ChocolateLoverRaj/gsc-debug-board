# GSC Debug Cable / Board
Information about my GSC Debug Cables / Boards

> [!IMPORTANT]
> Buyers in Europe: there is now a seller who is located in the UK. You can get cheaper and faster shipping from the UK. See [Buying from the UK Seller](#buying-from-the-uk-seller-lyubomir-krastanov)

> [!IMPORTANT]
> Buyers in Canada: you can save on shipping costs if you buy outside of eBay. See the [Pirate Ship Rates](https://www.pirateship.com/simple-export-rate) and [Insurance Rates](https://support.pirateship.com/en/articles/1068431-does-pirate-ship-offer-insurance#h_7256b8b35d) ($1). Contact [my email](mailto:paranjperajas@gmail.com) or [Chrultrabook forum account](https://forum.chrultrabook.com/u/chocolateloverraj/activity) to buy.

## What does it do?
This item (previously sold by [SparkFun which they called SuzyQable](https://web.archive.org/web/20231028183709/https://www.sparkfun.com/products/retired/14746)) is for Chromebooks which support [CCD (Closed Case Debugging)](https://web.archive.org/web/20231028184033/https://chromium.googlesource.com/chromiumos/third_party/hdctools/+/HEAD/docs/ccd.md). This item lets you communicate with the Google Security Chip inside Chromebooks, and is mainly used for disabling firmware write protect and unbricking.

## How to use it to disable firmware write protect
1. For this step, you do not need to have a debug cable plugged in. Note: After running the command, your Chromebook will return to not-developer mode, erasing all user data on your Chromebook. Run `sudo gsctool -a -o`. The command will say “Press PP button now!” Whenever it says that, press the power button on your Chromebook. Keep pressing the power button when needed until the command successfully completes. It will take around 3 minutes.
2. Re-enter developer mode
3. Plug in your USB-C cable into the debug board, orientation does not matter. Plug the debug board into the left USB-C port of your chromebook, Side A up. Plug the other end of your chromebook into a different USB port on your chromebook or into a USB port of a linux computer. On the linux computer which you plugged the cable into (which is your Chromebook if you plugged the board into your Chromebook) and run this command: `watch -n 1 'lsusb | grep -E "18d1:5014|18d1:504a"'`. The command will show all connected Cr50 or Ti50 USB devices every second. You should see a device called “Cr50” or “Ti50”. If you don’t, try plugging the debug board in with Side B up. If that still doesn’t work, try all other USB-C ports on your chromebook with both Side A and Side B until it works. If you’ve tried every combination then double check that your cable is working and contact me for help.
4. Run `ls /dev/ttyUSB*`. It should show `ttyUSB0`
5. Run `sudo bash`. This will switch to a root shell.
6. Run `echo "wp false" > /dev/ttyUSB0`
7. Run `echo "wp false atboot" > /dev/ttyUSB0`
8. Run `echo "ccd reset factory" > /dev/ttyUSB0`
9. Type `exit` to exit root shell
10. Run `gsctool -a -I`. All flags should show “Y/Always”
11. Run `sudo crossystem wpsw_cur`. It should output 0, which means firmware write protect is successfully disabled!

## Pricing for buying directly, shipping from the US

| |Buying outside of eBay|Ships from Pleasanton, CA 94566|See https://www.pirateship.com/rates for exact rates| | | | | |
|:----|:----|:----|:----|:----|:----|:----|:----|:----|
|Destination|International| | |Canada| |Within US|Cost varies by address, price is for 60007 (Chicago) See https://www.pirateship.com/rates for exact rates| |
|Shipping Service|Pirate Ship Simple Export Rate|UPS|Envelope|Pirate Ship Simple Export Rate|UPS® Standard|USPS Ground Advantage|USPS Priority Mail|FedEX|
|Time (estimate)|1-3+ weeks|2 to 5 business days|~2 weeks|1-3+ weeks|1 week|Up to 5 days not including Sundays|~2 Business Days|~2 Business Days|
| | | | | | | | | |
|Cost / board|$3.61|$3.61|$3.61|$3.61|$3.61|$3.61|$3.61|$3.61|
|Packaging Type|Compostable bubble mailer with compostable shipping label|Compostable bubble mailer with compostable shipping label|Envelope|Compostable bubble mailer with compostable shipping label|Compostable bubble mailer with compostable shipping label|Compostable bubble mailer with compostable shipping label|Compostable bubble mailer with compostable shipping label|Compostable bubble mailer with compostable shipping label|
|Packaging Cost|$0.68|$0.68|$0.13|$0.68|$0.68|$0.68|$0.68|$0.68|
|Handling Cost|$2.00|$3.00|$6.00|$2.00|$3.00|$1.70|$1.70|$4.50|
|Shipping|$13.99|$21.45|$2.00|$10.99|$16.64|$4.14| | |
|Shipping insurance|$1.00|$0.00|No insurance! At your own risk|$1.00|$0.00|0| | |
|Total|$21.28|$28.74|$11.74|$18.28|$23.93|$9.93| | |
| | | | | | | | | |
|Cost / cable|$0.84| | | | | | | |

### Contact
Email: paranjperajas@gmail.com

## Buying from the UK Seller (Lyubomir Krastanov)
Name: Lyubomir Krastanov

Email: lybo.farscape@gmail.com

Whatsapp:	+447759190013

### Total cost estimates
| | To UK mainland | To the	EU |
| -- | -- | -- |
| Tracked & Insured |	£14.00 | £20.00
| Untracked & Uninsured |	£10.00 | £12.00



## Versions
### Cable (56k Version)
[Original link to buy (Out of Stock, has been replaced by v4.1.0)](https://www.ebay.com/itm/334996831342)

This cable was made using [this guide](https://web.archive.org/web/20231028184553/https://chromium.googlesource.com/chromiumos/third_party/hdctools/+/474419984dd023a4c8a51381991b3a8c7a20772c/docs/ccd.md#SuzyQ-SuzyQable). It uses 22k and 56k resistors. It is a home made cable.

### v4.0.1
[Original link to buy (out of Stock, has been replaced by v4.1.0)](https://www.ebay.com/itm/335088802284)

[Made using this guide](https://web.archive.org/web/20231028184033/https://chromium.googlesource.com/chromiumos/third_party/hdctools/+/HEAD/docs/ccd.md#SuzyQ-SuzyQable)

Uses 22k and 45.3k resistors. Works with USB-A male to USB-C male cables. Does not work with USB-C male to USB-C male cables.

### v4.1.0
[Link to buy](https://www.ebay.com/itm/316024978790)

[Made using this guide](https://web.archive.org/web/20231028184033/https://chromium.googlesource.com/chromiumos/third_party/hdctools/+/HEAD/docs/ccd.md#SuzyQ-SuzyQable)

Uses 22k and 45.3k resistors. Works with both USB-A male to USB-C male cables and USB-C male to USB-C male cables. Shield ground is connected between both USB-C components.
