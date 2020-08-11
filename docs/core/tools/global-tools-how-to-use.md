---
title: 教學課程：安裝和使用 .NET Core 通用工具
description: 瞭解如何安裝和使用 .NET 工具做為通用工具。
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 28e34a4e5a0344e314c5d23228c1af5839db991c
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062765"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="df670-103">教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 通用工具</span><span class="sxs-lookup"><span data-stu-id="df670-103">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>

<span data-ttu-id="df670-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="df670-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="df670-105">本教學課程會教您如何安裝和使用通用工具。</span><span class="sxs-lookup"><span data-stu-id="df670-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="df670-106">您會使用在[本系列的第一個教學](global-tools-how-to-create.md)課程中建立的工具。</span><span class="sxs-lookup"><span data-stu-id="df670-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="df670-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="df670-107">Prerequisites</span></span>

* <span data-ttu-id="df670-108">完成[此系列的第一個教學](global-tools-how-to-create.md)課程。</span><span class="sxs-lookup"><span data-stu-id="df670-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="df670-109">使用工具作為通用工具</span><span class="sxs-lookup"><span data-stu-id="df670-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="df670-110">在*botsay*專案資料夾中執行[dotnet tool install](dotnet-tool-install.md)命令，以從套件安裝此工具：</span><span class="sxs-lookup"><span data-stu-id="df670-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *microsoft.botsay* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="df670-111">`--global`參數會告訴 .NET Core CLI 在自動新增至 PATH 環境變數的預設位置中安裝工具二進位檔。</span><span class="sxs-lookup"><span data-stu-id="df670-111">The `--global` parameter tells the .NET Core CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="df670-112">`--add-source`參數會告知 .NET Core CLI 暫時使用 */nupkg*目錄做為 NuGet 套件的其他來源摘要。</span><span class="sxs-lookup"><span data-stu-id="df670-112">The `--add-source` parameter tells the .NET Core CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="df670-113">您為套件提供了唯一的名稱，以確保它只會在 */nupkg*目錄中找到，而不是在 Nuget.org 網站上。</span><span class="sxs-lookup"><span data-stu-id="df670-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span>

   <span data-ttu-id="df670-114">輸出會顯示用來呼叫工具和所安裝版本的命令：</span><span class="sxs-lookup"><span data-stu-id="df670-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="df670-115">叫用工具：</span><span class="sxs-lookup"><span data-stu-id="df670-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="df670-116">如果此命令失敗，您可能需要開啟新的終端機以重新整理路徑。</span><span class="sxs-lookup"><span data-stu-id="df670-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="df670-117">執行[dotnet tool uninstall](dotnet-tool-uninstall.md)命令以移除此工具：</span><span class="sxs-lookup"><span data-stu-id="df670-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="df670-118">使用此工具作為自訂位置中安裝的通用工具</span><span class="sxs-lookup"><span data-stu-id="df670-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="df670-119">從套件安裝工具。</span><span class="sxs-lookup"><span data-stu-id="df670-119">Install the tool from the package.</span></span>

   <span data-ttu-id="df670-120">在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="df670-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="df670-121">在 Linux 或 macOS 上：</span><span class="sxs-lookup"><span data-stu-id="df670-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="df670-122">`--tool-path`參數會告知 .NET Core CLI 在指定的位置安裝工具二進位檔。</span><span class="sxs-lookup"><span data-stu-id="df670-122">The `--tool-path` parameter tells the .NET Core CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="df670-123">如果目錄不存在，則會建立它。</span><span class="sxs-lookup"><span data-stu-id="df670-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="df670-124">此目錄不會自動加入 PATH 環境變數中。</span><span class="sxs-lookup"><span data-stu-id="df670-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="df670-125">輸出會顯示用來呼叫工具和所安裝版本的命令：</span><span class="sxs-lookup"><span data-stu-id="df670-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="df670-126">叫用工具：</span><span class="sxs-lookup"><span data-stu-id="df670-126">Invoke the tool:</span></span>

   <span data-ttu-id="df670-127">在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="df670-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="df670-128">在 Linux 或 macOS 上：</span><span class="sxs-lookup"><span data-stu-id="df670-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="df670-129">執行[dotnet tool uninstall](dotnet-tool-uninstall.md)命令以移除此工具：</span><span class="sxs-lookup"><span data-stu-id="df670-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="df670-130">在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="df670-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   <span data-ttu-id="df670-131">在 Linux 或 macOS 上：</span><span class="sxs-lookup"><span data-stu-id="df670-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a><span data-ttu-id="df670-132">疑難排解</span><span class="sxs-lookup"><span data-stu-id="df670-132">Troubleshoot</span></span>

<span data-ttu-id="df670-133">如果您在教學課程之後收到錯誤訊息，請參閱針對[.Net Core 工具使用問題進行疑難排解](troubleshoot-usage-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="df670-133">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="df670-134">後續步驟</span><span class="sxs-lookup"><span data-stu-id="df670-134">Next steps</span></span>

<span data-ttu-id="df670-135">在本教學課程中，您已安裝並使用工具做為通用工具。</span><span class="sxs-lookup"><span data-stu-id="df670-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="df670-136">若要安裝和使用與本機工具相同的工具，請繼續進行下一個教學課程。</span><span class="sxs-lookup"><span data-stu-id="df670-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df670-137">安裝及使用本機工具</span><span class="sxs-lookup"><span data-stu-id="df670-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
