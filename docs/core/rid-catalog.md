---
title: .NET 執行時間識別碼 (RID) 目錄
description: 深入瞭解執行時間識別碼 (RID) 以及如何在 .NET 中使用 Rid。
ms.date: 01/28/2021
ms.openlocfilehash: e5e1c4712965211b25a02b14a7cf2c91d74d8306
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216001"
---
# <a name="net-rid-catalog"></a><span data-ttu-id="d7d34-103">.NET RID 目錄</span><span class="sxs-lookup"><span data-stu-id="d7d34-103">.NET RID Catalog</span></span>

<span data-ttu-id="d7d34-104">RID 是執行時間 *識別碼* 的縮寫。</span><span class="sxs-lookup"><span data-stu-id="d7d34-104">RID is short for *Runtime Identifier*.</span></span> <span data-ttu-id="d7d34-105">RID 值是用來識別應用程式執行所在的目標平台。</span><span class="sxs-lookup"><span data-stu-id="d7d34-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="d7d34-106">.NET 套件會使用它們來代表 NuGet 套件中的平台特定資產。</span><span class="sxs-lookup"><span data-stu-id="d7d34-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="d7d34-107">下列值是 RID 的範例：`linux-x64`、`ubuntu.14.04-x64`、`win7-x64` 或 `osx.10.12-x64`。</span><span class="sxs-lookup"><span data-stu-id="d7d34-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="d7d34-108">針對具有原生相依性的套件，RID 也可指定能在哪些平台上還原套件。</span><span class="sxs-lookup"><span data-stu-id="d7d34-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="d7d34-109">單一 RID 可在您專案檔的 `<RuntimeIdentifier>` 元素中設定。</span><span class="sxs-lookup"><span data-stu-id="d7d34-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="d7d34-110">可以在專案檔的 `<RuntimeIdentifiers>` 元素中，將多個 RID 定義為以分號分隔的清單。</span><span class="sxs-lookup"><span data-stu-id="d7d34-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="d7d34-111">您也可以使用 `--runtime` 下列 [.net CLI 命令](./tools/index.md)透過選項來使用它們：</span><span class="sxs-lookup"><span data-stu-id="d7d34-111">They're also used via the `--runtime` option with the following [.NET CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="d7d34-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d7d34-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="d7d34-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d7d34-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="d7d34-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d7d34-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="d7d34-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d7d34-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="d7d34-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d7d34-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="d7d34-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d7d34-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="d7d34-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="d7d34-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="d7d34-119">代表具體作業系統的 RID 通常遵循 `[os].[version]-[architecture]-[additional qualifiers]` 這個模式，其中：</span><span class="sxs-lookup"><span data-stu-id="d7d34-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="d7d34-120">`[os]` 是作業/平台系統 Moniker。</span><span class="sxs-lookup"><span data-stu-id="d7d34-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="d7d34-121">例如： `ubuntu` 。</span><span class="sxs-lookup"><span data-stu-id="d7d34-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="d7d34-122">`[version]` 是作業系統版本，使用以點分隔 (`.`) 的版本號碼表示。</span><span class="sxs-lookup"><span data-stu-id="d7d34-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="d7d34-123">例如： `15.10` 。</span><span class="sxs-lookup"><span data-stu-id="d7d34-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="d7d34-124">版本 **不應為** 行銷版本，因為行銷版本通常代表作業系統的多個個別版本，且具有不同平台 API 介面區。</span><span class="sxs-lookup"><span data-stu-id="d7d34-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="d7d34-125">`[architecture]` 處理器架構。</span><span class="sxs-lookup"><span data-stu-id="d7d34-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="d7d34-126">例如：`x86`、`x64`、`arm` 或 `arm64`。</span><span class="sxs-lookup"><span data-stu-id="d7d34-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="d7d34-127">`[additional qualifiers]` 進一步區分不同平台。</span><span class="sxs-lookup"><span data-stu-id="d7d34-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="d7d34-128">例如：`aot`。</span><span class="sxs-lookup"><span data-stu-id="d7d34-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="d7d34-129">RID 圖表</span><span class="sxs-lookup"><span data-stu-id="d7d34-129">RID graph</span></span>

