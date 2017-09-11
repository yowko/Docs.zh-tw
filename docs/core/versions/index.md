---
title: ".NET Core 版本控制"
description: "了解 .NET Core 的版本控制運作方式。"
author: bleroy
ms.author: mairaw
ms.date: 08/25/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: f6f684b1-1d2c-4105-8376-7c1959e23803
ms.translationtype: HT
ms.sourcegitcommit: 02cfb7708959057de593506db55e4f31f5ab4fd0
ms.openlocfilehash: 48343ad8d42ad576b1975e81cd764b4ec6f5bc76
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="net-core-versioning"></a><span data-ttu-id="41c39-103">.NET Core 版本控制</span><span class="sxs-lookup"><span data-stu-id="41c39-103">.NET Core versioning</span></span>

<span data-ttu-id="41c39-104">.NET Core 是由 [NuGet 套件](../packages.md)、工具及發佈為一個單位的架構所構成。</span><span class="sxs-lookup"><span data-stu-id="41c39-104">.NET Core is made of [NuGet packages](../packages.md), tools, and frameworks that are distributed as a unit.</span></span> <span data-ttu-id="41c39-105">每一個平台層級都可以分別建立版本，以取得更好的靈活度。</span><span class="sxs-lookup"><span data-stu-id="41c39-105">Each of these platform layers can be versioned separately, enabling better agility.</span></span> <span data-ttu-id="41c39-106">雖然這樣有顯著的版本控制彈性，但還是希望能將平台當作一個單位來建立版本，讓產品更容易了解。</span><span class="sxs-lookup"><span data-stu-id="41c39-106">While there is significant versioning flexibility in that regard, there's also a desire to version the platform as a unit to make the product easier to understand.</span></span>

<span data-ttu-id="41c39-107">本文旨在釐清 .NET Core SDK 和執行階段如何建立版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-107">This article aims at clarifying how the .NET Core SDK and runtime are versioned.</span></span>

<span data-ttu-id="41c39-108">.NET Core 中有許多活動的組件可獨立建立版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-108">There are lots of moving parts that version independently in .NET Core.</span></span> <span data-ttu-id="41c39-109">不過，從 .NET Core 2.0 開始，有一個大家都很容易明白的最上層版本號碼，就是 *".NET Core"*。</span><span class="sxs-lookup"><span data-stu-id="41c39-109">However, starting with .NET Core 2.0, there is an easy to understand top-level version number that everybody understands to be *the* version of ".NET Core" as a whole.</span></span> <span data-ttu-id="41c39-110">這份文件的其餘部分會深入說明所有這些組件的版本控制。</span><span class="sxs-lookup"><span data-stu-id="41c39-110">The rest of this document goes into the details of the versioning of all those parts.</span></span> <span data-ttu-id="41c39-111">假如您是套件管理員，這些詳細資料就很重要。</span><span class="sxs-lookup"><span data-stu-id="41c39-111">These details can be important if you're a package manager, for example.</span></span>

## <a name="versioning-details"></a><span data-ttu-id="41c39-112">版本控制的詳細資料</span><span class="sxs-lookup"><span data-stu-id="41c39-112">Versioning details</span></span>

<span data-ttu-id="41c39-113">從 .NET Core 2.0 開始，下載在其檔案名稱中只顯示單一版本號碼。</span><span class="sxs-lookup"><span data-stu-id="41c39-113">Starting with .NET Core 2.0, downloads show a single version number in their file name.</span></span> <span data-ttu-id="41c39-114">統一下列版本號碼：</span><span class="sxs-lookup"><span data-stu-id="41c39-114">The following version numbers were unified:</span></span>

* <span data-ttu-id="41c39-115">共用的架構和相關聯的執行階段。</span><span class="sxs-lookup"><span data-stu-id="41c39-115">The shared framework and associated runtime.</span></span>
* <span data-ttu-id="41c39-116">.NET Core SDK 和相關聯的 .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="41c39-116">The .NET Core SDK and associated .NET Core CLI.</span></span>
* <span data-ttu-id="41c39-117">`Microsoft.NETCore.App` 中繼套件。</span><span class="sxs-lookup"><span data-stu-id="41c39-117">The `Microsoft.NETCore.App` metapackage.</span></span>

<span data-ttu-id="41c39-118">使用單一版本號碼可讓使用者更容易了解在開發電腦上要安裝的 SDK 版本，以及佈建到生產環境時，應該使用的共用架構對應版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-118">The use of a single version number makes it easier for users to know what version of the SDK to install on their dev machines, and what the corresponding version of the shared framework should be when time comes to provision a production environment.</span></span> <span data-ttu-id="41c39-119">下載 SDK 或執行階段時，您看到的版本號碼就會是相同的。</span><span class="sxs-lookup"><span data-stu-id="41c39-119">When downloading an SDK or runtime, the version number you see is going to be the same.</span></span>

### <a name="installers"></a><span data-ttu-id="41c39-120">安裝程式</span><span class="sxs-lookup"><span data-stu-id="41c39-120">Installers</span></span>

