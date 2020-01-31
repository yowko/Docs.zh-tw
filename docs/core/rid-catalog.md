---
title: .NET Core 執行階段識別項 (RID) 目錄
description: 了解執行階段識別碼 (RID) 以及 RID 在 .NET Core 中的使用方式。
ms.date: 02/22/2019
ms.openlocfilehash: 4369e263f1f46c73f04c65e4124f63c68d133520
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789900"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="6055c-103">.NET Core RID 類別目錄</span><span class="sxs-lookup"><span data-stu-id="6055c-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="6055c-104">RID 是*執行階段識別項*的縮寫。</span><span class="sxs-lookup"><span data-stu-id="6055c-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="6055c-105">RID 值是用來識別應用程式執行所在的目標平台。</span><span class="sxs-lookup"><span data-stu-id="6055c-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="6055c-106">.NET 套件會使用它們來代表 NuGet 套件中的平台特定資產。</span><span class="sxs-lookup"><span data-stu-id="6055c-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="6055c-107">下列值是 RID 的範例：`linux-x64`、`ubuntu.14.04-x64`、`win7-x64` 或 `osx.10.12-x64`。</span><span class="sxs-lookup"><span data-stu-id="6055c-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="6055c-108">針對具有原生相依性的套件，RID 也可指定能在哪些平台上還原套件。</span><span class="sxs-lookup"><span data-stu-id="6055c-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="6055c-109">單一 RID 可在您專案檔的 `<RuntimeIdentifier>` 元素中設定。</span><span class="sxs-lookup"><span data-stu-id="6055c-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="6055c-110">可以在專案檔的 `<RuntimeIdentifiers>` 元素中，將多個 RID 定義為以分號分隔的清單。</span><span class="sxs-lookup"><span data-stu-id="6055c-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="6055c-111">它們也可以透過以`--runtime`選項搭配下列 [.NET Core CLI 命令](./tools/index.md)來使用：</span><span class="sxs-lookup"><span data-stu-id="6055c-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="6055c-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="6055c-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="6055c-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="6055c-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="6055c-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="6055c-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="6055c-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="6055c-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="6055c-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="6055c-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="6055c-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="6055c-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="6055c-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="6055c-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="6055c-119">代表具體作業系統的 RID 通常遵循 `[os].[version]-[architecture]-[additional qualifiers]` 這個模式，其中：</span><span class="sxs-lookup"><span data-stu-id="6055c-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="6055c-120">`[os]` 是作業/平台系統 Moniker。</span><span class="sxs-lookup"><span data-stu-id="6055c-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="6055c-121">例如，`ubuntu`。</span><span class="sxs-lookup"><span data-stu-id="6055c-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="6055c-122">`[version]` 是作業系統版本，使用以點分隔 (`.`) 的版本號碼表示。</span><span class="sxs-lookup"><span data-stu-id="6055c-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="6055c-123">例如，`15.10`。</span><span class="sxs-lookup"><span data-stu-id="6055c-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="6055c-124">版本**不應為**行銷版本，因為行銷版本通常代表作業系統的多個個別版本，且具有不同平台 API 介面區。</span><span class="sxs-lookup"><span data-stu-id="6055c-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="6055c-125">`[architecture]` 處理器架構。</span><span class="sxs-lookup"><span data-stu-id="6055c-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="6055c-126">例如：`x86`、`x64`、`arm` 或 `arm64`。</span><span class="sxs-lookup"><span data-stu-id="6055c-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="6055c-127">`[additional qualifiers]` 進一步區分不同平台。</span><span class="sxs-lookup"><span data-stu-id="6055c-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="6055c-128">例如：`aot`。</span><span class="sxs-lookup"><span data-stu-id="6055c-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="6055c-129">RID 圖表</span><span class="sxs-lookup"><span data-stu-id="6055c-129">RID graph</span></span>