<span data-ttu-id="d7d34-130">RID 圖表或執行階段後援圖形是與彼此相容的 RID 清單。</span><span class="sxs-lookup"><span data-stu-id="d7d34-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="d7d34-131">RID 是在 [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) 套件中定義。</span><span class="sxs-lookup"><span data-stu-id="d7d34-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="d7d34-132">您可以在儲存機制中的檔案 [*runtime.js*](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) 中，看到支援的 RID 和 RID 圖形清單 `dotnet/runtime` 。</span><span class="sxs-lookup"><span data-stu-id="d7d34-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file, which is located in the `dotnet/runtime` repository.</span></span> <span data-ttu-id="d7d34-133">在此檔案中，您可以看到所有 RID (基底項目除外) 都包含 `"#import"` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d7d34-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="d7d34-134">這些陳述式指出相容的 RID。</span><span class="sxs-lookup"><span data-stu-id="d7d34-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="d7d34-135">當 NuGet 還原套件時，它會嘗試尋找與所指定執行階段完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="d7d34-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="d7d34-136">若找不到完全相符的項目，NuGet 會返回到圖形，直到它根據 RID 圖形找到最接近的相容系統。</span><span class="sxs-lookup"><span data-stu-id="d7d34-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="d7d34-137">下列範例是 `osx.10.12-x64` RID 的實際項目：</span><span class="sxs-lookup"><span data-stu-id="d7d34-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="d7d34-138">上述 RID 指定 `osx.10.12-x64` 匯入 `osx.10.11-x64`。</span><span class="sxs-lookup"><span data-stu-id="d7d34-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="d7d34-139">因此，當 NuGet 還原套件時，它會嘗試在套件中尋找與 `osx.10.12-x64` 完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="d7d34-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="d7d34-140">例如，若 NuGet 找不到特定執行階段，它可以還原指定 `osx.10.11-x64` 執行階段的套件。</span><span class="sxs-lookup"><span data-stu-id="d7d34-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="d7d34-141">下列範例顯示也在 *runtime.json* 檔案中定義的稍大 RID 圖形：</span><span class="sxs-lookup"><span data-stu-id="d7d34-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="d7d34-142">所有的 RID 最終將對應至根 `any` RID。</span><span class="sxs-lookup"><span data-stu-id="d7d34-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="d7d34-143">處理 RID 時，您必須謹記一些考量：</span><span class="sxs-lookup"><span data-stu-id="d7d34-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="d7d34-144">請勿嘗試剖析 Rid 以取出元件部分。</span><span class="sxs-lookup"><span data-stu-id="d7d34-144">Don't try to parse RIDs to retrieve component parts.</span></span>
- <span data-ttu-id="d7d34-145">不要以程式設計方式建置 RID。</span><span class="sxs-lookup"><span data-stu-id="d7d34-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="d7d34-146">使用已針對平台定義的 RID。</span><span class="sxs-lookup"><span data-stu-id="d7d34-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="d7d34-147">RID 必須是特定的，因此不要假設實際 RID 值會怎樣。</span><span class="sxs-lookup"><span data-stu-id="d7d34-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="d7d34-148">使用 RID</span><span class="sxs-lookup"><span data-stu-id="d7d34-148">Using RIDs</span></span>

<span data-ttu-id="d7d34-149">若要使用 RID，必須先了解有哪些 RID 存在。</span><span class="sxs-lookup"><span data-stu-id="d7d34-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="d7d34-150">新的值會定期新增至平台。</span><span class="sxs-lookup"><span data-stu-id="d7d34-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="d7d34-151">如需最新的完整版本，請[](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json)參閱存放庫中的 `dotnet/runtime` 檔案runtime.js。</span><span class="sxs-lookup"><span data-stu-id="d7d34-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file in the `dotnet/runtime` repository.</span></span>

