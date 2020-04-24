---
title: 檢查 Windows、Linux 和 macOS 安裝的 .NET 核心版本 - .NET Core
description: 瞭解如何列出電腦上安裝了 .NET Core 的哪些版本。 這包括 .NET 核心運行時和 SDK。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 3a78acee6cf427085e98f14353fc2c0ac65d3d80
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645340"
---
# <a name="how-to-check-that-net-core-is-already-installed"></a><span data-ttu-id="0b4a8-104">如何檢查 .NET 核心是否已安裝</span><span class="sxs-lookup"><span data-stu-id="0b4a8-104">How to check that .NET Core is already installed</span></span>

<span data-ttu-id="0b4a8-105">本文教您如何檢查計算機上安裝了 .NET Core 運行時和 SDK 的哪些版本。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-105">This article teaches you how to check which versions of the .NET Core runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="0b4a8-106">如果您具有整合的開發環境(如適用於 Mac 的可視化工作室或視覺工作室),則可能已安裝 .NET 內核。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-106">.NET core may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="0b4a8-107">安裝 SDK 會安裝相應的運行時。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="0b4a8-108">如果本文中的任何命令失敗,則未安裝運行時或 SDK。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="0b4a8-109">有關詳細資訊,請參閱[下載並安裝 .NET 核心](index.md)。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-109">For more information, see [Download and install .NET Core](index.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="0b4a8-110">檢查 SDK 版本</span><span class="sxs-lookup"><span data-stu-id="0b4a8-110">Check SDK versions</span></span>

<span data-ttu-id="0b4a8-111">您可以看到 .NET 核心 SDK 的哪些版本當前隨終端一起安裝。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-111">You can see which versions of the .NET Core SDK are currently installed with a terminal.</span></span> <span data-ttu-id="0b4a8-112">打開終端並運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="0b4a8-113">您將獲得類似於以下內容的輸出。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-113">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
2.2.101 [C:\program files\dotnet\sdk]
3.0.100 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
2.2.101 [/home/user/dotnet/sdk]
3.0.100 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
2.2.101 [/usr/local/share/dotnet/sdk]
3.0.100 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a><span data-ttu-id="0b4a8-114">檢查執行時版本</span><span class="sxs-lookup"><span data-stu-id="0b4a8-114">Check runtime versions</span></span>

<span data-ttu-id="0b4a8-115">您可以看到 .NET Core 執行時的哪些版本目前已安裝以下命令。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-115">You can see which versions of the .NET Core runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="0b4a8-116">您將獲得類似於以下內容的輸出。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-116">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a><span data-ttu-id="0b4a8-117">檢查安裝資料夾</span><span class="sxs-lookup"><span data-stu-id="0b4a8-117">Check for install folders</span></span>

<span data-ttu-id="0b4a8-118">可能已安裝 .NET Core,但不會添加到作業系統或使用者`PATH`配置檔的變數中。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-118">It's possible that .NET Core is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="0b4a8-119">運行前幾節中的命令可能不起作用。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-119">Running the commands from the previous sections may not work.</span></span> <span data-ttu-id="0b4a8-120">作為替代方法,您可以檢查 .NET Core 安裝檔夾是否存在。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-120">As an alternative, you can check that the .NET Core install folders exist.</span></span>

<span data-ttu-id="0b4a8-121">從安裝程式或腳本安裝 .NET Core 時,它將安裝到標準資料夾中。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-121">When you install .NET Core from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="0b4a8-122">在安裝 .NET Core 的安裝程式或文稿的大部分時間裡,您都提供了安裝到其他資料夾的選項。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-122">Much of the time the installer or script you're using to install .NET Core gives you an option to install to a different folder.</span></span> <span data-ttu-id="0b4a8-123">如果選擇安裝到其他資料夾,請調整資料夾路徑的開頭。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="0b4a8-124">**點網執行**</span><span class="sxs-lookup"><span data-stu-id="0b4a8-124">**dotnet executable**</span></span>\
<span data-ttu-id="0b4a8-125">_C:\\\\程式\\檔案 dotnet dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="0b4a8-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="0b4a8-126">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="0b4a8-126">**.NET SDK**</span></span>\
<span data-ttu-id="0b4a8-127">_C:\\\\程式\\檔案 dotnet\\sdk [版本]\\_</span><span class="sxs-lookup"><span data-stu-id="0b4a8-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="0b4a8-128">**.NET 執行時**</span><span class="sxs-lookup"><span data-stu-id="0b4a8-128">**.NET Runtime**</span></span>\
<span data-ttu-id="0b4a8-129">_C:\\\\程式\\檔案 dotnet\\\\分享 [執行時類型] [版本]\\_</span><span class="sxs-lookup"><span data-stu-id="0b4a8-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="0b4a8-130">**點網執行**</span><span class="sxs-lookup"><span data-stu-id="0b4a8-130">**dotnet executable**</span></span>\
<span data-ttu-id="0b4a8-131">_/家庭/使用者/共享/點網/點網_</span><span class="sxs-lookup"><span data-stu-id="0b4a8-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="0b4a8-132">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="0b4a8-132">**.NET SDK**</span></span>\
<span data-ttu-id="0b4a8-133">_/家庭/使用者/共享/點網/sdk/{版本}/_</span><span class="sxs-lookup"><span data-stu-id="0b4a8-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="0b4a8-134">**.NET 執行時**</span><span class="sxs-lookup"><span data-stu-id="0b4a8-134">**.NET Runtime**</span></span>\
<span data-ttu-id="0b4a8-135">_/家庭/使用者/共用/點網/共用/[運行時類型]/{版本}/_</span><span class="sxs-lookup"><span data-stu-id="0b4a8-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="0b4a8-136">**點網執行**</span><span class="sxs-lookup"><span data-stu-id="0b4a8-136">**dotnet executable**</span></span>\
<span data-ttu-id="0b4a8-137">_/usr/本地/共用/點網/點網_</span><span class="sxs-lookup"><span data-stu-id="0b4a8-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="0b4a8-138">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="0b4a8-138">**.NET SDK**</span></span>\
<span data-ttu-id="0b4a8-139">_/usr/本地/共用/點網/sdk/{版本}/_</span><span class="sxs-lookup"><span data-stu-id="0b4a8-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="0b4a8-140">**.NET 執行時**</span><span class="sxs-lookup"><span data-stu-id="0b4a8-140">**.NET Runtime**</span></span>\
<span data-ttu-id="0b4a8-141">_/usr/本地/共用/點網/共用/[運行時類型]/[版本]/_</span><span class="sxs-lookup"><span data-stu-id="0b4a8-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="0b4a8-142">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0b4a8-142">More information</span></span>

<span data-ttu-id="0b4a8-143">您可以使用`dotnet --info`指令 同時查看 SDK 版本和執行時版本。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="0b4a8-144">您還將獲得其他與環境相關的資訊,如作業系統版本和運行時識別碼 (RID)。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0b4a8-145">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0b4a8-145">Next steps</span></span>

- <span data-ttu-id="0b4a8-146">[安裝 .NET 核心執行時](runtime.md)。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-146">[Install the .NET Core Runtime](runtime.md).</span></span>
- <span data-ttu-id="0b4a8-147">[安裝 .NET 核心 SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="0b4a8-147">[Install the .NET Core SDK](sdk.md).</span></span>
