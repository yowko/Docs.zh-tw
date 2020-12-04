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
# <a name="debug-net-apps-on-raspberry-pi"></a><span data-ttu-id="bbf32-103">在 Raspberry Pi 上進行 .NET 應用程式的偵錯工具</span><span class="sxs-lookup"><span data-stu-id="bbf32-103">Debug .NET apps on Raspberry Pi</span></span>

<span data-ttu-id="bbf32-104">在 Raspberry Pi 等 ARM 型 IoT 裝置上執行的 .NET 應用程式的偵錯工具，是一項獨特的挑戰。</span><span class="sxs-lookup"><span data-stu-id="bbf32-104">Debugging .NET apps running on ARM-based IoT devices like Raspberry Pi presents a unique challenge.</span></span> <span data-ttu-id="bbf32-105">您可以在 ARM 裝置上開發 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bbf32-105">It is possible to develop .NET apps on ARM devices.</span></span> <span data-ttu-id="bbf32-106">不過，若要在 Visual Studio 外部進行 .NET 應用程式的偵錯工具所需的 OmniSharp，與 ARM 裝置不相容。</span><span class="sxs-lookup"><span data-stu-id="bbf32-106">However, OmniSharp, which is required for debugging .NET apps outside of Visual Studio, is not compatible with ARM devices.</span></span> <span data-ttu-id="bbf32-107">因此，應用程式必須從相容的平臺進行遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="bbf32-107">As a result, apps must be debugged remotely from a compatible platform.</span></span>

::: zone pivot="vscode"

## <a name="debug-from-visual-studio-code-cross-platform"></a><span data-ttu-id="bbf32-108">從 Visual Studio Code (跨平臺) 進行 Debug 錯</span><span class="sxs-lookup"><span data-stu-id="bbf32-108">Debug from Visual Studio Code (cross-platform)</span></span>

<span data-ttu-id="bbf32-109">若要從 Visual Studio Code 在 Raspberry Pi 上進行 .NET 偵錯工具，必須在 Raspberry Pi 和專案的 *launch.js* 檔案中設定步驟。</span><span class="sxs-lookup"><span data-stu-id="bbf32-109">Debugging .NET on Raspberry Pi from Visual Studio Code requires configuration steps on the Raspberry Pi and in the project's *launch.json* file.</span></span>

### <a name="enable-ssh-on-the-raspberry-pi"></a><span data-ttu-id="bbf32-110">在 Raspberry Pi 上啟用 SSH</span><span class="sxs-lookup"><span data-stu-id="bbf32-110">Enable SSH on the Raspberry Pi</span></span>

