---
title: .NET Core 3.0 的新功能
description: 了解 .NET Core 3.0 所提供的新功能。
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 07/25/2019
ms.openlocfilehash: f1fce2899e9e11b1007d6c270180b27a29eaa167
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039441"
---
# <a name="whats-new-in-net-core-30-preview-7"></a><span data-ttu-id="1f106-103">.NET Core 3.0 (Preview 7) 的新功能</span><span class="sxs-lookup"><span data-stu-id="1f106-103">What's new in .NET Core 3.0 (Preview 7)</span></span>

<span data-ttu-id="1f106-104">本文描述 .NET Core 3.0 (到 Preview 7) 的新功能。</span><span class="sxs-lookup"><span data-stu-id="1f106-104">This article describes what is new in .NET Core 3.0 (through preview 7).</span></span> <span data-ttu-id="1f106-105">其中一個最大的增強功能是對 Windows 傳統型應用程式的支援 (僅限 Windows)。</span><span class="sxs-lookup"><span data-stu-id="1f106-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="1f106-106">您可以使用 .NET Core 3.0 SDK 元件「Windows 傳統型」來移植 Windows Forms 和 Windows Presentation Foundation (WPF) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1f106-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="1f106-107">具體而言，只有在 Windows 上才支援並包含「Windows 傳統型」元件。</span><span class="sxs-lookup"><span data-stu-id="1f106-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="1f106-108">如需詳細資訊，請參閱本文稍後的 [Windows 傳統型](#windows-desktop)一節。</span><span class="sxs-lookup"><span data-stu-id="1f106-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="1f106-109">.NET Core 3.0 新增 C# 8.0 支援。</span><span class="sxs-lookup"><span data-stu-id="1f106-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="1f106-110">強烈建議您搭配 OmniSharp 延伸模組使用[最新版的 Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview) 或 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="1f106-110">It's highly recommended that you use the [latest release of Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview), or Visual Studio Code with the OmniSharp extension.</span></span>

<span data-ttu-id="1f106-111">立即在 Windows、Mac 及 Linux 上[下載並開始使用 .NET Core 3.0 Preview 7](https://aka.ms/netcore3download)。</span><span class="sxs-lookup"><span data-stu-id="1f106-111">[Download and get started with .NET Core 3.0 preview 7](https://aka.ms/netcore3download) right now on Windows, Mac, and Linux.</span></span>

<span data-ttu-id="1f106-112">如需每個預覽版的詳細資訊，請參閱下列公告：</span><span class="sxs-lookup"><span data-stu-id="1f106-112">For more information about each preview release, see the following announcements:</span></span>

- [<span data-ttu-id="1f106-113">.NET Core 3.0 Preview 7 公告</span><span class="sxs-lookup"><span data-stu-id="1f106-113">.NET Core 3.0 Preview 7 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/)
- <span data-ttu-id="1f106-114">[.NET Core 3.0 Preview 6 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="1f106-114">[.NET Core 3.0 Preview 6 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)</span></span>
- [<span data-ttu-id="1f106-115">.NET Core 3.0 Preview 5 公告</span><span class="sxs-lookup"><span data-stu-id="1f106-115">.NET Core 3.0 Preview 5 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [<span data-ttu-id="1f106-116">.NET Core 3.0 Preview 4 公告</span><span class="sxs-lookup"><span data-stu-id="1f106-116">.NET Core 3.0 Preview 4 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [<span data-ttu-id="1f106-117">.NET Core 3.0 Preview 3 公告</span><span class="sxs-lookup"><span data-stu-id="1f106-117">.NET Core 3.0 Preview 3 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [<span data-ttu-id="1f106-118">.NET Core 3.0 Preview 2 公告</span><span class="sxs-lookup"><span data-stu-id="1f106-118">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [<span data-ttu-id="1f106-119">.NET Core 3.0 Preview 1 公告</span><span class="sxs-lookup"><span data-stu-id="1f106-119">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="production-supported-preview"></a><span data-ttu-id="1f106-120">支援生產環境的預覽</span><span class="sxs-lookup"><span data-stu-id="1f106-120">Production supported preview</span></span>

<span data-ttu-id="1f106-121">Microsoft 已將 .NET Core Preview 7 視為生產環境就緒，且已提供完整支援。</span><span class="sxs-lookup"><span data-stu-id="1f106-121">.NET Core Preview 7 is considered production ready by Microsoft and is fully supported.</span></span> <span data-ttu-id="1f106-122">從 Preview 7 開始，版本會著重於改善 .NET Core 3.0，而非新增新功能。</span><span class="sxs-lookup"><span data-stu-id="1f106-122">Starting with preview 7, releases will focus on polishing .NET Core 3.0 instead of adding new features.</span></span> <span data-ttu-id="1f106-123">如需 Preview 7 中變更項目的詳細資訊，請參閱 [Preview 7 公告](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/)。</span><span class="sxs-lookup"><span data-stu-id="1f106-123">For more information about what has changed in preview 7, see the [preview 7 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/).</span></span>

## <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="1f106-124">.NET Core SDK Windows Installer</span><span class="sxs-lookup"><span data-stu-id="1f106-124">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="1f106-125">Windows 的 MSI 安裝程式從 .NET Core 3.0 開始即已變更。</span><span class="sxs-lookup"><span data-stu-id="1f106-125">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="1f106-126">SDK 安裝程式現在會就地升級 SDK 功能帶版本。</span><span class="sxs-lookup"><span data-stu-id="1f106-126">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="1f106-127">功能帶是在版本號碼「修補程式」  部分以「一百」  為單位的群組中定義。</span><span class="sxs-lookup"><span data-stu-id="1f106-127">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="1f106-128">例如，**3.0._101_** 和 **3.0._201_** 便是位於兩個不同功能帶中的版本，而 **3.0._101_** 和 **3.0._199_** 則位於相同的功能帶。</span><span class="sxs-lookup"><span data-stu-id="1f106-128">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="1f106-129">此外，安裝 .NET Core SDK **3.0._101_** 時，.NET Core SDK **3.0._100_** 便會從電腦移除 (若存在的話)。</span><span class="sxs-lookup"><span data-stu-id="1f106-129">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="1f106-130">在相同電腦上安裝 .NET Core SDK **3.0._200_** 時，不會移除 .NET Core SDK **3.0._101_** 。</span><span class="sxs-lookup"><span data-stu-id="1f106-130">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="1f106-131">如需版本設定的詳細資訊，請參閱 [.NET Core 版本設定概觀](../versions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1f106-131">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

## <a name="c-80-preview"></a><span data-ttu-id="1f106-132">C# 8.0 Preview</span><span class="sxs-lookup"><span data-stu-id="1f106-132">C# 8.0 preview</span></span>

<span data-ttu-id="1f106-133">.NET Core 3.0 支援 C# 8 Preview。</span><span class="sxs-lookup"><span data-stu-id="1f106-133">.NET Core 3.0 supports C# 8 preview.</span></span> <span data-ttu-id="1f106-134">如需 C# 8.0 功能的詳細資訊，請參閱 [C# 8.0 的新功能](../../csharp/whats-new/csharp-8.md)。</span><span class="sxs-lookup"><span data-stu-id="1f106-134">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="1f106-135">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="1f106-135">.NET Standard 2.1</span></span>

<span data-ttu-id="1f106-136">雖然 .NET Core 3.0 支援 **.NET Standard 2.1**，但預設 `dotnet new classlib` 範本會產生以 **.NET Standard 2.0** 為目標的專案。</span><span class="sxs-lookup"><span data-stu-id="1f106-136">Even though .NET Core 3.0 supports **.NET Standard 2.1**, the default `dotnet new classlib` template generates a project that targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="1f106-137">若要以 **.NET Standard 2.1** 為目標，請編輯您的專案檔並將 `TargetFramework` 屬性變更為 `netstandard2.1`：</span><span class="sxs-lookup"><span data-stu-id="1f106-137">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

<span data-ttu-id="1f106-138">如果目前使用 Visual Studio，您需要 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)，因為 Visual Studio 2017 不支援 **.NET Standard 2.1** 或 **.NET Core 3.0**。</span><span class="sxs-lookup"><span data-stu-id="1f106-138">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="improved-net-core-version-apis"></a><span data-ttu-id="1f106-139">改善的 .NET Core 版本 API</span><span class="sxs-lookup"><span data-stu-id="1f106-139">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="1f106-140">從 .NET Core 3.0 開始，.NET Core 所提供版本 API 現在會傳回您預期的資訊。</span><span class="sxs-lookup"><span data-stu-id="1f106-140">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="1f106-141">例如：</span><span class="sxs-lookup"><span data-stu-id="1f106-141">For example:</span></span>

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> <span data-ttu-id="1f106-142">重大變更。</span><span class="sxs-lookup"><span data-stu-id="1f106-142">Breaking change.</span></span> <span data-ttu-id="1f106-143">這是技術上的重大變更，因為版本設定配置已變更。</span><span class="sxs-lookup"><span data-stu-id="1f106-143">This is technically a breaking change because the versioning scheme has changed.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="1f106-144">.NET 平台相依內建</span><span class="sxs-lookup"><span data-stu-id="1f106-144">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="1f106-145">已新增 API，允許存取特定效能導向的 CPU 指令，例如 **SIMD** 或**位元操作指令**集合。</span><span class="sxs-lookup"><span data-stu-id="1f106-145">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="1f106-146">這些指令可協助您在某些情況 (例如有效率地平行處理資料) 下大幅提升效能。</span><span class="sxs-lookup"><span data-stu-id="1f106-146">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> 

<span data-ttu-id="1f106-147">.NET 程式庫 (如果適用) 已開始使用這些指令來提升效能。</span><span class="sxs-lookup"><span data-stu-id="1f106-147">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="1f106-148">如需詳細資訊，請參閱 [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md) (.NET 平台相依內建)。</span><span class="sxs-lookup"><span data-stu-id="1f106-148">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

## <a name="default-executables"></a><span data-ttu-id="1f106-149">預設可執行檔</span><span class="sxs-lookup"><span data-stu-id="1f106-149">Default executables</span></span>

<span data-ttu-id="1f106-150">.NET Core 現在預設會建置[架構相依可執行檔](../deploying/index.md#framework-dependent-executables-fde)。</span><span class="sxs-lookup"><span data-stu-id="1f106-150">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="1f106-151">這對於使用 .NET Core 全域安裝版本的應用程式來說，是一項新行為。</span><span class="sxs-lookup"><span data-stu-id="1f106-151">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="1f106-152">先前，只有[獨立式部署](../deploying/index.md#self-contained-deployments-scd)會產生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="1f106-152">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="1f106-153">在 `dotnet build` 或 `dotnet publish` 期間，會建立符合您所用 SDK 環境和平台的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="1f106-153">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="1f106-154">針對這些可執行檔，您可以預期能夠進行與其他原生可執行檔相同的操作，例如：</span><span class="sxs-lookup"><span data-stu-id="1f106-154">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="1f106-155">您可以按兩下可執行檔。</span><span class="sxs-lookup"><span data-stu-id="1f106-155">You can double-click on the executable.</span></span>
* <span data-ttu-id="1f106-156">您可以直接從命令提示字元啟動應用程式，例如在 Windows 上為 `myapp.exe`，在 Linux 和 macOS 上為 `./myapp`。</span><span class="sxs-lookup"><span data-stu-id="1f106-156">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="single-file-executables"></a><span data-ttu-id="1f106-157">單一檔案可執行檔</span><span class="sxs-lookup"><span data-stu-id="1f106-157">Single-file executables</span></span>

<span data-ttu-id="1f106-158">`dotnet publish` 命令支援將您的應用程式封裝成平台特定單一檔案可執行檔。</span><span class="sxs-lookup"><span data-stu-id="1f106-158">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="1f106-159">可執行檔會自我解壓縮，並包含執行應用程式所需的所有相依性 (包括原生)。</span><span class="sxs-lookup"><span data-stu-id="1f106-159">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="1f106-160">第一次執行應用程式時，系統會將應用程式解壓縮到以應用程式名稱和組建識別碼為基礎的目錄。</span><span class="sxs-lookup"><span data-stu-id="1f106-160">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="1f106-161">再次執行應用程式時的啟動速度會更快。</span><span class="sxs-lookup"><span data-stu-id="1f106-161">Startup is faster when the application is run again.</span></span> <span data-ttu-id="1f106-162">除非使用新版本，否則應用程式不需要再次自我解壓縮。</span><span class="sxs-lookup"><span data-stu-id="1f106-162">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="1f106-163">若要發佈單一檔案可執行檔，請在專案中或在命令列上使用 `dotnet publish` 命令來設定 `PublishSingleFile`：</span><span class="sxs-lookup"><span data-stu-id="1f106-163">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="1f106-164">-或-</span><span class="sxs-lookup"><span data-stu-id="1f106-164">-or-</span></span>

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

<span data-ttu-id="1f106-165">如需單一檔案發佈的詳細資訊，請參閱[單一檔案搭配程式設計文件](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md)。</span><span class="sxs-lookup"><span data-stu-id="1f106-165">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

## <a name="assembly-linking"></a><span data-ttu-id="1f106-166">組件連結</span><span class="sxs-lookup"><span data-stu-id="1f106-166">Assembly linking</span></span>

<span data-ttu-id="1f106-167">.NET Core 3.0 SDK 隨附能透過分析 IL 並修剪未使用的組件來減少應用程式大小的工具。</span><span class="sxs-lookup"><span data-stu-id="1f106-167">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="1f106-168">自封式應用程式包含執行程式碼所需的一切項目，因此不需要在主機電腦上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="1f106-168">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="1f106-169">不過，應用程式經常只需要一小部分的架構子集便能運作，而其他未使用的程式庫則可以被移除。</span><span class="sxs-lookup"><span data-stu-id="1f106-169">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="1f106-170">.NET Core 現在包含會使用 [IL 連結器](https://github.com/mono/linker) \(英文\) 工具來掃描應用程式 IL 的設定。</span><span class="sxs-lookup"><span data-stu-id="1f106-170">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="1f106-171">此工具會偵測所需的程式碼，然後修剪未使用的程式庫。</span><span class="sxs-lookup"><span data-stu-id="1f106-171">this tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="1f106-172">此工具可以大幅減少某些應用程式的部署大小。</span><span class="sxs-lookup"><span data-stu-id="1f106-172">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="1f106-173">若要啟用此工具，請在專案中新增 `<PublishTrimmed>` 設定，並發佈獨立式應用程式：</span><span class="sxs-lookup"><span data-stu-id="1f106-173">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="1f106-174">例如，所包含的基本 "hello world" 新主控台專案在發佈時的大小大約是 70 MB。</span><span class="sxs-lookup"><span data-stu-id="1f106-174">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="1f106-175">透過使用 `<PublishTrimmed>`，該大小會被縮減為大約 30 MB。</span><span class="sxs-lookup"><span data-stu-id="1f106-175">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="1f106-176">請務必記得，對使用反映或相關動態功能的應用程式或架構 (包括 ASP.NET Core 和 WPF) 進行修剪經常會發生中斷的情況。</span><span class="sxs-lookup"><span data-stu-id="1f106-176">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="1f106-177">會發生此中斷的原因是因為連結器不知道此動態行為，因此無法判斷反映所需的架構類型有哪些。</span><span class="sxs-lookup"><span data-stu-id="1f106-177">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="1f106-178">可以對 IL 連結器工具加以設定來使其注意到此情況。</span><span class="sxs-lookup"><span data-stu-id="1f106-178">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="1f106-179">無論如何，請務必在修剪後測試您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1f106-179">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="1f106-180">如需 IL 連結器工具的詳細資訊，請參閱[文件](https://aka.ms/dotnet-illink) \(英文\) 或造訪 [mono/linker]( https://github.com/mono/linker) \(英文\) 存放庫。</span><span class="sxs-lookup"><span data-stu-id="1f106-180">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="1f106-181">階層式編譯</span><span class="sxs-lookup"><span data-stu-id="1f106-181">Tiered compilation</span></span>

<span data-ttu-id="1f106-182">.NET Core 3.0 預設會開啟[階層式編譯](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC)。</span><span class="sxs-lookup"><span data-stu-id="1f106-182">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="1f106-183">這項功能可讓執行階段更彈性地使用 Just-In-Time (JIT) 編譯器來獲得更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="1f106-183">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="1f106-184">TC 的主要優點是能夠啟用較慢品質但較快層級，或較高品質但較慢層級的 JIT (重新) 編譯方法。</span><span class="sxs-lookup"><span data-stu-id="1f106-184">The main benefit of TC is to enable (re-)jitting methods with a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="1f106-185">由於行經各種執行階段 (從啟動到穩定狀態)，因此有助於提升應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="1f106-185">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="1f106-186">這與非 TC 方法相反，在非 TC 方法中，所有方法都是以單一方式 (與高品質層相同) 進行編譯，這會偏重穩定狀態而非啟動效能。</span><span class="sxs-lookup"><span data-stu-id="1f106-186">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="1f106-187">若要啟用 Quick JIT (層級 0 JIT 編譯的程式碼)，請在您的專案檔中使用此設定：</span><span class="sxs-lookup"><span data-stu-id="1f106-187">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="1f106-188">若要完全停用 TC，請在您的專案檔中使用此設定：</span><span class="sxs-lookup"><span data-stu-id="1f106-188">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a><span data-ttu-id="1f106-189">ReadyToRun 映像</span><span class="sxs-lookup"><span data-stu-id="1f106-189">ReadyToRun images</span></span>

<span data-ttu-id="1f106-190">您可以透過將應用程式組件編譯為 ReadyToRun (R2R) 格式，來改善 .NET Core 應用程式的啟動時間。</span><span class="sxs-lookup"><span data-stu-id="1f106-190">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="1f106-191">R2R 是一種預先(AOT) 編譯。</span><span class="sxs-lookup"><span data-stu-id="1f106-191">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="1f106-192">R2R 二進位檔會透過減少 Just-In-Time (JIT) 編譯器在應用程式載入時所需執行的工作量，來改善啟動效能。</span><span class="sxs-lookup"><span data-stu-id="1f106-192">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="1f106-193">二進位檔包含的機器碼，與 JIT 所會產生的內容類似。</span><span class="sxs-lookup"><span data-stu-id="1f106-193">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="1f106-194">但是，R2R 二進位檔大小較大，因為它們會同時包含中繼語言 (IL) 程式碼 (在某些案例下仍需要使用)，以及相同程式碼的原生版本。</span><span class="sxs-lookup"><span data-stu-id="1f106-194">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="1f106-195">R2R 只有在您發佈以特定執行階段環境 (RID) (例如 Linux x64 或 Windows x64) 為目標的獨立式應用程式時才可供使用。</span><span class="sxs-lookup"><span data-stu-id="1f106-195">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="1f106-196">若要將您的專案編譯為 ReadyToRun，請執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="1f106-196">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="1f106-197">將 `<PublishReadyToRun>` 設定新增至專案</span><span class="sxs-lookup"><span data-stu-id="1f106-197">Add the `<PublishReadyToRun>` setting to your project</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="1f106-198">發佈自封式應用程式。</span><span class="sxs-lookup"><span data-stu-id="1f106-198">Publish a self-contained app.</span></span> <span data-ttu-id="1f106-199">例如，此命令會針對 64 位元版本的 Windows 建立自封式應用程式：</span><span class="sxs-lookup"><span data-stu-id="1f106-199">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```console
    dotnet publish -c Release -r win-x64 --self-contained true
    ```

### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="1f106-200">跨平台/架構限制</span><span class="sxs-lookup"><span data-stu-id="1f106-200">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="1f106-201">ReadyToRun 編譯器目前不支援跨目標。</span><span class="sxs-lookup"><span data-stu-id="1f106-201">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="1f106-202">您必須在指定的目標上進行編譯。</span><span class="sxs-lookup"><span data-stu-id="1f106-202">You must compile on a given target.</span></span> <span data-ttu-id="1f106-203">例如，如果您想要適用於 Windows x64 的 R2R 映像，便需要在該環境上執行發佈命令。</span><span class="sxs-lookup"><span data-stu-id="1f106-203">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="1f106-204">鎖定多重目標的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="1f106-204">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="1f106-205">Windows x64 可以用來編譯 Windows ARM32、ARM64 及 x86 映像。</span><span class="sxs-lookup"><span data-stu-id="1f106-205">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="1f106-206">Windows x86 可以用來編譯 Windows ARM32 映像。</span><span class="sxs-lookup"><span data-stu-id="1f106-206">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="1f106-207">Linux x64 可以用來編譯 Linux ARM32 和 ARM64 映像。</span><span class="sxs-lookup"><span data-stu-id="1f106-207">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="1f106-208">組建複本相依性</span><span class="sxs-lookup"><span data-stu-id="1f106-208">Build copies dependencies</span></span>

<span data-ttu-id="1f106-209">`dotnet build` 命令現在會從 NuGet 快取將您應用程式的 NuGet 相依性複製到組建輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="1f106-209">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="1f106-210">先前，只有在進行 `dotnet publish` 的過程中，才會複製相依性。</span><span class="sxs-lookup"><span data-stu-id="1f106-210">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="1f106-211">有些作業 (例如連結和 Razor 頁面發佈) 仍然需要發佈。</span><span class="sxs-lookup"><span data-stu-id="1f106-211">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-tools"></a><span data-ttu-id="1f106-212">本機工具</span><span class="sxs-lookup"><span data-stu-id="1f106-212">Local tools</span></span>

<span data-ttu-id="1f106-213">.NET Core 3.0 引進本機工具。</span><span class="sxs-lookup"><span data-stu-id="1f106-213">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="1f106-214">本機工具與[全域工具](../tools/global-tools.md)類似，但與磁碟上的某個特定位置立建立關聯。</span><span class="sxs-lookup"><span data-stu-id="1f106-214">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="1f106-215">本機工具並非全域可用，而是以 NuGet 套件形式散發。</span><span class="sxs-lookup"><span data-stu-id="1f106-215">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="1f106-216">如果您在 .NET Core 3.0 Preview 1 中嘗試本機工具 (例如執行 `dotnet tool restore` 或 `dotnet tool install`)，請刪除本機工具快取資料夾。</span><span class="sxs-lookup"><span data-stu-id="1f106-216">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="1f106-217">否則，本機工具將無法在任何較新版本中運作。</span><span class="sxs-lookup"><span data-stu-id="1f106-217">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="1f106-218">此資料夾位於：</span><span class="sxs-lookup"><span data-stu-id="1f106-218">This folder is located at:</span></span>
>
> <span data-ttu-id="1f106-219">在 macOS 上，Linux：`rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="1f106-219">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="1f106-220">在 Windows 上：`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="1f106-220">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="1f106-221">本機工具會倚賴您目前目錄中名為 `dotnet-tools.json` 的資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="1f106-221">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="1f106-222">此資訊清單檔定義可在該資料夾和以下資料夾提供的工具。</span><span class="sxs-lookup"><span data-stu-id="1f106-222">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="1f106-223">您可以隨程式碼散發資訊清單檔，確保使用您程式碼的任何人都能進行還原並使用相同工具。</span><span class="sxs-lookup"><span data-stu-id="1f106-223">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="1f106-224">不論是全域工具還是區域工具，都需要一個相容的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="1f106-224">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="1f106-225">NuGet.org 上目前許多工具都以 .NET Core 執行階段 2.1 為目標。</span><span class="sxs-lookup"><span data-stu-id="1f106-225">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="1f106-226">若要在全域或本機安裝這些工具，您仍然需要安裝 [.NET Core 2.1 執行階段](https://dotnet.microsoft.com/download/dotnet-core/2.1)。</span><span class="sxs-lookup"><span data-stu-id="1f106-226">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="major-version-roll-forward"></a><span data-ttu-id="1f106-227">主要版本向前復原</span><span class="sxs-lookup"><span data-stu-id="1f106-227">Major-version Roll Forward</span></span>

<span data-ttu-id="1f106-228">.NET Core 3.0 引進選擇性功能，可讓您的應用程式向前復原到 .NET Core 最新主要版本。</span><span class="sxs-lookup"><span data-stu-id="1f106-228">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="1f106-229">此外，也已新增設定來控制如何將向前復原套用至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1f106-229">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="1f106-230">這可透過下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="1f106-230">This can be configured in the following ways:</span></span>

- <span data-ttu-id="1f106-231">專案檔屬性：`RollForward`</span><span class="sxs-lookup"><span data-stu-id="1f106-231">Project file property: `RollForward`</span></span>
- <span data-ttu-id="1f106-232">執行階段組態檔屬性：`rollForward`</span><span class="sxs-lookup"><span data-stu-id="1f106-232">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="1f106-233">環境變數：`DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="1f106-233">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="1f106-234">命令列引數：`--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="1f106-234">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="1f106-235">必須指定下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="1f106-235">One of the following values must be specified.</span></span> <span data-ttu-id="1f106-236">若省略設定，**Minor** 會是預設值。</span><span class="sxs-lookup"><span data-stu-id="1f106-236">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="1f106-237">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="1f106-237">**LatestPatch**</span></span>\
<span data-ttu-id="1f106-238">向前復原到最高的修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="1f106-238">Roll forward to the highest patch version.</span></span> <span data-ttu-id="1f106-239">這會停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="1f106-239">This disables minor version roll forward.</span></span>
- <span data-ttu-id="1f106-240">**Minor**</span><span class="sxs-lookup"><span data-stu-id="1f106-240">**Minor**</span></span>\
<span data-ttu-id="1f106-241">如果缺少要求的次要版本，則會向前復原到最低次要版本中次高的版本。</span><span class="sxs-lookup"><span data-stu-id="1f106-241">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="1f106-242">如果要求的次要版本存在，則會使用 **LatestPatch** 原則。</span><span class="sxs-lookup"><span data-stu-id="1f106-242">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="1f106-243">**Major**</span><span class="sxs-lookup"><span data-stu-id="1f106-243">**Major**</span></span>\
<span data-ttu-id="1f106-244">如果缺少要求的主要版本，則會向前復原到最低主要版本中次高的版本，以及最低的次要版本。</span><span class="sxs-lookup"><span data-stu-id="1f106-244">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="1f106-245">如果要求的主要版本存在，則會使用 **Minor** 原則。</span><span class="sxs-lookup"><span data-stu-id="1f106-245">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="1f106-246">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="1f106-246">**LatestMinor**</span></span>\
<span data-ttu-id="1f106-247">向前復原到最高的次要版本，即使要求的次要版本存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="1f106-247">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="1f106-248">適用於裝載案例的元件。</span><span class="sxs-lookup"><span data-stu-id="1f106-248">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="1f106-249">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="1f106-249">**LatestMajor**</span></span>\
<span data-ttu-id="1f106-250">向前復原到最高主要版本和最高次要版本，即使要求的主要版本存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="1f106-250">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="1f106-251">適用於裝載案例的元件。</span><span class="sxs-lookup"><span data-stu-id="1f106-251">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="1f106-252">**Disable**</span><span class="sxs-lookup"><span data-stu-id="1f106-252">**Disable**</span></span>\
<span data-ttu-id="1f106-253">不會向前復原。</span><span class="sxs-lookup"><span data-stu-id="1f106-253">Don't roll forward.</span></span> <span data-ttu-id="1f106-254">只會繫結至指定的版本。</span><span class="sxs-lookup"><span data-stu-id="1f106-254">Only bind to specified version.</span></span> <span data-ttu-id="1f106-255">此原則不建議一般用途，因為它會停用向前復原到最新修補程式的功能。</span><span class="sxs-lookup"><span data-stu-id="1f106-255">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="1f106-256">只有測試時才建議使用這個值。</span><span class="sxs-lookup"><span data-stu-id="1f106-256">This value is only recommended for testing.</span></span>

<span data-ttu-id="1f106-257">除了 **Disable** 設定，所有設定都會使用最高可用的修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="1f106-257">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="1f106-258">Windows 桌面</span><span class="sxs-lookup"><span data-stu-id="1f106-258">Windows desktop</span></span>

<span data-ttu-id="1f106-259">.NET Core 3.0 支援使用 Windows Presentation Foundation (WPF) 和 Windows Forms 的 Windows 傳統型應用程式。</span><span class="sxs-lookup"><span data-stu-id="1f106-259">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="1f106-260">這些架構也支援透過 [XAML 島](/windows/uwp/xaml-platform/xaml-host-controls)使用來自 Windows UI XAML 程式庫 (WinUI) 的新式控制項和 Fluent 樣式。</span><span class="sxs-lookup"><span data-stu-id="1f106-260">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="1f106-261">「Windows 傳統型」元件是 Windows .NET Core 3.0 SDK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="1f106-261">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="1f106-262">您可以使用下列 `dotnet` 命令來建立新的 WPF 或 Windows Forms 應用程式：</span><span class="sxs-lookup"><span data-stu-id="1f106-262">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="1f106-263">Visual Studio 2019 會新增 [新增專案]  範本，供 .NET Core 3.0 Windows Forms 和 WPF 使用。</span><span class="sxs-lookup"><span data-stu-id="1f106-263">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="1f106-264">如需如何移植現有 .NET Framework 應用程式的詳細資訊，請參閱[移植 WPF 專案](../porting/wpf.md)和[移植 Windows Forms 專案](../porting/winforms.md)。</span><span class="sxs-lookup"><span data-stu-id="1f106-264">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../porting/wpf.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

## <a name="com-callable-components---windows-desktop"></a><span data-ttu-id="1f106-265">COM 可呼叫元件 - Windows 傳統型</span><span class="sxs-lookup"><span data-stu-id="1f106-265">COM-callable components - Windows Desktop</span></span>

<span data-ttu-id="1f106-266">您現在可以在 Windows 上建立 COM 可呼叫受控元件。</span><span class="sxs-lookup"><span data-stu-id="1f106-266">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="1f106-267">此功能對於搭配 COM 增益集模型使用 .NET Core 很重要，也提供 .NET Framework 同位。</span><span class="sxs-lookup"><span data-stu-id="1f106-267">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="1f106-268">不同於 .NET Framework (其中使用 *mscoree.dll* 作為 COM 伺服器)，.NET Core 會在您建置 COM 元件時，將原生啟動器 DLL 新增至 *bin* 目錄。</span><span class="sxs-lookup"><span data-stu-id="1f106-268">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="1f106-269">如需如何建立及取用 COM 元件的範例，請參閱 [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) (COM 示範)。</span><span class="sxs-lookup"><span data-stu-id="1f106-269">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

## <a name="msix-deployment---windows-desktop"></a><span data-ttu-id="1f106-270">MSIX 部署 - Windows 傳統型</span><span class="sxs-lookup"><span data-stu-id="1f106-270">MSIX Deployment - Windows Desktop</span></span>

<span data-ttu-id="1f106-271">[MSIX](https://docs.microsoft.com/windows/msix/) 是新的 Windows 應用程式套件格式。</span><span class="sxs-lookup"><span data-stu-id="1f106-271">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="1f106-272">它可以用來將 .NET Core 3.0 桌面應用程式部署至 Windows 10。</span><span class="sxs-lookup"><span data-stu-id="1f106-272">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="1f106-273">Visual Studio 2019 中提供的 [Windows 應用程式套件專案](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net) \(機器翻譯\) 可讓您利用[獨立式](../deploying/index.md#self-contained-deployments-scd) .NET Core 應用程式建立 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="1f106-273">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="1f106-274">.NET Core 專案檔必須指定在 `<RuntimeIdentifiers>` 屬性中支援的執行階段：</span><span class="sxs-lookup"><span data-stu-id="1f106-274">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-high-dpi"></a><span data-ttu-id="1f106-275">WinForms 高 DPI</span><span class="sxs-lookup"><span data-stu-id="1f106-275">WinForms high DPI</span></span>

<span data-ttu-id="1f106-276">.NET Core Windows Forms 應用程式可以使用 <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType> 設定高 DPI 模式。</span><span class="sxs-lookup"><span data-stu-id="1f106-276">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1f106-277">除非已透過其他方法 (例如在 `Application.Run` 前面加上 `App.Manifest` 或 P/Invoke) 進行設定，否則 `SetHighDpiMode` 方法可以設定對應的高 DPI 模式。</span><span class="sxs-lookup"><span data-stu-id="1f106-277">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="1f106-278">可能的 `highDpiMode` 值 (如 <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> 列舉所示) 為：</span><span class="sxs-lookup"><span data-stu-id="1f106-278">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

<span data-ttu-id="1f106-279">如需高 DPI 模式的詳細資訊，請參閱 [Windows 上的高 DPI 傳統型應用程式開發](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows)。</span><span class="sxs-lookup"><span data-stu-id="1f106-279">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

## <a name="ranges-and-indices"></a><span data-ttu-id="1f106-280">範圍和索引</span><span class="sxs-lookup"><span data-stu-id="1f106-280">Ranges and indices</span></span>

<span data-ttu-id="1f106-281">新的 <xref:System.Index?displayProperty=nameWithType> 類型可用於編製索引。</span><span class="sxs-lookup"><span data-stu-id="1f106-281">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="1f106-282">您可以從會從開頭算起的 `int` 或使用會從結尾算起的前置詞 `^` 運算子 (C#)，來建立一個索引：</span><span class="sxs-lookup"><span data-stu-id="1f106-282">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="1f106-283">此外，還有 <xref:System.Range?displayProperty=nameWithType> 類型，此類型由兩個 `Index` 值所組成 (一個代表開頭，一個代表結尾)，並可用 `x..y` 範圍運算式 (C#) 來撰寫。</span><span class="sxs-lookup"><span data-stu-id="1f106-283">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="1f106-284">您可以接著使用 `Range` 來編製索引以產生配量：</span><span class="sxs-lookup"><span data-stu-id="1f106-284">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="1f106-285">如需詳細資訊，請參閱[範圍和索引教學課程](../../csharp/tutorials/ranges-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="1f106-285">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

## <a name="async-streams"></a><span data-ttu-id="1f106-286">非同步資料流</span><span class="sxs-lookup"><span data-stu-id="1f106-286">Async streams</span></span>

<span data-ttu-id="1f106-287"><xref:System.Collections.Generic.IAsyncEnumerable%601> 類型是 <xref:System.Collections.Generic.IEnumerable%601> 的新非同步版本。</span><span class="sxs-lookup"><span data-stu-id="1f106-287">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="1f106-288">此語言可讓您透過 `IAsyncEnumerable<T>` 執行 `await foreach` 以取用其元素，然後對它們使用 `yield return` 以產生元素。</span><span class="sxs-lookup"><span data-stu-id="1f106-288">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="1f106-289">下列範例同時示範如何產生和取用非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="1f106-289">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="1f106-290">`foreach` 是非同步陳述式，其本身會使用 `yield return` 來為呼叫端產生非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="1f106-290">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="1f106-291">此模式 (使用 `yield return`) 是針對產生非同步資料流建議採用的模型。</span><span class="sxs-lookup"><span data-stu-id="1f106-291">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="1f106-292">除了能夠執行 `await foreach` 之外，您也可以建立非同步迭代器，例如建立一個會傳回 `IAsyncEnumerable/IAsyncEnumerator` 以供您在其中執行 `await` 和 `yield` 的迭代器。</span><span class="sxs-lookup"><span data-stu-id="1f106-292">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="1f106-293">針對需要處置的物件，您可以使用各種 BCL 類型 (例如 `Stream` 和 `Timer`) 所實作的 `IAsyncDisposable`。</span><span class="sxs-lookup"><span data-stu-id="1f106-293">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="1f106-294">如需詳細資訊，請參閱[非同步資料流教學課程](../../csharp/tutorials/generate-consume-asynchronous-stream.md)。</span><span class="sxs-lookup"><span data-stu-id="1f106-294">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="1f106-295">IEEE 浮點增強功能</span><span class="sxs-lookup"><span data-stu-id="1f106-295">IEEE Floating-point improvements</span></span>

<span data-ttu-id="1f106-296">正在更新浮點 API，以遵守 [IEEE 754-2008 修訂](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)。</span><span class="sxs-lookup"><span data-stu-id="1f106-296">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="1f106-297">這些變更的目標是公開所有的**必要**作業，並確定它們在行為上符合 IEEE 規格。如需浮點增強功能的詳細資訊，請參閱 [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) (.NET Core 3.0 中的浮點剖析和格式化增強功能) 部落格文章。</span><span class="sxs-lookup"><span data-stu-id="1f106-297">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="1f106-298">剖析與格式化修正包括：</span><span class="sxs-lookup"><span data-stu-id="1f106-298">Parsing and formatting fixes include:</span></span>

* <span data-ttu-id="1f106-299">正確地剖析並捨入任意長度的輸入。</span><span class="sxs-lookup"><span data-stu-id="1f106-299">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="1f106-300">正確地剖析並格式化負零。</span><span class="sxs-lookup"><span data-stu-id="1f106-300">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="1f106-301">正確地剖析 `Infinity` 和 `NaN`，方法為執行不區分大小寫的檢查，並允許適當時在前面選擇性加上 `+`。</span><span class="sxs-lookup"><span data-stu-id="1f106-301">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="1f106-302">新的 <xref:System.Math?displayProperty=nameWithType> API 包括：</span><span class="sxs-lookup"><span data-stu-id="1f106-302">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

* <span data-ttu-id="1f106-303"><xref:System.Math.BitIncrement(System.Double)> 和 <xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="1f106-303"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="1f106-304">對應至 `nextUp` 和 `nextDown` IEEE 作業。</span><span class="sxs-lookup"><span data-stu-id="1f106-304">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="1f106-305">它們會傳回最小浮點數，比較大於或小於輸入 (分別)。</span><span class="sxs-lookup"><span data-stu-id="1f106-305">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="1f106-306">例如，`Math.BitIncrement(0.0)` 會傳回 `double.Epsilon`。</span><span class="sxs-lookup"><span data-stu-id="1f106-306">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* <span data-ttu-id="1f106-307"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> 和 <xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="1f106-307"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="1f106-308">對應至 `maxNumMag` 和 `minNumMag`IEEE 作業，它們傳回的值大於或小於兩個輸入的範圍 (分別)。</span><span class="sxs-lookup"><span data-stu-id="1f106-308">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="1f106-309">例如，`Math.MaxMagnitude(2.0, -3.0)` 會傳回 `-3.0`。</span><span class="sxs-lookup"><span data-stu-id="1f106-309">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="1f106-310">對應至傳回整數值的 `logB` IEEE 作業，它會傳回輸入參數的對數，以整數 2 為底數。</span><span class="sxs-lookup"><span data-stu-id="1f106-310">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="1f106-311">此方法實際上與 `floor(log2(x))` 相同，但完成時發生最少捨入錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f106-311">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="1f106-312">對應至採用整數值的 `scaleB` IEEE 作業，它會有效傳回 `x * pow(2, n)`，但完成時發生最少捨入錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f106-312">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="1f106-313">對應至 `log2` IEEE 作業，它會傳回 2 為底數的對數。</span><span class="sxs-lookup"><span data-stu-id="1f106-313">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="1f106-314">它會將捨入錯誤減至最少。</span><span class="sxs-lookup"><span data-stu-id="1f106-314">It minimizes rounding error.</span></span>

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="1f106-315">對應至 `fma` IEEE 作業，它會執行融合的乘積和。</span><span class="sxs-lookup"><span data-stu-id="1f106-315">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="1f106-316">亦即，它會將 `(x * y) + z` 當作單一作業來執行，藉此將捨入錯誤減至最少。</span><span class="sxs-lookup"><span data-stu-id="1f106-316">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="1f106-317">範例將是傳回 `1e308` 的 `FusedMultiplyAdd(1e308, 2.0, -1e308)`。</span><span class="sxs-lookup"><span data-stu-id="1f106-317">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="1f106-318">一般 `(1e308 * 2.0) - 1e308` 會傳回 `double.PositiveInfinity`。</span><span class="sxs-lookup"><span data-stu-id="1f106-318">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="1f106-319">對應至 `copySign` IEEE 作業，它會傳回 `x` 的值，但具有 `y` 的符號。</span><span class="sxs-lookup"><span data-stu-id="1f106-319">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="1f106-320">快速的內建 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="1f106-320">Fast built-in JSON support</span></span>

<span data-ttu-id="1f106-321">.NET 使用者大幅倚賴 [**Json.NET**](https://www.newtonsoft.com/json) 及其他熱門的 JSON 程式庫 (這些仍持續是絕佳的選擇)。</span><span class="sxs-lookup"><span data-stu-id="1f106-321">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="1f106-322">**Json.NET** 使用 .NET 字串作為其基底資料類型，實際上就是 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="1f106-322">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="1f106-323">新的內建 JSON 支援是高效能、低配置，並以 `Span<byte>` 為基礎。</span><span class="sxs-lookup"><span data-stu-id="1f106-323">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="1f106-324">三個新的主要 JSON 相關類型已新增到 .NET Core 3.0 <xref:System.Text.Json?displayProperty=nameWithType> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f106-324">Three new main JSON-related types have been added to .NET Core 3.0 the <xref:System.Text.Json?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="1f106-325">這些類型「尚未」  支援簡單的 CLR 物件 (POCO) 序列化與還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1f106-325">These types don't *yet* support plain old CLR object (POCO) serialization and deserialization.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="1f106-326">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="1f106-326">Utf8JsonReader</span></span>

<span data-ttu-id="1f106-327"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> 是一個高效能、低配置、只能順向讀取的 UTF-8 編碼 JSON 文字讀取器，會從 `ReadOnlySpan<byte>` 開始讀取。</span><span class="sxs-lookup"><span data-stu-id="1f106-327"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="1f106-328">`Utf8JsonReader` 是一個基礎的低階類型，可用來建置自訂剖析器和還原序列化程式。</span><span class="sxs-lookup"><span data-stu-id="1f106-328">The `Utf8JsonReader` is a foundational, low-level type, that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="1f106-329">使用新的 `Utf8JsonReader` 來讀取 JSON 承載會比使用來自 **Json.NET** 的讀取器快兩倍。</span><span class="sxs-lookup"><span data-stu-id="1f106-329">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="1f106-330">它會等到您需要將 JSON 權杖實現為 (UTF-16) 字串時，才進行配置。</span><span class="sxs-lookup"><span data-stu-id="1f106-330">It doesn't allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="1f106-331">以下是完整閱讀 Visual Studio Code 所建立 [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) 檔案的範例：</span><span class="sxs-lookup"><span data-stu-id="1f106-331">Here is an example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a><span data-ttu-id="1f106-332">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="1f106-332">Utf8JsonWriter</span></span>

<span data-ttu-id="1f106-333"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> 提供高效能、非快取、僅轉接方式，從常見的 .NET 類型 (像是 `String`、`Int32` 和 `DateTime`) 撰寫 UTF-8 編碼的 JSON 文字。</span><span class="sxs-lookup"><span data-stu-id="1f106-333"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="1f106-334">如同讀取器，寫入器是一個基礎的低階類型，可用來建置自訂序列化程式。</span><span class="sxs-lookup"><span data-stu-id="1f106-334">Like the reader, the writer is a foundational, low-level type, that can be used to build custom serializers.</span></span> <span data-ttu-id="1f106-335">使用新的 `Utf8JsonWriter` 撰寫 JSON 承載，其速度比從 **Json.NET** 使用寫入器還要快 30-80%，且不會配置。</span><span class="sxs-lookup"><span data-stu-id="1f106-335">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and doesn't allocate.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="1f106-336">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="1f106-336">JsonDocument</span></span>

<span data-ttu-id="1f106-337"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> 是組建在 `Utf8JsonReader` 之上。</span><span class="sxs-lookup"><span data-stu-id="1f106-337"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="1f106-338">`JsonDocument` 可讓您剖析 JSON 資料和組建唯讀文件物件模型 (DOM)，而您可以查詢此模型來支援隨機存取和列舉。</span><span class="sxs-lookup"><span data-stu-id="1f106-338">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="1f106-339">撰寫資料的 JSON 項目可以透過 <xref:System.Text.Json.JsonElement> 類型來存取，而此類型被 `JsonDocument` 公開為稱為 `RootElement` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="1f106-339">The JSON elements that compose the data can be accessed via the <xref:System.Text.Json.JsonElement> type that is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="1f106-340">`JsonElement` 包含 JSON 陣列和物件列舉程式，以及將 JSON 文字轉換為一般.NET 類型的 API。</span><span class="sxs-lookup"><span data-stu-id="1f106-340">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="1f106-341">使用 `JsonDocument` 剖析一般 JSON 承載，並存取其所有成員，速度比 **Json.NET** 還要快 2-3 倍，且極少配置合理大小 (亦即 < 1 MB) 的資料。</span><span class="sxs-lookup"><span data-stu-id="1f106-341">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with little allocations for data that is reasonably sized (that is, < 1 MB).</span></span>

<span data-ttu-id="1f106-342">以下是 `JsonDocument` 和 `JsonElement` 的使用方式樣本，其可作為起點：</span><span class="sxs-lookup"><span data-stu-id="1f106-342">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

<span data-ttu-id="1f106-343">以下是完整閱讀 Visual Studio Code 所建立 [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) 檔案的 C# 8.0 範例：</span><span class="sxs-lookup"><span data-stu-id="1f106-343">Here is a C# 8.0 example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a><span data-ttu-id="1f106-344">JsonSerializer</span><span class="sxs-lookup"><span data-stu-id="1f106-344">JsonSerializer</span></span>

<span data-ttu-id="1f106-345"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> 建置在 <xref:System.Text.Json.Utf8JsonReader> 和 <xref:System.Text.Json.Utf8JsonWriter> 之上，以在使用 JSON 文件和片段時，提供快速的低記憶體序列化選項。</span><span class="sxs-lookup"><span data-stu-id="1f106-345"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> is built on top of <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter> to provide a fast, low-memory serialization option when working with JSON documents and fragments.</span></span>

<span data-ttu-id="1f106-346">以下是將物件序列化成 JSON 的範例：</span><span class="sxs-lookup"><span data-stu-id="1f106-346">Here is an example of serializing an object to JSON:</span></span>

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

<span data-ttu-id="1f106-347">以下是將 JSON 字串還原序列化成物件的範例。</span><span class="sxs-lookup"><span data-stu-id="1f106-347">Here is an example of deserializing a JSON string to an object.</span></span> <span data-ttu-id="1f106-348">您可以使用上述範例所產生的 JSON 字串：</span><span class="sxs-lookup"><span data-stu-id="1f106-348">You can use the JSON string produced by the previous example:</span></span>

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a><span data-ttu-id="1f106-349">Interop 增強功能</span><span class="sxs-lookup"><span data-stu-id="1f106-349">Interop improvements</span></span>

<span data-ttu-id="1f106-350">.NET Core 3.0 改善原生 API Interop。</span><span class="sxs-lookup"><span data-stu-id="1f106-350">.NET Core 3.0 improves native API interop.</span></span>

### <a name="type-nativelibrary"></a><span data-ttu-id="1f106-351">類型：NativeLibrary</span><span class="sxs-lookup"><span data-stu-id="1f106-351">Type: NativeLibrary</span></span>

<span data-ttu-id="1f106-352"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> 提供封裝來載入原生程式庫 (使用與 .NET Core P/Invoke 相同的負載邏輯)，並提供相關的 Helper 函式 (例如 `getSymbol`)。</span><span class="sxs-lookup"><span data-stu-id="1f106-352"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> provides an encapsulation for loading a native library (using the same load logic as .NET Core P/Invoke) and providing the relevant helper functions such as `getSymbol`.</span></span> <span data-ttu-id="1f106-353">如需程式碼範例，請參閱 [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin) (DLLMap 示範)。</span><span class="sxs-lookup"><span data-stu-id="1f106-353">For a code example, see the [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="1f106-354">Windows 原生 Interop</span><span class="sxs-lookup"><span data-stu-id="1f106-354">Windows Native Interop</span></span>

<span data-ttu-id="1f106-355">Windows 提供豐富的原生 API，其採用的形式為一般 C API、COM 和 WinRT。</span><span class="sxs-lookup"><span data-stu-id="1f106-355">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="1f106-356">除了 .NET Core 3.0 支援 **P/Invoke** 之外，.NET Core 3.0 還新增 **CoCreate COM API** 和 **Activate WinRT API** 的功能。</span><span class="sxs-lookup"><span data-stu-id="1f106-356">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="1f106-357">如需程式碼範例，請參閱 [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo) (Excel 示範)。</span><span class="sxs-lookup"><span data-stu-id="1f106-357">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="http2-support"></a><span data-ttu-id="1f106-358">HTTP/2 支援</span><span class="sxs-lookup"><span data-stu-id="1f106-358">HTTP/2 support</span></span>

<span data-ttu-id="1f106-359"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 類型支援 HTTP/2 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="1f106-359">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="1f106-360">如果啟用 HTTP/2，則會透過 TLS/ALPN 交涉 HTTP 通訊協定版本，並會在伺服器選擇使用它時使用 HTTP/2。</span><span class="sxs-lookup"><span data-stu-id="1f106-360">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="1f106-361">預設通訊協定會保持為 HTTP/1.1，但 HTTP/2 可以兩種不同的方式啟用。</span><span class="sxs-lookup"><span data-stu-id="1f106-361">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="1f106-362">首先，您可以設定 HTTP 要求訊息來使用 HTTP/2：</span><span class="sxs-lookup"><span data-stu-id="1f106-362">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="1f106-363">再來，您可以變更 <xref:System.Net.Http.HttpClient> 來預設使用 HTTP/2：</span><span class="sxs-lookup"><span data-stu-id="1f106-363">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="1f106-364">當您在開發應用程式時，經常會想要使用未加密的連線。</span><span class="sxs-lookup"><span data-stu-id="1f106-364">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="1f106-365">如果您知道目標端點會使用 HTTP/2，便可以針對 HTTP/2 開啟未加密的連線。</span><span class="sxs-lookup"><span data-stu-id="1f106-365">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="1f106-366">若要開啟它，您可以將 `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` 環境變數設定為 `1`，或是在應用程式內容中啟用它：</span><span class="sxs-lookup"><span data-stu-id="1f106-366">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="1f106-367">Linux 上的 TLS 1.3 和 OpenSSL 1.1.1</span><span class="sxs-lookup"><span data-stu-id="1f106-367">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="1f106-368">.NET Core 現在會利用 [OpenSSL 1.1.1 中的 TLS 1.3 支援](https://www.openssl.org/blog/blog/2018/09/11/release111/) (當在指定的環境中有提供時)。</span><span class="sxs-lookup"><span data-stu-id="1f106-368">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="1f106-369">透過 TLS 1.3：</span><span class="sxs-lookup"><span data-stu-id="1f106-369">With TLS 1.3:</span></span>

* <span data-ttu-id="1f106-370">因為用戶端與伺服器之間所需的來回行程次數減少，所以改善了連線時間。</span><span class="sxs-lookup"><span data-stu-id="1f106-370">Connection times are improved with reduced round trips required between the client and server.</span></span>
* <span data-ttu-id="1f106-371">因為移除各種已淘汰和不安全的密碼編譯演算法，所以提升了安全性。</span><span class="sxs-lookup"><span data-stu-id="1f106-371">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="1f106-372">.NET Core 3.0 在 Linux 系統上使用 **OpenSSL 1.1.1**、**OpenSSL 1.1.0** 或 **OpenSSL 1.0.2** (若可供使用)。</span><span class="sxs-lookup"><span data-stu-id="1f106-372">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="1f106-373">當 **OpenSSL 1.1.1** 可供使用時，<xref:System.Net.Security.SslStream?displayProperty=nameWithType> 和 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 類型就會使用 **TLS 1.3** (假設用戶端和伺服器都支援 **TLS 1.3**)。</span><span class="sxs-lookup"><span data-stu-id="1f106-373">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="1f106-374">Windows 和 macOS 尚未支援 **TLS 1.3**。</span><span class="sxs-lookup"><span data-stu-id="1f106-374">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="1f106-375">.NET Core 3.0 將在有支援可用時，在這些作業系統上支援 **TLS 1.3**。</span><span class="sxs-lookup"><span data-stu-id="1f106-375">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="1f106-376">下列 C# 8.0 範例示範連線至 <https://www.cloudflare.com> 之 Ubuntu 18.10 上的 .NET Core 3.0：</span><span class="sxs-lookup"><span data-stu-id="1f106-376">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a><span data-ttu-id="1f106-377">密碼編譯加密方式</span><span class="sxs-lookup"><span data-stu-id="1f106-377">Cryptography ciphers</span></span>

<span data-ttu-id="1f106-378">.NET 3.0 新增對 **AES-GCM** 和 **AES-CCM** 加密方式的支援，分別透過 <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> 和 <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> 來實作。</span><span class="sxs-lookup"><span data-stu-id="1f106-378">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="1f106-379">這些演算法都是[搭配關聯資料的驗證加密 (AEAD) 演算法](https://en.wikipedia.org/wiki/Authenticated_encryption)。</span><span class="sxs-lookup"><span data-stu-id="1f106-379">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="1f106-380">下列程式碼示範如何使用 `AesGcm` 加密方式將隨機資料加密和解密。</span><span class="sxs-lookup"><span data-stu-id="1f106-380">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="1f106-381">密碼編譯金鑰匯入/匯出</span><span class="sxs-lookup"><span data-stu-id="1f106-381">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="1f106-382">.NET Core 3.0 支援從標準格式匯入及匯出非對稱式公開金鑰與私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="1f106-382">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="1f106-383">您無須使用 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="1f106-383">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="1f106-384">所有金鑰類型 (例如 *RSA*、*DSA*、*ECDsa* 和 *ECDiffieHellman*) 都支援下列格式：</span><span class="sxs-lookup"><span data-stu-id="1f106-384">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

* <span data-ttu-id="1f106-385">**公開金鑰**</span><span class="sxs-lookup"><span data-stu-id="1f106-385">**Public Key**</span></span>
  * <span data-ttu-id="1f106-386">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="1f106-386">X.509 SubjectPublicKeyInfo</span></span>

* <span data-ttu-id="1f106-387">**私密金鑰**</span><span class="sxs-lookup"><span data-stu-id="1f106-387">**Private key**</span></span>
  * <span data-ttu-id="1f106-388">PKCS#8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="1f106-388">PKCS#8 PrivateKeyInfo</span></span>
  * <span data-ttu-id="1f106-389">PKCS#8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="1f106-389">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="1f106-390">RSA 金鑰也支援：</span><span class="sxs-lookup"><span data-stu-id="1f106-390">RSA keys also support:</span></span>

* <span data-ttu-id="1f106-391">**公開金鑰**</span><span class="sxs-lookup"><span data-stu-id="1f106-391">**Public Key**</span></span>
  * <span data-ttu-id="1f106-392">PKCS#1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="1f106-392">PKCS#1 RSAPublicKey</span></span>

* <span data-ttu-id="1f106-393">**私密金鑰**</span><span class="sxs-lookup"><span data-stu-id="1f106-393">**Private key**</span></span>
  * <span data-ttu-id="1f106-394">PKCS#1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="1f106-394">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="1f106-395">匯出方法會產生 DER 編碼的二進位資料，而匯入方法也是如此。</span><span class="sxs-lookup"><span data-stu-id="1f106-395">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="1f106-396">如果金鑰是以適合文字的 PEM 格式儲存的，呼叫端在呼叫匯入方法之前，就必須先對內容進行 Base64 解碼。</span><span class="sxs-lookup"><span data-stu-id="1f106-396">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="1f106-397">**PKCS#8** 檔案可以使用 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> 來檢查，而 **PFX/PKCS#12** 檔案可以使用 <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType> 來檢查。</span><span class="sxs-lookup"><span data-stu-id="1f106-397">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1f106-398">**PFX/PKCS#12** 檔案可以使用 <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType> 來操作。</span><span class="sxs-lookup"><span data-stu-id="1f106-398">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="1f106-399">適用於 Linux 的 SerialPort</span><span class="sxs-lookup"><span data-stu-id="1f106-399">SerialPort for Linux</span></span>

<span data-ttu-id="1f106-400">.NET Core 3.0 在 Linux 上支援 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1f106-400">.NET Core 3.0 supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="1f106-401">先前，.NET Core 僅支援在 Windows 上使用 `SerialPort`。</span><span class="sxs-lookup"><span data-stu-id="1f106-401">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

## <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="1f106-402">Docker 和 cgroup 記憶體限制</span><span class="sxs-lookup"><span data-stu-id="1f106-402">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="1f106-403">從 Preview 3 開始，在 Linux 上執行 .NET Core 3.0 和 Docker 搭配 cgroup 記憶體限制的效果最佳。</span><span class="sxs-lookup"><span data-stu-id="1f106-403">Starting with Preview 3, running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="1f106-404">使用記憶體限制 (例如使用 `docker run -m`) 執行 Docker 容器會變更 .NET Core 的運作方式。</span><span class="sxs-lookup"><span data-stu-id="1f106-404">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

* <span data-ttu-id="1f106-405">預設記憶體回收行程 (GC) 堆積大小：上限為 20 MB，或容器上 75% 的記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="1f106-405">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
* <span data-ttu-id="1f106-406">可將明確大小設定為 cgroup 限制的絕對數目或百分比。</span><span class="sxs-lookup"><span data-stu-id="1f106-406">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
* <span data-ttu-id="1f106-407">每個 GC 堆積的保留區段大小下限為 16 MB。</span><span class="sxs-lookup"><span data-stu-id="1f106-407">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="1f106-408">此大小可減少電腦上所建立的堆積數目。</span><span class="sxs-lookup"><span data-stu-id="1f106-408">This size reduces the number of heaps that are created on machines.</span></span>

## <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="1f106-409">較小的記憶體回收堆積大小</span><span class="sxs-lookup"><span data-stu-id="1f106-409">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="1f106-410">已減少記憶體回收行程的預設堆積大小，而導致 .NET Core 使用較少的記憶體。</span><span class="sxs-lookup"><span data-stu-id="1f106-410">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="1f106-411">這項變更較符合使用新式處理器快取大小的層代 0 配置預算。</span><span class="sxs-lookup"><span data-stu-id="1f106-411">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

## <a name="garbage-collection-large-page-support"></a><span data-ttu-id="1f106-412">記憶體回收大型頁面支援</span><span class="sxs-lookup"><span data-stu-id="1f106-412">Garbage Collection Large Page support</span></span>

<span data-ttu-id="1f106-413">大型頁面 (Large Page，在 Linux 上又稱為 Huge Page) 是一項功能，其中作業系統能夠建立大於原生頁面大小 (通常為 4K) 的記憶體區域，以提升要求這些大型頁面的應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="1f106-413">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="1f106-414">記憶體回收行程現在可以設定 **GCLargePages** 設定作為選擇性功能，來選擇在 Windows 上配置大型頁面。</span><span class="sxs-lookup"><span data-stu-id="1f106-414">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="1f106-415">Raspberry Pi 的 GPIO 支援</span><span class="sxs-lookup"><span data-stu-id="1f106-415">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="1f106-416">兩個套件已發佈至您可以用於 GPIO 程式設計的 NuGet：</span><span class="sxs-lookup"><span data-stu-id="1f106-416">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

* [<span data-ttu-id="1f106-417">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="1f106-417">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
* [<span data-ttu-id="1f106-418">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="1f106-418">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="1f106-419">GPIO 套件包含 *GPIO*、*SPI*、*I2C* 和 *PWM* 裝置的 API。</span><span class="sxs-lookup"><span data-stu-id="1f106-419">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="1f106-420">IoT 繫結套件包含裝置繫結。</span><span class="sxs-lookup"><span data-stu-id="1f106-420">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="1f106-421">如需詳細資訊，請參閱[裝置 GitHub 存放庫](https://github.com/dotnet/iot/blob/master/src/devices/)。</span><span class="sxs-lookup"><span data-stu-id="1f106-421">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="1f106-422">ARM64 Linux 支援</span><span class="sxs-lookup"><span data-stu-id="1f106-422">ARM64 Linux support</span></span>

<span data-ttu-id="1f106-423">.NET Core 3.0 新增 ARM64 for Linux 的支援。</span><span class="sxs-lookup"><span data-stu-id="1f106-423">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="1f106-424">ARM64 的主要使用案例目前是搭配 IoT 案例。</span><span class="sxs-lookup"><span data-stu-id="1f106-424">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="1f106-425">如需詳細資訊，請參閱 [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) (.NET Core ARM64 狀態)。</span><span class="sxs-lookup"><span data-stu-id="1f106-425">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="1f106-426">[ARM64 上適用於 .NET Core 的 Docker 映像](https://hub.docker.com/r/microsoft/dotnet/)可供 Alpine、Debian 和 Ubuntu 使用。</span><span class="sxs-lookup"><span data-stu-id="1f106-426">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="1f106-427">目前尚未提供 **ARM64** Windows 支援。</span><span class="sxs-lookup"><span data-stu-id="1f106-427">**ARM64** Windows support isn't yet available.</span></span>
