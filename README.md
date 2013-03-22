powershell-taglib
=================

A PowerShell module for manipulating metadata in media files with [TagLibSharp](https://github.com/mono/taglib-sharp)
* [Installation](#installation)
* [Functions](#functions)
* [License](#license)

## <a id="installation">Installation</a>
1. Clone this repo to your PSModulePath (typically `$Env:UserProfile\Documents\WindowsPowerShell\Modules`)

    ```ps1
        C:\cd cd $Env:PSModulePath.split(';')[0]
        C:\Users\illearth\Documents\WindowsPowerShell\Modules>git clone git@github.com:illearth/powershell-taglib.git taglib
    ```
1. Import-Module taglib

## <a id="functions">Functions</a>
* [set-artist](#set-artist)
* [set-title](#set-title)
* [set-album](#set-album)
* [set-track](#set-track)
* [set-disc](#set-disc)
* [update-trackAndDisc](#update-trackAndDisc)

### <a id="set-artist">set-artist</a>
**Type**: Filter   

**Parameter [string]**: value to set as the artist    

**Description**: Sets the ID tag artist    

**Example**:   

```ps1
   C:\mp3\Fugazi\13 Songs> get-childitem *.mp3 | set-artist "Fugazi"
```

### <a id="set-title">set-title</a>
**Type**: Filter   

**Parameter [string]**: *Optional* value to set as the title. If not passed the name of the file (less the extension) will be used (e.g. if the file is named "Waiting Room.mp3" then the title would be set at "Waiting Room")    

**Description**: Sets the ID tag title    

**Example**:   

```ps1
    C:\mp3\Fugazi\13 Songs> get-childitem WaitingRoom.mp3 | set-title "Waiting Room"
```

### <a id="set-album">set-album</a>
**Type**: Filter   

**Parameter [string]**: value to set as the album    

**Description**: Sets the ID tag album    

**Example**:   

```ps1
    C:\mp3\Fugazi\13 Songs> get-childitem *.mp3 | set-album "13 Songs"
```

### <a id="set-track">set-track</a>
**Type**: Filter   

**Parameter [int]**: value to set as the track    

**Description**: Sets the ID tag track, or the track number on the album

**Example**:   

```ps1
    C:\mp3\Fugazi\13 Songs> get-childitem WaitingRoom.mp3 | set-track 1
```

### <a id="set-disc">set-disc</a>
**Type**: Filter   

**Parameter [int]**: value to set as the disc    

**Description**: Sets the ID tag disc, or the disc number for multi-disc sets

**Example**:   

```ps1
    C:\mp3\Fugazi\13 Songs> get-childitem *.mp3 | set-disc 1
```

### <a id="update-trackAndDisc">update-trackAndDisc</a>
**Type**: Filter   

**Parameter [string]**: *Optional* regular expression to use to match the disc and track from the title. Defaults to "D(?<disc>[0-9]+)T(?<track>[0-9]+)" which will match the disc and track from a pattern of DXXTXX. Disc and track need to be named expression groups.     

**Description**: Sets the disc and track of a files from a mulit-disc set by extracting the disc and track from the filename. Useful for audio book sets where you have multiple discs of a single book in a single directory.

**Example**:   

```ps1
    C:\mp3\George R. R. Martin\A Clash of Kings> get-childitem *.mp3 | update-trackAndDisc
```

## <a id="license">License</a>
Distributed under the [MIT License](http://opensource.org/licenses/mit-license.php)
