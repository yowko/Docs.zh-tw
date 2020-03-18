---
title: 教程：安裝和使用 .NET 核心全域工具
description: 瞭解如何安裝和使用 .NET 工具作為全域工具。
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156734"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="46126-103">教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心全域工具</span><span class="sxs-lookup"><span data-stu-id="46126-103">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>

<span data-ttu-id="46126-104">**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="46126-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="46126-105">本教程將教您如何安裝和使用全域工具。</span><span class="sxs-lookup"><span data-stu-id="46126-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="46126-106">使用在本[系列的第一個教程](global-tools-how-to-create.md)中創建的工具。</span><span class="sxs-lookup"><span data-stu-id="46126-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="46126-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="46126-107">Prerequisites</span></span>

* <span data-ttu-id="46126-108">完成[本系列的第一個教程](global-tools-how-to-create.md)。</span><span class="sxs-lookup"><span data-stu-id="46126-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="46126-109">將該工具用作全域工具</span><span class="sxs-lookup"><span data-stu-id="46126-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="46126-110">通過在*microsoft.botsay*專案資料夾中運行[dotnet 工具安裝](dotnet-tool-install.md)命令，從包中安裝該工具：</span><span class="sxs-lookup"><span data-stu-id="46126-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *microsoft.botsay* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="46126-111">該`--global`參數告訴 .NET Core CLI 在自動添加到 PATH 環境變數的預設位置安裝工具二進位檔案。</span><span class="sxs-lookup"><span data-stu-id="46126-111">The `--global` parameter tells the .NET Core CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="46126-112">該`--add-source`參數告訴 .NET Core CLI 暫時使用 *./nupkg*目錄作為 NuGet 包的附加源源。</span><span class="sxs-lookup"><span data-stu-id="46126-112">The `--add-source` parameter tells the .NET Core CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="46126-113">您為包指定了一個唯一的名稱，以確保它僅在 *./nupkg*目錄中找到，而不是在Nuget.org網站中找到。</span><span class="sxs-lookup"><span data-stu-id="46126-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span>

   <span data-ttu-id="46126-114">輸出顯示用於調用該工具的命令和安裝的版本：</span><span class="sxs-lookup"><span data-stu-id="46126-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="46126-115">調用該工具：</span><span class="sxs-lookup"><span data-stu-id="46126-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="46126-116">如果此命令失敗，您可能需要打開一個新終端來刷新 PATH。</span><span class="sxs-lookup"><span data-stu-id="46126-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="46126-117">通過運行[dotnet 工具卸載](dotnet-tool-uninstall.md)命令移除工具：</span><span class="sxs-lookup"><span data-stu-id="46126-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="46126-118">將該工具用作安裝在自訂位置的全域工具</span><span class="sxs-lookup"><span data-stu-id="46126-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="46126-119">從包安裝該工具。</span><span class="sxs-lookup"><span data-stu-id="46126-119">Install the tool from the package.</span></span>

   <span data-ttu-id="46126-120">在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="46126-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="46126-121">在 Linux 或 macOS 上：</span><span class="sxs-lookup"><span data-stu-id="46126-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="46126-122">該`--tool-path`參數告訴 .NET 核心 CLI 在指定位置安裝工具二進位檔案。</span><span class="sxs-lookup"><span data-stu-id="46126-122">The `--tool-path` parameter tells the .NET Core CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="46126-123">如果目錄不存在，則創建該目錄。</span><span class="sxs-lookup"><span data-stu-id="46126-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="46126-124">此目錄不會自動添加到 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="46126-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="46126-125">輸出顯示用於調用該工具的命令和安裝的版本：</span><span class="sxs-lookup"><span data-stu-id="46126-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="46126-126">調用該工具：</span><span class="sxs-lookup"><span data-stu-id="46126-126">Invoke the tool:</span></span>

   <span data-ttu-id="46126-127">在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="46126-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="46126-128">在 Linux 或 macOS 上：</span><span class="sxs-lookup"><span data-stu-id="46126-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="46126-129">通過運行[dotnet 工具卸載](dotnet-tool-uninstall.md)命令移除工具：</span><span class="sxs-lookup"><span data-stu-id="46126-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="46126-130">在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="46126-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   <span data-ttu-id="46126-131">在 Linux 或 macOS 上：</span><span class="sxs-lookup"><span data-stu-id="46126-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a><span data-ttu-id="46126-132">疑難排解</span><span class="sxs-lookup"><span data-stu-id="46126-132">Troubleshoot</span></span>

<span data-ttu-id="46126-133">如果您在學習本教程時收到錯誤訊息，請參閱[疑難排解 .NET Core 工具使用問題](troubleshoot-usage-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="46126-133">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="46126-134">後續步驟</span><span class="sxs-lookup"><span data-stu-id="46126-134">Next steps</span></span>

<span data-ttu-id="46126-135">在本教程中，您安裝並使用了工具作為全域工具。</span><span class="sxs-lookup"><span data-stu-id="46126-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="46126-136">要安裝和使用與本地工具相同的工具，請先進行下一個教程。</span><span class="sxs-lookup"><span data-stu-id="46126-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="46126-137">安裝和使用本地工具</span><span class="sxs-lookup"><span data-stu-id="46126-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
