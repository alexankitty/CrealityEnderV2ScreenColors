![image](https://user-images.githubusercontent.com/45508320/206162345-78630474-685d-4453-96c6-1d0343e1f3a7.png)


# Color your Ender V2 3D Printer Screen!
This is a simple and rather untested project for replacing the icons with those of different colors for the Ender 3D printer screen. This supports both DWIN and DACAI type screens.  
In theory this should work with stock Marlin firmwares, however do yourself a favor and get [Mrisco's Professional firmware](https://github.com/mriscoc/Ender3V2S1) instead, it's everything you could ever want. 
# How To
Follows the same flashing process for any other screen firmware but we'll go through the basics.  
1. Get an SD card (under 32gb?)
2. Format as FAT32
3. Set allocation size to 4096
4. Put the files either in the DWIN_SET directory at the sdcard root, or the files inside of DACAI. (I have no experience with the DWIN screens, so YMMV is the phrase of the day)
5. Disassemble your screen to expose the SD card slot
6. Put the sd card in and plug the display in, it should boot up into a firmware download and apply the color you want.

# Fonts
There are a small handful of fonts that work, though the only alternative font I've tested that seems to look okay is the DroidSans font. Due to the low resolution of the screen though, the fonts will look a little chunky compared to the bitmap style of the SimSun font that the unit ships with. Test it out to your hearts content, just keep in mind the private directory for DACAI units is limited to 2mb.

# Making your own
The icon sets I've used are included in the bootsplash and assets folders, look through those and edit as desired. For DWIN screens, you can just repack the ICO using [dwin-ico-tools](https://github.com/b-pub/dwin-ico-tools). For those of us unfortunate to have a DACAI screen one more step is required. First you'll need to acquire the xgus tool from http://www.gz-dc.com/category/typeid/412#mainTop / Direct link: http://kaifabao.gz-dc.com/xgus%E8%BD%AC%E6%8D%A2%E5%B7%A5%E5%85%B7.zip
1. Rebuild the DWIN_SET with your newly packed ICO
2. Unpack the zip of xgus
3. Find ProjectConvert.exe and run it.
4. In the first text box, point it to your DWIN_SET path
5. Hit the big button saying 开始转换 (Start Converting).
6. It will complain about font.ttf is missing, we don't really care about that. Hit OK.
7. It'll pop up another window with screen settings. Once again these don't matter. Hit 确定 (Okay).
8. It'll complain about the font one more time. Hit OK again, and then it'll open a Project_Convert folder
9. Go into the private folder, then icon.
10. Copy over the 9.zico file in there to a template DACAI firmware folder (hint: any of the DACAI folders in this prokect will work.
11. Copy the contents of your newly created DACAI firmware to the root of the SD card and test to see if it works.

# Other Notes
For colorizing I recommend using a bulk tool like batch image manipulation program for GIMP. 
For boot splash and baked in font JPG images, the format is baseline DCT (not progressive) with chroma subsampling of 4:2:0. Do not save any metadata, it's a waste of space.
