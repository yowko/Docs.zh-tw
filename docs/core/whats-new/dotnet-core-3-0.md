---
title: .NET Core 3.0 的新功能
description: 了解 .NET Core 3.0 所提供的新功能。
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 05/06/2019
ms.openlocfilehash: 8d6ff6bc55384281119600f2323212441c1815e9
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452476"
---
# <a name="whats-new-in-net-core-30-preview-5"></a><span data-ttu-id="60ff6-103">.NET Core 3.0 (Preview 5) 的新功能</span><span class="sxs-lookup"><span data-stu-id="60ff6-103">What's new in .NET Core 3.0 (Preview 5)</span></span>

<span data-ttu-id="60ff6-104">本文描述 .NET Core 3.0 (到 Preview 5) 的新功能。</span><span class="sxs-lookup"><span data-stu-id="60ff6-104">This article describes what is new in .NET Core 3.0 (through preview 5).</span></span> <span data-ttu-id="60ff6-105">其中一個最大的增強功能是對 Windows 傳統型應用程式的支援 (僅限 Windows)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="60ff6-106">您可以使用 .NET Core 3.0 SDK 元件「Windows 傳統型」來移植 Windows Forms 和 Windows Presentation Foundation (WPF) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="60ff6-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="60ff6-107">具體而言，只有在 Windows 上才支援並包含「Windows 傳統型」元件。</span><span class="sxs-lookup"><span data-stu-id="60ff6-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="60ff6-108">如需詳細資訊，請參閱本文稍後的 [Windows 傳統型](#windows-desktop)一節。</span><span class="sxs-lookup"><span data-stu-id="60ff6-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="60ff6-109">.NET Core 3.0 新增 C# 8.0 支援。</span><span class="sxs-lookup"><span data-stu-id="60ff6-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="60ff6-110">強烈建議您搭配 OmniSharp 延伸模組使用最新版的 Visual Studio 2019 Update 1 Preview 或 VSCode。</span><span class="sxs-lookup"><span data-stu-id="60ff6-110">It's highly recommended that you use the latest release of Visual Studio 2019 Update 1 Preview or VSCode with the OmniSharp extension.</span></span>

<span data-ttu-id="60ff6-111">立即在 Windows、Mac 及 Linux 上[下載並開始使用 .NET Core 3.0 Preview 5](https://aka.ms/netcore3download)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-111">[Download and get started with .NET Core 3.0 Preview 5](https://aka.ms/netcore3download) right now on Windows, Mac, and Linux.</span></span>

<span data-ttu-id="60ff6-112">如需每個預覽版的詳細資訊，請參閱下列公告：</span><span class="sxs-lookup"><span data-stu-id="60ff6-112">For more information about each preview release, see the following announcements:</span></span>

- [<span data-ttu-id="60ff6-113">.NET Core 3.0 Preview 5 公告</span><span class="sxs-lookup"><span data-stu-id="60ff6-113">.NET Core 3.0 Preview 5 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [<span data-ttu-id="60ff6-114">.NET Core 3.0 Preview 4 公告</span><span class="sxs-lookup"><span data-stu-id="60ff6-114">.NET Core 3.0 Preview 4 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [<span data-ttu-id="60ff6-115">.NET Core 3.0 Preview 3 公告</span><span class="sxs-lookup"><span data-stu-id="60ff6-115">.NET Core 3.0 Preview 3 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [<span data-ttu-id="60ff6-116">.NET Core 3.0 Preview 2 公告</span><span class="sxs-lookup"><span data-stu-id="60ff6-116">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [<span data-ttu-id="60ff6-117">.NET Core 3.0 Preview 1 公告</span><span class="sxs-lookup"><span data-stu-id="60ff6-117">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="60ff6-118">.NET Core SDK Windows Installer</span><span class="sxs-lookup"><span data-stu-id="60ff6-118">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="60ff6-119">Windows 的 MSI 安裝程式從 .NET Core 3.0 開始即已變更。</span><span class="sxs-lookup"><span data-stu-id="60ff6-119">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="60ff6-120">SDK 安裝程式現在會就地升級 SDK 功能帶版本。</span><span class="sxs-lookup"><span data-stu-id="60ff6-120">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="60ff6-121">功能帶是在版本號碼「修補程式」部分以「一百」為單位的群組中定義。</span><span class="sxs-lookup"><span data-stu-id="60ff6-121">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="60ff6-122">例如，**3.0.\*101**\* 和 **3.0.\*201**\* 是兩個不同功能帶中的版本，而 **3.0.\*101**\* 和 **3.0.\*199**\* 則位於相同的功能帶。</span><span class="sxs-lookup"><span data-stu-id="60ff6-122">For example, **3.0.\*101**\* and **3.0.\*201**\* are versions in two different feature bands while **3.0.\*101**\* and **3.0.\*199**\* are in the same feature band.</span></span> <span data-ttu-id="60ff6-123">此外，當安裝 .NET Core SDK **3.0.\*101**\* 時，會從電腦中移除 .NET Core SDK **3.0.\*100**\* (如果存在)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-123">And, when .NET Core SDK **3.0.\*101**\* is installed, .NET Core SDK **3.0.\*100**\* will be removed from the machine if it exists.</span></span> <span data-ttu-id="60ff6-124">當在相同的電腦上安裝 **3.0.\*200**\* 時，不會移除 .NET Core SDK \**3.0.*101\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="60ff6-124">When .NET Core SDK **3.0.\*200**\* is installed on the same machine, .NET Core SDK **3.0.\*101**\* won't be removed.</span></span>

<span data-ttu-id="60ff6-125">如需版本設定的詳細資訊，請參閱 [.NET Core 版本設定概觀](../versions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-125">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

## <a name="c-80-preview"></a><span data-ttu-id="60ff6-126">C# 8.0 Preview</span><span class="sxs-lookup"><span data-stu-id="60ff6-126">C# 8.0 preview</span></span>

<span data-ttu-id="60ff6-127">.NET Core 3.0 支援 C# 8 Preview。</span><span class="sxs-lookup"><span data-stu-id="60ff6-127">.NET Core 3.0 supports C# 8 preview.</span></span> <span data-ttu-id="60ff6-128">如需 C# 8.0 功能的詳細資訊，請參閱 [C# 8.0 的新功能](../../csharp/whats-new/csharp-8.md)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-128">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="60ff6-129">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="60ff6-129">.NET Standard 2.1</span></span>

<span data-ttu-id="60ff6-130">雖然 .NET Core 3.0 支援 **.NET Standard 2.1**，但預設 `dotnet new classlib` 範本會產生以 **.NET Standard 2.0** 為目標的專案。</span><span class="sxs-lookup"><span data-stu-id="60ff6-130">Even though .NET Core 3.0 supports **.NET Standard 2.1**, the default `dotnet new classlib` template generates a project that targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="60ff6-131">若要以 **.NET Standard 2.1** 為目標，請編輯您的專案檔並將 `TargetFramework` 屬性變更為 `netstandard2.1`：</span><span class="sxs-lookup"><span data-stu-id="60ff6-131">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

<span data-ttu-id="60ff6-132">如果您使用 Visual Studio，則需要 Visual Studio 2019，因為 Visual Studio 2017 不支援 **.NET Standard 2.1** 或 **.NET Core 3.0**。</span><span class="sxs-lookup"><span data-stu-id="60ff6-132">If you're using Visual Studio, you need Visual Studio 2019, as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span> <span data-ttu-id="60ff6-133">強烈建議您使用 [Visual Studio 2019 Update 1 Preview](https://visualstudio.microsoft.com/vs/preview/)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-133">We highly recommend that you use [Visual Studio 2019 Update 1 Preview](https://visualstudio.microsoft.com/vs/preview/).</span></span>

## <a name="improved-net-core-version-apis"></a><span data-ttu-id="60ff6-134">改善的 .NET Core 版本 API</span><span class="sxs-lookup"><span data-stu-id="60ff6-134">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="60ff6-135">從 .NET Core 3.0 開始，.NET Core 所提供版本 API 現在會傳回您預期的資訊。</span><span class="sxs-lookup"><span data-stu-id="60ff6-135">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="60ff6-136">例如：</span><span class="sxs-lookup"><span data-stu-id="60ff6-136">For example:</span></span>

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
> <span data-ttu-id="60ff6-137">重大變更。</span><span class="sxs-lookup"><span data-stu-id="60ff6-137">Breaking change.</span></span> <span data-ttu-id="60ff6-138">這是技術上的重大變更，因為版本設定配置已變更。</span><span class="sxs-lookup"><span data-stu-id="60ff6-138">This is technically a breaking change because the versioning scheme has changed.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="60ff6-139">.NET 平台相依內建</span><span class="sxs-lookup"><span data-stu-id="60ff6-139">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="60ff6-140">已新增 API，允許存取特定效能導向的 CPU 指令，例如 **SIMD** 或**位元操作指令**集合。</span><span class="sxs-lookup"><span data-stu-id="60ff6-140">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="60ff6-141">這些指令可協助您在某些情況 (例如有效率地平行處理資料) 下大幅提升效能。</span><span class="sxs-lookup"><span data-stu-id="60ff6-141">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> 

<span data-ttu-id="60ff6-142">.NET 程式庫 (如果適用) 已開始使用這些指令來提升效能。</span><span class="sxs-lookup"><span data-stu-id="60ff6-142">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="60ff6-143">如需詳細資訊，請參閱 [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md) (.NET 平台相依內建)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-143">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

## <a name="default-executables"></a><span data-ttu-id="60ff6-144">預設可執行檔</span><span class="sxs-lookup"><span data-stu-id="60ff6-144">Default executables</span></span>

<span data-ttu-id="60ff6-145">.NET Core 現在預設會建置[架構相依可執行檔](../deploying/index.md#framework-dependent-executables-fde)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-145">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="60ff6-146">這對於使用 .NET Core 全域安裝版本的應用程式來說，是一項新行為。</span><span class="sxs-lookup"><span data-stu-id="60ff6-146">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="60ff6-147">先前，只有[獨立式部署](../deploying/index.md#self-contained-deployments-scd)會產生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="60ff6-147">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="60ff6-148">在 `dotnet build` 或 `dotnet publish` 期間，會建立符合您所用 SDK 環境和平台的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="60ff6-148">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="60ff6-149">針對這些可執行檔，您可以預期能夠進行與其他原生可執行檔相同的操作，例如：</span><span class="sxs-lookup"><span data-stu-id="60ff6-149">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="60ff6-150">您可以按兩下可執行檔。</span><span class="sxs-lookup"><span data-stu-id="60ff6-150">You can double-click on the executable.</span></span>
* <span data-ttu-id="60ff6-151">您可以直接從命令提示字元啟動應用程式，例如在 Windows 上為 `myapp.exe`，在 Linux 和 macOS 上為 `./myapp`。</span><span class="sxs-lookup"><span data-stu-id="60ff6-151">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="single-file-executables"></a><span data-ttu-id="60ff6-152">單一檔案可執行檔</span><span class="sxs-lookup"><span data-stu-id="60ff6-152">Single-file executables</span></span>

<span data-ttu-id="60ff6-153">`dotnet publish` 命令支援將您的應用程式封裝成平台特定單一檔案可執行檔。</span><span class="sxs-lookup"><span data-stu-id="60ff6-153">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="60ff6-154">可執行檔會自我解壓縮，並包含執行應用程式所需的所有相依性 (包括原生)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-154">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="60ff6-155">第一次執行應用程式時，系統會將應用程式解壓縮到以應用程式名稱和組建識別碼為基礎的目錄。</span><span class="sxs-lookup"><span data-stu-id="60ff6-155">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="60ff6-156">再次執行應用程式時的啟動速度會更快。</span><span class="sxs-lookup"><span data-stu-id="60ff6-156">Startup is faster when the application is run again.</span></span> <span data-ttu-id="60ff6-157">除非使用新版本，否則應用程式不需要再次自我解壓縮。</span><span class="sxs-lookup"><span data-stu-id="60ff6-157">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="60ff6-158">若要發佈單一檔案可執行檔，請在專案中或在命令列上使用 `dotnet publish` 命令來設定 `PublishSingleFile`：</span><span class="sxs-lookup"><span data-stu-id="60ff6-158">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

<span data-ttu-id="60ff6-159">如需單一檔案發佈的詳細資訊，請參閱[單一檔案搭配程式設計文件](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-159">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="60ff6-160">階層式編譯</span><span class="sxs-lookup"><span data-stu-id="60ff6-160">Tiered compilation</span></span>

<span data-ttu-id="60ff6-161">.NET Core 3.0 預設會開啟[階層式編譯](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-161">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="60ff6-162">這項功能可讓執行階段更彈性地使用 Just-In-Time (JIT) 編譯器來獲得更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="60ff6-162">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="60ff6-163">TC 的主要優點是能夠啟用較慢速但較快產生程式碼，或品質較高但較慢產生程式碼的 JIT 重新編譯方法。</span><span class="sxs-lookup"><span data-stu-id="60ff6-163">The main benefit of TC is to enable (re-)jitting methods with slower-but-faster to produce code or higher-quality-but-slower to produce code.</span></span> <span data-ttu-id="60ff6-164">由於行經各種執行階段 (從啟動到穩定狀態)，因此有助於提升應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="60ff6-164">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="60ff6-165">這與非 TC 方法相反，在非 TC 方法中，所有方法都是以單一方式 (與高品質層相同) 進行編譯，這會偏重穩定狀態而非啟動效能。</span><span class="sxs-lookup"><span data-stu-id="60ff6-165">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="60ff6-166">若要啟用 Quick JIT (層級 0 JIT 編譯的程式碼)，請在您的專案檔中使用此設定：</span><span class="sxs-lookup"><span data-stu-id="60ff6-166">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="60ff6-167">若要完全停用 TC，請在您的專案檔中使用此設定：</span><span class="sxs-lookup"><span data-stu-id="60ff6-167">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="build-copies-dependencies"></a><span data-ttu-id="60ff6-168">組建複本相依性</span><span class="sxs-lookup"><span data-stu-id="60ff6-168">Build copies dependencies</span></span>

<span data-ttu-id="60ff6-169">`dotnet build` 命令現在會從 NuGet 快取將您應用程式的 NuGet 相依性複製到組建輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="60ff6-169">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="60ff6-170">先前，只有在進行 `dotnet publish` 的過程中，才會複製相依性。</span><span class="sxs-lookup"><span data-stu-id="60ff6-170">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="60ff6-171">有些作業 (例如連結和 Razor 頁面發佈) 仍然需要發佈。</span><span class="sxs-lookup"><span data-stu-id="60ff6-171">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-tools"></a><span data-ttu-id="60ff6-172">本機工具</span><span class="sxs-lookup"><span data-stu-id="60ff6-172">Local tools</span></span>

<span data-ttu-id="60ff6-173">.NET Core 3.0 引進本機工具。</span><span class="sxs-lookup"><span data-stu-id="60ff6-173">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="60ff6-174">本機工具與[全域工具](../tools/global-tools.md)類似，但與磁碟上的某個特定位置立建立關聯。</span><span class="sxs-lookup"><span data-stu-id="60ff6-174">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="60ff6-175">本機工具並非全域可用，而是以 NuGet 套件形式散發。</span><span class="sxs-lookup"><span data-stu-id="60ff6-175">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="60ff6-176">如果您在 .NET Core 3.0 Preview 1 中嘗試本機工具 (例如執行 `dotnet tool restore` 或 `dotnet tool install`)，請刪除本機工具快取資料夾。</span><span class="sxs-lookup"><span data-stu-id="60ff6-176">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="60ff6-177">否則，本機工具將無法在任何較新版本中運作。</span><span class="sxs-lookup"><span data-stu-id="60ff6-177">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="60ff6-178">此資料夾位於：</span><span class="sxs-lookup"><span data-stu-id="60ff6-178">This folder is located at:</span></span>
>
> <span data-ttu-id="60ff6-179">在 macOS 上，Linux：`rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="60ff6-179">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="60ff6-180">在 Windows 上：`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="60ff6-180">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="60ff6-181">本機工具會倚賴您目前目錄中名為 `dotnet-tools.json` 的資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="60ff6-181">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="60ff6-182">此資訊清單檔定義可在該資料夾和以下資料夾提供的工具。</span><span class="sxs-lookup"><span data-stu-id="60ff6-182">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="60ff6-183">您可以隨程式碼散發資訊清單檔，確保使用您程式碼的任何人都能進行還原並使用相同工具。</span><span class="sxs-lookup"><span data-stu-id="60ff6-183">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="60ff6-184">不論是全域工具還是區域工具，都需要一個相容的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="60ff6-184">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="60ff6-185">NuGet.org 上目前許多工具都以 .NET Core 執行階段 2.1 為目標。</span><span class="sxs-lookup"><span data-stu-id="60ff6-185">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="60ff6-186">若要在全域或本機安裝這些工具，您仍然需要安裝 [.NET Core 2.1 執行階段](https://dotnet.microsoft.com/download/dotnet-core/2.1)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-186">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="major-version-roll-forward"></a><span data-ttu-id="60ff6-187">主要版本向前復原</span><span class="sxs-lookup"><span data-stu-id="60ff6-187">Major-version Roll Forward</span></span>

<span data-ttu-id="60ff6-188">.NET Core 3.0 引進選擇性功能，可讓您的應用程式向前復原到 .NET Core 最新主要版本。</span><span class="sxs-lookup"><span data-stu-id="60ff6-188">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="60ff6-189">此外，也已新增設定來控制如何將向前復原套用至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="60ff6-189">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="60ff6-190">這可透過下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="60ff6-190">This can be configured in the following ways:</span></span>

- <span data-ttu-id="60ff6-191">專案檔屬性：`RollForward`</span><span class="sxs-lookup"><span data-stu-id="60ff6-191">Project file property: `RollForward`</span></span>
- <span data-ttu-id="60ff6-192">執行階段組態檔屬性：`rollForward`</span><span class="sxs-lookup"><span data-stu-id="60ff6-192">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="60ff6-193">環境變數：`DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="60ff6-193">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="60ff6-194">命令列引數：`--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="60ff6-194">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="60ff6-195">必須指定下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="60ff6-195">One of the following values must be specified.</span></span> <span data-ttu-id="60ff6-196">若省略設定，**Minor** 會是預設值。</span><span class="sxs-lookup"><span data-stu-id="60ff6-196">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="60ff6-197">**LatestPatch**\\</span><span class="sxs-lookup"><span data-stu-id="60ff6-197">**LatestPatch**\\</span></span>
<span data-ttu-id="60ff6-198">向前復原到最高的修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="60ff6-198">Roll forward to the highest patch version.</span></span> <span data-ttu-id="60ff6-199">這會停用次要版本向前復原。</span><span class="sxs-lookup"><span data-stu-id="60ff6-199">This disables minor version roll forward.</span></span>
- <span data-ttu-id="60ff6-200">**Minor**\\</span><span class="sxs-lookup"><span data-stu-id="60ff6-200">**Minor**\\</span></span>
<span data-ttu-id="60ff6-201">如果缺少要求的次要版本，則會向前復原到最低次要版本中次高的版本。</span><span class="sxs-lookup"><span data-stu-id="60ff6-201">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="60ff6-202">如果要求的次要版本存在，則會使用 **LatestPatch** 原則。</span><span class="sxs-lookup"><span data-stu-id="60ff6-202">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="60ff6-203">**Major**\\</span><span class="sxs-lookup"><span data-stu-id="60ff6-203">**Major**\\</span></span>
<span data-ttu-id="60ff6-204">如果缺少要求的主要版本，則會向前復原到最低主要版本中次高的版本，以及最低的次要版本。</span><span class="sxs-lookup"><span data-stu-id="60ff6-204">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="60ff6-205">如果要求的主要版本存在，則會使用 **Minor** 原則。</span><span class="sxs-lookup"><span data-stu-id="60ff6-205">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="60ff6-206">**LatestMinor**\\</span><span class="sxs-lookup"><span data-stu-id="60ff6-206">**LatestMinor**\\</span></span>
<span data-ttu-id="60ff6-207">向前復原到最高的次要版本，即使要求的次要版本存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="60ff6-207">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="60ff6-208">適用於裝載案例的元件。</span><span class="sxs-lookup"><span data-stu-id="60ff6-208">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="60ff6-209">**LatestMajor**\\</span><span class="sxs-lookup"><span data-stu-id="60ff6-209">**LatestMajor**\\</span></span>
<span data-ttu-id="60ff6-210">向前復原到最高主要版本和最高次要版本，即使要求的主要版本存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="60ff6-210">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="60ff6-211">適用於裝載案例的元件。</span><span class="sxs-lookup"><span data-stu-id="60ff6-211">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="60ff6-212">**Disable**\\</span><span class="sxs-lookup"><span data-stu-id="60ff6-212">**Disable**\\</span></span>
<span data-ttu-id="60ff6-213">不會向前復原。</span><span class="sxs-lookup"><span data-stu-id="60ff6-213">Don't roll forward.</span></span> <span data-ttu-id="60ff6-214">只會繫結至指定的版本。</span><span class="sxs-lookup"><span data-stu-id="60ff6-214">Only bind to specified version.</span></span> <span data-ttu-id="60ff6-215">此原則不建議一般用途，因為它會停用向前復原到最新修補程式的功能。</span><span class="sxs-lookup"><span data-stu-id="60ff6-215">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="60ff6-216">只有測試時才建議使用這個值。</span><span class="sxs-lookup"><span data-stu-id="60ff6-216">This value is only recommended for testing.</span></span>

<span data-ttu-id="60ff6-217">除了 **Disable** 設定，所有設定都會使用最高可用的修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="60ff6-217">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="60ff6-218">Windows 桌面</span><span class="sxs-lookup"><span data-stu-id="60ff6-218">Windows desktop</span></span>

<span data-ttu-id="60ff6-219">.NET Core 3.0 支援使用 Windows Presentation Foundation (WPF) 和 Windows Forms 的 Windows 傳統型應用程式。</span><span class="sxs-lookup"><span data-stu-id="60ff6-219">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="60ff6-220">這些架構也支援透過 [XAML 島](/windows/uwp/xaml-platform/xaml-host-controls)使用來自 Windows UI XAML 程式庫 (WinUI) 的新式控制項和 Fluent 樣式。</span><span class="sxs-lookup"><span data-stu-id="60ff6-220">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="60ff6-221">「Windows 傳統型」元件是 Windows .NET Core 3.0 SDK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="60ff6-221">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="60ff6-222">您可以使用下列 `dotnet` 命令來建立新的 WPF 或 Windows Forms 應用程式：</span><span class="sxs-lookup"><span data-stu-id="60ff6-222">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="60ff6-223">Visual Studio 2019 會新增 [新增專案] 範本，供 .NET Core 3.0 Windows Forms 和 WPF 使用。</span><span class="sxs-lookup"><span data-stu-id="60ff6-223">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="60ff6-224">如需如何移植現有 .NET Framework 應用程式的詳細資訊，請參閱[移植 WPF 專案](../porting/wpf.md)和[移植 Windows Forms 專案](../porting/winforms.md)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-224">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../porting/wpf.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

## <a name="com-callable-components---windows-desktop"></a><span data-ttu-id="60ff6-225">COM 可呼叫元件 - Windows 傳統型</span><span class="sxs-lookup"><span data-stu-id="60ff6-225">COM-callable components - Windows Desktop</span></span>

<span data-ttu-id="60ff6-226">您現在可以在 Windows 上建立 COM 可呼叫受控元件。</span><span class="sxs-lookup"><span data-stu-id="60ff6-226">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="60ff6-227">此功能對於搭配 COM 增益集模型使用 .NET Core 很重要，也提供 .NET Framework 同位。</span><span class="sxs-lookup"><span data-stu-id="60ff6-227">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="60ff6-228">不同於 .NET Framework (其中使用 *mscoree.dll* 作為 COM 伺服器)，.NET Core 會在您建置 COM 元件時，將原生啟動器 DLL 新增至 *bin* 目錄。</span><span class="sxs-lookup"><span data-stu-id="60ff6-228">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="60ff6-229">如需如何建立及取用 COM 元件的範例，請參閱 [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) (COM 示範)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-229">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

## <a name="msix-deployment---windows-desktop"></a><span data-ttu-id="60ff6-230">MSIX 部署 - Windows 傳統型</span><span class="sxs-lookup"><span data-stu-id="60ff6-230">MSIX Deployment - Windows Desktop</span></span>

<span data-ttu-id="60ff6-231">[MSIX](https://docs.microsoft.com/windows/msix/) 是新的 Windows 應用程式套件格式。</span><span class="sxs-lookup"><span data-stu-id="60ff6-231">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="60ff6-232">它可以用來將 .NET Core 3.0 桌面應用程式部署至 Windows 10。</span><span class="sxs-lookup"><span data-stu-id="60ff6-232">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="60ff6-233">Visual Studio 2019 中提供的 [Windows 應用程式套件專案](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net) \(機器翻譯\) 可讓您利用[獨立式](../deploying/index.md#self-contained-deployments-scd) .NET Core 應用程式建立 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="60ff6-233">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="60ff6-234">.NET Core 專案檔必須指定在 `<RuntimeIdentifiers>` 屬性中支援的執行階段：</span><span class="sxs-lookup"><span data-stu-id="60ff6-234">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a><span data-ttu-id="60ff6-235">WinForms HighDPI</span><span class="sxs-lookup"><span data-stu-id="60ff6-235">WinForms HighDPI</span></span>

<span data-ttu-id="60ff6-236">.NET Core Windows Forms 應用程式可以使用 <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType> 設定高 DPI 模式。</span><span class="sxs-lookup"><span data-stu-id="60ff6-236">.NET Core Windows Forms applications can set High DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="60ff6-237">除非已透過其他方法 (例如在 `Application.Run` 前面加上 `App.Manifest` 或 P/Invoke) 進行設定，否則 `SetHighDpiMode` 方法可以設定對應的高 DPI 模式。</span><span class="sxs-lookup"><span data-stu-id="60ff6-237">The `SetHighDpiMode` method sets the corresponding High DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="60ff6-238">可能的 `highDpiMode` 值 (如 <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> 列舉所示) 為：</span><span class="sxs-lookup"><span data-stu-id="60ff6-238">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

<span data-ttu-id="60ff6-239">如需高 DPI 模式的詳細資訊，請參閱 [Windows 上的高 DPI 傳統型應用程式開發](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-239">For more information about High DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="60ff6-240">範圍和索引</span><span class="sxs-lookup"><span data-stu-id="60ff6-240">Ranges and indices</span></span>

<span data-ttu-id="60ff6-241">新的 <xref:System.Index?displayProperty=nameWithType> 類型可用於編製索引。</span><span class="sxs-lookup"><span data-stu-id="60ff6-241">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="60ff6-242">您可以從會從開頭算起的 `int` 或使用會從結尾算起的前置詞 `^` 運算子 (C#)，來建立一個索引：</span><span class="sxs-lookup"><span data-stu-id="60ff6-242">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="60ff6-243">此外，還有 <xref:System.Range?displayProperty=nameWithType> 類型，此類型由兩個 `Index` 值所組成 (一個代表開頭，一個代表結尾)，並可用 `x..y` 範圍運算式 (C#) 來撰寫。</span><span class="sxs-lookup"><span data-stu-id="60ff6-243">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="60ff6-244">您可以接著使用 `Range` 來編製索引以產生配量：</span><span class="sxs-lookup"><span data-stu-id="60ff6-244">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="60ff6-245">如需詳細資訊，請參閱[範圍和索引教學課程](../../csharp/tutorials/ranges-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-245">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="60ff6-246">非同步資料流</span><span class="sxs-lookup"><span data-stu-id="60ff6-246">Async streams</span></span>

<span data-ttu-id="60ff6-247"><xref:System.Collections.Generic.IAsyncEnumerable%601> 類型是 <xref:System.Collections.Generic.IEnumerable%601> 的新非同步版本。</span><span class="sxs-lookup"><span data-stu-id="60ff6-247">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="60ff6-248">此語言可讓您透過 `IAsyncEnumerable<T>` 執行 `await foreach` 以取用其元素，然後對它們使用 `yield return` 以產生元素。</span><span class="sxs-lookup"><span data-stu-id="60ff6-248">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="60ff6-249">下列範例同時示範如何產生和取用非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="60ff6-249">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="60ff6-250">`foreach` 是非同步陳述式，其本身會使用 `yield return` 來為呼叫端產生非同步資料流。</span><span class="sxs-lookup"><span data-stu-id="60ff6-250">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="60ff6-251">此模式 (使用 `yield return`) 是針對產生非同步資料流建議採用的模型。</span><span class="sxs-lookup"><span data-stu-id="60ff6-251">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="60ff6-252">除了能夠執行 `await foreach` 之外，您也可以建立非同步迭代器，例如建立一個會傳回 `IAsyncEnumerable/IAsyncEnumerator` 以供您在其中執行 `await` 和 `yield` 的迭代器。</span><span class="sxs-lookup"><span data-stu-id="60ff6-252">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="60ff6-253">針對需要處置的物件，您可以使用各種 BCL 類型 (例如 `Stream` 和 `Timer`) 所實作的 `IAsyncDisposable`。</span><span class="sxs-lookup"><span data-stu-id="60ff6-253">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="60ff6-254">如需詳細資訊，請參閱[非同步資料流教學課程](../../csharp/tutorials/generate-consume-asynchronous-stream.md)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-254">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="60ff6-255">IEEE 浮點增強功能</span><span class="sxs-lookup"><span data-stu-id="60ff6-255">IEEE Floating-point improvements</span></span>

<span data-ttu-id="60ff6-256">正在更新浮點 API，以遵守 [IEEE 754-2008 修訂](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-256">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="60ff6-257">這些變更的目標是公開所有的**必要**作業，並確定它們在行為上符合 IEEE 規格。如需浮點增強功能的詳細資訊，請參閱 [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) (.NET Core 3.0 中的浮點剖析和格式化增強功能) 部落格文章。</span><span class="sxs-lookup"><span data-stu-id="60ff6-257">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="60ff6-258">剖析與格式化修正包括：</span><span class="sxs-lookup"><span data-stu-id="60ff6-258">Parsing and formatting fixes include:</span></span>

* <span data-ttu-id="60ff6-259">正確地剖析並捨入任意長度的輸入。</span><span class="sxs-lookup"><span data-stu-id="60ff6-259">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="60ff6-260">正確地剖析並格式化負零。</span><span class="sxs-lookup"><span data-stu-id="60ff6-260">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="60ff6-261">正確地剖析 `Infinity` 和 `NaN`，方法為執行不區分大小寫的檢查，並允許適當時在前面選擇性加上 `+`。</span><span class="sxs-lookup"><span data-stu-id="60ff6-261">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="60ff6-262">新的 <xref:System.Math?displayProperty=nameWithType> API 包括：</span><span class="sxs-lookup"><span data-stu-id="60ff6-262">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

* <span data-ttu-id="60ff6-263"><xref:System.Math.BitIncrement(System.Double)> 和 <xref:System.Math.BitDecrement(System.Double)>\\</span><span class="sxs-lookup"><span data-stu-id="60ff6-263"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)>\\</span></span>
<span data-ttu-id="60ff6-264">對應至 `nextUp` 和 `nextDown` IEEE 作業。</span><span class="sxs-lookup"><span data-stu-id="60ff6-264">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="60ff6-265">它們會傳回最小浮點數，比較大於或小於輸入 (分別)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-265">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="60ff6-266">例如，`Math.BitIncrement(0.0)` 會傳回 `double.Epsilon`。</span><span class="sxs-lookup"><span data-stu-id="60ff6-266">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* <span data-ttu-id="60ff6-267"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> 和 <xref:System.Math.MinMagnitude(System.Double,System.Double)>\\</span><span class="sxs-lookup"><span data-stu-id="60ff6-267"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)>\\</span></span>
<span data-ttu-id="60ff6-268">對應至 `maxNumMag` 和 `minNumMag`IEEE 作業，它們傳回的值大於或小於兩個輸入的範圍 (分別)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-268">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="60ff6-269">例如，`Math.MaxMagnitude(2.0, -3.0)` 會傳回 `-3.0`。</span><span class="sxs-lookup"><span data-stu-id="60ff6-269">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="60ff6-270">對應至傳回整數值的 `logB` IEEE 作業，它會傳回輸入參數的對數，以整數 2 為底數。</span><span class="sxs-lookup"><span data-stu-id="60ff6-270">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="60ff6-271">此方法實際上與 `floor(log2(x))` 相同，但完成時發生最少捨入錯誤。</span><span class="sxs-lookup"><span data-stu-id="60ff6-271">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="60ff6-272">對應至採用整數值的 `scaleB` IEEE 作業，它會有效傳回 `x * pow(2, n)`，但完成時發生最少捨入錯誤。</span><span class="sxs-lookup"><span data-stu-id="60ff6-272">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="60ff6-273">對應至 `log2` IEEE 作業，它會傳回 2 為底數的對數。</span><span class="sxs-lookup"><span data-stu-id="60ff6-273">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="60ff6-274">它會將捨入錯誤減至最少。</span><span class="sxs-lookup"><span data-stu-id="60ff6-274">It minimizes rounding error.</span></span>

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="60ff6-275">對應至 `fma` IEEE 作業，它會執行融合的乘積和。</span><span class="sxs-lookup"><span data-stu-id="60ff6-275">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="60ff6-276">亦即，它會將 `(x * y) + z` 當作單一作業來執行，藉此將捨入錯誤減至最少。</span><span class="sxs-lookup"><span data-stu-id="60ff6-276">That is, it does `(x * y) + z` as a single operation, there-by minimizing the rounding error.</span></span> <span data-ttu-id="60ff6-277">範例將是傳回 `1e308` 的 `FusedMultiplyAdd(1e308, 2.0, -1e308)`。</span><span class="sxs-lookup"><span data-stu-id="60ff6-277">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="60ff6-278">一般 `(1e308 * 2.0) - 1e308` 會傳回 `double.PositiveInfinity`。</span><span class="sxs-lookup"><span data-stu-id="60ff6-278">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="60ff6-279">對應至 `copySign` IEEE 作業，它會傳回 `x` 的值，但具有 `y` 的符號。</span><span class="sxs-lookup"><span data-stu-id="60ff6-279">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="60ff6-280">快速的內建 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="60ff6-280">Fast built-in JSON support</span></span>

<span data-ttu-id="60ff6-281">.NET 使用者大幅倚賴 [**Json.NET**](https://www.newtonsoft.com/json) 及其他熱門的 JSON 程式庫 (這些仍持續是絕佳的選擇)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-281">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="60ff6-282">**Json.NET** 使用 .NET 字串作為其基底資料類型，實際上就是 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="60ff6-282">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="60ff6-283">新的內建 JSON 支援是高效能、低配置，並以 `Span<byte>` 為基礎。</span><span class="sxs-lookup"><span data-stu-id="60ff6-283">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="60ff6-284">三個新的主要 JSON 相關類型已新增到 .NET Core 3.0 <xref:System.Text.Json?displayProperty=nameWithType> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="60ff6-284">Three new main JSON-related types have been added to .NET Core 3.0 the <xref:System.Text.Json?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="60ff6-285">這些類型「尚未」支援簡單的 CLR 物件 (POCO) 序列化與還原序列化。</span><span class="sxs-lookup"><span data-stu-id="60ff6-285">These types don't *yet* support plain old CLR object (POCO) serialization and deserialization.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="60ff6-286">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="60ff6-286">Utf8JsonReader</span></span>

<span data-ttu-id="60ff6-287"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> 是一個高效能、低配置、只能順向讀取的 UTF-8 編碼 JSON 文字讀取器，會從 `ReadOnlySpan<byte>` 開始讀取。</span><span class="sxs-lookup"><span data-stu-id="60ff6-287"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="60ff6-288">`Utf8JsonReader` 是一個基礎的低階類型，可用來建置自訂剖析器和還原序列化程式。</span><span class="sxs-lookup"><span data-stu-id="60ff6-288">The `Utf8JsonReader` is a foundational, low-level type, that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="60ff6-289">使用新的 `Utf8JsonReader` 來讀取 JSON 承載會比使用來自 **Json.NET** 的讀取器快兩倍。</span><span class="sxs-lookup"><span data-stu-id="60ff6-289">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="60ff6-290">它會等到您需要將 JSON 權杖實現為 (UTF-16) 字串時，才進行配置。</span><span class="sxs-lookup"><span data-stu-id="60ff6-290">It doesn't allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="60ff6-291">以下是完整閱讀 Visual Studio Code 所建立 [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) 檔案的範例：</span><span class="sxs-lookup"><span data-stu-id="60ff6-291">Here is an example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a><span data-ttu-id="60ff6-292">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="60ff6-292">Utf8JsonWriter</span></span>

<span data-ttu-id="60ff6-293"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> 提供高效能、非快取、僅轉接方式，從常見的 .NET 類型 (像是 `String`、`Int32` 和 `DateTime`) 撰寫 UTF-8 編碼的 JSON 文字。</span><span class="sxs-lookup"><span data-stu-id="60ff6-293"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="60ff6-294">如同讀取器，寫入器是一個基礎的低階類型，可用來建置自訂序列化程式。</span><span class="sxs-lookup"><span data-stu-id="60ff6-294">Like the reader, the writer is a foundational, low-level type, that can be used to build custom serializers.</span></span> <span data-ttu-id="60ff6-295">使用新的 `Utf8JsonWriter` 撰寫 JSON 承載，其速度比從 **Json.NET** 使用寫入器還要快 30-80%，且不會配置。</span><span class="sxs-lookup"><span data-stu-id="60ff6-295">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and doesn't allocate.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="60ff6-296">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="60ff6-296">JsonDocument</span></span>

<span data-ttu-id="60ff6-297"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> 是組建在 `Utf8JsonReader` 之上。</span><span class="sxs-lookup"><span data-stu-id="60ff6-297"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="60ff6-298">`JsonDocument` 可讓您剖析 JSON 資料和組建唯讀文件物件模型 (DOM)，而您可以查詢此模型來支援隨機存取和列舉。</span><span class="sxs-lookup"><span data-stu-id="60ff6-298">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="60ff6-299">撰寫資料的 JSON 項目可以透過 <xref:System.Text.Json.JsonElement> 類型來存取，而此類型被 `JsonDocument` 公開為稱為 `RootElement` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="60ff6-299">The JSON elements that compose the data can be accessed via the <xref:System.Text.Json.JsonElement> type that is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="60ff6-300">`JsonElement` 包含 JSON 陣列和物件列舉程式，以及將 JSON 文字轉換為一般.NET 類型的 API。</span><span class="sxs-lookup"><span data-stu-id="60ff6-300">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="60ff6-301">使用 `JsonDocument` 剖析一般 JSON 承載，並存取其所有成員，速度比 **Json.NET** 還要快 2-3 倍，且極少配置合理大小 (亦即 < 1 MB) 的資料。</span><span class="sxs-lookup"><span data-stu-id="60ff6-301">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with little allocations for data that is reasonably sized (that is, < 1 MB).</span></span>

<span data-ttu-id="60ff6-302">以下是 `JsonDocument` 和 `JsonElement` 的使用方式樣本，其可作為起點：</span><span class="sxs-lookup"><span data-stu-id="60ff6-302">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

<span data-ttu-id="60ff6-303">以下是完整閱讀 Visual Studio Code 所建立 [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) 檔案的 C# 8.0 範例：</span><span class="sxs-lookup"><span data-stu-id="60ff6-303">Here is a C# 8.0 example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a><span data-ttu-id="60ff6-304">JsonSerializer</span><span class="sxs-lookup"><span data-stu-id="60ff6-304">JsonSerializer</span></span>

<span data-ttu-id="60ff6-305"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> 建置在 <xref:System.Text.Json.Utf8JsonReader> 和 <xref:System.Text.Json.Utf8JsonWriter> 之上，以在使用 JSON 文件和片段時，提供快速的低記憶體序列化選項。</span><span class="sxs-lookup"><span data-stu-id="60ff6-305"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> is built on top of <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter> to provide a fast low-memory serialization option when working with JSON documents and fragments.</span></span>

<span data-ttu-id="60ff6-306">查看： https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md 以取得要移植到本文的範例</span><span class="sxs-lookup"><span data-stu-id="60ff6-306">EXAMINE: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md for an example to port to this article</span></span>

<span data-ttu-id="60ff6-307">以下是將物件序列化成 JSON 的範例：</span><span class="sxs-lookup"><span data-stu-id="60ff6-307">Here is an example of serializing an object to JSON:</span></span>

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

<span data-ttu-id="60ff6-308">以下是將 JSON 字串還原序列化成物件的範例。</span><span class="sxs-lookup"><span data-stu-id="60ff6-308">Here is an example of deserializing a JSON string to an object.</span></span> <span data-ttu-id="60ff6-309">您可以使用上述範例所產生的 JSON 字串：</span><span class="sxs-lookup"><span data-stu-id="60ff6-309">You can use the JSON string produced by the previous example:</span></span>

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a><span data-ttu-id="60ff6-310">Interop 增強功能</span><span class="sxs-lookup"><span data-stu-id="60ff6-310">Interop improvements</span></span>

<span data-ttu-id="60ff6-311">.NET Core 3.0 改善原生 API Interop。</span><span class="sxs-lookup"><span data-stu-id="60ff6-311">.NET Core 3.0 improves native API interop.</span></span>

### <a name="type-nativelibrary"></a><span data-ttu-id="60ff6-312">類型：NativeLibrary</span><span class="sxs-lookup"><span data-stu-id="60ff6-312">Type: NativeLibrary</span></span>

<span data-ttu-id="60ff6-313"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> 提供封裝來載入原生程式庫 (使用與 .NET Core P/Invoke 相同的負載邏輯)，並提供相關的 Helper 函式 (例如 `getSymbol`)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-313"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> provides an encapsulation for loading a native library (using the same load logic as .NET Core P/Invoke) and providing the relevant helper functions such as `getSymbol`.</span></span> <span data-ttu-id="60ff6-314">如需程式碼範例，請參閱 [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin) (DLLMap 示範)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-314">For a code example, see the [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="60ff6-315">Windows 原生 Interop</span><span class="sxs-lookup"><span data-stu-id="60ff6-315">Windows Native Interop</span></span>

<span data-ttu-id="60ff6-316">Windows 提供豐富的原生 API，其採用的形式為一般 C API、COM 和 WinRT。</span><span class="sxs-lookup"><span data-stu-id="60ff6-316">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="60ff6-317">除了 .NET Core 3.0 支援 **P/Invoke** 之外，.NET Core 3.0 還新增 **CoCreate COM API** 和 **Activate WinRT API** 的功能。</span><span class="sxs-lookup"><span data-stu-id="60ff6-317">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="60ff6-318">如需程式碼範例，請參閱 [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo) (Excel 示範)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-318">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="http2-support"></a><span data-ttu-id="60ff6-319">HTTP/2 支援</span><span class="sxs-lookup"><span data-stu-id="60ff6-319">HTTP/2 support</span></span>

<span data-ttu-id="60ff6-320"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 類型支援 HTTP/2 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="60ff6-320">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="60ff6-321">目前停用支援，但可在使用 <xref:System.Net.Http.HttpClient> 之前呼叫 `AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2Support", true);` 來開啟。</span><span class="sxs-lookup"><span data-stu-id="60ff6-321">Support is currently disabled but can be turned on by calling `AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2Support", true);` before you use <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="60ff6-322">您也可以在執行應用程式之前將 `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` 環境變數設定為 `true` 來啟用 HTTP/2 支援。</span><span class="sxs-lookup"><span data-stu-id="60ff6-322">You can also enable HTTP/2 support by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` environment variable to `true` before you run your app.</span></span>

<span data-ttu-id="60ff6-323">如果啟用 HTTP/2，則會透過 TLS/ALPN 交涉 HTTP 通訊協定版本，且只有在伺服器選擇使用時才會使用 HTTP/2。</span><span class="sxs-lookup"><span data-stu-id="60ff6-323">If HTTP/2 is enabled, the HTTP protocol version will be negotiated via TLS/ALPN, and HTTP/2 will only be used if the server selects to use it.</span></span>

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="60ff6-324">Linux 上的 TLS 1.3 和 OpenSSL 1.1.1</span><span class="sxs-lookup"><span data-stu-id="60ff6-324">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="60ff6-325">.NET Core 現在會利用 [OpenSSL 1.1.1 中的 TLS 1.3 支援](https://www.openssl.org/blog/blog/2018/09/11/release111/) (當在指定的環境中有提供時)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-325">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="60ff6-326">透過 TLS 1.3：</span><span class="sxs-lookup"><span data-stu-id="60ff6-326">With TLS 1.3:</span></span>

* <span data-ttu-id="60ff6-327">因為用戶端與伺服器之間所需的來回行程次數減少，所以改善了連線時間。</span><span class="sxs-lookup"><span data-stu-id="60ff6-327">Connection times are improved with reduced round trips required between the client and server.</span></span>
* <span data-ttu-id="60ff6-328">因為移除各種已淘汰和不安全的密碼編譯演算法，所以提升了安全性。</span><span class="sxs-lookup"><span data-stu-id="60ff6-328">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="60ff6-329">.NET Core 3.0 在 Linux 系統上使用 **OpenSSL 1.1.1**、**OpenSSL 1.1.0** 或 **OpenSSL 1.0.2** (若可供使用)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-329">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="60ff6-330">當 **OpenSSL 1.1.1** 可供使用時，<xref:System.Net.Security.SslStream?displayProperty=nameWithType> 和 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 類型就會使用 **TLS 1.3** (假設用戶端和伺服器都支援 **TLS 1.3**)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-330">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="60ff6-331">Windows 和 macOS 尚未支援 **TLS 1.3**。</span><span class="sxs-lookup"><span data-stu-id="60ff6-331">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="60ff6-332">.NET Core 3.0 將在有支援可用時，在這些作業系統上支援 **TLS 1.3**。</span><span class="sxs-lookup"><span data-stu-id="60ff6-332">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="60ff6-333">下列 C# 8.0 範例示範連線至 <https://www.cloudflare.com> 之 Ubuntu 18.10 上的 .NET Core 3.0：</span><span class="sxs-lookup"><span data-stu-id="60ff6-333">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a><span data-ttu-id="60ff6-334">密碼編譯加密方式</span><span class="sxs-lookup"><span data-stu-id="60ff6-334">Cryptography ciphers</span></span>

<span data-ttu-id="60ff6-335">.NET 3.0 新增對 **AES-GCM** 和 **AES-CCM** 加密方式的支援，分別透過 <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> 和 <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> 來實作。</span><span class="sxs-lookup"><span data-stu-id="60ff6-335">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="60ff6-336">這些演算法都是[搭配關聯資料的驗證加密 (AEAD) 演算法](https://en.wikipedia.org/wiki/Authenticated_encryption)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-336">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="60ff6-337">下列程式碼示範如何使用 `AesGcm` 加密方式將隨機資料加密和解密。</span><span class="sxs-lookup"><span data-stu-id="60ff6-337">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="60ff6-338">密碼編譯金鑰匯入/匯出</span><span class="sxs-lookup"><span data-stu-id="60ff6-338">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="60ff6-339">.NET Core 3.0 支援從標準格式匯入及匯出非對稱式公開金鑰與私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="60ff6-339">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="60ff6-340">您無須使用 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="60ff6-340">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="60ff6-341">所有金鑰類型 (例如 *RSA*、*DSA*、*ECDsa* 和 *ECDiffieHellman*) 都支援下列格式：</span><span class="sxs-lookup"><span data-stu-id="60ff6-341">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

* <span data-ttu-id="60ff6-342">**公開金鑰**</span><span class="sxs-lookup"><span data-stu-id="60ff6-342">**Public Key**</span></span>
  * <span data-ttu-id="60ff6-343">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="60ff6-343">X.509 SubjectPublicKeyInfo</span></span>

* <span data-ttu-id="60ff6-344">**私密金鑰**</span><span class="sxs-lookup"><span data-stu-id="60ff6-344">**Private key**</span></span>
  * <span data-ttu-id="60ff6-345">PKCS#8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="60ff6-345">PKCS#8 PrivateKeyInfo</span></span>
  * <span data-ttu-id="60ff6-346">PKCS#8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="60ff6-346">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="60ff6-347">RSA 金鑰也支援：</span><span class="sxs-lookup"><span data-stu-id="60ff6-347">RSA keys also support:</span></span>

* <span data-ttu-id="60ff6-348">**公開金鑰**</span><span class="sxs-lookup"><span data-stu-id="60ff6-348">**Public Key**</span></span>
  * <span data-ttu-id="60ff6-349">PKCS#1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="60ff6-349">PKCS#1 RSAPublicKey</span></span>

* <span data-ttu-id="60ff6-350">**私密金鑰**</span><span class="sxs-lookup"><span data-stu-id="60ff6-350">**Private key**</span></span>
  * <span data-ttu-id="60ff6-351">PKCS#1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="60ff6-351">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="60ff6-352">匯出方法會產生 DER 編碼的二進位資料，而匯入方法也是如此。</span><span class="sxs-lookup"><span data-stu-id="60ff6-352">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="60ff6-353">如果金鑰是以適合文字的 PEM 格式儲存的，呼叫端在呼叫匯入方法之前，就必須先對內容進行 Base64 解碼。</span><span class="sxs-lookup"><span data-stu-id="60ff6-353">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="60ff6-354">**PKCS#8** 檔案可以使用 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> 來檢查，而 **PFX/PKCS#12** 檔案可以使用 <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType> 來檢查。</span><span class="sxs-lookup"><span data-stu-id="60ff6-354">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="60ff6-355">**PFX/PKCS#12** 檔案可以使用 <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType> 來操作。</span><span class="sxs-lookup"><span data-stu-id="60ff6-355">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="60ff6-356">適用於 Linux 的 SerialPort</span><span class="sxs-lookup"><span data-stu-id="60ff6-356">SerialPort for Linux</span></span>

<span data-ttu-id="60ff6-357">.NET Core 3.0 在 Linux 上支援 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="60ff6-357">.NET Core 3.0 supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="60ff6-358">先前，.NET Core 僅支援在 Windows 上使用 `SerialPort`。</span><span class="sxs-lookup"><span data-stu-id="60ff6-358">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

## <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="60ff6-359">Docker 和 cgroup 記憶體限制</span><span class="sxs-lookup"><span data-stu-id="60ff6-359">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="60ff6-360">從 Preview 3 開始，在 Linux 上執行 .NET Core 3.0 和 Docker 搭配 cgroup 記憶體限制的效果最佳。</span><span class="sxs-lookup"><span data-stu-id="60ff6-360">Starting with Preview 3, running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="60ff6-361">使用記憶體限制 (例如使用 `docker run -m`) 執行 Docker 容器會變更 .NET Core 的運作方式。</span><span class="sxs-lookup"><span data-stu-id="60ff6-361">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

* <span data-ttu-id="60ff6-362">預設記憶體回收行程 (GC) 堆積大小：上限為 20 MB，或容器上 75% 的記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="60ff6-362">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
* <span data-ttu-id="60ff6-363">可將明確大小設定為 cgroup 限制的絕對數目或百分比。</span><span class="sxs-lookup"><span data-stu-id="60ff6-363">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
* <span data-ttu-id="60ff6-364">每個 GC 堆積的保留區段大小下限為 16 MB。</span><span class="sxs-lookup"><span data-stu-id="60ff6-364">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="60ff6-365">此大小可減少電腦上所建立的堆積數目。</span><span class="sxs-lookup"><span data-stu-id="60ff6-365">This size reduces the number of heaps that are created on machines.</span></span>

## <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="60ff6-366">較小的記憶體回收堆積大小</span><span class="sxs-lookup"><span data-stu-id="60ff6-366">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="60ff6-367">已減少記憶體回收行程的預設堆積大小，而導致 .NET Core 使用較少的記憶體。</span><span class="sxs-lookup"><span data-stu-id="60ff6-367">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="60ff6-368">這項變更較符合使用新式處理器快取大小的層代 0 配置預算。</span><span class="sxs-lookup"><span data-stu-id="60ff6-368">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

## <a name="garbage-collection-large-page-support"></a><span data-ttu-id="60ff6-369">記憶體回收大型頁面支援</span><span class="sxs-lookup"><span data-stu-id="60ff6-369">Garbage Collection Large Page support</span></span>

<span data-ttu-id="60ff6-370">大型頁面 (Large Page，在 Linux 上又稱為 Huge Page) 是一項功能，其中作業系統能夠建立大於原生頁面大小 (通常為 4K) 的記憶體區域，以提升要求這些大型頁面的應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="60ff6-370">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="60ff6-371">記憶體回收行程現在可以設定 **GCLargePages** 設定作為選擇性功能，來選擇在 Windows 上配置大型頁面。</span><span class="sxs-lookup"><span data-stu-id="60ff6-371">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="60ff6-372">Raspberry Pi 的 GPIO 支援</span><span class="sxs-lookup"><span data-stu-id="60ff6-372">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="60ff6-373">兩個套件已發佈至您可以用於 GPIO 程式設計的 NuGet：</span><span class="sxs-lookup"><span data-stu-id="60ff6-373">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

* [<span data-ttu-id="60ff6-374">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="60ff6-374">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
* [<span data-ttu-id="60ff6-375">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="60ff6-375">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="60ff6-376">GPIO 套件包含 *GPIO*、*SPI*、*I2C* 和 *PWM* 裝置的 API。</span><span class="sxs-lookup"><span data-stu-id="60ff6-376">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="60ff6-377">IoT 繫結套件包含裝置繫結。</span><span class="sxs-lookup"><span data-stu-id="60ff6-377">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="60ff6-378">如需詳細資訊，請參閱[裝置 GitHub 存放庫](https://github.com/dotnet/iot/blob/master/src/devices/)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-378">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="60ff6-379">ARM64 Linux 支援</span><span class="sxs-lookup"><span data-stu-id="60ff6-379">ARM64 Linux support</span></span>

<span data-ttu-id="60ff6-380">.NET Core 3.0 新增 ARM64 for Linux 的支援。</span><span class="sxs-lookup"><span data-stu-id="60ff6-380">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="60ff6-381">ARM64 的主要使用案例目前是搭配 IoT 案例。</span><span class="sxs-lookup"><span data-stu-id="60ff6-381">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="60ff6-382">如需詳細資訊，請參閱 [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) (.NET Core ARM64 狀態)。</span><span class="sxs-lookup"><span data-stu-id="60ff6-382">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="60ff6-383">[ARM64 上適用於 .NET Core 的 Docker 映像](https://hub.docker.com/r/microsoft/dotnet/)可供 Alpine、Debian 和 Ubuntu 使用。</span><span class="sxs-lookup"><span data-stu-id="60ff6-383">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="60ff6-384">目前尚未提供 **ARM64** Windows 支援。</span><span class="sxs-lookup"><span data-stu-id="60ff6-384">**ARM64** Windows support isn't yet available.</span></span>
