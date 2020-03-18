---
title: 使用 .NET 核心 CLI 開發庫
description: 瞭解如何使用 .NET 核心 CLI 創建 .NET 核心庫。 您將建立支援多個架構的程式庫。
author: cartermp
ms.date: 05/01/2017
ms.openlocfilehash: c23c1f027b4d6d09c50eb2257d34f72ec56302f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503503"
---
# <a name="develop-libraries-with-the-net-core-cli"></a><span data-ttu-id="211e6-104">使用 .NET 核心 CLI 開發庫</span><span class="sxs-lookup"><span data-stu-id="211e6-104">Develop libraries with the .NET Core CLI</span></span>

<span data-ttu-id="211e6-105">本文介紹如何使用 .NET 核心 CLI 為 .NET 編寫庫。</span><span class="sxs-lookup"><span data-stu-id="211e6-105">This article covers how to write libraries for .NET using the .NET Core CLI.</span></span> <span data-ttu-id="211e6-106">CLI 提供可在所有支援的作業系統上運作的有效率且低階體驗。</span><span class="sxs-lookup"><span data-stu-id="211e6-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="211e6-107">您仍然可以使用 Visual Studio 來建置程式庫，而且，如果那是您偏好的體驗，[請參閱 Visual Studio 指南](library-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="211e6-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="211e6-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="211e6-108">Prerequisites</span></span>

