---
title: 在 Raspberry Pi 上進行 .NET 應用程式的偵錯工具
description: 瞭解如何在 Raspberry Pi 和類似裝置上進行 .NET 應用程式的偵錯工具。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
zone_pivot_groups: ide-set-one
ms.openlocfilehash: 7b9872304ee53071452772e3da02081a7def4d80
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "96586626"
---
# <a name="debug-net-apps-on-raspberry-pi"></a>在 Raspberry Pi 上進行 .NET 應用程式的偵錯工具

在 Raspberry Pi 等 ARM 型 IoT 裝置上執行的 .NET 應用程式的偵錯工具，是一項獨特的挑戰。 您可以在 ARM 裝置上開發 .NET 應用程式。 不過，若要在 Visual Studio 外部進行 .NET 應用程式的偵錯工具所需的 OmniSharp，與 ARM 裝置不相容。 因此，應用程式必須從相容的平臺進行遠端偵錯。

::: zone pivot="vscode"

## <a name="debug-from-visual-studio-code-cross-platform"></a>從 Visual Studio Code (跨平臺) 進行 Debug 錯

若要從 Visual Studio Code 在 Raspberry Pi 上進行 .NET 偵錯工具，必須在 Raspberry Pi 和專案的 *launch.js* 檔案中設定步驟。

### <a name="enable-ssh-on-the-raspberry-pi"></a>在 Raspberry Pi 上啟用 SSH

需要 SSH 以進行遠端偵錯程式。 若要啟用 SSH，請 [參閱 Raspberry Pi 檔中的 *啟用 ssh*](https://www.raspberrypi.org/documentation/remote-access/ssh/) <span class="docon docon-navigate-external x-hidden-focus"></span> 。

### <a name="install-the-visual-studio-remote-debugger-on-the-raspberry-pi"></a>在 Raspberry Pi 上安裝 Visual Studio 遠端偵錯工具

在 Raspberry Pi 上的 Bash 主控台中 (本機或透過 SSH) ，完成下列步驟：

1. 執行下列命令，以下載並安裝 Raspberry Pi 上的 Visual Studio 遠端偵錯工具：

    ```bash
    curl -sSL https://aka.ms/getvsdbgsh | /bin/sh /dev/stdin -v latest -l ~/vsdbg
    ```

1. 偵錯工具需要以執行為 `root` 。 根據預設， `root` Raspberry Pi 上沒有任何密碼。 藉 `root` 由執行下列命令並遵循提示來設定的密碼。

    ```bash
    sudo passwd root
    ```

1. Visual Studio Code 使用 SSH 通訊協定進行遠端偵錯。 基於安全性考慮， `root` 預設不允許透過 SSH 登入。 若要啟用透過 `root` SSH 登入，請完成下列步驟：

    1. 執行下列命令，在 [nano](https://www.nano-editor.org/docs.php)中開啟 */etc/ssh/sshd_config* <span class="docon docon-navigate-external x-hidden-focus"></span> 。

        ```bash
        sudo nano /etc/ssh/sshd_config
        ```

    1. 按 <kbd>Ctrl + W</kbd> 並搜尋 **PermitRootLogin**。
    1. 如有需要，請使用 **PermitRootLogin** 將該行取消批註。
    1. 將這一行變更為 [讀取]，如下所示：

        ```console
        PermitRootLogin yes
        ```

        > [!NOTE]
        > 如果 */etc/ssh/sshd_config* 中沒有任何 **PermitRootLogin** 行，請新增具有上述值的新行。

    1. 按 <kbd>Ctrl + X</kbd> 結束並節省您的機會。 當系統提示您 **儲存修改過的緩衝區** 時，請按 <kbd>Y</kbd> 來確認。 按 <kbd>enter</kbd> 以確認覆寫原始檔案。
    1. 藉由執行下列命令來重新開機 Raspberry Pi：

        ```bash
        sudo reboot
        ```

### <a name="setup-launchjson-in-visual-studio-code"></a>在 Visual Studio Code 中安裝 launch.js

將啟動設定新增至專案的 *launch.js*。 如果專案的檔案沒有 *launch.js* ，請切換至 [ **執行** ] 索引標籤，選取 [ **在檔案上建立 launch.js**]，然後在對話方塊中選取 [ **.net** ] 或 [ **.net Core** ]，以新增一個檔案。

*launch.js* 中的新設定看起來應該像這樣：

```json
"configurations": [
    {
        "name": ".NET Core Launch (remote console)",
        "type": "coreclr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "/home/pi/.dotnet/dotnet",
        "args": ["/home/pi/sample/Sample.dll"],
        "cwd": "/home/pi/sample",
        "stopAtEntry": false,
        "console": "internalConsole",
        "pipeTransport": {
            "pipeCwd": "${workspaceFolder}",
            "pipeProgram": "C:\\Program Files\\PuTTY\\PLINK.EXE",
            "pipeArgs": [
                "-pw",
                "P@ssw0rd",
                "root@raspberrypi"
            ],
            "debuggerPath": "/home/pi/vsdbg/vsdbg"
        }
    },
```

請注意：

- `program` 是 Pi 上 .NET 執行時間的路徑。
- `args` 這是 Pi 上要進行偵錯工具的元件路徑。
- `cwd` 是在 Pi 上啟動應用程式時所使用的工作目錄。
- `pipeProgram` 是本機電腦上 SSH 用戶端的路徑。
- `pipeArgs` 是要傳遞至 SSH 用戶端的參數。 請務必指定 password 參數，以及 `root` 格式的使用者 `<user>@<hostname>` 。

> [!IMPORTANT]
> 上述範例使用 [PuTTY](https://www.ssh.com/ssh/putty/) SSH 用戶端的 *plink* 元件 <span class="docon docon-navigate-external x-hidden-focus"></span> 。 [OpenSSH](https://www.openssh.com/)您 <span class="docon docon-navigate-external x-hidden-focus"></span> 可以改為使用 OpenSSH （包含在最新版本的 Windows 和 Linux 中）。 不過，OpenSSH 不支援以命令列參數的方式傳送密碼。 若要使用 OpenSSH，請 [設定您的 Raspberry Pi 以無密碼 SSH 存取](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md) <span class="docon docon-navigate-external x-hidden-focus"></span> 。

### <a name="deploy-the-app"></a>部署應用程式

依照 [將 .net 應用程式部署至 Raspberry Pi](deployment.md)中所述的方式部署應用程式。 請確定部署路徑與設定中launch.js的參數所指定的路徑相同。 `cwd` *launch.json*

### <a name="launch-the-debugger"></a>啟動偵錯工具

在 [ **執行** ] 索引標籤上，選取 [ **.net Core 啟動 (遠端主控台)** 設定]，然後選取 [ **開始調試**]。 應用程式會在 Raspberry Pi 上啟動。 偵錯工具可用來設定中斷點、檢查區域變數等等。

## <a name="references"></a>參考資料

[使用 ARM 上的 .Net Core 在 Windows 上將 VS Code 從遠端偵錯至 Raspberry Pi](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm)<span class="docon docon-navigate-external x-hidden-focus"></span>

::: zone-end

::: zone pivot="visualstudio"

## <a name="debug-from-visual-studio-on-windows"></a>從 Windows 上的 Visual Studio 進行調試

Visual Studio 可以透過 SSH 在遠端裝置上進行 .NET 應用程式的偵錯工具。 裝置上不需要任何特殊設定。 如需使用 Visual Studio 從遠端偵錯程式的詳細資訊，請參閱 [使用 SSH 在 Linux 上的遠端偵錯程式 .net](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019)。

::: zone-end
