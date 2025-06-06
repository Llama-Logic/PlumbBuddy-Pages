<template>
    <MenuToggleBreadcrumbs
        color="success"
        :items="[{title: 'Guides', to: '/text-guides'}, {title: 'Mod Health'}]"
    />
    <v-container>
        <p>
            <center><img src="/img/nurse-health.jpeg"</center>
        </p>
        <p style="font-size:3em;">
            <center>Mod Health</center>
        </p>
        <p style="font-size:1.5em;">
            <center>What the Scans Tell You</center>
        </p>
        <v-divider />
        <p>
            <center>Jump To:</center>
            <center><a href="#mod-setting-scan">In The Sims 4 game options…</a> &emsp; <a href="#depth-scan">Inside your Mods Folder, I find...</a> &emsp; <a href="#mccc-missing-scan">Inside your Installation and Mods Folders, I DO NOT find...</a> &emsp; <a href="#cache-staleness-scan">Mod file analysis suggests...</a> &emsp; <a href="#mismatched-inscribed-hashes-scan">(Mod Name) has been Altered</a></center>
        </p>
        <v-divider />
        <p>
            When you installed PlumbBuddy for the first time, there were many Mod Health scans that you could turn on or off.<br><br>

            For Creators, most scans are off by default. You can turn them on (or off again) in PlumbBuddy settings, accessed through the menu on the left, or by clicking 'Stop Telling Me' when Mod Health finds something to tell you about.<br><br>

            In the Mod Health section of PlumbBuddy settings, there are four categories:<br><br>

            1. <b>In The Sims 4 game options...</b> — <i>For things about the game itself</i><br>
            2. <b>Inside your Mods Folder, I find...</b> — <i>For things to do with the health of your mods folder</i><br>
            3. <b>Inside your Installation and Mods Folders, I DO NOT find...</b> — <i>For things that you don't have that you might need or want</i><br>
            4. <b>Mod file analysis suggests...</b> — <i>For things that PlumbBuddy has found about your mods</i><br><br>

            Each of these sections has multiple scans that you can turn off or on if you find them useful. Read below to find out what these scan check for and what you can do when they alert you to a potential problem.<br><br>

            Pay special attention to the very last scan on the page. It's the one designed specifically to help creators, and it's the only one enabled for creators by default.<br><br>

            Each alert you get in PlumbBuddy will have a question mark on it to bring you to this page if you want more information.
        </p>
        <v-divider />
        <GuideMenu
            :guides="guides"
        />
    </v-container>
</template>