<span data-ttu-id="211e6-109">您需要在電腦上安裝 [.NET Core SDK 和 CLI](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="211e6-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="211e6-110">針對這份文件中處理 .NET Framework 版本的一節，您需要在 Windows 電腦上安裝 [.NET Framework](https://dotnet.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="211e6-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="211e6-111">此外，如果您希望支援較舊的 .NET 框架目標，則需要從[.NET 下載存檔頁](https://dotnet.microsoft.com/download/archives)安裝目標包或開發人員包。</span><span class="sxs-lookup"><span data-stu-id="211e6-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="211e6-112">請參閱這張表格︰</span><span class="sxs-lookup"><span data-stu-id="211e6-112">Refer to this table:</span></span>

| <span data-ttu-id="211e6-113">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="211e6-113">.NET Framework version</span></span> | <span data-ttu-id="211e6-114">要下載的項目</span><span class="sxs-lookup"><span data-stu-id="211e6-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="211e6-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="211e6-115">4.6.1</span></span>                  | <span data-ttu-id="211e6-116">.NET Framework 4.6.1 目標套件</span><span class="sxs-lookup"><span data-stu-id="211e6-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="211e6-117">4.6</span><span class="sxs-lookup"><span data-stu-id="211e6-117">4.6</span></span>                    | <span data-ttu-id="211e6-118">.NET Framework 4.6 目標套件</span><span class="sxs-lookup"><span data-stu-id="211e6-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="211e6-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="211e6-119">4.5.2</span></span>                  | <span data-ttu-id="211e6-120">.NET Framework 4.5.2 開發人員套件</span><span class="sxs-lookup"><span data-stu-id="211e6-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="211e6-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="211e6-121">4.5.1</span></span>                  | <span data-ttu-id="211e6-122">.NET Framework 4.5.1 開發人員套件</span><span class="sxs-lookup"><span data-stu-id="211e6-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="211e6-123">4.5</span><span class="sxs-lookup"><span data-stu-id="211e6-123">4.5</span></span>                    | <span data-ttu-id="211e6-124">適用於 Windows 8 的 Windows 軟體開發套件</span><span class="sxs-lookup"><span data-stu-id="211e6-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="211e6-125">4.0</span><span class="sxs-lookup"><span data-stu-id="211e6-125">4.0</span></span>                    | <span data-ttu-id="211e6-126">適用於 Windows 7 的 Windows SDK 及 .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="211e6-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="211e6-127">2.0、3.0 和 3.5</span><span class="sxs-lookup"><span data-stu-id="211e6-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="211e6-128">.NET Framework 3.5 SP1 執行階段 (或 Windows 8+ 版本)</span><span class="sxs-lookup"><span data-stu-id="211e6-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="211e6-129">如何將目標設為 .NET Standard</span><span class="sxs-lookup"><span data-stu-id="211e6-129">How to target the .NET Standard</span></span>

<span data-ttu-id="211e6-130">如果您不熟悉 .NET 標準，請參閱[.NET 標準](../../standard/net-standard.md)以瞭解更多資訊。</span><span class="sxs-lookup"><span data-stu-id="211e6-130">If you're not familiar with .NET Standard, refer to [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="211e6-131">在該文章中，有一個表將 .NET 標準版本映射到各種實現：</span><span class="sxs-lookup"><span data-stu-id="211e6-131">In that article, there is a table that maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="211e6-132">以下是這個資料表在建立程式庫時的意義︰</span><span class="sxs-lookup"><span data-stu-id="211e6-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="211e6-133">您選擇的 .NET 標準版本將是訪問最新 API 和定位更多 .NET 實現和 .NET 標準版本的能力之間的權衡。</span><span class="sxs-lookup"><span data-stu-id="211e6-133">The version of .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="211e6-134">通過選擇`netstandardX.X`版本號（其中`X.X`版本號）並將其添加到專案檔案（`.csproj`或`.fsproj`）的版本，可以控制目標平臺和版本的範圍。</span><span class="sxs-lookup"><span data-stu-id="211e6-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="211e6-135">根據您的需求，在定位 .NET 標準時，您有三個主要選項。</span><span class="sxs-lookup"><span data-stu-id="211e6-135">You have three primary options when targeting .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="211e6-136">您可以使用範本提供的 .NET 標準的預設版本 ，`netstandard1.4`它允許您訪問 .NET 標準上的大多數 API，同時仍與 UWP、.NET 框架 4.6.1 和 .NET 標準 2.0 相容。</span><span class="sxs-lookup"><span data-stu-id="211e6-136">You can use the default version of .NET Standard supplied by templates, `netstandard1.4`, which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="211e6-137">您可以通過修改專案檔案`TargetFramework`節點中的值來使用較低版本或更高版本的 .NET 標準。</span><span class="sxs-lookup"><span data-stu-id="211e6-137">You can use a lower or higher version of .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="211e6-138">.NET Standard 版本具備回溯相容。</span><span class="sxs-lookup"><span data-stu-id="211e6-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="211e6-139">這表示 `netstandard1.0` 程式庫是在 `netstandard1.1` 平台和更高版本上執行。</span><span class="sxs-lookup"><span data-stu-id="211e6-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="211e6-140">但是，沒有正向相容性。</span><span class="sxs-lookup"><span data-stu-id="211e6-140">However, there is no forward compatibility.</span></span> <span data-ttu-id="211e6-141">下部 .NET 標準平臺不能引用較高的平臺。</span><span class="sxs-lookup"><span data-stu-id="211e6-141">Lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="211e6-142">這表示 `netstandard1.0` 程式庫無法參考目標設為 `netstandard1.1` 或更高版本的程式庫。</span><span class="sxs-lookup"><span data-stu-id="211e6-142">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="211e6-143">針對您的需求，選取正確混合使用 API 與平台支援的標準版本。</span><span class="sxs-lookup"><span data-stu-id="211e6-143">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="211e6-144">現在建議使用 `netstandard1.4`。</span><span class="sxs-lookup"><span data-stu-id="211e6-144">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="211e6-145">如果要以 .NET 框架版本 4.0 或以下為目標，或者希望使用 .NET 框架中可用的 API，但不希望在 .NET`System.Drawing`標準（例如），請閱讀以下各節並瞭解如何多目標。</span><span class="sxs-lookup"><span data-stu-id="211e6-145">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="211e6-146">如何定位 .NET 框架</span><span class="sxs-lookup"><span data-stu-id="211e6-146">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="211e6-147">這些說明假定您的電腦上安裝了 .NET 框架。</span><span class="sxs-lookup"><span data-stu-id="211e6-147">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="211e6-148">請參閱安裝相依性的[必要條件](#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="211e6-148">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="211e6-149">請記住，此處使用的一些 .NET 框架版本不再受支援。</span><span class="sxs-lookup"><span data-stu-id="211e6-149">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="211e6-150">如需不支援的版本，請參閱 [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) (.NET Framework 支援週期原則 FAQ)。</span><span class="sxs-lookup"><span data-stu-id="211e6-150">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="211e6-151">如果要達到開發人員和專案的最大數量，請使用 .NET 框架 4.0 作為基準目標。</span><span class="sxs-lookup"><span data-stu-id="211e6-151">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="211e6-152">要定位 .NET 框架，首先使用與您希望支援 .NET 框架版本對應的正確目標框架 Moniker （TFM）。</span><span class="sxs-lookup"><span data-stu-id="211e6-152">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="211e6-153">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="211e6-153">.NET Framework version</span></span> | <span data-ttu-id="211e6-154">TFM</span><span class="sxs-lookup"><span data-stu-id="211e6-154">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="211e6-155">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="211e6-155">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="211e6-156">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="211e6-156">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="211e6-157">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="211e6-157">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="211e6-158">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="211e6-158">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="211e6-159">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="211e6-159">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="211e6-160">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="211e6-160">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="211e6-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="211e6-161">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="211e6-162">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="211e6-162">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="211e6-163">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="211e6-163">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="211e6-164">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="211e6-164">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="211e6-165">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="211e6-165">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="211e6-166">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="211e6-166">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="211e6-167">您接著將這個 TFM 插入專案檔的 `TargetFramework` 區段。</span><span class="sxs-lookup"><span data-stu-id="211e6-167">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="211e6-168">例如，下面介紹如何編寫以 .NET 框架 4.0 為目標的庫：</span><span class="sxs-lookup"><span data-stu-id="211e6-168">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="211e6-169">就這麼簡單！</span><span class="sxs-lookup"><span data-stu-id="211e6-169">And that's it!</span></span> <span data-ttu-id="211e6-170">儘管此僅為 .NET 框架 4 編譯，但您可以在較新版本的 .NET Framework 上使用庫。</span><span class="sxs-lookup"><span data-stu-id="211e6-170">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="211e6-171">如何多目標</span><span class="sxs-lookup"><span data-stu-id="211e6-171">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="211e6-172">下列指示假設您已在電腦上安裝 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="211e6-172">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="211e6-173">請參閱[必要條件](#prerequisites)小節，了解您需要安裝的相依性以及其下載位置。</span><span class="sxs-lookup"><span data-stu-id="211e6-173">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="211e6-174">當您的專案同時支援 .NET Framework 和 .NET Core 時，可能需要將目標設為舊版 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="211e6-174">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="211e6-175">在這個案例中，如果您想要為較新的目標使用較新的 API 和語言建構，請在程式碼中使用 `#if` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="211e6-175">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="211e6-176">您也可能需要針對設為目標的每個平台新增不同的套件和相依性，以包含每個案例所需的不同 API。</span><span class="sxs-lookup"><span data-stu-id="211e6-176">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="211e6-177">例如，假設您的程式庫透過 HTTP 執行網路作業。</span><span class="sxs-lookup"><span data-stu-id="211e6-177">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="211e6-178">針對 .NET Standard 和 .NET Framework 4.5 版或更高版本，您可以使用 `System.Net.Http` 命名空間中的 `HttpClient` 類別。</span><span class="sxs-lookup"><span data-stu-id="211e6-178">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="211e6-179">不過，舊版 .NET Framework 沒有 `HttpClient` 類別，因此您可以改用這些項目之 `System.Net` 命名空間中的 `WebClient` 類別。</span><span class="sxs-lookup"><span data-stu-id="211e6-179">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="211e6-180">專案檔如下所示：</span><span class="sxs-lookup"><span data-stu-id="211e6-180">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="211e6-181">您可在這裡發現三個主要變更︰</span><span class="sxs-lookup"><span data-stu-id="211e6-181">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="211e6-182">`TargetFramework` 節點已取代為 `TargetFrameworks`，而且其內表示三個 TFM。</span><span class="sxs-lookup"><span data-stu-id="211e6-182">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="211e6-183">提取至一個 .NET Framework 參考的 `net40` 目標有一個 `<ItemGroup>` 節點。</span><span class="sxs-lookup"><span data-stu-id="211e6-183">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="211e6-184">提取至兩個 .NET Framework 參考的 `net45` 目標有一個 `<ItemGroup>` 節點。</span><span class="sxs-lookup"><span data-stu-id="211e6-184">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="211e6-185">建置系統會得知 `#if` 指示詞中所使用的下列前置處理器符號︰</span><span class="sxs-lookup"><span data-stu-id="211e6-185">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="211e6-186">以下是利用個別目標之條件式編譯的範例︰</span><span class="sxs-lookup"><span data-stu-id="211e6-186">Here is an example making use of conditional compilation per-target:</span></span>

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "https://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="211e6-187">如果您使用 `dotnet build` 建置此專案，則會在 `bin/` 資料夾下方發現三個目錄：</span><span class="sxs-lookup"><span data-stu-id="211e6-187">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="211e6-188">所有這些都包含每個目標的 `.dll` 檔案。</span><span class="sxs-lookup"><span data-stu-id="211e6-188">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="211e6-189">如何測試 .NET Core 上的程式庫</span><span class="sxs-lookup"><span data-stu-id="211e6-189">How to test libraries on .NET Core</span></span>

<span data-ttu-id="211e6-190">重要的是一定要可以跨平台進行測試。</span><span class="sxs-lookup"><span data-stu-id="211e6-190">It's important to be able to test across platforms.</span></span> <span data-ttu-id="211e6-191">您可以使用現成的 [xUnit](https://xunit.github.io/) 或 MSTest。</span><span class="sxs-lookup"><span data-stu-id="211e6-191">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="211e6-192">兩者都完全適用於在 .NET Core 上對程式庫進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="211e6-192">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="211e6-193">如何設定具有測試專案的方案，將取決於[方案結構](#structuring-a-solution)。</span><span class="sxs-lookup"><span data-stu-id="211e6-193">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="211e6-194">下列範例假設測試及來源目錄位於相同的最上層目錄中。</span><span class="sxs-lookup"><span data-stu-id="211e6-194">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="211e6-195">這使用一些[.NET 核心 CLI](../tools/index.md)命令。</span><span class="sxs-lookup"><span data-stu-id="211e6-195">This uses some [.NET Core CLI](../tools/index.md) commands.</span></span> <span data-ttu-id="211e6-196">如需詳細資訊，請參閱 [dotnet new](../tools/dotnet-new.md) 及 [dotnet sln](../tools/dotnet-sln.md)。</span><span class="sxs-lookup"><span data-stu-id="211e6-196">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="211e6-197">設定方案。</span><span class="sxs-lookup"><span data-stu-id="211e6-197">Set up your solution.</span></span> <span data-ttu-id="211e6-198">您可以使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="211e6-198">You can do so with the following commands:</span></span>

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="211e6-199">這會建立專案，並將它們同時連結在方案中。</span><span class="sxs-lookup"><span data-stu-id="211e6-199">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="211e6-200">您的 `SolutionWithSrcAndTest` 目錄應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="211e6-200">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="211e6-201">巡覽至測試專案的目錄，並將參考從 `MyProject` 新增至 `MyProject.Test`。</span><span class="sxs-lookup"><span data-stu-id="211e6-201">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="211e6-202">還原套件並建置專案︰</span><span class="sxs-lookup"><span data-stu-id="211e6-202">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="211e6-203">執行 `dotnet test` 命令，確認已執行 xUnit。</span><span class="sxs-lookup"><span data-stu-id="211e6-203">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="211e6-204">如果您選擇使用 MSTest，則應該會改為執行 MSTest 主控台執行器。</span><span class="sxs-lookup"><span data-stu-id="211e6-204">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="211e6-205">就這麼簡單！</span><span class="sxs-lookup"><span data-stu-id="211e6-205">And that's it!</span></span> <span data-ttu-id="211e6-206">現在，您可以使用命令列工具跨所有平臺測試庫。</span><span class="sxs-lookup"><span data-stu-id="211e6-206">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="211e6-207">若要在設定好所有項目之後立即繼續測試，測試程式庫就會非常簡單︰</span><span class="sxs-lookup"><span data-stu-id="211e6-207">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="211e6-208">對程式庫進行變更。</span><span class="sxs-lookup"><span data-stu-id="211e6-208">Make changes to your library.</span></span>
1. <span data-ttu-id="211e6-209">在測試目錄中，從命令列中使用 `dotnet test` 命令來執行測試。</span><span class="sxs-lookup"><span data-stu-id="211e6-209">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="211e6-210">當您叫用 `dotnet test` 命令時，將會自動重建程式碼。</span><span class="sxs-lookup"><span data-stu-id="211e6-210">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="211e6-211">如何使用多個專案</span><span class="sxs-lookup"><span data-stu-id="211e6-211">How to use multiple projects</span></span>

<span data-ttu-id="211e6-212">較大程式庫的常見需求是將功能放在不同的專案中。</span><span class="sxs-lookup"><span data-stu-id="211e6-212">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="211e6-213">假設您要構建一個可以在慣用 C# 和 F# 中使用的庫。</span><span class="sxs-lookup"><span data-stu-id="211e6-213">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="211e6-214">這意味著庫的消費者會以 C# 或 F# 自然的方式使用它。</span><span class="sxs-lookup"><span data-stu-id="211e6-214">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="211e6-215">例如，在 C# 中，您可能會如下使用程式庫︰</span><span class="sxs-lookup"><span data-stu-id="211e6-215">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="211e6-216">在 F# 中，它可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="211e6-216">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="211e6-217">這類使用案例表示針對 C# 和 F#，正在存取的 API 必須具有不同的結構。</span><span class="sxs-lookup"><span data-stu-id="211e6-217">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="211e6-218">完成這項作業的常見方法將程式庫的所有邏輯都納入核心專案，而且 C# 和 F# 專案定義呼叫該核心專案的 API 層。</span><span class="sxs-lookup"><span data-stu-id="211e6-218">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="211e6-219">區段的其餘部分將使用下列名稱︰</span><span class="sxs-lookup"><span data-stu-id="211e6-219">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="211e6-220">**真棒庫.Core** - 包含庫所有邏輯的核心專案</span><span class="sxs-lookup"><span data-stu-id="211e6-220">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="211e6-221">**真棒庫.CSharp** - 一個公共 API 的專案，旨在用於 C 中使用#</span><span class="sxs-lookup"><span data-stu-id="211e6-221">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="211e6-222">**真棒庫.FSharp** - 一個公共 API 的專案，用於在 F 中使用#</span><span class="sxs-lookup"><span data-stu-id="211e6-222">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="211e6-223">您可以在終端機中執行下列命令，以產生與本指南相同的結構︰</span><span class="sxs-lookup"><span data-stu-id="211e6-223">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```dotnetcli
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="211e6-224">這將添加上述三個專案以及一個將它們連結在一起的解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="211e6-224">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="211e6-225">創建解決方案檔和連結專案將允許您從頂層還原和生成專案。</span><span class="sxs-lookup"><span data-stu-id="211e6-225">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="211e6-226">專案對專案參考</span><span class="sxs-lookup"><span data-stu-id="211e6-226">Project-to-project referencing</span></span>

<span data-ttu-id="211e6-227">參考專案的最佳方式是使用 .NET Core CLI 來新增專案參考。</span><span class="sxs-lookup"><span data-stu-id="211e6-227">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="211e6-228">從 **AwesomeLibrary.CSharp** 及 **AwesomeLibrary.FSharp** 專案目錄中，您可以執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="211e6-228">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="211e6-229">**AwesomeLibrary.CSharp** 及 **AwesomeLibrary.FSharp** 的專案檔現在參考 **AwesomeLibrary.Core** 作為 `ProjectReference` 目標。</span><span class="sxs-lookup"><span data-stu-id="211e6-229">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="211e6-230">檢查專案檔並查看其中的下列內容，即可確認這項作業︰</span><span class="sxs-lookup"><span data-stu-id="211e6-230">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="211e6-231">如果您不想要使用 .NET Core CLI，則可以手動將這個區段新增至每個專案檔。</span><span class="sxs-lookup"><span data-stu-id="211e6-231">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="211e6-232">建構方案</span><span class="sxs-lookup"><span data-stu-id="211e6-232">Structuring a solution</span></span>

<span data-ttu-id="211e6-233">多專案方案的另一個重要部分是建立不錯的整體專案結構。</span><span class="sxs-lookup"><span data-stu-id="211e6-233">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="211e6-234">不過，您可以視需要組織程式碼，而且只要您使用 `dotnet sln add` 將每個專案連結至方案檔，就可以在方案層級執行 `dotnet restore` 及 `dotnet build`。</span><span class="sxs-lookup"><span data-stu-id="211e6-234">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