<span data-ttu-id="d7d34-152">可移植 Rid 是新增至 RID 圖形的值，不會系結至特定版本或 OS 散發套件。</span><span class="sxs-lookup"><span data-stu-id="d7d34-152">Portable RIDs are values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="d7d34-153">這些是慣用的選擇，特別是在處理多個 Linux 散發版本時，因為大部分的散發 Rid 都對應到可移植 Rid。</span><span class="sxs-lookup"><span data-stu-id="d7d34-153">They are the preferred choice, especially when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="d7d34-154">下列清單顯示用於每個 OS 的一小部分最常見 RID。</span><span class="sxs-lookup"><span data-stu-id="d7d34-154">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="d7d34-155">Windows RID</span><span class="sxs-lookup"><span data-stu-id="d7d34-155">Windows RIDs</span></span>

<span data-ttu-id="d7d34-156">僅列出常見值。</span><span class="sxs-lookup"><span data-stu-id="d7d34-156">Only common values are listed.</span></span> <span data-ttu-id="d7d34-157">如需最新的完整版本，請[](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json)參閱存放庫中的 `dotnet/runtime` 檔案runtime.js。</span><span class="sxs-lookup"><span data-stu-id="d7d34-157">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file in the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="d7d34-158">可攜式</span><span class="sxs-lookup"><span data-stu-id="d7d34-158">Portable</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="d7d34-159">Windows 7/Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="d7d34-159">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="d7d34-160">Windows 8.1/Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d7d34-160">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="d7d34-161">Windows 10/Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="d7d34-161">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="d7d34-162">如需詳細資訊，請參閱 .Net 相依性 [和需求](./install/windows.md#dependencies)。</span><span class="sxs-lookup"><span data-stu-id="d7d34-162">For more information, see [.NET dependencies and requirements](./install/windows.md#dependencies).</span></span>

## <a name="linux-rids"></a><span data-ttu-id="d7d34-163">Linux RID</span><span class="sxs-lookup"><span data-stu-id="d7d34-163">Linux RIDs</span></span>

