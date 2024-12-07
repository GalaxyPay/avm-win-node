# ![icon](assets/icon.png) Funk's Ultimate Node Controller (FUNC)

FUNC is a Cross-platform Service that makes it easy to spin up a node for Algorand or Voi and start participating in consensus.

![screenshot](assets/screenshot.png)

## Installation

Head over to the [releases page](https://github.com/GalaxyPay/func/releases) and download the install file for your OS.

The installer does not include the node software. It is automatically downloaded from [this open-source repo](https://github.com/GalaxyPay/go-algo-win) (Windows) or [the official Algorand repo](https://github.com/algorand/go-algorand) (Mac/Linux) the first time you open the app. This separation allows the node software to be updated without needing to update this app.

### Windows

In order to run it, you'll need to click "More info" on the "Windows protected your PC" dialog.
Then click the "Run Anyway" button.
The code is open-source so you can review it yourself or have a trusted friend do so.

When updating a previous installation, the installer will recommend to let it automatically close applications and restart them after install. You should allow it to do this.

### Linux

After downloading the `.deb` file to your machine, run

```sh
sudo dpkg -i func_<version>_amd64.deb
```

Then visit the locally hosted webpage at <http://localhost:3536> (for remote access see notes below)

## Uninstall

The app is a **Node Service Manager** - uninstalling it will **_not_** remove node services that you create with it. If you wish to remove everything, use the app to Remove Services and even Delete Node Data before uninstalling the app.

## Manage Node Menu Options

### Create Service

- Creates and starts a new Service to run the Node
- Only available when Service does not exist

### Start Node

- Starts Service that runs the Node
- Only available when Service is stopped

### Stop Node

- Stops Service that runs the Node
- Only available when Service is running

### Remove Service

- Removes Service that runs the Node
- Only available when Service is stopped

### Delete Node Data

- Deletes all node data, including any participation and KMD keys
- Only available when Service does not exist

## Notes

- The app is a [locally hosted webpage](http://localhost:3536). After install, bookmark it for easy access.

  - If you want to access the site from another computer on your network, you will need to open the following ports:

    - 3536 - FUNC UI and API
    - 8081 - Algorand algod
    - 8082 - Voi algod
    - 8083 - Fnet algod

  - The `algod` ports are configurable through the UI, and you only need to open the ones for the networks you use

  - This should **ONLY** be done on a local network - **DO NOT** open these ports to the internet

- The node will restart automatically if your computer reboots, but you will need to configure your computer to **_not_** go into Sleep mode in order to keep the node running 24/7.

- If you Stop a node and restart your computer, the node will restart automatically. You must remove the service if you want the node to not restart. Removing the service preserves the node data; deleting the data is a separate step.

## Build (for Developers)

You can fork the repo and let Github Actions do the build for you, or you can run [LocalPublish.ps1](LocalPublish.ps1) for Windows, or [local-publish.sh](local-publish.sh) and [create-package.sh](create-package.sh) for Linux.

Dependencies include .NET Core 8, Node.js, pnpm, and Inno Setup.