<span data-ttu-id="6055c-130">RID 圖表或執行階段後援圖形是與彼此相容的 RID 清單。</span><span class="sxs-lookup"><span data-stu-id="6055c-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="6055c-131">RID 是在 [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) 套件中定義。</span><span class="sxs-lookup"><span data-stu-id="6055c-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="6055c-132">您可以在位於 `dotnet/runtime` 存放庫的[*執行時間. json*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json)檔案中，看到支援的 RID 和 rid 圖表清單。</span><span class="sxs-lookup"><span data-stu-id="6055c-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the `dotnet/runtime` repository.</span></span> <span data-ttu-id="6055c-133">在此檔案中，您可以看到所有 RID (基底項目除外) 都包含 `"#import"` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6055c-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="6055c-134">這些陳述式指出相容的 RID。</span><span class="sxs-lookup"><span data-stu-id="6055c-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="6055c-135">當 NuGet 還原套件時，它會嘗試尋找與所指定執行階段完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="6055c-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="6055c-136">若找不到完全相符的項目，NuGet 會返回到圖形，直到它根據 RID 圖形找到最接近的相容系統。</span><span class="sxs-lookup"><span data-stu-id="6055c-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="6055c-137">下列範例是 `osx.10.12-x64` RID 的實際項目：</span><span class="sxs-lookup"><span data-stu-id="6055c-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="6055c-138">上述 RID 指定 `osx.10.12-x64` 匯入 `osx.10.11-x64`。</span><span class="sxs-lookup"><span data-stu-id="6055c-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="6055c-139">因此，當 NuGet 還原套件時，它會嘗試在套件中尋找與 `osx.10.12-x64` 完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="6055c-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="6055c-140">例如，若 NuGet 找不到特定執行階段，它可以還原指定 `osx.10.11-x64` 執行階段的套件。</span><span class="sxs-lookup"><span data-stu-id="6055c-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="6055c-141">下列範例顯示也在 *runtime.json* 檔案中定義的稍大 RID 圖形：</span><span class="sxs-lookup"><span data-stu-id="6055c-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

<span data-ttu-id="6055c-142">所有的 RID 最終將對應至根 `any` RID。</span><span class="sxs-lookup"><span data-stu-id="6055c-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="6055c-143">處理 RID 時，您必須謹記一些考量：</span><span class="sxs-lookup"><span data-stu-id="6055c-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="6055c-144">RID 是**隱晦字串**，因此必須以黑箱視之。</span><span class="sxs-lookup"><span data-stu-id="6055c-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="6055c-145">不要以程式設計方式建置 RID。</span><span class="sxs-lookup"><span data-stu-id="6055c-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="6055c-146">使用已針對平台定義的 RID。</span><span class="sxs-lookup"><span data-stu-id="6055c-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="6055c-147">RID 必須是特定的，因此不要假設實際 RID 值會怎樣。</span><span class="sxs-lookup"><span data-stu-id="6055c-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="6055c-148">使用 RID</span><span class="sxs-lookup"><span data-stu-id="6055c-148">Using RIDs</span></span>

<span data-ttu-id="6055c-149">若要使用 RID，必須先了解有哪些 RID 存在。</span><span class="sxs-lookup"><span data-stu-id="6055c-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="6055c-150">新的值會定期新增至平台。</span><span class="sxs-lookup"><span data-stu-id="6055c-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="6055c-151">如需最新且完整的版本，請參閱 `dotnet/runtime` 儲存機制上的[執行時間. json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json)檔案。</span><span class="sxs-lookup"><span data-stu-id="6055c-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

<span data-ttu-id="6055c-152">.NET Core 2.0 SDK 引進可攜式 RID 的概念。</span><span class="sxs-lookup"><span data-stu-id="6055c-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="6055c-153">它們是新增到 RID 圖形且未繫結到特定版本或 OS 發行版本的新值，適用於 .NET Core 2.0 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="6055c-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span></span> <span data-ttu-id="6055c-154">由於大部分發行版本的 RID 都會對應至可攜式 RID，因此在處理多個 Linux 發行版本時特別有用。</span><span class="sxs-lookup"><span data-stu-id="6055c-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="6055c-155">下列清單顯示用於每個 OS 的一小部分最常見 RID。</span><span class="sxs-lookup"><span data-stu-id="6055c-155">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="6055c-156">Windows RID</span><span class="sxs-lookup"><span data-stu-id="6055c-156">Windows RIDs</span></span>