<script setup>
    const guides = [
        {
            id: 'mod-setting-scan',
            color: 'primary',
            icon: 'mdi-radiobox-indeterminate-variant',
            name: 'In The Sims 4 game options…',
            image: 'casual-packages-disabled.png',
            description: `### Mods/Script Mods are Disabled in Options

*Settings:*

![image](/img/setting-mods-disabled.png "…Mods are disabled even though you have .package files")

![image](/img/setting-scripts-disabled.png "…Script mods are disabled even though you have .ts4script files")

---

*What it means:*

* You have mods and/or custom content installed.
* Mods are turned off in your game settings, so the game does not know they exist.

or

* You have script mods installed (meaning mods that contain files that have the .ts4script file type).
* Script mods are turned off in your game settings, so the game does not know they exist.

---

*What you can do:*

* PlumbBuddy will offer to enable this game option for you.

---

*Extra info:*

* If you have mods turned on but not script mods, the game will try to load half a mod. This will result in a broken mod, which can cause a wide range of issues, up to the game not loading or being extremely broken if it does.
* Script mods are turned off by default by the game, so if you’ve never turned them on, they will be off.
* They are also turned off after many game patches and need to be turned back on.`,
        },
        {
            id: 'show-mod-list-startup-setting-scan',
            color: 'primary',
            icon: 'mdi-radiobox-indeterminate-variant',
            name: 'In The Sims 4 game options…',
            image: 'casual-modlist-enabled.png',
            description: `### Show Mod List is Enabled in Options

*Setting:*

![image](/img/setting-mod-list.png "…Show At Startup is enabled in View Custom Content")

---

*What is means:*

* You have mods and/or custom content in your Mods folder.
* The list of mods that shows when you start the game in enabled in your game settings.
* This which will result in the game taking longer to load.

---

*What you can do:*

* PlumbBuddy will offer to disable this game option for you.

---

*Extra info:*

* When you start the game, by default, the game will show you a list of all mods and custom content that you have installed.
* This can be the cause of very long loading times, and PlumbBuddy will offer to turn this game option off for you to reduce that loading time.
* This can mean the difference between a loading time of up to several hours and a loading time counted in minutes.`,
        },
        {
            id: 'depth-scan',
            color: 'secondary',
            icon: 'mdi-folder',
            name: 'Inside your Mods Folder, I find…',
            image: 'casual-package-too-deep.png',
            description: `### A Mod File is Too Deep

*Settings:*

![image](/img/setting-package-too-deep.png "…a .package file more than five subfolders deep")

![image](/img/setting-script-too-deep.png "…a .ts4script file is more than one subfolder deep")

---

*What is means:*

* You have a mod or custom content file in your mods folder that is in too many folders and the game can't read it.

---

*What you can do:*

* PlumbBuddy will offer to move the file, and any file that seems to be from the same mod, up to be less than five subfolders deep.
* Alternatively, PlumbBuddy will offer to show you the file so that you can move it yourself.

---

*Extra info:*

* The game is able to read package files that are up to five subfolders deep in your mods folder, or .ts4script files that are no more than one subfolder deep.
> CC (1) > CAS CC (2) > Clothes (3) > Outfits (4) > Dresses (5) > dress.package
* The game can't read .packages that are more than five subfolders deep.
> CC (1) > CAS CC (2) > Clothes (3) > Outfits (4) > Dresses (5) > Toddlers (6) > dress.package
* PlumbBuddy would offer to move *dress.package* so that it is only 5 subfolders deep (in Dresses instead of in Toddlers).

*And:*

* The game is able to read .ts4script files that are no more than one subfolder deep.
> Mod Name (1) > mod.ts4script
* The game can't read .ts4script that are more than five subfolders deep.
> Creator Name (1) > Mod Name (2) > mod.ts4script
* PlumbBuddy would offer to move *mod.ts4script* (and likely the rest of the mod) up to Creator Name.`,
        },
        {
            id: 'loose-zip-archive-scan',
            color: 'secondary',
            icon: 'mdi-folder',
            name: 'Inside your Mods Folder, I find…',
            image: 'casual-zip.png',
            description: `### I Found a ZIP File

*Setting:*

![image](/img/setting-zip.png "…a .zip file")

---

*What is means:*

* There is a .zip file in your Mods folder.
* This can cause issues in your game.

---

*What you can do:*

* PlumbBuddy will offer to move that file to your downloads folder, where you can safely extract it if you haven’t already and move the files it contains (usually .package and .ts4script files) to your mods folder.
* Alternatively, PlumbBuddy will offer to show you the file so that you can deal with it yourself.

---

*Extra info:*

* .Zip files are compressed files that need to be extracted before they can be used by the game. They are convenient ways to upload multiple files at once. But .zip files are special to The Sims 4.
* At one point, .ts4script files used the extension .zip, and .ts4script files are just renamed .zip files.
* This can sometimes result in the game reading parts of what’s inside a .zip file, and the game reading part of something is never good. It can cause strange errors that are difficult to diagnose.`,
        },
        {
            id: 'loose-archive-scan',
            color: 'secondary',
            icon: 'mdi-folder',
            name: 'Inside your Mods Folder, I find…',
            image: 'casual-rar.png',
            description: `### I found a RAR/7-Zip File

*Settings:*

![image](/img/setting-rar.png "…a .rar file")

![image](/img/setting-7z.png "…a .7z file")

---

*What is means:*

* There is a .RAR or .7z file in your Mods folder.

---

*What you can do:*

* PlumbBuddy will offer to move that file to your downloads folder, where you can safely extract it if you haven’t already and move the files it contains (usually .package and .ts4script files) to your mods folder.
* Alternatively, PlumbBuddy will offer to show you the file so that you can deal with it yourself.

---

*Extra info:*

* .RAR and .7z files are compressed files that need to be extracted before they can be used by the game.
* They are convenient ways to upload multiple files at once, but that game can't read their contents.`,
        },
        {
            id: 'corrupt-scan',
            color: 'secondary',
            icon: 'mdi-folder',
            name: 'Inside your Mods Folder, I find…',
            image: 'casual-corrupt-file.png',
            description: `### A Mod File is Corrupt

*Settings:*

![image](/img/setting-corrupt-package.png "…a corrupt .package file")

![image](/img/setting-corrupt-script.png "…a corrupt .ts4script file")

---

*What is means:*

* PlumbBuddy has found a mod or custom content file in your Mods folder that **cannot be read**.
* If this file stays in your mods folder, it will prevent the game from starting.

---

*What you can do:*

* PlumbBuddy will offer to move that file to your downloads folder, where it can't cause issues for your game.
* Alternatively, PlumbBuddy will offer to show you the file so that you can deal with it yourself.

---

*Extra info:*

* If this file is in a *__MACOSX* folder, you should delete the entire folder and everything that it contains. It is a hidden file from a Mac computer. It has no use, and will only cause problems.
* If it begins with ._, you should delete it. It is almost certainly a hidden file from a Mac computer. It has no use, and will only cause problems.
* These hidden Mac files are included in .zip files created on Mac computers. It's probably a good idea to report these to the creator, so that they can resolve the issue on their end, and either delete the files or zip the files in a way that doesn't include these hidden files.
* If it appears to be a normal .package or .ts4script file, check the download site. Perhaps it got corrupted in downloading (or in uploading).

If you are a mod creator on a Mac, please be aware of these files and [try to avoid including them in your uploads](https://docs.google.com/document/d/1i5I6eWjcEW9JxRpdHDlgG1blp8CXM7pi50ttx-JzQHE/edit?usp=sharing).`,
        },
        {
            id: 'error-log-scan',
            color: 'secondary',
            icon: 'mdi-folder',
            name: 'Inside your Mods Folder, I find…',
            image: 'enthusiast-error-found.png',
            description: `### A File Likely Containing an Error Has Been Found!

*Setting:*

![image](/img/setting-error.png "…a file that appears to contain error information")

---

*What is means:*

* PlumbBuddy has found what looks like an error file — usually one that has error or exception in the file name.

---

*What you can do:*

* PlumbBuddy will offer to guide you through getting help with this error, either from a support venue or through some self-help steps.
* PlumbBuddy will also offer to show you the file.
* You can also choose to just delete the file, and any other error files that were found.`,
        },
        {
            id: 'mccc-missing-scan',
            color: 'tertiary',
            icon: 'mdi-folder-search',
            name: 'Inside your Installation and Mods Folders, I DO NOT find…',
            image: 'casual-no-mccc.png',
            description: `### MC Command Center is Missing

*Setting:*

![image](/img/setting-no-mccc.png "…Deaderpool's MC Command Center")

---

*What is means:*

* The mod MC Command Center (MCCC) isn't installed in your Mods folder.

---

*What you can do:*

* PlumbBuddy will offer to take you to the MCCC website, where you can download MCCC.

---

*Extra info:*

* MCCC is a mod that does many things.
* One of its benefits is that when you get certain kinds of errors, it gives an error file that contains much more information that the game's error file, in the same place as MCCC's own files.
    * MCCC's error file (*mc_lastexception*, or MCLE) is also formatted so that it's easier for humans to read.
    * This is the preferred error file of many support volunteers, and will let them help you more easily than if you only have the game's *lastexception.txt* file.
    * MCCC will notify you in game that the error happened. The game doesn't do that.

* All parts except the main .package and .ts4script (*mc_cmd_center.package* and *mc_cmd_center.ts4script*) are optional.
    * Some features of the main two files include auto save and custom aging.
    * Some other features of the mod include increased control over story progression and better control over what NPC sims wear.`,
        },
        {
            id: 'be-missing-scan',
            color: 'tertiary',
            icon: 'mdi-folder-search',
            name: 'Inside your Installation and Mods Folders, I DO NOT find…',
            image: 'casual-no-BE.png',
            description: `### Better Exceptions is Missing

*Setting:*

![image](/img/setting-no-BE.png "…TwistedMexi's Better Exceptions")

---

*What is means:*

* The mod Better Exceptions (BE) isn't installed in your Mods folder.

---

*What you can do:*

* PlumbBuddy will offer to take you to TwistedMexi's Patreon, where you can download BE.

---

*Extra info:*

* BE is a mod whose primary purpose is to give error files that are improved over the ones the game creates.
* When you get certain kinds of errors in game, BE will create an error file (usually *BE-ExceptionReport.html*, sometimes *BE-UIExceptionReport.html*) in your The Sims 4 folder.
    * BE's error file is formatted to be easier for humans to read. It can often (but not always) track an error to a specific mod.
    * The *BE-ExceptionReport.html* gives information about various issues in may find in your Mods folder in addition to your error.
    * This file can often be created even if you're not able to load into your save file.
    * This is a commonly accepted error file by many support volunteers, and will let them help you more easily than if you only have the game's *lastexception.txt* file.
    * BE will notify you in game that the error happened. The game doesn't do that.
* BE will freeze the game when you get an error while it scans for the cause.
* Other features of BE include detecting the CC a sim is wearing in live mode and patch day scans, *which can be very useful for creators*.`,
        },
        {
            id: 'modguard-missing-scan',
            color: 'tertiary',
            icon: 'mdi-folder-search',
            name: 'Inside your Installation and Mods Folders, I DO NOT find…',
            image: 'casual-no-modguard.png',
            description: `### ModGuard is Missing

*Setting:*

![image](/img/setting-no-modguard.png "…TwistedMexi's ModGuard")

---

*What is means:*

* The mod ModGuard isn't installed in your Mods folder.

---

*What you can do:*

* PlumbBuddy will offer to take you to TwistedMexi's Patreon, where you can download ModGuard.

---

*Extra info:*

* ModGuard is essentially an anti-virus for .ts4script files. It will block attempts by them to install or run malicious files and warn you.`,
        },
        {
            id: 'dependency-scan',
            color: 'tertiary',
            icon: 'mdi-folder-search',
            name: 'Inside your Installation and Mods Folders, I DO NOT find…',
            image: 'casual-missing-req.png',
            description: `### (A Mod) needs (a Required Pack or Mod) Installed

*Setting:*

![image](/img/setting-missing-req.png "…a pack or mod required by another mod you have installed")

---

*What is means:*

* PlumbBuddy has scanned the manifested mods in your Mods folder and found that there's something missing that the creator said that you need.

---

*What you can do:*

* If it's a missing mod: PlumbBuddy will offer to take you to download the missing requirement.
* If it's a missing pack: PlumbBuddy will offer to take you to purchase the missing pack.
    * If the creator included a referral code in their manifest, PlumbBuddy will remind you to use it.
* Alternatively, PlumbBuddy will offer to show you the file in your Mods folder. This can be useful if you want to delete that file.

---

*Extra info:*

* PlumbBuddy can only give you this information if the creator has both manifested their mod and included information about requirements in that manifest.
* In the case of the requirement being a mod, PlumbBuddy can only give you this information both mods have been manifested. This is more likely to be an issue if the required mod is by a different creator.
* Having a mod installed but not having everything required to use it can lead to problems in game — from visual issues to errors to the game not loading — or to the mod not functioning at all.

This scan is entirely dependent on mod manifests.`,

        },
        {
            id: 'cache-staleness-scan',
            color: 'warning',
            icon: 'mdi-sync-alert',
            name: 'Mod file analysis suggests…',
            image: 'enth-cache-stale.png',
            description: `### The Cache is Stale

*Setting:*

![image](/img/setting-cache.png "…it is appropriate to clear the cache files")

---

*What is means:*

* PlumbBuddy has detected changes made to your Mods folder that suggest that you should clear your cache.

---

*What you can do:*

* There's a button in the scan result that you can click to clear your cache files.
* There's also an eraser button at the top of the window that you can click.
* In addition, there's a button in PlumbBuddy's menu on the left, accessed through the three lines at the top, to clear your cache.

---

*Extra info:*

* PlumbBuddy watches all changes made to your mods folder while it’s active to determine when your cache should be cleared.
* Not clearing your cache can mean that your game is holding on to old information, such as data from mods or custom content that you’ve deleted, or files that have been moved so that the game is now reading them differently. It can sometimes cause weird bugs when you're testing a mod that make no sense whatsoever.`,
        },
        {
            id: 'multiple-mod-version-scan',
            color: 'warning',
            icon: 'mdi-sync-alert',
            name: 'Mod file analysis suggests…',
            image: 'casual-mult-ver.png',
            description: `### I Found Multiple Version of (Mod Name) Installed

*Setting:*

![image](/img/setting-mult-ver.png "…multiple versions of the same mod")

---

*What is means:*

* PlumbBuddy has found two (or more) copies of a manifested mod in your mods folder.

---

*What you can do:*

* PlumbBuddy will tell you the file names and locations, and the version numbers if the manifests included that information.
* PlumbBuddy will offer to take you to the download page for the mod, so that you can find out what went wrong.
* PlumbBuddy will also offer to show you each copy of the mod in your Mods folder, so that you can decide which copy you want to keep.

This scan is entirely dependent on mod manifests.`,
        },
        {
            id: 'exclusivity-scan',
            color: 'warning',
            icon: 'mdi-sync-alert',
            name: 'Mod file analysis suggests…',
            image: 'casual-conflict.png',
            description: `### Multiple Mods Claim (Exclusivity)

*Setting:*

![image](/img/setting-conflict.png "…one or more mutually-exclusive mods")

---

*What is means:*

* PlumbBuddy has found files in your Mods folder that can't be used at the same time.

---

*What you can do:*

* PlumbBuddy will tell you the mod names, file names, and file locations.
* PlumbBuddy will offer to show you each file in your Mods folder, so that you can decide which copy you want to keep.
* You will also be warned that you should check the Catalog tab to see if any of your other mods require one or both of these files.

---

*Extra info:*

* These may be files from the same mod but are a 'pick one version' type of conflict. For example, maybe you're supposed to pick one uniform colour.
* These may be mods that conflict as a whole, and you need to pick one and delete the other.
* If both mods have other mods that require them, you may be able to use either, or some mods require a specific mod. In that case, you'd have to make a decision about which you would keep after checking the mod descriptions.

This scan is entirely dependent on mod manifests.`,
        },
        {
            id: 'mismatched-inscribed-hashes-scan',
            color: 'warning',
            icon: 'mdi-sync-alert',
            name: 'Mod file analysis suggests…',
            image: 'creator-altered-mod.png',
            description: `### (Mod Name) has been Altered

*Setting:*

![image](/img/setting-altered-mod.png "…mismatched inscribed mod manifest hashes")

---

*What is means:*

* One of your mods has been altered so that it no longer matches its manifest.

---

*What you can do:*

**If you have your .yml scaffolding file for the mod in your Mods folder**:

* PlumbBuddy will offer to take you to immediately update the manifest.
* PlumbBuddy will also offer to take you to the first file in the mod.

**If you don't have your .yml scaffolding file for the mod in your Mods folder, or it's not your mod**:

* PlumbBuddy will offer to take you to redownload the mod.
* PlumbBuddy will also offer to take you to the first file in the mod, so that you can deal with it there.

---

*Extra info:*

* If a file has been altered so that it no longer matches the manifest, the information it contains may not be reliable, so the information from scans and in the Catalog may not be accurate or helpful.
* If you downloaded the mod from anywhere except the original creator's site, you should be very wary of this mod.

This scan is entirely dependent on mod manifests.

This scan is intended to remind you to update your mod manifests, and is the only scan that's on by default for mod creators.`,
        },
    ];
</script>