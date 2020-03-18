---
title: 教程：安裝和使用 .NET 核心本地工具
description: 瞭解如何安裝和使用 .NET 工具作為本地工具。
ms.date: 02/12/2020
ms.openlocfilehash: a4355886513040e2436bdbd87905e5baee2dd7a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156695"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a><span data-ttu-id="dc6e9-103">教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心本地工具</span><span class="sxs-lookup"><span data-stu-id="dc6e9-103">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>

<span data-ttu-id="dc6e9-104">**本文適用于：✔️** .NET Core 3.0 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="dc6e9-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="dc6e9-105">本教程將教您如何安裝和使用本地工具。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-105">This tutorial teaches you how to install and use a local tool.</span></span> <span data-ttu-id="dc6e9-106">使用在本[系列的第一個教程](global-tools-how-to-create.md)中創建的工具。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc6e9-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="dc6e9-107">Prerequisites</span></span>

* <span data-ttu-id="dc6e9-108">完成[本系列的第一個教程](global-tools-how-to-create.md)。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>
* <span data-ttu-id="dc6e9-109">安裝 .NET 核心 2.1 運行時。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-109">Install the .NET Core 2.1 runtime.</span></span>

  <span data-ttu-id="dc6e9-110">在本教程中，您可以安裝並使用以 .NET Core 2.1 為目標的工具，因此需要在電腦上安裝該運行時。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-110">For this tutorial you install and use a tool that targets .NET Core 2.1, so you need to have that runtime installed on your machine.</span></span> <span data-ttu-id="dc6e9-111">要安裝 2.1 運行時，請轉到[.NET Core 2.1 下載頁面](https://dotnet.microsoft.com/download/dotnet-core/2.1)，並在 **"運行應用 - 運行時**"列中找到運行時安裝連結。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-111">To install the 2.1 runtime, go to the [.NET Core 2.1 download page](https://dotnet.microsoft.com/download/dotnet-core/2.1) and find the runtime installation link in the **Run apps - Runtime** column.</span></span>

## <a name="create-a-manifest-file"></a><span data-ttu-id="dc6e9-112">創建清單檔</span><span class="sxs-lookup"><span data-stu-id="dc6e9-112">Create a manifest file</span></span>

<span data-ttu-id="dc6e9-113">要僅安裝本地訪問工具（對於目前的目錄和子目錄），必須將其添加到清單檔中。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-113">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a manifest file.</span></span>

<span data-ttu-id="dc6e9-114">從*Microsoft.botsay*資料夾，向上導航一個級別到*存儲庫*資料夾：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-114">From the *microsoft.botsay* folder, navigate up one level to the *repository* folder:</span></span>

```console
cd ..
```

<span data-ttu-id="dc6e9-115">通過運行[dotnet 新](dotnet-new.md)命令創建清單檔：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-115">Create a manifest file by running the [dotnet new](dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="dc6e9-116">輸出指示檔成功創建。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-116">The output indicates successful creation of the file.</span></span>

```console
The template "Dotnet local tool manifest file" was created successfully.
```

<span data-ttu-id="dc6e9-117">*.config/dotnet-tools.json*檔中尚未包含任何工具：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-117">The *.config/dotnet-tools.json* file has no tools in it yet:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="dc6e9-118">清單檔中列出的工具可用於目前的目錄和子目錄。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-118">The tools listed in a manifest file are available to the current directory and subdirectories.</span></span> <span data-ttu-id="dc6e9-119">目前的目錄是包含包含清單檔的 *.config*目錄的目錄。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-119">The current directory is the one that contains the *.config* directory with the manifest file.</span></span>

<span data-ttu-id="dc6e9-120">當您使用引用本地工具的 CLI 命令時，SDK 將搜索目前的目錄和父目錄中的清單檔。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-120">When you use a CLI command that refers to a local tool, the SDK searches for a manifest file in the current directory and parent directories.</span></span> <span data-ttu-id="dc6e9-121">如果它找到清單檔，但該檔不包括引用的工具，它將通過父目錄繼續搜索。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-121">If it finds a manifest file, but the file doesn't include the referenced tool, it continues the search up through parent directories.</span></span> <span data-ttu-id="dc6e9-122">搜索在找到引用的工具或找到設置為`isRoot``true`的清單檔時結束。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-122">The search ends when it finds the referenced tool or it finds a manifest file with `isRoot` set to `true`.</span></span>

## <a name="install-botsay-as-a-local-tool"></a><span data-ttu-id="dc6e9-123">將僵屍資訊作為本地工具安裝</span><span class="sxs-lookup"><span data-stu-id="dc6e9-123">Install botsay as a local tool</span></span>

<span data-ttu-id="dc6e9-124">從第一個教程中創建的包安裝該工具：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-124">Install the tool from the package that you created in the first tutorial:</span></span>

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

<span data-ttu-id="dc6e9-125">此命令將該工具添加到您在上一步中創建的清單檔中。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-125">This command adds the tool to the manifest file that you created in the preceding step.</span></span> <span data-ttu-id="dc6e9-126">命令輸出顯示新安裝的工具的清單檔位於：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-126">The command output shows which manifest file the newly installed tool is in:</span></span>

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

<span data-ttu-id="dc6e9-127">*.config/dotnet 工具.json*檔現在有一個工具：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-127">The *.config/dotnet-tools.json* file now has one tool:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "microsoft.botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a><span data-ttu-id="dc6e9-128">使用工具</span><span class="sxs-lookup"><span data-stu-id="dc6e9-128">Use the tool</span></span>

<span data-ttu-id="dc6e9-129">通過從`dotnet tool run`*存儲庫*資料夾中運行命令來調用該工具：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-129">Invoke the tool by running the `dotnet tool run` command from the *repository* folder:</span></span>

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a><span data-ttu-id="dc6e9-130">還原其他人安裝的本地工具</span><span class="sxs-lookup"><span data-stu-id="dc6e9-130">Restore a local tool installed by others</span></span>

<span data-ttu-id="dc6e9-131">通常在存儲庫的根目錄中安裝本地工具。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-131">You typically install a local tool in the root directory of the repository.</span></span> <span data-ttu-id="dc6e9-132">將清單檔簽入存儲庫後，其他開發人員可以獲取最新的清單檔。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-132">After you check in the manifest file to the repository, other developers can get the latest manifest file.</span></span> <span data-ttu-id="dc6e9-133">要安裝清單檔中列出的所有工具，它們可以運行單個`dotnet tool restore`命令。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-133">To install all of the tools listed in the manifest file, they can run a single `dotnet tool restore` command.</span></span>

1. <span data-ttu-id="dc6e9-134">打開 *.config/dotnet 工具.json*檔，並將內容替換為以下 JSON：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-134">Open the *.config/dotnet-tools.json* file, and replace the contents with the following JSON:</span></span>

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "microsoft.botsay": {
         "version": "1.0.0",
         "commands": [
           "botsay"
         ]
       },
       "dotnetsay": {
         "version": "2.1.3",
         "commands": [
           "dotnetsay"
         ]
       }
     }
   }
   ```

1. <span data-ttu-id="dc6e9-135">替換為`<name>`用於創建專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-135">Replace `<name>` with the name you used to create the project.</span></span>

1. <span data-ttu-id="dc6e9-136">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-136">Save your changes.</span></span>

   <span data-ttu-id="dc6e9-137">進行此更改與在其他人為專案目錄安裝包`dotnetsay`後從存儲庫獲取最新版本相同。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-137">Making this change is the same as getting the latest version from the repository after someone else installed the package `dotnetsay` for the project directory.</span></span>

1. <span data-ttu-id="dc6e9-138">執行 `dotnet tool restore` 命令。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-138">Run the `dotnet tool restore` command.</span></span>

   ```dotnetcli
   dotnet tool restore
   ```

   <span data-ttu-id="dc6e9-139">該命令生成輸出，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-139">The command produces output like the following example:</span></span>

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. <span data-ttu-id="dc6e9-140">驗證這些工具是否可用：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-140">Verify that the tools are available:</span></span>

   ```dotnetcli
   dotnet tool list
   ```

   <span data-ttu-id="dc6e9-141">輸出是包和命令的清單，類似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-141">The output is a list of packages and commands, similar to the following example:</span></span>

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. <span data-ttu-id="dc6e9-142">測試控管：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-142">Test the tools:</span></span>

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a><span data-ttu-id="dc6e9-143">更新本地工具</span><span class="sxs-lookup"><span data-stu-id="dc6e9-143">Update a local tool</span></span>

<span data-ttu-id="dc6e9-144">本地工具`dotnetsay`的已安裝版本為 2.1.3。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-144">The installed version of local tool `dotnetsay` is 2.1.3.</span></span>  <span data-ttu-id="dc6e9-145">最新版本為 2.1.4。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-145">The latest version is 2.1.4.</span></span> <span data-ttu-id="dc6e9-146">使用[dotnet 工具更新](dotnet-tool-update.md)命令將該工具更新到最新版本。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-146">Use the [dotnet tool update](dotnet-tool-update.md) command to update the tool to the latest version.</span></span>

```dotnetcli
dotnet tool update dotnetsay
```

<span data-ttu-id="dc6e9-147">輸出指示新版本號：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-147">The output indicates the new version number:</span></span>

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

<span data-ttu-id="dc6e9-148">更新命令查找包含包 ID 並更新它的第一個清單檔。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-148">The update command finds the first manifest file that contains the package ID and updates it.</span></span> <span data-ttu-id="dc6e9-149">如果在搜尋範圍內的任何清單檔中沒有此類包 ID，SDK 會向最近的清單檔添加新條目。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-149">If there is no such package ID in any manifest file that is in the scope of the search, the SDK adds a new entry to the closest manifest file.</span></span> <span data-ttu-id="dc6e9-150">搜尋範圍通過父目錄向上，直到找到 具有 的`isRoot = true`清單檔。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-150">The search scope is up through parent directories until a manifest file with `isRoot = true` is found.</span></span>

## <a name="remove-local-tools"></a><span data-ttu-id="dc6e9-151">刪除本地工具</span><span class="sxs-lookup"><span data-stu-id="dc6e9-151">Remove local tools</span></span>

<span data-ttu-id="dc6e9-152">通過運行[dotnet 工具卸載](dotnet-tool-uninstall.md)命令刪除已安裝的工具：</span><span class="sxs-lookup"><span data-stu-id="dc6e9-152">Remove the installed tools by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a><span data-ttu-id="dc6e9-153">疑難排解</span><span class="sxs-lookup"><span data-stu-id="dc6e9-153">Troubleshoot</span></span>

<span data-ttu-id="dc6e9-154">如果您在學習本教程時收到錯誤訊息，請參閱[疑難排解 .NET Core 工具使用問題](troubleshoot-usage-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="dc6e9-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dc6e9-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc6e9-155">See also</span></span>

<span data-ttu-id="dc6e9-156">有關詳細資訊，請參閱[.NET 核心工具](global-tools.md)</span><span class="sxs-lookup"><span data-stu-id="dc6e9-156">For more information, see [.NET Core tools](global-tools.md)</span></span>
