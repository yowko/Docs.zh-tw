---
title: 檢查 Windows、Linux 和 macOS 上已安裝的 .NET Core 版本-.NET Core
description: 瞭解如何列出電腦上已安裝的 .NET Core 版本。 這包括 .NET Core 執行時間和 SDK。
author: adegeo
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: cc4d9c6a366cd0e5da4c3446536c93efdc9f5503
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324816"
---
# <a name="how-to-check-that-net-core-is-already-installed"></a><span data-ttu-id="2dddf-104">如何檢查是否已安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="2dddf-104">How to check that .NET Core is already installed</span></span>

<span data-ttu-id="2dddf-105">本文會教您如何檢查電腦上已安裝的 .NET Core 執行時間和 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="2dddf-105">This article teaches you how to check which versions of the .NET Core runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="2dddf-106">如果您有整合式開發環境（例如 Visual Studio 或 Visual Studio for Mac），則可能已經安裝 .NET core。</span><span class="sxs-lookup"><span data-stu-id="2dddf-106">.NET core may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="2dddf-107">安裝 SDK 會安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="2dddf-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="2dddf-108">如果本文中有任何命令失敗，您就不會安裝執行時間或 SDK。</span><span class="sxs-lookup"><span data-stu-id="2dddf-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="2dddf-109">如需詳細資訊，請參閱[下載並安裝 .Net Core](index.md)。</span><span class="sxs-lookup"><span data-stu-id="2dddf-109">For more information, see [Download and install .NET Core](index.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="2dddf-110">檢查 SDK 版本</span><span class="sxs-lookup"><span data-stu-id="2dddf-110">Check SDK versions</span></span>

<span data-ttu-id="2dddf-111">您可以查看目前已安裝終端機的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="2dddf-111">You can see which versions of the .NET Core SDK are currently installed with a terminal.</span></span> <span data-ttu-id="2dddf-112">開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="2dddf-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="2dddf-113">您會取得如下所示的輸出。</span><span class="sxs-lookup"><span data-stu-id="2dddf-113">You get output similar to the following.</span></span>

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

## <a name="check-runtime-versions"></a><span data-ttu-id="2dddf-114">檢查執行階段版本</span><span class="sxs-lookup"><span data-stu-id="2dddf-114">Check runtime versions</span></span>

<span data-ttu-id="2dddf-115">您可以使用下列命令來查看目前安裝的 .NET Core 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="2dddf-115">You can see which versions of the .NET Core runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="2dddf-116">您會取得如下所示的輸出。</span><span class="sxs-lookup"><span data-stu-id="2dddf-116">You get output similar to the following.</span></span>

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

## <a name="check-for-install-folders"></a><span data-ttu-id="2dddf-117">檢查安裝資料夾</span><span class="sxs-lookup"><span data-stu-id="2dddf-117">Check for install folders</span></span>

<span data-ttu-id="2dddf-118">.NET Core 可能已安裝，但未新增至 `PATH` 您的作業系統或使用者設定檔的變數。</span><span class="sxs-lookup"><span data-stu-id="2dddf-118">It's possible that .NET Core is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="2dddf-119">執行先前章節中的命令可能無法運作。</span><span class="sxs-lookup"><span data-stu-id="2dddf-119">Running the commands from the previous sections may not work.</span></span> <span data-ttu-id="2dddf-120">或者，您可以檢查 .NET Core 安裝資料夾是否存在。</span><span class="sxs-lookup"><span data-stu-id="2dddf-120">As an alternative, you can check that the .NET Core install folders exist.</span></span>

<span data-ttu-id="2dddf-121">當您從安裝程式或腳本安裝 .NET Core 時，它會安裝到標準資料夾中。</span><span class="sxs-lookup"><span data-stu-id="2dddf-121">When you install .NET Core from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="2dddf-122">在大部分的情況中，您用來安裝 .NET Core 的安裝程式或腳本，都能讓您選擇安裝到不同的資料夾。</span><span class="sxs-lookup"><span data-stu-id="2dddf-122">Much of the time the installer or script you're using to install .NET Core gives you an option to install to a different folder.</span></span> <span data-ttu-id="2dddf-123">如果您選擇安裝到不同的資料夾，請調整資料夾路徑的開頭。</span><span class="sxs-lookup"><span data-stu-id="2dddf-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="2dddf-124">**dotnet 可執行檔**</span><span class="sxs-lookup"><span data-stu-id="2dddf-124">**dotnet executable**</span></span>\
<span data-ttu-id="2dddf-125">_C： \\ program files \\ dotnet \\dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="2dddf-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="2dddf-126">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="2dddf-126">**.NET SDK**</span></span>\
<span data-ttu-id="2dddf-127">_C： \\ program files \\ dotnet \\ sdk \\ {version}\\_</span><span class="sxs-lookup"><span data-stu-id="2dddf-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="2dddf-128">**.NET 執行時間**</span><span class="sxs-lookup"><span data-stu-id="2dddf-128">**.NET Runtime**</span></span>\
<span data-ttu-id="2dddf-129">_C： \\ program files \\ dotnet \\ shared \\ {runtime-type} \\ {version}\\_</span><span class="sxs-lookup"><span data-stu-id="2dddf-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="2dddf-130">**dotnet 可執行檔**</span><span class="sxs-lookup"><span data-stu-id="2dddf-130">**dotnet executable**</span></span>\
<span data-ttu-id="2dddf-131">_/home/user/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="2dddf-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="2dddf-132">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="2dddf-132">**.NET SDK**</span></span>\
<span data-ttu-id="2dddf-133">_/home/user/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="2dddf-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="2dddf-134">**.NET 執行時間**</span><span class="sxs-lookup"><span data-stu-id="2dddf-134">**.NET Runtime**</span></span>\
<span data-ttu-id="2dddf-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="2dddf-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="2dddf-136">**dotnet 可執行檔**</span><span class="sxs-lookup"><span data-stu-id="2dddf-136">**dotnet executable**</span></span>\
<span data-ttu-id="2dddf-137">_/usr/local/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="2dddf-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="2dddf-138">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="2dddf-138">**.NET SDK**</span></span>\
<span data-ttu-id="2dddf-139">_/usr/local/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="2dddf-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="2dddf-140">**.NET 執行時間**</span><span class="sxs-lookup"><span data-stu-id="2dddf-140">**.NET Runtime**</span></span>\
<span data-ttu-id="2dddf-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="2dddf-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="2dddf-142">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="2dddf-142">More information</span></span>

<span data-ttu-id="2dddf-143">您可以使用命令來查看 SDK 版本和執行階段版本 `dotnet --info` 。</span><span class="sxs-lookup"><span data-stu-id="2dddf-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="2dddf-144">您也會取得其他環境相關資訊，例如作業系統版本和執行時間識別碼（RID）。</span><span class="sxs-lookup"><span data-stu-id="2dddf-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2dddf-145">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2dddf-145">Next steps</span></span>

- <span data-ttu-id="2dddf-146">[安裝 .Net Core 運行](runtime.md)時間。</span><span class="sxs-lookup"><span data-stu-id="2dddf-146">[Install the .NET Core Runtime](runtime.md).</span></span>
- <span data-ttu-id="2dddf-147">[安裝 .NET Core SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="2dddf-147">[Install the .NET Core SDK](sdk.md).</span></span>