<span data-ttu-id="41c39-121">從 .NET Core 2.0 開始，[Daily Builds](https://github.com/dotnet/core-setup#daily-builds) (每日組建) 和[版本](https://www.microsoft.com/net/download/core)的下載會沿用容易了解的新命名配置。</span><span class="sxs-lookup"><span data-stu-id="41c39-121">Starting with .NET Core 2.0, downloads for our [daily builds](https://github.com/dotnet/core-setup#daily-builds) and [our releases](https://www.microsoft.com/net/download/core) adhere to a new naming scheme that is easier to understand.</span></span>
<span data-ttu-id="41c39-122">這些下載的安裝程式 UI 也經過修改，以清楚呈現要安裝元件的名稱和版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-122">The installer UI in those downloads were also modified to clearly present the names and versions of the components being installed.</span></span> <span data-ttu-id="41c39-123">特別是，標題現在在下載檔案名稱中會顯示相同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="41c39-123">In particular, titles now show the same version number that is in the download's file name.</span></span>

#### <a name="file-name-format"></a><span data-ttu-id="41c39-124">檔案名稱格式</span><span class="sxs-lookup"><span data-stu-id="41c39-124">File name format</span></span>

`[product]-[component]-[major].[minor].[patch]-[previewN]-[optional build #]-[rid].[file ext]`

<span data-ttu-id="41c39-125">以下是此格式的一些範例：</span><span class="sxs-lookup"><span data-stu-id="41c39-125">Here are some examples of this format:</span></span>

```
dotnet-runtime-2.0.4-macos.10.12-x64.pkg            # Mac runtime installer
dotnet-sdk-2.0.4-win10-x64.exe                      # Windows SDK installer
dotnet-sdk-2.0.4-fedora.24-x64.tar.gz               # Fedora 24 binary archive

#Ubuntu file set needed for the SDK
dotnet-host-2.0.4-ubuntu.16.04-x64.deb              # Host / muxer and host policy
dotnet-runtime-2.0.4-ubuntu.16.04-x64.deb           # runtime
dotnet-sdk-2.0.4-ubuntu.16.04-x64.deb               # SDK tools
```

<span data-ttu-id="41c39-126">此格式易讀，並會清楚顯示您要下載的項目、版本和可以使用的位置。</span><span class="sxs-lookup"><span data-stu-id="41c39-126">The format is readable and clearly shows what you're downloading, what version it is, and where you can use it.</span></span> <span data-ttu-id="41c39-127">執行階段套件名稱包含 `runtime`，SDK 則包含 `SDK`。</span><span class="sxs-lookup"><span data-stu-id="41c39-127">The runtime package name includes `runtime`, and the SDK includes `SDK`.</span></span>

#### <a name="ui-string-format"></a><span data-ttu-id="41c39-128">UI 字串格式</span><span class="sxs-lookup"><span data-stu-id="41c39-128">UI string format</span></span>

<span data-ttu-id="41c39-129">所有網站描述與安裝程式中的 UI 字串都保持一致、正確且簡單。</span><span class="sxs-lookup"><span data-stu-id="41c39-129">All web site descriptions and UI strings in the installers are kept consistent, accurate, and simple.</span></span> <span data-ttu-id="41c39-130">下表提供一些範例：</span><span class="sxs-lookup"><span data-stu-id="41c39-130">The following table shows some examples:</span></span>

| <span data-ttu-id="41c39-131">Installer</span><span class="sxs-lookup"><span data-stu-id="41c39-131">Installer</span></span> | <span data-ttu-id="41c39-132">視窗標題</span><span class="sxs-lookup"><span data-stu-id="41c39-132">Window Title</span></span>                          | <span data-ttu-id="41c39-133">安裝程式的其他內容</span><span class="sxs-lookup"><span data-stu-id="41c39-133">Other content in installer</span></span> | <span data-ttu-id="41c39-134">安裝的項目</span><span class="sxs-lookup"><span data-stu-id="41c39-134">What is installed</span></span>                               |
| :--       | :--                                   | :--                        | :--                                             |
| <span data-ttu-id="41c39-135">SDK</span><span class="sxs-lookup"><span data-stu-id="41c39-135">SDK</span></span>       | <span data-ttu-id="41c39-136">.NET Core 2.0 SDK (x64) 安裝程式</span><span class="sxs-lookup"><span data-stu-id="41c39-136">.NET Core 2.0 SDK (x64) Installer</span></span>     | <span data-ttu-id="41c39-137">.NET Core 2.0.4 SDK</span><span class="sxs-lookup"><span data-stu-id="41c39-137">.NET Core 2.0.4 SDK</span></span>        | <span data-ttu-id="41c39-138">.NET Core 2.0.4 工具 + .NET Core 2.0.4 執行階段</span><span class="sxs-lookup"><span data-stu-id="41c39-138">.NET Core 2.0.4 Tools + .NET Core 2.0.4 Runtime</span></span> |
| <span data-ttu-id="41c39-139">執行階段</span><span class="sxs-lookup"><span data-stu-id="41c39-139">Runtime</span></span>   | <span data-ttu-id="41c39-140">.NET Core 2.0 執行階段 (x64) 安裝程式</span><span class="sxs-lookup"><span data-stu-id="41c39-140">.NET Core 2.0 Runtime (x64) Installer</span></span> | <span data-ttu-id="41c39-141">.NET Core 2.0.4 執行階段</span><span class="sxs-lookup"><span data-stu-id="41c39-141">.NET Core 2.0.4 Runtime</span></span>    | <span data-ttu-id="41c39-142">.NET Core 2.0.4 執行階段</span><span class="sxs-lookup"><span data-stu-id="41c39-142">.NET Core 2.0.4 Runtime</span></span>                         |

<span data-ttu-id="41c39-143">Preview 版本略有不同：</span><span class="sxs-lookup"><span data-stu-id="41c39-143">Preview releases differ only slightly:</span></span>

| <span data-ttu-id="41c39-144">Installer</span><span class="sxs-lookup"><span data-stu-id="41c39-144">Installer</span></span> | <span data-ttu-id="41c39-145">視窗標題</span><span class="sxs-lookup"><span data-stu-id="41c39-145">Window Title</span></span>                                    | <span data-ttu-id="41c39-146">安裝程式的其他內容</span><span class="sxs-lookup"><span data-stu-id="41c39-146">Other content in installer</span></span>        | <span data-ttu-id="41c39-147">安裝的項目</span><span class="sxs-lookup"><span data-stu-id="41c39-147">What is installed</span></span>                                                   |
| :--       | :--                                             | :--                               | :--                                                                 |
| <span data-ttu-id="41c39-148">SDK</span><span class="sxs-lookup"><span data-stu-id="41c39-148">SDK</span></span>       | <span data-ttu-id="41c39-149">.NET Core 2.0 Preview 1 SDK (x64) 安裝程式</span><span class="sxs-lookup"><span data-stu-id="41c39-149">.NET Core 2.0 Preview 1 SDK (x64) Installer</span></span>     | <span data-ttu-id="41c39-150">.NET Core 2.0.0 Preview 1 SDK</span><span class="sxs-lookup"><span data-stu-id="41c39-150">.NET Core 2.0.0 Preview 1 SDK</span></span>     | <span data-ttu-id="41c39-151">.NET Core 2.0.0 Preview 1 工具 + .NET Core 2.0.0 Preview 1 執行階段</span><span class="sxs-lookup"><span data-stu-id="41c39-151">.NET Core 2.0.0 Preview 1 Tools + .NET Core 2.0.0 Preview 1 Runtime</span></span> |
| <span data-ttu-id="41c39-152">執行階段</span><span class="sxs-lookup"><span data-stu-id="41c39-152">Runtime</span></span>   | <span data-ttu-id="41c39-153">.NET Core 2.0 Preview 1 執行階段 (x64) 安裝程式</span><span class="sxs-lookup"><span data-stu-id="41c39-153">.NET Core 2.0 Preview 1 Runtime (x64) Installer</span></span> | <span data-ttu-id="41c39-154">.NET Core 2.0.0 Preview 1 執行階段</span><span class="sxs-lookup"><span data-stu-id="41c39-154">.NET Core 2.0.0 Preview 1 Runtime</span></span> | <span data-ttu-id="41c39-155">.NET Core 2.0.0 Preview 1 執行階段</span><span class="sxs-lookup"><span data-stu-id="41c39-155">.NET Core 2.0.0 Preview 1 Runtime</span></span>                                   |

<span data-ttu-id="41c39-156">SDK 版本可能會包含多個執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-156">It may happen that an SDK release contains more than one version of the runtime.</span></span> <span data-ttu-id="41c39-157">當發生這種情況時，安裝程式 UX 看起來會像這樣 (只顯示 SDK 版本，已安裝的執行階段版本會顯示在 Windows 和 Mac 安裝程序結尾的摘要頁面上)：</span><span class="sxs-lookup"><span data-stu-id="41c39-157">When that happens, the installer UX looks like the following (only the SDK version is shown and the installed Runtime versions are shown on a summary page at the end of the installation process on Windows and Mac):</span></span>

| <span data-ttu-id="41c39-158">Installer</span><span class="sxs-lookup"><span data-stu-id="41c39-158">Installer</span></span> | <span data-ttu-id="41c39-159">視窗標題</span><span class="sxs-lookup"><span data-stu-id="41c39-159">Window Title</span></span>                      | <span data-ttu-id="41c39-160">安裝程式的其他內容</span><span class="sxs-lookup"><span data-stu-id="41c39-160">Other content in installer</span></span>                                   | <span data-ttu-id="41c39-161">安裝的項目</span><span class="sxs-lookup"><span data-stu-id="41c39-161">What is installed</span></span>                                                         |
| :--       | :--                               | :--                                                          | :--                                                                       |
| <span data-ttu-id="41c39-162">SDK</span><span class="sxs-lookup"><span data-stu-id="41c39-162">SDK</span></span>       | <span data-ttu-id="41c39-163">.NET Core 2.1 SDK (x64) 安裝程式</span><span class="sxs-lookup"><span data-stu-id="41c39-163">.NET Core 2.1 SDK (x64) Installer</span></span> | <span data-ttu-id="41c39-164">.NET Core 2.1.1 SDK</span><span class="sxs-lookup"><span data-stu-id="41c39-164">.NET Core 2.1.1 SDK</span></span> <br> <span data-ttu-id="41c39-165">.NET Core 2.1.1 執行階段</span><span class="sxs-lookup"><span data-stu-id="41c39-165">.NET Core 2.1.1 Runtime</span></span> <br> <span data-ttu-id="41c39-166">.NET Core 2.0.6 執行階段</span><span class="sxs-lookup"><span data-stu-id="41c39-166">.NET Core 2.0.6 Runtime</span></span> | <span data-ttu-id="41c39-167">.NET Core 2.1.1 工具 + .NET Core 2.1.1 執行階段 + .NET Core 2.0.6 執行階段</span><span class="sxs-lookup"><span data-stu-id="41c39-167">.NET Core 2.1.1 Tools + .NET Core 2.1.1 Runtime + .NET Core 2.0.6 Runtime</span></span> |

<span data-ttu-id="41c39-168">也可能是 .NET Core 工具需要更新，但執行階段不需要變更。</span><span class="sxs-lookup"><span data-stu-id="41c39-168">It's also possible that .NET Core Tools need to be updated, without runtime changes.</span></span> <span data-ttu-id="41c39-169">在此情況下，SDK 版本會增加 (例如，變成 2.1.2)，然後執行階段下次趕上 (例如，執行階段和 SDK 下次都變成 2.1.3)。</span><span class="sxs-lookup"><span data-stu-id="41c39-169">In that case, the SDK version is increased (for example, to 2.1.2) and then the Runtime catches up the next time it ships (for example, both the Runtime and SDK ship the next time as 2.1.3).</span></span>

### <a name="package-managers"></a><span data-ttu-id="41c39-170">套件管理員</span><span class="sxs-lookup"><span data-stu-id="41c39-170">Package managers</span></span>

<span data-ttu-id="41c39-171">Microsoft 以外的其他實體也可以散佈 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="41c39-171">.NET Core can be distributed by other entities than Microsoft.</span></span> <span data-ttu-id="41c39-172">特別是，Linux 發行版本的擁有者和套件維護者，可將 .NET Core 套件新增至其套件管理員。</span><span class="sxs-lookup"><span data-stu-id="41c39-172">In particular, Linux distribution owners and package maintainers may add .NET Core packages to their package managers.</span></span> <span data-ttu-id="41c39-173">如需這些套件應如何命名和建立版本的建議，請參閱 [.NET Core 發佈封裝](../build/distribution-packaging.md)。</span><span class="sxs-lookup"><span data-stu-id="41c39-173">For recommendations on how those packages should be named and versioned, see [.NET Core distribution packaging](../build/distribution-packaging.md).</span></span>

#### <a name="minimum-package-set"></a><span data-ttu-id="41c39-174">最小封裝集合</span><span class="sxs-lookup"><span data-stu-id="41c39-174">Minimum package set</span></span>

* <span data-ttu-id="41c39-175">`dotnet-runtime-[major].[minor]`：指定版本的執行階段 (針對指定的主要 + 次要組合，套件管理員中僅可使用最新的更新程式版本)。</span><span class="sxs-lookup"><span data-stu-id="41c39-175">`dotnet-runtime-[major].[minor]`: a runtime with the specified version (only the latest patch version for a given major+minor combination should be available in the package manager).</span></span> <span data-ttu-id="41c39-176">新的修補程式版本會更新套件，但新的次要版本或主要版本是個別的套件。</span><span class="sxs-lookup"><span data-stu-id="41c39-176">New patch versions update the package, but new minor or major versions are separate packages.</span></span>
 
  <span data-ttu-id="41c39-177">**相依性**：`dotnet-host`</span><span class="sxs-lookup"><span data-stu-id="41c39-177">**Dependencies**: `dotnet-host`</span></span>

* <span data-ttu-id="41c39-178">`dotnet-sdk`：最新的 SDK。</span><span class="sxs-lookup"><span data-stu-id="41c39-178">`dotnet-sdk`: the latest SDK.</span></span> <span data-ttu-id="41c39-179">`update` 會向前復原主要、次要和修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-179">`update` rolls forward major, minor, and patch versions.</span></span>

  <span data-ttu-id="41c39-180">**相依性**：最新的 `dotnet-sdk-[major].[minor]`。</span><span class="sxs-lookup"><span data-stu-id="41c39-180">**Dependencies**: the latest `dotnet-sdk-[major].[minor]`.</span></span>

* <span data-ttu-id="41c39-181">`dotnet-sdk-[major].[minor]`：指定版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="41c39-181">`dotnet-sdk-[major].[minor]`: the SDK with the specified version.</span></span> <span data-ttu-id="41c39-182">指定的版本是內含共用架構的最高內含版本，因此使用者可以輕鬆地將 SDK 與共用架構相關聯。</span><span class="sxs-lookup"><span data-stu-id="41c39-182">The version specified is the highest included version of included shared frameworks, so that users can easily relate an SDK to a shared framework.</span></span> <span data-ttu-id="41c39-183">新的修補程式版本會更新套件，但新的次要版本或主要版本是個別的套件。</span><span class="sxs-lookup"><span data-stu-id="41c39-183">New patch versions update the package, but new minor or major versions are separate packages.</span></span>

  <span data-ttu-id="41c39-184">**相依性**：`dotnet-host`，一或多個 `dotnet-runtime-[major].[minor]` (其中之一由 SDK 程式碼本身使用，其他執行階段則是供使用者作為目標建置和執行)。</span><span class="sxs-lookup"><span data-stu-id="41c39-184">**Dependencies**: `dotnet-host`, one or more `dotnet-runtime-[major].[minor]` (one of those is used by the SDK code itself, the others are here for users to build and run against).</span></span>

* <span data-ttu-id="41c39-185">`dotnet-host`：最新的主機。</span><span class="sxs-lookup"><span data-stu-id="41c39-185">`dotnet-host`: the latest host.</span></span>

##### <a name="preview-versions"></a><span data-ttu-id="41c39-186">預覽版本</span><span class="sxs-lookup"><span data-stu-id="41c39-186">Preview versions</span></span>

<span data-ttu-id="41c39-187">套件維護人員可能會決定要包含執行階段和 SDK 的預覽版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-187">Package maintainers may decide to include preview versions of the runtime and SDK.</span></span> <span data-ttu-id="41c39-188">不包含未建立版本的 `dotnet-sdk` 套件中的預覽版本，但可以作為已建立版本的套件發佈，且將其他預覽標記附加到名稱的主要版本和次要版本區段。</span><span class="sxs-lookup"><span data-stu-id="41c39-188">Don't include those preview versions in the unversioned `dotnet-sdk` package, but you can release them as versioned packages with an additional preview marker appended to the major and minor version sections of the name.</span></span> <span data-ttu-id="41c39-189">例如，可能會有 `dotnet-sdk-2.0-preview1-final` 套件。</span><span class="sxs-lookup"><span data-stu-id="41c39-189">For example, there may be a `dotnet-sdk-2.0-preview1-final` package.</span></span>

### <a name="docker"></a><span data-ttu-id="41c39-190">Docker</span><span class="sxs-lookup"><span data-stu-id="41c39-190">Docker</span></span>

<span data-ttu-id="41c39-191">一般的 Docker 標記命名慣例，是版本號碼在元件名稱之前。</span><span class="sxs-lookup"><span data-stu-id="41c39-191">A general Docker tag naming convention is to place the version number before the component name.</span></span> <span data-ttu-id="41c39-192">這個慣例會繼續使用。</span><span class="sxs-lookup"><span data-stu-id="41c39-192">This convention may continue to be utilized.</span></span> <span data-ttu-id="41c39-193">目前的標記只包含執行階段版本，如下所示。</span><span class="sxs-lookup"><span data-stu-id="41c39-193">The current tags include only the Runtime version as follows.</span></span>

* <span data-ttu-id="41c39-194">1.0.8-runtime</span><span class="sxs-lookup"><span data-stu-id="41c39-194">1.0.8-runtime</span></span>
* <span data-ttu-id="41c39-195">1.0.8-sdk</span><span class="sxs-lookup"><span data-stu-id="41c39-195">1.0.8-sdk</span></span>
* <span data-ttu-id="41c39-196">2.0.4-runtime</span><span class="sxs-lookup"><span data-stu-id="41c39-196">2.0.4-runtime</span></span>
* <span data-ttu-id="41c39-197">2.0.4-sdk</span><span class="sxs-lookup"><span data-stu-id="41c39-197">2.0.4-sdk</span></span>
* <span data-ttu-id="41c39-198">2.1.1-runtime</span><span class="sxs-lookup"><span data-stu-id="41c39-198">2.1.1-runtime</span></span>
* <span data-ttu-id="41c39-199">2.1.1-sdk</span><span class="sxs-lookup"><span data-stu-id="41c39-199">2.1.1-sdk</span></span>

<span data-ttu-id="41c39-200">SDK 標記應該更新，以表示 SDK 版本，而不是表示執行階段。</span><span class="sxs-lookup"><span data-stu-id="41c39-200">The SDK tags should be updated to represent the SDK version rather than Runtime.</span></span>

<span data-ttu-id="41c39-201">我們可能也需要修復 .NET Core 工具，但重新附帶現有的執行階段。</span><span class="sxs-lookup"><span data-stu-id="41c39-201">It's also possible that we need to fix the .NET Core Tools but reship an existing runtime.</span></span> <span data-ttu-id="41c39-202">在此情況下，SDK 版本會增加 (例如，變成 2.1.2)，然後執行階段下次趕上 (例如，執行階段和 SDK 下次都變成 2.1.3)。</span><span class="sxs-lookup"><span data-stu-id="41c39-202">In that case, the SDK version is increased (for example, to 2.1.2) and then the Runtime catches up the next time it ships (for example, both the Runtime and SDK ship the following time as 2.1.3).</span></span>

## <a name="semantic-versioning"></a><span data-ttu-id="41c39-203">語意版本控制</span><span class="sxs-lookup"><span data-stu-id="41c39-203">Semantic Versioning</span></span>

<span data-ttu-id="41c39-204">.NET Core 使用[語意版本控制 (SemVer)](http://semver.org/)，並採用 `MAJOR.MINOR.PATCH` 版本控制，使用版本號碼的不同部分來描述變更的程度和類型。</span><span class="sxs-lookup"><span data-stu-id="41c39-204">.NET Core uses [Semantic Versioning (SemVer)](http://semver.org/), adopting the use of `MAJOR.MINOR.PATCH` versioning, using the various parts of the version number to describe the degree and type of change.</span></span>

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

<span data-ttu-id="41c39-205">選擇性的 `PRERELEASE` 和 `BUILDNUMBER` 組件只存在於本機從來源目標建置的每日組建中，絕不會屬於支援的版本和不支援的預覽版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-205">The optional `PRERELEASE` and `BUILDNUMBER` parts will never be part of supported releases, and only exist on nightly builds, locally built from source targets, and unsupported preview releases.</span></span>

### <a name="how-version-numbers-are-incremented"></a><span data-ttu-id="41c39-206">版本號碼如何遞增？</span><span class="sxs-lookup"><span data-stu-id="41c39-206">How version numbers are incremented?</span></span>

<span data-ttu-id="41c39-207">`MAJOR` 的遞增時機為：</span><span class="sxs-lookup"><span data-stu-id="41c39-207">`MAJOR` is incremented when:</span></span>
  - <span data-ttu-id="41c39-208">不再支援舊版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-208">An old version is no longer supported.</span></span>
  - <span data-ttu-id="41c39-209">採用現有相依性的較新 `MAJOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-209">A newer `MAJOR` version of an existing dependency is adopted.</span></span>
  - <span data-ttu-id="41c39-210">相容性實際的預設設定變更為 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="41c39-210">The default setting of a compatibility quirk is changed to "off."</span></span>

<span data-ttu-id="41c39-211">`MINOR` 的遞增時機為：</span><span class="sxs-lookup"><span data-stu-id="41c39-211">`MINOR` is incremented when:</span></span>
  - <span data-ttu-id="41c39-212">新增公用 API 介面區。</span><span class="sxs-lookup"><span data-stu-id="41c39-212">Public API surface area is added.</span></span>
  - <span data-ttu-id="41c39-213">新增新的行為。</span><span class="sxs-lookup"><span data-stu-id="41c39-213">A new behavior is added.</span></span>
  - <span data-ttu-id="41c39-214">採用現有相依性的較新 `MINOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-214">A newer `MINOR` version of an existing dependency is adopted.</span></span>
  - <span data-ttu-id="41c39-215">引入新的相依性。</span><span class="sxs-lookup"><span data-stu-id="41c39-215">A new dependency is introduced.</span></span>
  
<span data-ttu-id="41c39-216">`PATCH` 的遞增時機為：</span><span class="sxs-lookup"><span data-stu-id="41c39-216">`PATCH` is incremented when:</span></span>
  - <span data-ttu-id="41c39-217">已修正 Bug。</span><span class="sxs-lookup"><span data-stu-id="41c39-217">Bug fixes are made.</span></span>
  - <span data-ttu-id="41c39-218">新增對較新平台的支援。</span><span class="sxs-lookup"><span data-stu-id="41c39-218">Support for a newer platform is added.</span></span>
  - <span data-ttu-id="41c39-219">採用現有相依性的較新 `PATCH` 版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-219">A newer `PATCH` version of an existing dependency is adopted.</span></span>
  - <span data-ttu-id="41c39-220">任何其他變更，不符合其中一個先前的案例。</span><span class="sxs-lookup"><span data-stu-id="41c39-220">Any other change that doesn't fit one of the previous cases.</span></span>

<span data-ttu-id="41c39-221">當有多項變更時，因個別變更而影響的最高項目就會遞增，而下列項目會重設為零。</span><span class="sxs-lookup"><span data-stu-id="41c39-221">When there are multiple changes, the highest element affected by individual changes is incremented, and the following ones are reset to zero.</span></span> <span data-ttu-id="41c39-222">例如，當 `MAJOR` 遞增時，`MINOR` 和 `PATCH` 會重設為零。</span><span class="sxs-lookup"><span data-stu-id="41c39-222">For example, when `MAJOR` is incremented, `MINOR` and `PATCH` are reset to zero.</span></span> <span data-ttu-id="41c39-223">當 `MINOR` 遞增時，`PATCH` 會重設為零而 `MAJOR` 保持不變。</span><span class="sxs-lookup"><span data-stu-id="41c39-223">When `MINOR` is incremented, `PATCH` is reset to zero while `MAJOR` is left untouched.</span></span>

### <a name="preview-versions"></a><span data-ttu-id="41c39-224">預覽版本</span><span class="sxs-lookup"><span data-stu-id="41c39-224">Preview versions</span></span>

<span data-ttu-id="41c39-225">預覽版本將 `-preview[number]-([build]|"final")` 附加至版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-225">Preview versions have a `-preview[number]-([build]|"final")` appended to the version.</span></span> <span data-ttu-id="41c39-226">例如，`2.0.0-preview1-final`。</span><span class="sxs-lookup"><span data-stu-id="41c39-226">For example, `2.0.0-preview1-final`.</span></span>

### <a name="servicing-versions"></a><span data-ttu-id="41c39-227">服務版本</span><span class="sxs-lookup"><span data-stu-id="41c39-227">Servicing versions</span></span>

<span data-ttu-id="41c39-228">版本發行之後，版本分支通常會停止產生每日組建，改為開始產生服務組建。</span><span class="sxs-lookup"><span data-stu-id="41c39-228">After a release goes out, the release branches generally stop producing daily builds and instead start producing servicing builds.</span></span> <span data-ttu-id="41c39-229">服務版本會將 `-servicing-[number]` 附加至版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-229">Servicing versions have a `-servicing-[number]` appended to the version.</span></span> <span data-ttu-id="41c39-230">例如，`2.0.1-servicing-006924`。</span><span class="sxs-lookup"><span data-stu-id="41c39-230">For example, `2.0.1-servicing-006924`.</span></span>

### <a name="lts-vs-current"></a><span data-ttu-id="41c39-231">LTS 與目前的</span><span class="sxs-lookup"><span data-stu-id="41c39-231">LTS vs. current</span></span>

<span data-ttu-id="41c39-232">有兩個 .NET Core 版本序列：長期支援 (LTS) 和目前。</span><span class="sxs-lookup"><span data-stu-id="41c39-232">There are two trains of releases for .NET Core: Long Term Support (LTS) and Current.</span></span> <span data-ttu-id="41c39-233">讓使用者挑選他們想要且仍受支援的穩定性層級和新功能。</span><span class="sxs-lookup"><span data-stu-id="41c39-233">That enables users to pick the level of stability and new features they want, while still being supported.</span></span>

- <span data-ttu-id="41c39-234">LTS 表示取得新功能的頻率較低，但有較成熟的平台。</span><span class="sxs-lookup"><span data-stu-id="41c39-234">LTS means you get new features less frequently, but you have a more mature platform.</span></span> <span data-ttu-id="41c39-235">LTS 支援時間也較長。</span><span class="sxs-lookup"><span data-stu-id="41c39-235">LTS also has a longer period of support.</span></span>
- <span data-ttu-id="41c39-236">「目前」表示取得新功能和 API 的頻率較高，但缺點是安裝更新的時段較短，以及這些更新發生地更頻繁。</span><span class="sxs-lookup"><span data-stu-id="41c39-236">Current means you get new features and APIs more frequently, but the disadvantage is that you have a shorter window of time to install updates, and those updates happen more frequently.</span></span> <span data-ttu-id="41c39-237">「目前」也受到完全支援，但支援時間比 LTS 短。</span><span class="sxs-lookup"><span data-stu-id="41c39-237">Current is also fully supported but the support period is shorter than LTS.</span></span>

<span data-ttu-id="41c39-238">「目前」的版本可升級為 LTS。</span><span class="sxs-lookup"><span data-stu-id="41c39-238">A "Current" version may get promoted to LTS.</span></span>

<span data-ttu-id="41c39-239">"LTS" 和「目前」應視為給特定版本的標籤，以表述相關聯的支援層級。</span><span class="sxs-lookup"><span data-stu-id="41c39-239">"LTS" and "Current" should be considered as labels that we put on specific releases to make a statement about the associated level of support.</span></span>

<span data-ttu-id="41c39-240">如需詳細資訊，請參閱 [.NET Core 支援週期資料表](https://www.microsoft.com/net/core/support)。</span><span class="sxs-lookup"><span data-stu-id="41c39-240">For more information, see [.NET Core Support Lifecycle Fact Sheet](https://www.microsoft.com/net/core/support).</span></span>

## <a name="versioning-scheme-details"></a><span data-ttu-id="41c39-241">版本控制配置詳細資料</span><span class="sxs-lookup"><span data-stu-id="41c39-241">Versioning scheme details</span></span>

<span data-ttu-id="41c39-242">.NET Core 由下列組件構成：</span><span class="sxs-lookup"><span data-stu-id="41c39-242">.NET Core is made of the following parts:</span></span>

- <span data-ttu-id="41c39-243">主機 (也稱為 muxer)：具有 `hostfxr` 原則庫的 `dotnet.exe`。</span><span class="sxs-lookup"><span data-stu-id="41c39-243">A host (also known as muxer): `dotnet.exe` with `hostfxr` policy libraries.</span></span>
- <span data-ttu-id="41c39-244">SDK (開發人員電腦上必要的工具集，但不是生產環境中必要的)。</span><span class="sxs-lookup"><span data-stu-id="41c39-244">An SDK (the set of tools necessary on a developer's machine, but not in production).</span></span>
- <span data-ttu-id="41c39-245">執行階段。</span><span class="sxs-lookup"><span data-stu-id="41c39-245">A runtime.</span></span>
- <span data-ttu-id="41c39-246">共用架構實作，以套件進行散發。</span><span class="sxs-lookup"><span data-stu-id="41c39-246">A shared framework implementation, distributed as packages.</span></span> <span data-ttu-id="41c39-247">每個套件會獨立建立版本，尤其是修補程式版本控制。</span><span class="sxs-lookup"><span data-stu-id="41c39-247">Each package is versioned independently, particularly for patch versioning.</span></span>
- <span data-ttu-id="41c39-248">或者，一組[中繼套件](../packages.md)，將細部套件當成已建立版本單位的參考。</span><span class="sxs-lookup"><span data-stu-id="41c39-248">Optionally, a set of [metapackages](../packages.md) that reference fine-grained packages as a versioned unit.</span></span> <span data-ttu-id="41c39-249">中繼套件可與套件分開建立版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-249">Metapackages can be versioned separately from packages.</span></span>

<span data-ttu-id="41c39-250">.NET Core 也包含一組目標 Framework (例如，`netstandard` 或 `netcoreapp`)，代表過大的 API 集，因為版本號碼遞增。</span><span class="sxs-lookup"><span data-stu-id="41c39-250">.NET Core also includes a set of target frameworks (for example, `netstandard` or `netcoreapp`) that represent a progressively larger API set, as version numbers are incremented.</span></span>

### <a name="net-standard"></a><span data-ttu-id="41c39-251">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="41c39-251">.NET Standard</span></span>

<span data-ttu-id="41c39-252">.NET Standard 一直使用 `MAJOR.MINOR` 版本設定配置。</span><span class="sxs-lookup"><span data-stu-id="41c39-252">.NET Standard has been using a `MAJOR.MINOR` versioning scheme.</span></span> <span data-ttu-id="41c39-253">`PATCH` 層級不適合 .NET Standard，因為它傳達的是不常反覆運算且不會呈現與實際實作相同之版本控制需求的合約集合。</span><span class="sxs-lookup"><span data-stu-id="41c39-253">`PATCH` level isn't useful for .NET Standard because it expresses a set of contracts that are iterated on less often and doesn't present the same requirements for versioning as an actual implementation.</span></span>

<span data-ttu-id="41c39-254">.NET Standard 版本和 .NET Core 版本之間沒有實際結合：.NET Core 2.0 剛巧實作 .NET Standard 2.0，但不保證未來的 .NET Core 版本也會對應至相同的 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-254">There is no real coupling between .NET Standard versions and .NET Core versions: .NET Core 2.0 happens to implement .NET Standard 2.0, but there is no guarantee that future versions of .NET Core will map to the same .NET Standard version.</span></span> <span data-ttu-id="41c39-255">.NET Core 可以附帶不是 .NET Standard 定義的 API；如此，不需要新的 .NET Standard 也可以附帶新版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-255">.NET Core can ship APIs that aren't defined by .NET Standard, and, as such, may ship new versions without requiring a new .NET Standard.</span></span> <span data-ttu-id="41c39-256">.NET Standard 也是適用其他目標的概念，例如 .NET Framework 或 Mono，即使它一開始與 .NET Core 一致。</span><span class="sxs-lookup"><span data-stu-id="41c39-256">.NET Standard is also a concept that applies to other targets, such as .NET Framework or Mono, even if its inception happened to coincide with that of .NET Core.</span></span>

### <a name="packages"></a><span data-ttu-id="41c39-257">封裝</span><span class="sxs-lookup"><span data-stu-id="41c39-257">Packages</span></span>

<span data-ttu-id="41c39-258">程式庫套件會獨立演化及進行版本控制。</span><span class="sxs-lookup"><span data-stu-id="41c39-258">Library packages evolve and version independently.</span></span> <span data-ttu-id="41c39-259">與 .NET Framework 系統重疊的套件。\* 組件通常使用 4.x 版本，並與 .NET Framework 4.x 版本控制 (一個歷史選項) 一致。</span><span class="sxs-lookup"><span data-stu-id="41c39-259">Packages that overlap with .NET Framework System.\* assemblies typically use 4.x versions, aligning with the .NET Framework 4.x versioning (a historical choice).</span></span> <span data-ttu-id="41c39-260">不與 .NET Framework 程式庫重疊的套件 (例如，[`System.Reflection.Metadata`](https://www.nuget.org/packages/System.Reflection.Metadata)) 通常從 1.0 開始，並從該處遞增。</span><span class="sxs-lookup"><span data-stu-id="41c39-260">Packages that do not overlap with the .NET Framework libraries (for example, [`System.Reflection.Metadata`](https://www.nuget.org/packages/System.Reflection.Metadata)) typically start at 1.0 and increment from there.</span></span>

<span data-ttu-id="41c39-261">[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) 所描述的套件會被特別處理，因為它們是平台的基底。</span><span class="sxs-lookup"><span data-stu-id="41c39-261">The packages described by [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) are treated specially due to being at the base of the platform.</span></span>

<span data-ttu-id="41c39-262">`NETStandard.Library` 套件通常會作為一個集合來進行版本控制，因為它們彼此之間有實作層級的相依性。</span><span class="sxs-lookup"><span data-stu-id="41c39-262">`NETStandard.Library` packages will typically version as a set, since they have implementation-level dependencies between them.</span></span>

### <a name="metapackages"></a><span data-ttu-id="41c39-263">中繼套件</span><span class="sxs-lookup"><span data-stu-id="41c39-263">Metapackages</span></span>

<span data-ttu-id="41c39-264">.NET Core 中繼套件的版本控制是以其所屬的 .NET Core 版本為基礎。</span><span class="sxs-lookup"><span data-stu-id="41c39-264">Versioning for .NET Core metapackages is based on the .NET Core version they are a part of.</span></span>

<span data-ttu-id="41c39-265">例如，.NET Core 2.1.3 中繼套件的 `MAJOR` 和 `MINOR` 版本號碼應該全都有 2.1。</span><span class="sxs-lookup"><span data-stu-id="41c39-265">For instance, the metapackages in .NET Core 2.1.3 should all have 2.1 as their `MAJOR` and `MINOR` version numbers.</span></span>

<span data-ttu-id="41c39-266">每次更新參考的套件時，中繼套件的修補程式版本就會遞增。</span><span class="sxs-lookup"><span data-stu-id="41c39-266">The patch version for the metapackage is incremented every time any referenced package is updated.</span></span> <span data-ttu-id="41c39-267">修補程式版本不包含更新的架構版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-267">Patch versions don't include an updated framework version.</span></span> <span data-ttu-id="41c39-268">因此，中繼套件並不與 SemVer 完相容，因為其版本控制配置並不代表基礎套件中的變更程度，而是主要代表 API 層級。</span><span class="sxs-lookup"><span data-stu-id="41c39-268">As a result, the metapackages aren't strictly SemVer-compliant because their versioning scheme doesn't represent the degree of change in the underlying packages, but primarily the API level.</span></span> 

<span data-ttu-id="41c39-269">.NET Core 目前有兩個主要中繼套件：</span><span class="sxs-lookup"><span data-stu-id="41c39-269">There are currently two primary metapackages for .NET Core:</span></span>

<span data-ttu-id="41c39-270">**Microsoft.NETCore.App**</span><span class="sxs-lookup"><span data-stu-id="41c39-270">**Microsoft.NETCore.App**</span></span>

- <span data-ttu-id="41c39-271">截至 .NET Core 1.0 為 1.0 版 (這些版本會相符)。</span><span class="sxs-lookup"><span data-stu-id="41c39-271">v1.0 as of .NET Core 1.0 (these versions match).</span></span>
- <span data-ttu-id="41c39-272">對應至 `netcoreapp` 架構。</span><span class="sxs-lookup"><span data-stu-id="41c39-272">Maps to the `netcoreapp` framework.</span></span>
- <span data-ttu-id="41c39-273">描述 .NET Core 散發套件中的套件。</span><span class="sxs-lookup"><span data-stu-id="41c39-273">Describes the packages in the .NET Core distribution.</span></span>

<span data-ttu-id="41c39-274">注意：[`Microsoft.NETCore.Portable.Compatibility`](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) 是另一個 .NET Core 中繼套件，是為了與 .NET 的預先 .NET Standard 實作相容而存在。</span><span class="sxs-lookup"><span data-stu-id="41c39-274">Note: [`Microsoft.NETCore.Portable.Compatibility`](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) is another .NET Core metapackage that exists to enable compatibility with pre-.NET Standard implementation of .NET.</span></span> <span data-ttu-id="41c39-275">它不會對應至特定的架構，因此其版本控制類似套件。</span><span class="sxs-lookup"><span data-stu-id="41c39-275">It doesn't map to a particular framework, so it versions like a package.</span></span>

<span data-ttu-id="41c39-276">**NETStandard.Library**</span><span class="sxs-lookup"><span data-stu-id="41c39-276">**NETStandard.Library**</span></span>

<span data-ttu-id="41c39-277">[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) 描述 [.NET Standard](../../standard/library.md) 所包含的程式庫。</span><span class="sxs-lookup"><span data-stu-id="41c39-277">[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) describes the libraries that are part of the [.NET Standard](../../standard/library.md).</span></span> <span data-ttu-id="41c39-278">適用於所有支援 .NET Standard 的 .NET 實作，例如，.NET Framework、.NET Core 和 Mono。</span><span class="sxs-lookup"><span data-stu-id="41c39-278">Applies to all .NET implementations that support .NET Standard, such as .NET Framework, .NET Core, and Mono.</span></span>

### <a name="target-frameworks"></a><span data-ttu-id="41c39-279">目標 Framework</span><span class="sxs-lookup"><span data-stu-id="41c39-279">Target frameworks</span></span>

<span data-ttu-id="41c39-280">新增新的 API 時，會更新目標架構版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-280">Target framework versions are updated when new APIs are added.</span></span> <span data-ttu-id="41c39-281">它們有沒有修補程式版本的概念，因為它們代表 API 圖形，而不是實作考量。</span><span class="sxs-lookup"><span data-stu-id="41c39-281">They have no concept of patch version, since they represent API shape and not implementation concerns.</span></span> <span data-ttu-id="41c39-282">主要和次要的版本控制會遵循之前指定的 SemVer 規則，符合實作它們之 .NET Core 發佈的 `MAJOR` 和 `MINOR` 號碼。</span><span class="sxs-lookup"><span data-stu-id="41c39-282">Major and minor versioning follows the SemVer rules specified earlier, and coincides with the `MAJOR` and `MINOR` numbers of the .NET Core distributions that implement them.</span></span>

## <a name="versioning-in-practice"></a><span data-ttu-id="41c39-283">版本控制實作</span><span class="sxs-lookup"><span data-stu-id="41c39-283">Versioning in practice</span></span>

<span data-ttu-id="41c39-284">下載 .NET Core 時，您下載的檔案名稱攜有版本，例如 `dotnet-sdk-2.0.4-win10-x64.exe`。</span><span class="sxs-lookup"><span data-stu-id="41c39-284">When you download .NET Core, the name of the file you download carries the version, for example, `dotnet-sdk-2.0.4-win10-x64.exe`.</span></span>

<span data-ttu-id="41c39-285">GitHub 上的 .NET Core 存放庫每天都有認可和提取要求，進而產生許多程式庫的新組建。</span><span class="sxs-lookup"><span data-stu-id="41c39-285">There are commits and pull requests on .NET Core repos on GitHub on a daily basis, resulting in new builds of many libraries.</span></span> <span data-ttu-id="41c39-286">為每一項變更建立新的公用版本 .NET Core 並不實際。</span><span class="sxs-lookup"><span data-stu-id="41c39-286">It isn't practical to create new public versions of .NET Core for every change.</span></span> <span data-ttu-id="41c39-287">相反地，會針對一段不定時間 (例如，數週或數個月) 彙總變更，然後才製作新的公用穩定 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="41c39-287">Instead, changes are aggregated over an undetermined period of time (for example, weeks or months) before making a new public stable .NET Core version.</span></span>

<span data-ttu-id="41c39-288">新的 .NET Core 版本可能意謂著幾件事︰</span><span class="sxs-lookup"><span data-stu-id="41c39-288">A new version of .NET Core could mean several things:</span></span>

- <span data-ttu-id="41c39-289">新版本的套件和中繼套件。</span><span class="sxs-lookup"><span data-stu-id="41c39-289">New versions of packages and metapackages.</span></span>
- <span data-ttu-id="41c39-290">新版本的各種架構，假設新增 API 版本的話。</span><span class="sxs-lookup"><span data-stu-id="41c39-290">New versions of various frameworks, assuming the addition of new APIs.</span></span>
- <span data-ttu-id="41c39-291">新版本的 .NET Core 散發套件。</span><span class="sxs-lookup"><span data-stu-id="41c39-291">New version of the .NET Core distribution.</span></span>

### <a name="shipping-a-patch-release"></a><span data-ttu-id="41c39-292">修補程式版本出貨</span><span class="sxs-lookup"><span data-stu-id="41c39-292">Shipping a patch release</span></span>

<span data-ttu-id="41c39-293">.NET Core 主要版本出貨之後，例如 2.0.0 版，會針對 .NET Core 程式庫進行修補程式層級的變更，修正 Bug 並改善效能和可靠性。</span><span class="sxs-lookup"><span data-stu-id="41c39-293">After shipping a major release of .NET Core, such as version 2.0.0, patch-level changes are made to .NET Core libraries to fix bugs and improve performance and reliability.</span></span> <span data-ttu-id="41c39-294">這表示未引入新的 API。</span><span class="sxs-lookup"><span data-stu-id="41c39-294">That means that no new APIs are introduced.</span></span> <span data-ttu-id="41c39-295">各種中繼套件會更新，參考更新過的 .NET Core 程式庫套件。</span><span class="sxs-lookup"><span data-stu-id="41c39-295">The various metapackages are updated to reference the updated .NET Core library packages.</span></span> <span data-ttu-id="41c39-296">中繼套件是將版本建立為修補程式的更新 (`MAJOR.MINOR.PATCH`)。</span><span class="sxs-lookup"><span data-stu-id="41c39-296">The metapackages are versioned as patch updates (`MAJOR.MINOR.PATCH`).</span></span> <span data-ttu-id="41c39-297">目標 Framework 不會更新為更新版本的一部分。</span><span class="sxs-lookup"><span data-stu-id="41c39-297">Target frameworks are never updated as part of patch releases.</span></span> <span data-ttu-id="41c39-298">新的 .NET Core 發佈發行時，版本號碼會與 `Microsoft.NETCore.App` 中繼套件的版本號碼相符。</span><span class="sxs-lookup"><span data-stu-id="41c39-298">A new .NET Core distribution is released with a version number that matches that of the `Microsoft.NETCore.App` metapackage.</span></span>

### <a name="shipping-a-minor-release"></a><span data-ttu-id="41c39-299">次要版本出貨</span><span class="sxs-lookup"><span data-stu-id="41c39-299">Shipping a minor release</span></span>

<span data-ttu-id="41c39-300">有遞增 `MAJOR` 版本號碼的 .NET Core 版本出貨之後，新的 API 會新增至 .NET Core 程式庫，以啟用新案例。</span><span class="sxs-lookup"><span data-stu-id="41c39-300">After shipping a .NET Core version with an incremented `MAJOR` version number, new APIs are added to .NET Core libraries to enable new scenarios.</span></span> <span data-ttu-id="41c39-301">各種中繼套件會更新，參考更新過的 .NET Core 程式庫套件。</span><span class="sxs-lookup"><span data-stu-id="41c39-301">The various metapackages are updated to reference the updated .NET Core library packages.</span></span> <span data-ttu-id="41c39-302">中繼套件建立的版本是修補程式更新加上符合新架構版本的 `MAJOR` 和 `MINOR` 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="41c39-302">The metapackages are versioned as patch updates with `MAJOR` and `MINOR` version numbers matching the new framework version.</span></span> <span data-ttu-id="41c39-303">新增新的目標架構名稱和新的 `MAJOR.MINOR` 版本，以描述新的 API (例如，`netcoreapp2.1`)。</span><span class="sxs-lookup"><span data-stu-id="41c39-303">New target framework names with the new `MAJOR.MINOR` version are added to describe the new APIs (for example, `netcoreapp2.1`).</span></span> <span data-ttu-id="41c39-304">新的 .NET Core 散發套件發行時，版本號碼會與 `Microsoft.NETCore.App` 中繼套件相符。</span><span class="sxs-lookup"><span data-stu-id="41c39-304">A new .NET Core distribution is released with a matching version number to the `Microsoft.NETCore.App` metapackage.</span></span>

### <a name="shipping-a-major-release"></a><span data-ttu-id="41c39-305">主要版本出貨</span><span class="sxs-lookup"><span data-stu-id="41c39-305">Shipping a major release</span></span>

<span data-ttu-id="41c39-306">每次新的 .NET Core 主要版本出貨時，`MAJOR` 版本號碼就會遞增，而 `MINOR` 版本號碼則重設為零。</span><span class="sxs-lookup"><span data-stu-id="41c39-306">Every time a new major version of .NET Core ships, the `MAJOR` version number gets incremented, and the `MINOR` version number gets reset to zero.</span></span> <span data-ttu-id="41c39-307">新的主要版本至少包含全部 API，它們是次要版本在前一個主要版本後新增的。</span><span class="sxs-lookup"><span data-stu-id="41c39-307">The new major version contains at least all the APIs that were added by minor releases after the previous major version.</span></span> <span data-ttu-id="41c39-308">新的主要版本應該啟用重要的新案例，也可以中止對舊平台的支援。</span><span class="sxs-lookup"><span data-stu-id="41c39-308">A new major version should enable important new scenarios, and it may also drop support for an older platform.</span></span>

<span data-ttu-id="41c39-309">各種中繼套件會更新，參考更新過的 .NET Core 程式庫套件。</span><span class="sxs-lookup"><span data-stu-id="41c39-309">The various metapackages are updated to reference the updated .NET Core library packages.</span></span> <span data-ttu-id="41c39-310">[`Microsoft.NETCore.App`](https://www.nuget.org/packages/Microsoft.NETCore.App) 中繼套件和 `netcore` 目標架構建立的版本是符合新版 `MAJOR` 版本號碼的重大更新。</span><span class="sxs-lookup"><span data-stu-id="41c39-310">The [`Microsoft.NETCore.App`](https://www.nuget.org/packages/Microsoft.NETCore.App) metapackage and the `netcore` target framework are versioned as a major update matching the `MAJOR` version number of the new release.</span></span>

## <a name="see-also"></a><span data-ttu-id="41c39-311">請參閱</span><span class="sxs-lookup"><span data-stu-id="41c39-311">See also</span></span>
<span data-ttu-id="41c39-312">[目標 Framework](../../standard/frameworks.md) </span><span class="sxs-lookup"><span data-stu-id="41c39-312">[Target frameworks](../../standard/frameworks.md) </span></span>  
<span data-ttu-id="41c39-313">[.NET Core 發佈封裝](../build/distribution-packaging.md) </span><span class="sxs-lookup"><span data-stu-id="41c39-313">[.NET Core distribution packaging](../build/distribution-packaging.md) </span></span>  
<span data-ttu-id="41c39-314">[.NET Core 支援週期資料表](https://www.microsoft.com/net/core/support) </span><span class="sxs-lookup"><span data-stu-id="41c39-314">[.NET Core Support Lifecycle Fact Sheet](https://www.microsoft.com/net/core/support) </span></span>  
<span data-ttu-id="41c39-315">[.NET Core 2+ Version Binding](https://github.com/dotnet/designs/issues/3) (.NET Core 2+ 版本繫結)</span><span class="sxs-lookup"><span data-stu-id="41c39-315">[.NET Core 2+ Version Binding](https://github.com/dotnet/designs/issues/3)</span></span>   