<span data-ttu-id="bbf32-111">需要 SSH 以進行遠端偵錯程式。</span><span class="sxs-lookup"><span data-stu-id="bbf32-111">SSH is required for remote debugging.</span></span> <span data-ttu-id="bbf32-112">若要啟用 SSH，請 [參閱 Raspberry Pi 檔中的 *啟用 ssh*](https://www.raspberrypi.org/documentation/remote-access/ssh/) <span class="docon docon-navigate-external x-hidden-focus"></span> 。</span><span class="sxs-lookup"><span data-stu-id="bbf32-112">To enable SSH, [refer to *Enable SSH* in the Raspberry Pi documentation](https://www.raspberrypi.org/documentation/remote-access/ssh/) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

### <a name="install-the-visual-studio-remote-debugger-on-the-raspberry-pi"></a><span data-ttu-id="bbf32-113">在 Raspberry Pi 上安裝 Visual Studio 遠端偵錯工具</span><span class="sxs-lookup"><span data-stu-id="bbf32-113">Install the Visual Studio Remote Debugger on the Raspberry Pi</span></span>

<span data-ttu-id="bbf32-114">在 Raspberry Pi 上的 Bash 主控台中 (本機或透過 SSH) ，完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="bbf32-114">Within a Bash console on the Raspberry Pi (either locally or via SSH), complete the following steps:</span></span>

1. <span data-ttu-id="bbf32-115">執行下列命令，以下載並安裝 Raspberry Pi 上的 Visual Studio 遠端偵錯工具：</span><span class="sxs-lookup"><span data-stu-id="bbf32-115">Execute the following command to download and install the Visual Studio Remote Debugger on the Raspberry Pi:</span></span>

    ```bash
    curl -sSL https://aka.ms/getvsdbgsh | /bin/sh /dev/stdin -v latest -l ~/vsdbg
    ```

1. <span data-ttu-id="bbf32-116">偵錯工具需要以執行為 `root` 。</span><span class="sxs-lookup"><span data-stu-id="bbf32-116">The debugger requires running as `root`.</span></span> <span data-ttu-id="bbf32-117">根據預設， `root` Raspberry Pi 上沒有任何密碼。</span><span class="sxs-lookup"><span data-stu-id="bbf32-117">By default, `root` has no password on Raspberry Pi.</span></span> <span data-ttu-id="bbf32-118">藉 `root` 由執行下列命令並遵循提示來設定的密碼。</span><span class="sxs-lookup"><span data-stu-id="bbf32-118">Set a password for `root` by executing the following command and following the prompts.</span></span>

    ```bash
    sudo passwd root
    ```

1. <span data-ttu-id="bbf32-119">Visual Studio Code 使用 SSH 通訊協定進行遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="bbf32-119">Visual Studio Code uses the SSH protocol to debug remotely.</span></span> <span data-ttu-id="bbf32-120">基於安全性考慮， `root` 預設不允許透過 SSH 登入。</span><span class="sxs-lookup"><span data-stu-id="bbf32-120">For security purposes, `root` is not permitted to log on via SSH by default.</span></span> <span data-ttu-id="bbf32-121">若要啟用透過 `root` SSH 登入，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="bbf32-121">To enable `root` to log on via SSH, complete the following steps:</span></span>

    1. <span data-ttu-id="bbf32-122">執行下列命令，在 [nano](https://www.nano-editor.org/docs.php)中開啟 */etc/ssh/sshd_config* <span class="docon docon-navigate-external x-hidden-focus"></span> 。</span><span class="sxs-lookup"><span data-stu-id="bbf32-122">Execute the following command to open */etc/ssh/sshd_config* in [nano](https://www.nano-editor.org/docs.php) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

        ```bash
        sudo nano /etc/ssh/sshd_config
        ```

    1. <span data-ttu-id="bbf32-123">按 <kbd>Ctrl + W</kbd> 並搜尋 **PermitRootLogin**。</span><span class="sxs-lookup"><span data-stu-id="bbf32-123">Press <kbd>Ctrl+W</kbd> and search for **PermitRootLogin**.</span></span>
    1. <span data-ttu-id="bbf32-124">如有需要，請使用 **PermitRootLogin** 將該行取消批註。</span><span class="sxs-lookup"><span data-stu-id="bbf32-124">Uncomment the line with **PermitRootLogin** if needed.</span></span>
    1. <span data-ttu-id="bbf32-125">將這一行變更為 [讀取]，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bbf32-125">Change the line to read as follows:</span></span>

        ```console
        PermitRootLogin yes
        ```

        > [!NOTE]
        > <span data-ttu-id="bbf32-126">如果 */etc/ssh/sshd_config* 中沒有任何 **PermitRootLogin** 行，請新增具有上述值的新行。</span><span class="sxs-lookup"><span data-stu-id="bbf32-126">If there is no **PermitRootLogin** line in */etc/ssh/sshd_config*, add a new line with the value shown above.</span></span>

    1. <span data-ttu-id="bbf32-127">按 <kbd>Ctrl + X</kbd> 結束並節省您的機會。</span><span class="sxs-lookup"><span data-stu-id="bbf32-127">Press <kbd>Ctrl+X</kbd> to exit and save your chances.</span></span> <span data-ttu-id="bbf32-128">當系統提示您 **儲存修改過的緩衝區** 時，請按 <kbd>Y</kbd> 來確認。</span><span class="sxs-lookup"><span data-stu-id="bbf32-128">When prompted **Save modified buffer?**, press <kbd>Y</kbd> to confirm.</span></span> <span data-ttu-id="bbf32-129">按 <kbd>enter</kbd> 以確認覆寫原始檔案。</span><span class="sxs-lookup"><span data-stu-id="bbf32-129">Press <kbd>Enter</kbd> to confirm overwriting the original file.</span></span>
    1. <span data-ttu-id="bbf32-130">藉由執行下列命令來重新開機 Raspberry Pi：</span><span class="sxs-lookup"><span data-stu-id="bbf32-130">Reboot the Raspberry Pi by executing the following command:</span></span>

        ```bash
        sudo reboot
        ```

### <a name="setup-launchjson-in-visual-studio-code"></a><span data-ttu-id="bbf32-131">在 Visual Studio Code 中安裝 launch.js</span><span class="sxs-lookup"><span data-stu-id="bbf32-131">Setup launch.json in Visual Studio Code</span></span>

<span data-ttu-id="bbf32-132">將啟動設定新增至專案的 *launch.js*。</span><span class="sxs-lookup"><span data-stu-id="bbf32-132">Add a launch configuration to the project's *launch.json*.</span></span> <span data-ttu-id="bbf32-133">如果專案的檔案沒有 *launch.js* ，請切換至 [ **執行** ] 索引標籤，選取 [ **在檔案上建立 launch.js**]，然後在對話方塊中選取 [ **.net** ] 或 [ **.net Core** ]，以新增一個檔案。</span><span class="sxs-lookup"><span data-stu-id="bbf32-133">If the project doesn't have a *launch.json* file, add one by switching to the **Run** tab, selecting **create a launch.json file**, and selecting **.NET** or **.NET Core** in the dialog.</span></span>

<span data-ttu-id="bbf32-134">*launch.js* 中的新設定看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="bbf32-134">The new configuration in *launch.json* should look similar to this:</span></span>

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

<span data-ttu-id="bbf32-135">請注意：</span><span class="sxs-lookup"><span data-stu-id="bbf32-135">Notice the following:</span></span>

- <span data-ttu-id="bbf32-136">`program` 是 Pi 上 .NET 執行時間的路徑。</span><span class="sxs-lookup"><span data-stu-id="bbf32-136">`program` is the path to the .NET runtime on the Pi.</span></span>
- <span data-ttu-id="bbf32-137">`args` 這是 Pi 上要進行偵錯工具的元件路徑。</span><span class="sxs-lookup"><span data-stu-id="bbf32-137">`args` is the path to the assembly to debug on the Pi.</span></span>
- <span data-ttu-id="bbf32-138">`cwd` 是在 Pi 上啟動應用程式時所使用的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="bbf32-138">`cwd` is the working directory to use when launching the app on the Pi.</span></span>
- <span data-ttu-id="bbf32-139">`pipeProgram` 是本機電腦上 SSH 用戶端的路徑。</span><span class="sxs-lookup"><span data-stu-id="bbf32-139">`pipeProgram` is the path to an SSH client on the local machine.</span></span>
- <span data-ttu-id="bbf32-140">`pipeArgs` 是要傳遞至 SSH 用戶端的參數。</span><span class="sxs-lookup"><span data-stu-id="bbf32-140">`pipeArgs` are the parameters to be passed to the SSH client.</span></span> <span data-ttu-id="bbf32-141">請務必指定 password 參數，以及 `root` 格式的使用者 `<user>@<hostname>` 。</span><span class="sxs-lookup"><span data-stu-id="bbf32-141">Be sure to specify the password parameter, as well as the `root` user in the format `<user>@<hostname>`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bbf32-142">上述範例使用 [PuTTY](https://www.ssh.com/ssh/putty/) SSH 用戶端的 *plink* 元件 <span class="docon docon-navigate-external x-hidden-focus"></span> 。</span><span class="sxs-lookup"><span data-stu-id="bbf32-142">The above example uses *plink*, a component of the [PuTTY](https://www.ssh.com/ssh/putty/)<span class="docon docon-navigate-external x-hidden-focus"></span> SSH client.</span></span> <span data-ttu-id="bbf32-143">[OpenSSH](https://www.openssh.com/)您 <span class="docon docon-navigate-external x-hidden-focus"></span> 可以改為使用 OpenSSH （包含在最新版本的 Windows 和 Linux 中）。</span><span class="sxs-lookup"><span data-stu-id="bbf32-143">[OpenSSH](https://www.openssh.com/)<span class="docon docon-navigate-external x-hidden-focus"></span>, which is included in recent versions of Windows and Linux, may be used instead.</span></span> <span data-ttu-id="bbf32-144">不過，OpenSSH 不支援以命令列參數的方式傳送密碼。</span><span class="sxs-lookup"><span data-stu-id="bbf32-144">However, OpenSSH doesn't support sending passwords as a command-line parameter.</span></span> <span data-ttu-id="bbf32-145">若要使用 OpenSSH，請 [設定您的 Raspberry Pi 以無密碼 SSH 存取](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md) <span class="docon docon-navigate-external x-hidden-focus"></span> 。</span><span class="sxs-lookup"><span data-stu-id="bbf32-145">To use OpenSSH, [configure your Raspberry Pi for passwordless SSH access](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

### <a name="deploy-the-app"></a><span data-ttu-id="bbf32-146">部署應用程式</span><span class="sxs-lookup"><span data-stu-id="bbf32-146">Deploy the app</span></span>

<span data-ttu-id="bbf32-147">依照 [將 .net 應用程式部署至 Raspberry Pi](deployment.md)中所述的方式部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="bbf32-147">Deploy the app as described in [Deploy .NET apps to Raspberry Pi](deployment.md).</span></span> <span data-ttu-id="bbf32-148">請確定部署路徑與設定中launch.js的參數所指定的路徑相同。 `cwd` *launch.json*</span><span class="sxs-lookup"><span data-stu-id="bbf32-148">Ensure the deployment path is the same path specified in the `cwd` parameter in the *launch.json* configuration.</span></span>

### <a name="launch-the-debugger"></a><span data-ttu-id="bbf32-149">啟動偵錯工具</span><span class="sxs-lookup"><span data-stu-id="bbf32-149">Launch the debugger</span></span>

<span data-ttu-id="bbf32-150">在 [ **執行** ] 索引標籤上，選取 [ **.net Core 啟動 (遠端主控台)** 設定]，然後選取 [ **開始調試**]。</span><span class="sxs-lookup"><span data-stu-id="bbf32-150">On the **Run** tab, select the **.NET Core Launch (remote console)** configuration and select **Start Debugging**.</span></span> <span data-ttu-id="bbf32-151">應用程式會在 Raspberry Pi 上啟動。</span><span class="sxs-lookup"><span data-stu-id="bbf32-151">The app launches on the Raspberry Pi.</span></span> <span data-ttu-id="bbf32-152">偵錯工具可用來設定中斷點、檢查區域變數等等。</span><span class="sxs-lookup"><span data-stu-id="bbf32-152">The debugger may be used to set breakpoints, inspect locals, and more.</span></span>

## <a name="references"></a><span data-ttu-id="bbf32-153">參考資料</span><span class="sxs-lookup"><span data-stu-id="bbf32-153">References</span></span>

<span data-ttu-id="bbf32-154">[使用 ARM 上的 .Net Core 在 Windows 上將 VS Code 從遠端偵錯至 Raspberry Pi](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="bbf32-154">[Remote debugging with VS Code on Windows to a Raspberry Pi using .NET Core on ARM](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>

::: zone-end

::: zone pivot="visualstudio"

## <a name="debug-from-visual-studio-on-windows"></a><span data-ttu-id="bbf32-155">從 Windows 上的 Visual Studio 進行調試</span><span class="sxs-lookup"><span data-stu-id="bbf32-155">Debug from Visual Studio on Windows</span></span>

<span data-ttu-id="bbf32-156">Visual Studio 可以透過 SSH 在遠端裝置上進行 .NET 應用程式的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bbf32-156">Visual Studio can debug .NET apps on remote devices via SSH.</span></span> <span data-ttu-id="bbf32-157">裝置上不需要任何特殊設定。</span><span class="sxs-lookup"><span data-stu-id="bbf32-157">No specialized configuration is required on the device.</span></span> <span data-ttu-id="bbf32-158">如需使用 Visual Studio 從遠端偵錯程式的詳細資訊，請參閱 [使用 SSH 在 Linux 上的遠端偵錯程式 .net](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019)。</span><span class="sxs-lookup"><span data-stu-id="bbf32-158">For details on using Visual Studio to debug .NET remotely, see [Remote debug .NET on Linux using SSH](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019).</span></span>

::: zone-end