<span data-ttu-id="d7d34-164">僅列出常見值。</span><span class="sxs-lookup"><span data-stu-id="d7d34-164">Only common values are listed.</span></span> <span data-ttu-id="d7d34-165">如需最新的完整版本，請[](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json)參閱存放庫中的 `dotnet/runtime` 檔案runtime.js。</span><span class="sxs-lookup"><span data-stu-id="d7d34-165">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file in the `dotnet/runtime` repository.</span></span> <span data-ttu-id="d7d34-166">如果下方未列出裝置執行的發行版本，裝置可能可以使用其中一個可攜式 RID。</span><span class="sxs-lookup"><span data-stu-id="d7d34-166">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="d7d34-167">例如，如果 Raspberry Pi 裝置執行未列出的 Linux 發行版本，則可以 `linux-arm` 為目標。</span><span class="sxs-lookup"><span data-stu-id="d7d34-167">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="d7d34-168">可攜式</span><span class="sxs-lookup"><span data-stu-id="d7d34-168">Portable</span></span>
  - <span data-ttu-id="d7d34-169">`linux-x64` (大部分的桌面散發套件，例如 CentOS、Debian、Fedora、Ubuntu 和衍生) </span><span class="sxs-lookup"><span data-stu-id="d7d34-169">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu, and derivatives)</span></span>
  - <span data-ttu-id="d7d34-170">`linux-musl-x64` (使用 [musl](https://wiki.musl-libc.org/projects-using-musl.html) 的輕量發行版本，如 Alpine Linux)</span><span class="sxs-lookup"><span data-stu-id="d7d34-170">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="d7d34-171">`linux-arm` 在 ARM 上執行的 (Linux 散發套件，例如 Raspberry Pi 模型 2 +) 上的 Raspbian</span><span class="sxs-lookup"><span data-stu-id="d7d34-171">`linux-arm` (Linux distributions running on ARM like Raspbian on Raspberry Pi Model 2+)</span></span>
  - <span data-ttu-id="d7d34-172">`linux-arm64` 在 Raspberry Pi 模型 3 +) 上執行于64位 ARM 上的 (Linux 散發套件（如 Ubuntu Server 64 位）</span><span class="sxs-lookup"><span data-stu-id="d7d34-172">`linux-arm64` (Linux distributions running on 64-bit ARM like Ubuntu Server 64-bit on Raspberry Pi Model 3+)</span></span>
- <span data-ttu-id="d7d34-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="d7d34-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="d7d34-174">`rhel-x64` (RHEL 6 版以上已由 `linux-x64` 取代)</span><span class="sxs-lookup"><span data-stu-id="d7d34-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - `rhel.6-x64`
- <span data-ttu-id="d7d34-175">Tizen</span><span class="sxs-lookup"><span data-stu-id="d7d34-175">Tizen</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="d7d34-176">如需詳細資訊，請參閱 .Net 相依性 [和需求](./install/linux.md)。</span><span class="sxs-lookup"><span data-stu-id="d7d34-176">For more information, see [.NET dependencies and requirements](./install/linux.md).</span></span>

## <a name="macos-rids"></a><span data-ttu-id="d7d34-177">macOS RID</span><span class="sxs-lookup"><span data-stu-id="d7d34-177">macOS RIDs</span></span>

<span data-ttu-id="d7d34-178">macOS RID 使用較舊的 "OSX" 商標。</span><span class="sxs-lookup"><span data-stu-id="d7d34-178">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="d7d34-179">僅列出常見值。</span><span class="sxs-lookup"><span data-stu-id="d7d34-179">Only common values are listed.</span></span> <span data-ttu-id="d7d34-180">如需最新的完整版本，請[](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json)參閱存放庫中的 `dotnet/runtime` 檔案runtime.js。</span><span class="sxs-lookup"><span data-stu-id="d7d34-180">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) file in the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="d7d34-181">可攜式</span><span class="sxs-lookup"><span data-stu-id="d7d34-181">Portable</span></span>
  - <span data-ttu-id="d7d34-182">`osx-x64` (最低 OS 版本為 macOS 10.12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="d7d34-182">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="d7d34-183">macOS 10.10  Yosemite</span><span class="sxs-lookup"><span data-stu-id="d7d34-183">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="d7d34-184">macOS 10.11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="d7d34-184">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="d7d34-185">macOS 10.12 Sierra</span><span class="sxs-lookup"><span data-stu-id="d7d34-185">macOS 10.12 Sierra</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="d7d34-186">macOS 10.13 High Sierra</span><span class="sxs-lookup"><span data-stu-id="d7d34-186">macOS 10.13 High Sierra</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="d7d34-187">macOS 10.14 Mojave</span><span class="sxs-lookup"><span data-stu-id="d7d34-187">macOS 10.14 Mojave</span></span>
  - `osx.10.14-x64`
- <span data-ttu-id="d7d34-188">macOS 10.15 Catalina</span><span class="sxs-lookup"><span data-stu-id="d7d34-188">macOS 10.15 Catalina</span></span>
  - `osx.10.15-x64`
- <span data-ttu-id="d7d34-189">macOS 11.01 Big Sur</span><span class="sxs-lookup"><span data-stu-id="d7d34-189">macOS 11.01 Big Sur</span></span>
  - `osx.11.0-x64`
  - `osx.11.0-arm64`

<span data-ttu-id="d7d34-190">如需詳細資訊，請參閱 .Net 相依性 [和需求](./install/macos.md#dependencies)。</span><span class="sxs-lookup"><span data-stu-id="d7d34-190">For more information, see [.NET dependencies and requirements](./install/macos.md#dependencies).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7d34-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7d34-191">See also</span></span>

- [<span data-ttu-id="d7d34-192">執行階段識別碼</span><span class="sxs-lookup"><span data-stu-id="d7d34-192">Runtime IDs</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/readme.md)
