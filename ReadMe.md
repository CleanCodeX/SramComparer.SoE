# SoE-SramComparer
Allows to compare (unknown) buffers and manipulate offset values in Secret of Evermore's SRAM file.

## Features
* Display (or manipulate and save) offset values
* Comparison of Unknowns only (*default*) or whole game buffer (**optional**)
* Comparison of whole sram outside games (**optional**)
* Display of differences in decimal, hex and binary format
* Comparison of all 4 games (*default*) or one specific current game with same or different comparison game (**optional**)
* Export comparison result as text file
* Backup / restore functionality of current and comparison sram file
* Transfer of SRAM data to similar game 
* Display of changed or all checksums (**optional**)
* All settings can be set by cmd line arguments

## What's still unknown?
A little less than 50% of SoE's SRAM file game slot format is still considered as 'unknown', meaning that we don't really know what these parts of SRAM actually do.
Most of unknown parts are reserved for pick-up information of various ingredient sniff spots, opened chests, gourds, pots and which persons were spoken to twice. Despite these there are also game relevant progress flags which we want to know to write more capable SRAM editors.
A non exhaustive list can be found here:
[Unknown Offsets](https://raw.githubusercontent.com/CleanCodeX/SramComparer.SoE/master/Markdown/Unknowns.md)

## How can I help?
You could join to help finding meanings for various SRAM offsets.
This can be done either by using 

* [Web Comparison](http://compare.xeth.de)
* Release

Once you found a meaning for a offset value, try to enable or disable this flag in other SRAM (*.srm) files to prove your discovery. 
Reading and manipulating offset values can be done either by using  

* [Web Offset Editor](http://offset.xeth.de)
* Release

## Prerequisites (Runtime)
This application uses the latest .NET 5 runtime.

1) Head to [.Net](https://dotnet.microsoft.com)
2) Click on Download button.
3) Users see "Run apps - Runtime" column, coders see "Build apps - SDK" column.

## Download Binaries
[Releases](http://xeth.de/Releases/SramComparer)

## How to use
**Steps**:

***1.1)*** Have a look into [Unknowns](http://unknowns.xeth.de) to see examples of what parts of SRAM structure are still 
     considered as unknown.
***1.2)*** Most emulators have the option to save the game's S-RAM automatically after a change occurs. 
     Make sure this is enabled if existing. Otherwise you have manually ensure that the emulator updates 
     the *.srm file.
***1.3)*** Start the application by passing the game's srm filepath as first command parameter. The file can also be 
     dragged onto the application.

***2)***   Then press (ow) to create a comparison copy of your current SRAM file. This allows to compare with after the current SRAM file changed.

***3.1)*** Cause in-game a SRAM change. (e.g. let a game progress event happen or 
    open an unopened chest) To force the SRAM file to be updated, save your game in-game at the inn.
***3.2)*** Press (c) to compare the current srm file with comparison file. 
     (If the SRAM file did not change at all, you probably did not save in-game or the emulator didn't
     (yet!) update the SRAM (srm) file automatically. Check the modification date of the game's srm file.
     For Example: Snes9x's default srm update period is 30 seconds. Decrease it to a lower value, like 1 second,
     but not to 0 (which deactivates the automatism).  

***4.1)*** Make sure to change as little as possible between two saves to avoid unnecessary noise. Alleged assignments are often just coincidence.
***4.2)*** As soon as you can clearly assign a change in the game to a change in the SRAM, you have found a meaning for this specific offset. Then press (e) to export the comparison result as a text file in your export directory.
***4.3)*** Rename the file according to your find.
***4.4)*** Check whether the change found also occurs in other game versions. E.g. unpatched or patched versions.
***4.5) If it is reproducible, report the find via community.xeth.de. If necessary, create a pull request for a change to the documentation and the SRAM structure in the GitHub repository..

***5)***   To start a "fresh" comparison without previous SRAM changes, press again (ow) to save your current SRAM file 
     as comparison file. Then start again at step 3.1.

***6.1)*** (optional, advanced) If you have more than one slot with changes to comparison file, press (sg) to
     set the game's save slot (1-4) to avoid comparing other game slots. If two different game slots should be 
     compared with each other, additionally press (sgc) to set the the slot of comparison file, too.
***6.2)*** (optional, advanced) Press (fwg | fng) to set comparison modes. 
     If you are unsure, leave at default to compare as less as possible bytes.

***7)***   (optional) Current and comparison srm file can be backed-up (b|bc) or restored (r|rc) individually.

***8)***   (optional) SRAM offset values for specific game slots can be displayed by pressing (dev) or manipulated by (mov). You can decide whether to update your current SRAM file (backup recommended) or creating a new file.

## Screenshots
![Commands](Images/Cmd.png "Commands")

![Few Flags Change](Images/FewFlagsChange.png "Few Flags Change")

![Many Values Change](Images/ManyValuesChange.png "Many Values Change")

![No SRAM Change](Images/NoChange.png "No SRAM Change")

![Whole Game Comparison](Images/WholeGameComparison.png "Whole Game Comparison")

![Whole Game Comparison #2](Images/WholeGameComparison2.png "Whole Game Comparison #2")

![Optional Game Info](Images/OptionalGameInfo.png "Optional Game Info")
