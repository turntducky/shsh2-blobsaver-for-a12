# shsh2-blobsaver-for-a12
how to save shsh2 blobs for an a12 device

You only need to do the parts 1-4 once. Make sure to save your generated nonce somewhere safe for further use.
Blobs saved without a nonce (on A12) are INVALID.
Requirements
iPhone XS, XS Max, XR or iPad Pro 2018 on iOS 12.0-12.1.2.
A computer with Windows, macOS or Linux. If you're on Windows you need to have iTunes installed as well.
USB cable
Cydia Impactor
Latest version of unc0ver or Chimera.
libimobiledevice tools - Installation instructions available below.
1. Installing libimobiledevice.
GNU/Linux: You can use the package manager of choice and install libimobiledevice or imobiledevice.
MacOS: Read this comment., if it doesn't work: use Homebrew or similar. For Homebrew: brew install libimobiledevice (in Terminal).
Windows: You can get the binaries from here (updated link, courtesy of /u/tateu). iTunes is required.
You can use Chimera to set the nonce instead of unc0ver; for steps 2; 3.
Use Chimera's default nonce instead of 0x1111111111111111, though.
2. Installing unc0ver.
Use Cydia Impactor as usual to install the Unc0ver IPA. Download latest beta build of Unc0ver 3.x.x from here.
3. Setting the nonce generator.
If unc0ver/Chimera don't work you can use stek29's voucher_nonce Xcode project. Tutorial
unc0ver:
Open unc0ver. (You may get a popup about an untrusted certificate, go to Settings > General > Device Management and Trust your certificate)
Go to the Settings tab in unc0ver.
Make sure "Overwrite Boot Nonce" is enabled and that "Boot Nonce" is set to 0x1111111111111111.
Go to the Jailbreak tab and press Jailbreak.
You're done with this part of the tutorial.
Chimera:
Open Chimera. (You may get a popup about an untrusted certificate, go to Settings > General > Device Management and Trust your certificate)
Scroll down.
Click on "Set Nonce".
Jailbreak.
Done!
4. Getting the nonce from your device.
Open your Terminal app. (Windows: navigate with it to where your downloaded binaries are).
Run the following commands. If any of these commands fail, run them with sudo (on Linux and macOS).
ideviceinfo - Look for "UniqueDeviceID" in the output. Text after ": " is your UDID. You may need to trust your PC on your iPhone for this to work. If you don't know your ECID it's the "UniqueChipID", your model is "ProductType".
ideviceenterrecovery UDID - Replace UDID with your UDID from above.
# Important install https://github.com/libimobiledevice/libirecovery… then cd into the folder in terminal and run these commands:
# ./autogen.sh
# make
# sudo make install
# After that you will be able to run the command no problem
irecovery -q - Look for "NONC" in the input, this is your APNonce (the text after "NONC: "). You can use irecovery -q | grep NONC on GNU/Linux and macOS.
irecovery -n - This will reboot you back to the non-recovery mode.
5. Saving your blobs.
Save your generated nonce, ECID and model in a file somewhere, it shouldn't change in the future so you only need to do the above steps once.
Go to https://tsssaver.1conan.com/ with a browser of your choice.
Change the drop down field that says "Hex (iTunes)" to "Dec (UDID Calculator/ideviceinfo)", input your ECID in the "Type ECID Here..." field, select your model in "Identifier:" and make sure it matches the ProductType from above.
Check the "Manually specify an apnonce (ADVANCED USERS ONLY)" checkbox, and type your APNonce from above (NONC) here.
Fill in the CAPTCHA and press "Submit".
That's it your blobs will be saved.

# NOTE: If you are having problems with libimobiledevice on Mojave try this:
# brew update
# brew uninstall --ignore-dependencies libimobiledevice
# brew uninstall --ignore-dependencies usbmuxd
# brew install --HEAD usbmuxd
# brew install --HEAD libimobiledevice
