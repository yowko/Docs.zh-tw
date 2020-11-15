---
title: 教學課程：安裝和使用 .NET 本機工具
description: 瞭解如何安裝和使用 .NET 工具作為本機工具。
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 2cb25443706293b66325d43136afcd3fd886294d
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633877"
---
# <a name="tutorial-install-and-use-a-net-local-tool-using-the-net-cli"></a><span data-ttu-id="a3f35-103">教學課程：使用 .NET CLI 安裝和使用 .NET 本機工具</span><span class="sxs-lookup"><span data-stu-id="a3f35-103">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>

<span data-ttu-id="a3f35-104">本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a3f35-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="a3f35-105">本教學課程會教您如何安裝和使用本機工具。</span><span class="sxs-lookup"><span data-stu-id="a3f35-105">This tutorial teaches you how to install and use a local tool.</span></span> <span data-ttu-id="a3f35-106">您可以使用您在 [本系列的第一個教學](global-tools-how-to-create.md)課程中建立的工具。</span><span class="sxs-lookup"><span data-stu-id="a3f35-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a3f35-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="a3f35-107">Prerequisites</span></span>

* <span data-ttu-id="a3f35-108">完成 [本系列的第一個教學](global-tools-how-to-create.md)課程。</span><span class="sxs-lookup"><span data-stu-id="a3f35-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>
* <span data-ttu-id="a3f35-109">安裝 .NET Core 2.1 執行時間。</span><span class="sxs-lookup"><span data-stu-id="a3f35-109">Install the .NET Core 2.1 runtime.</span></span>

  <span data-ttu-id="a3f35-110">在本教學課程中，您會安裝並使用以 .NET Core 2.1 為目標的工具，因此您必須在電腦上安裝該執行時間。</span><span class="sxs-lookup"><span data-stu-id="a3f35-110">For this tutorial you install and use a tool that targets .NET Core 2.1, so you need to have that runtime installed on your machine.</span></span> <span data-ttu-id="a3f35-111">若要安裝2.1 執行時間，請移至 [.Net Core 2.1 下載頁面](https://dotnet.microsoft.com/download/dotnet-core/2.1) ，並在 [ **執行應用程式-運行** 時間] 資料行中尋找執行時間安裝連結。</span><span class="sxs-lookup"><span data-stu-id="a3f35-111">To install the 2.1 runtime, go to the [.NET Core 2.1 download page](https://dotnet.microsoft.com/download/dotnet-core/2.1) and find the runtime installation link in the **Run apps - Runtime** column.</span></span>

## <a name="create-a-manifest-file"></a><span data-ttu-id="a3f35-112">建立資訊清單檔</span><span class="sxs-lookup"><span data-stu-id="a3f35-112">Create a manifest file</span></span>

<span data-ttu-id="a3f35-113">若要安裝僅限本機存取的工具 (針對目前的目錄和子目錄) ，必須將其新增至資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="a3f35-113">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a manifest file.</span></span>

<span data-ttu-id="a3f35-114">從 *botsay* 資料夾中，流覽至存放 *庫* 資料夾的其中一個層級：</span><span class="sxs-lookup"><span data-stu-id="a3f35-114">From the *microsoft.botsay* folder, navigate up one level to the *repository* folder:</span></span>

```console
cd ..
```

<span data-ttu-id="a3f35-115">藉由執行 [dotnet new](dotnet-new.md) 命令來建立資訊清單檔案：</span><span class="sxs-lookup"><span data-stu-id="a3f35-115">Create a manifest file by running the [dotnet new](dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="a3f35-116">輸出會指出檔案已成功建立。</span><span class="sxs-lookup"><span data-stu-id="a3f35-116">The output indicates successful creation of the file.</span></span>

```console
The template "Dotnet local tool manifest file" was created successfully.
```

<span data-ttu-id="a3f35-117">檔案 *上的 .config/dotnet-tools.js* 還沒有工具：</span><span class="sxs-lookup"><span data-stu-id="a3f35-117">The *.config/dotnet-tools.json* file has no tools in it yet:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="a3f35-118">資訊清單檔中所列的工具可供目前的目錄和子目錄使用。</span><span class="sxs-lookup"><span data-stu-id="a3f35-118">The tools listed in a manifest file are available to the current directory and subdirectories.</span></span> <span data-ttu-id="a3f35-119">目前的目錄是包含 *.config* 目錄與資訊清單檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="a3f35-119">The current directory is the one that contains the *.config* directory with the manifest file.</span></span>

<span data-ttu-id="a3f35-120">當您使用參考本機工具的 CLI 命令時，SDK 會在目前目錄和父目錄中搜尋資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="a3f35-120">When you use a CLI command that refers to a local tool, the SDK searches for a manifest file in the current directory and parent directories.</span></span> <span data-ttu-id="a3f35-121">如果它找到資訊清單檔案，但檔案未包含參考的工具，它會繼續透過上層目錄進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="a3f35-121">If it finds a manifest file, but the file doesn't include the referenced tool, it continues the search up through parent directories.</span></span> <span data-ttu-id="a3f35-122">當搜尋找到參考的工具，或找到的資訊清單檔案的設定為時，就會結束搜尋 `isRoot` `true` 。</span><span class="sxs-lookup"><span data-stu-id="a3f35-122">The search ends when it finds the referenced tool or it finds a manifest file with `isRoot` set to `true`.</span></span>

## <a name="install-botsay-as-a-local-tool"></a><span data-ttu-id="a3f35-123">將 botsay 安裝為本機工具</span><span class="sxs-lookup"><span data-stu-id="a3f35-123">Install botsay as a local tool</span></span>

<span data-ttu-id="a3f35-124">從您在第一個教學課程中建立的套件安裝工具：</span><span class="sxs-lookup"><span data-stu-id="a3f35-124">Install the tool from the package that you created in the first tutorial:</span></span>

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

<span data-ttu-id="a3f35-125">此命令會將工具新增至您在上一個步驟中建立的資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="a3f35-125">This command adds the tool to the manifest file that you created in the preceding step.</span></span> <span data-ttu-id="a3f35-126">命令輸出會顯示新安裝的工具所在的資訊清單檔案：</span><span class="sxs-lookup"><span data-stu-id="a3f35-126">The command output shows which manifest file the newly installed tool is in:</span></span>

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

<span data-ttu-id="a3f35-127">檔案 *上的 .config/dotnet-tools.js* 現在有一項工具：</span><span class="sxs-lookup"><span data-stu-id="a3f35-127">The *.config/dotnet-tools.json* file now has one tool:</span></span>

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

## <a name="use-the-tool"></a><span data-ttu-id="a3f35-128">使用工具</span><span class="sxs-lookup"><span data-stu-id="a3f35-128">Use the tool</span></span>

<span data-ttu-id="a3f35-129">`dotnet tool run`從存放 *庫* 資料夾執行命令來叫用工具：</span><span class="sxs-lookup"><span data-stu-id="a3f35-129">Invoke the tool by running the `dotnet tool run` command from the *repository* folder:</span></span>

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a><span data-ttu-id="a3f35-130">還原其他人所安裝的本機工具</span><span class="sxs-lookup"><span data-stu-id="a3f35-130">Restore a local tool installed by others</span></span>

<span data-ttu-id="a3f35-131">您通常會在存放庫的根目錄中安裝本機工具。</span><span class="sxs-lookup"><span data-stu-id="a3f35-131">You typically install a local tool in the root directory of the repository.</span></span> <span data-ttu-id="a3f35-132">將資訊清單檔案簽入存放庫之後，其他開發人員就可以取得最新的資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="a3f35-132">After you check in the manifest file to the repository, other developers can get the latest manifest file.</span></span> <span data-ttu-id="a3f35-133">若要安裝資訊清單檔案中列出的所有工具，可以執行單一 `dotnet tool restore` 命令。</span><span class="sxs-lookup"><span data-stu-id="a3f35-133">To install all of the tools listed in the manifest file, they can run a single `dotnet tool restore` command.</span></span>

1. <span data-ttu-id="a3f35-134">開啟檔案的 *.config/dotnet-tools.js* ，並將內容取代為下列 JSON：</span><span class="sxs-lookup"><span data-stu-id="a3f35-134">Open the *.config/dotnet-tools.json* file, and replace the contents with the following JSON:</span></span>

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

1. <span data-ttu-id="a3f35-135">取代為 `<name>` 您用來建立專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3f35-135">Replace `<name>` with the name you used to create the project.</span></span>

1. <span data-ttu-id="a3f35-136">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="a3f35-136">Save your changes.</span></span>

   <span data-ttu-id="a3f35-137">進行這項變更與從儲存機制取得最新版本的方式相同，就是在其他人安裝了專案目錄的封裝之後 `dotnetsay` 。</span><span class="sxs-lookup"><span data-stu-id="a3f35-137">Making this change is the same as getting the latest version from the repository after someone else installed the package `dotnetsay` for the project directory.</span></span>

1. <span data-ttu-id="a3f35-138">執行 `dotnet tool restore` 命令。</span><span class="sxs-lookup"><span data-stu-id="a3f35-138">Run the `dotnet tool restore` command.</span></span>

   ```dotnetcli
   dotnet tool restore
   ```

   <span data-ttu-id="a3f35-139">此命令會產生如下列範例所示的輸出：</span><span class="sxs-lookup"><span data-stu-id="a3f35-139">The command produces output like the following example:</span></span>

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. <span data-ttu-id="a3f35-140">確認工具可供使用：</span><span class="sxs-lookup"><span data-stu-id="a3f35-140">Verify that the tools are available:</span></span>

   ```dotnetcli
   dotnet tool list
   ```

   <span data-ttu-id="a3f35-141">輸出是套件和命令的清單，類似于下列範例：</span><span class="sxs-lookup"><span data-stu-id="a3f35-141">The output is a list of packages and commands, similar to the following example:</span></span>

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. <span data-ttu-id="a3f35-142">測試控管：</span><span class="sxs-lookup"><span data-stu-id="a3f35-142">Test the tools:</span></span>

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a><span data-ttu-id="a3f35-143">更新本機工具</span><span class="sxs-lookup"><span data-stu-id="a3f35-143">Update a local tool</span></span>

<span data-ttu-id="a3f35-144">安裝的本機工具版本 `dotnetsay` 是2.1.3。</span><span class="sxs-lookup"><span data-stu-id="a3f35-144">The installed version of local tool `dotnetsay` is 2.1.3.</span></span>  <span data-ttu-id="a3f35-145">最新版本是2.1.4。</span><span class="sxs-lookup"><span data-stu-id="a3f35-145">The latest version is 2.1.4.</span></span> <span data-ttu-id="a3f35-146">使用 [dotnet tool update](dotnet-tool-update.md) 命令將工具更新為最新版本。</span><span class="sxs-lookup"><span data-stu-id="a3f35-146">Use the [dotnet tool update](dotnet-tool-update.md) command to update the tool to the latest version.</span></span>

```dotnetcli
dotnet tool update dotnetsay
```

<span data-ttu-id="a3f35-147">輸出會指出新的版本號碼：</span><span class="sxs-lookup"><span data-stu-id="a3f35-147">The output indicates the new version number:</span></span>

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

<span data-ttu-id="a3f35-148">Update 命令會尋找包含封裝識別碼的第一個資訊清單檔，並加以更新。</span><span class="sxs-lookup"><span data-stu-id="a3f35-148">The update command finds the first manifest file that contains the package ID and updates it.</span></span> <span data-ttu-id="a3f35-149">如果搜尋範圍內的任何資訊清單檔中沒有這類套件識別碼，SDK 會將新專案新增至最接近的資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="a3f35-149">If there is no such package ID in any manifest file that is in the scope of the search, the SDK adds a new entry to the closest manifest file.</span></span> <span data-ttu-id="a3f35-150">搜尋範圍會透過父目錄來執行，直到找到具有的資訊清單檔為止 `isRoot = true` 。</span><span class="sxs-lookup"><span data-stu-id="a3f35-150">The search scope is up through parent directories until a manifest file with `isRoot = true` is found.</span></span>

## <a name="remove-local-tools"></a><span data-ttu-id="a3f35-151">移除本機工具</span><span class="sxs-lookup"><span data-stu-id="a3f35-151">Remove local tools</span></span>

<span data-ttu-id="a3f35-152">執行 [dotnet tool uninstall](dotnet-tool-uninstall.md) 命令以移除已安裝的工具：</span><span class="sxs-lookup"><span data-stu-id="a3f35-152">Remove the installed tools by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a><span data-ttu-id="a3f35-153">疑難排解</span><span class="sxs-lookup"><span data-stu-id="a3f35-153">Troubleshoot</span></span>

<span data-ttu-id="a3f35-154">如果您在遵循本教學課程時收到錯誤訊息，請參閱 [疑難排解 .net 工具使用問題](troubleshoot-usage-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="a3f35-154">If you get an error message while following the tutorial, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a3f35-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3f35-155">See also</span></span>

<span data-ttu-id="a3f35-156">如需詳細資訊，請參閱[.Net Core 工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="a3f35-156">For more information, see [.NET Core tools](global-tools.md)</span></span>