<span data-ttu-id="6055c-157">僅列出常見值。</span><span class="sxs-lookup"><span data-stu-id="6055c-157">Only common values are listed.</span></span> <span data-ttu-id="6055c-158">如需最新且完整的版本，請參閱 `dotnet/runtime` 儲存機制上的[執行時間. json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json)檔案。</span><span class="sxs-lookup"><span data-stu-id="6055c-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="6055c-159">可攜式 (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="6055c-159">Portable (.NET Core 2.0 or later versions)</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="6055c-160">Windows 7/Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="6055c-160">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="6055c-161">Windows 8.1/Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6055c-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="6055c-162">Windows 10/Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="6055c-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="6055c-163">如需詳細資訊，請參閱[.Net Core 相依性和需求](install/dependencies.md?tabs=netcore30&pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="6055c-163">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

## <a name="linux-rids"></a><span data-ttu-id="6055c-164">Linux RID</span><span class="sxs-lookup"><span data-stu-id="6055c-164">Linux RIDs</span></span>

<span data-ttu-id="6055c-165">僅列出常見值。</span><span class="sxs-lookup"><span data-stu-id="6055c-165">Only common values are listed.</span></span> <span data-ttu-id="6055c-166">如需最新且完整的版本，請參閱 `dotnet/runtime` 儲存機制上的[執行時間. json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json)檔案。</span><span class="sxs-lookup"><span data-stu-id="6055c-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span> <span data-ttu-id="6055c-167">如果下方未列出裝置執行的發行版本，裝置可能可以使用其中一個可攜式 RID。</span><span class="sxs-lookup"><span data-stu-id="6055c-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="6055c-168">例如，如果 Raspberry Pi 裝置執行未列出的 Linux 發行版本，則可以 `linux-arm` 為目標。</span><span class="sxs-lookup"><span data-stu-id="6055c-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="6055c-169">可攜式 (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="6055c-169">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="6055c-170">`linux-x64` （大部分的桌面散發套件，例如 CentOS、Debian、Fedora、Ubuntu 和衍生版本）</span><span class="sxs-lookup"><span data-stu-id="6055c-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu, and derivatives)</span></span>
  - <span data-ttu-id="6055c-171">`linux-musl-x64` (使用 [musl](https://wiki.musl-libc.org/projects-using-musl.html) 的輕量發行版本，如 Alpine Linux)</span><span class="sxs-lookup"><span data-stu-id="6055c-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="6055c-172">`linux-arm` (在 ARM 上執行的 Linux 發行版本，如 Raspberry Pi)</span><span class="sxs-lookup"><span data-stu-id="6055c-172">`linux-arm` (Linux distributions running on ARM like Raspberry Pi)</span></span>
- <span data-ttu-id="6055c-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="6055c-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="6055c-174">`rhel-x64` (RHEL 6 版以上已由 `linux-x64` 取代)</span><span class="sxs-lookup"><span data-stu-id="6055c-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - <span data-ttu-id="6055c-175">`rhel.6-x64` (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="6055c-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="6055c-176">Tizen (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="6055c-176">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="6055c-177">如需詳細資訊，請參閱[.Net Core 相依性和需求](install/dependencies.md?tabs=netcore30&pivots=os-linux)。</span><span class="sxs-lookup"><span data-stu-id="6055c-177">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-linux).</span></span>

## <a name="macos-rids"></a><span data-ttu-id="6055c-178">macOS RID</span><span class="sxs-lookup"><span data-stu-id="6055c-178">macOS RIDs</span></span>

<span data-ttu-id="6055c-179">macOS RID 使用較舊的 "OSX" 商標。</span><span class="sxs-lookup"><span data-stu-id="6055c-179">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="6055c-180">僅列出常見值。</span><span class="sxs-lookup"><span data-stu-id="6055c-180">Only common values are listed.</span></span> <span data-ttu-id="6055c-181">如需最新且完整的版本，請參閱 `dotnet/runtime` 儲存機制上的[執行時間. json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json)檔案。</span><span class="sxs-lookup"><span data-stu-id="6055c-181">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="6055c-182">可攜式 (.NET Core 2.0 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="6055c-182">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="6055c-183">`osx-x64` (最低 OS 版本為 macOS 10.12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="6055c-183">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="6055c-184">macOS 10.10  Yosemite</span><span class="sxs-lookup"><span data-stu-id="6055c-184">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="6055c-185">macOS 10.11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="6055c-185">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="6055c-186">macOS 10.12 Sierra (.NET Core 1.1 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="6055c-186">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="6055c-187">macOS 10.13 High Sierra (.NET Core 1.1 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="6055c-187">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="6055c-188">macOS 10.14 Mojave (.NET Core 1.1 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="6055c-188">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.14-x64`

<span data-ttu-id="6055c-189">如需詳細資訊，請參閱[.Net Core 相依性和需求](install/dependencies.md?tabs=netcore30&pivots=os-macos)。</span><span class="sxs-lookup"><span data-stu-id="6055c-189">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-macos).</span></span>

## <a name="see-also"></a><span data-ttu-id="6055c-190">請參閱</span><span class="sxs-lookup"><span data-stu-id="6055c-190">See also</span></span>

- [<span data-ttu-id="6055c-191">執行階段識別碼</span><span class="sxs-lookup"><span data-stu-id="6055c-191">Runtime IDs</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/readme.md)
