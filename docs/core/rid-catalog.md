---
title: ".NET Core 執行階段識別項 (RID) 目錄"
description: "了解執行階段識別碼 (RID) 以及 RID 在 .NET Core 中的使用方式。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 08/22/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b2032f5d-771f-48d9-917c-587d9509035c
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3490fb639efd223dc36190324bdf3a06bc23c10e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="net-core-runtime-identifier-rid-catalog"></a><span data-ttu-id="b51bc-104">.NET Core 執行階段識別項 (RID) 目錄</span><span class="sxs-lookup"><span data-stu-id="b51bc-104">.NET Core Runtime IDentifier (RID) catalog</span></span>

## <a name="what-are-rids"></a><span data-ttu-id="b51bc-105">什麼是 RID？</span><span class="sxs-lookup"><span data-stu-id="b51bc-105">What are RIDs?</span></span>
<span data-ttu-id="b51bc-106">RID 是*執行階段識別項*的縮寫。</span><span class="sxs-lookup"><span data-stu-id="b51bc-106">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="b51bc-107">RID 可用來識別執行應用程式或資產 (亦即組件) 的目標作業系統。</span><span class="sxs-lookup"><span data-stu-id="b51bc-107">RIDs are used to identify target operating systems where an application or asset (that is, assembly) will run.</span></span> <span data-ttu-id="b51bc-108">它們看起來類似："ubuntu.14.04-x64"、"win7-x64"、"osx.10.11-x64"。</span><span class="sxs-lookup"><span data-stu-id="b51bc-108">They look like this: "ubuntu.14.04-x64", "win7-x64", "osx.10.11-x64".</span></span> <span data-ttu-id="b51bc-109">針對具有原生相依性的套件，RID 也可指定能在哪些平台上還原套件。</span><span class="sxs-lookup"><span data-stu-id="b51bc-109">For the packages with native dependencies, it will designate on which platforms the package can be restored.</span></span> 

<span data-ttu-id="b51bc-110">請務必注意，RID 是不透明的字串。</span><span class="sxs-lookup"><span data-stu-id="b51bc-110">It is important to note that RIDs are really opaque strings.</span></span> <span data-ttu-id="b51bc-111">這表示它們必須完全相符，使用這些項目的作業才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="b51bc-111">This means that they have to match exactly for operations using them to work.</span></span> <span data-ttu-id="b51bc-112">舉例來說，讓我們來看看[基礎作業系統](https://elementary.io/)的案例，這個作業系統是 Ubuntu 14.04 的直接複製品。</span><span class="sxs-lookup"><span data-stu-id="b51bc-112">As an example, let us consider the case of [Elementary OS](https://elementary.io/), which is a straightforward clone of Ubuntu 14.04.</span></span> <span data-ttu-id="b51bc-113">雖然 .NET Core 和 CLI 可在該版本的 Ubuntu 上運作，但如果您不經任何修改就嘗試在基礎作業系統中加以使用，任何套件的還原作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="b51bc-113">Although .NET Core and CLI work on top of that version of Ubuntu, if you try to use them on Elementary OS without any modifications, the restore operation for any package will fail.</span></span> <span data-ttu-id="b51bc-114">這是因為我們目前沒有任何 RID 指定將基礎作業系統做為平台。</span><span class="sxs-lookup"><span data-stu-id="b51bc-114">This is because we currently don't have a RID that designates Elementary OS as a platform.</span></span> 

<span data-ttu-id="b51bc-115">代表具體作業系統的 RID 通常遵循 `[os].[version]-[arch]` 這個模式，其中：</span><span class="sxs-lookup"><span data-stu-id="b51bc-115">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[arch]` where:</span></span>
- <span data-ttu-id="b51bc-116">`ubuntu` 是作業系統 Moniker，例如 `[os]`。</span><span class="sxs-lookup"><span data-stu-id="b51bc-116">`[os]` is the operating system moniker, for example, `ubuntu`.</span></span>
- <span data-ttu-id="b51bc-117">`[version]` 是作業系統版本，其中以點 (`.`) 來分隔版本號碼，例如 `15.10`，其精確度足以合理允許資產將目標設為該版本所代表的作業系統平台 API。</span><span class="sxs-lookup"><span data-stu-id="b51bc-117">`[version]` is the operating system version in the form of a dot (`.`) separated version number, for example, `15.10`, accurate enough to reasonably enable assets to target operating system platform APIs represented by that version.</span></span>
  - <span data-ttu-id="b51bc-118">此項目**不應為**行銷版本，因為行銷版本通常代表多個作業系統個別版本，且搭配不同平台 API 介面區。</span><span class="sxs-lookup"><span data-stu-id="b51bc-118">This **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>
- <span data-ttu-id="b51bc-119">`[arch]` 是處理器架構，例如 `x86`、`x64`、`arm`、`arm64` 等。</span><span class="sxs-lookup"><span data-stu-id="b51bc-119">`[arch]` is the processor architecture, for example, `x86`, `x64`, `arm`, `arm64`, etc.</span></span>

<span data-ttu-id="b51bc-120">`Microsoft.NETCore.Platforms` 套件的 `runtime.json` 檔案中有定義 RID 圖形，您可以在 [CoreFX 存放庫](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json)中看到這個檔案。</span><span class="sxs-lookup"><span data-stu-id="b51bc-120">The RID graph is defined in a package called `Microsoft.NETCore.Platforms` in a file called `runtime.json`, which you can see on the [CoreFX repo](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json).</span></span> <span data-ttu-id="b51bc-121">使用此檔案時，您會發現部分 RID 當中有 `"#import"` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b51bc-121">If you use this file, you will notice that some of the RIDs have an `"#import"` statement in them.</span></span> <span data-ttu-id="b51bc-122">這些陳述式是相容性陳述式。</span><span class="sxs-lookup"><span data-stu-id="b51bc-122">These statements are compatibility statements.</span></span> <span data-ttu-id="b51bc-123">這表示如果某個 RID 包含匯入的 RID，它就可能是該 RID 還原套件的目標。</span><span class="sxs-lookup"><span data-stu-id="b51bc-123">That means that a RID that has an imported RID in it can be a target for restoring packages for that RID.</span></span> <span data-ttu-id="b51bc-124">聽起來有點令人困惑，讓我們來看看範例。</span><span class="sxs-lookup"><span data-stu-id="b51bc-124">Slightly confusing, but let's look at an example.</span></span> <span data-ttu-id="b51bc-125">舉 macOS 來說：</span><span class="sxs-lookup"><span data-stu-id="b51bc-125">Let's take a look at macOS:</span></span>

```json
"osx.10.11-x64": {
    "#import": [ "osx.10.11", "osx.10.10-x64" ]
}
```
<span data-ttu-id="b51bc-126">上述 RID 指定 `osx.10.11-x64` 匯入 `osx.10.10-x64`。</span><span class="sxs-lookup"><span data-stu-id="b51bc-126">The above RID specifies that `osx.10.11-x64` imports `osx.10.10-x64`.</span></span> <span data-ttu-id="b51bc-127">這表示，如果套件指定在 `osx.10.11-x64` 上需具備 `osx.10.10-x64`，則在還原套件時 NuGet 可順利還原這些套件。</span><span class="sxs-lookup"><span data-stu-id="b51bc-127">This means that when restoring packages, NuGet will be able to restore packages that specify that they need `osx.10.10-x64` on `osx.10.11-x64`.</span></span>

<span data-ttu-id="b51bc-128">稍大的 RID 圖表範例：</span><span class="sxs-lookup"><span data-stu-id="b51bc-128">A slightly bigger example RID graph:</span></span>  

- `win10-arm`
  - `win10`
  - `win81-arm`
    - `win81`
    - `win8-arm`
      - `win8`
        - `win7`
          - `win`
            - `any`

<span data-ttu-id="b51bc-129">所有的 RID 最終將對應至根 `any` RID。</span><span class="sxs-lookup"><span data-stu-id="b51bc-129">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="b51bc-130">雖然 RID 似乎很容易使用，但在使用時也要謹記一些特殊的注意事項︰</span><span class="sxs-lookup"><span data-stu-id="b51bc-130">Although they look easy enough to use, there are some special things about RIDs that you have to keep in mind when working with them:</span></span>

* <span data-ttu-id="b51bc-131">它們是**不透明字串**，且應該視為黑箱處理。</span><span class="sxs-lookup"><span data-stu-id="b51bc-131">They are **opaque strings** and should be treated as black boxes</span></span>
    * <span data-ttu-id="b51bc-132">您不應以程式設計方式建構 RID。</span><span class="sxs-lookup"><span data-stu-id="b51bc-132">You should not construct RIDs programmatically</span></span>
* <span data-ttu-id="b51bc-133">您必須使用已針對平台定義且這份文件中有說明的 RID。</span><span class="sxs-lookup"><span data-stu-id="b51bc-133">You need to use the RIDs that are already defined for the platform and this document shows that</span></span>
* <span data-ttu-id="b51bc-134">RID 具有針對性，因此請不要從實際的 RID 值來進行假設；請參閱這份文件，判斷特定平台所需的 RID。</span><span class="sxs-lookup"><span data-stu-id="b51bc-134">The RIDs do need to be specific so don't assume anything from the actual RID value; please consult this document to determine which RID(s) you need for a given platform</span></span>

## <a name="using-rids"></a><span data-ttu-id="b51bc-135">使用 RID</span><span class="sxs-lookup"><span data-stu-id="b51bc-135">Using RIDs</span></span>
<span data-ttu-id="b51bc-136">若要使用 RID，必須先了解有哪些 RID。</span><span class="sxs-lookup"><span data-stu-id="b51bc-136">In order to use RIDs, you have to know which RIDs there are.</span></span> <span data-ttu-id="b51bc-137">新的 RID 會定期新增至平台。</span><span class="sxs-lookup"><span data-stu-id="b51bc-137">New RIDs are added regularly to the platform.</span></span> <span data-ttu-id="b51bc-138">如需最新的版本，請查看 CoreFX 存放庫上的 [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) 檔案。</span><span class="sxs-lookup"><span data-stu-id="b51bc-138">For the latest version, please check the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

> [!NOTE]
> <span data-ttu-id="b51bc-139">我們正努力以互動性更高的形式提供這些資訊。</span><span class="sxs-lookup"><span data-stu-id="b51bc-139">We are working towards getting this information into a more interactive form.</span></span> <span data-ttu-id="b51bc-140">等這項工作完成時，此頁面即會更新為指向該工具及/或其使用方式的文件。</span><span class="sxs-lookup"><span data-stu-id="b51bc-140">When that happens, this page will be updated to point to that tool and/or its usage documentation.</span></span> 

## <a name="windows-rids"></a><span data-ttu-id="b51bc-141">Windows RID</span><span class="sxs-lookup"><span data-stu-id="b51bc-141">Windows RIDs</span></span>

* <span data-ttu-id="b51bc-142">Windows 7/Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="b51bc-142">Windows 7 / Windows Server 2008 R2</span></span>
    * `win7-x64`
    * `win7-x86`
* <span data-ttu-id="b51bc-143">Windows 8/Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="b51bc-143">Windows 8 / Windows Server 2012</span></span>
    * `win8-x64`
    * `win8-x86`
    * `win8-arm`
* <span data-ttu-id="b51bc-144">Windows 8.1/Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="b51bc-144">Windows 8.1 / Windows Server 2012 R2</span></span>
    * `win81-x64`
    * `win81-x86`
    * `win81-arm`
* <span data-ttu-id="b51bc-145">Windows 10/Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="b51bc-145">Windows 10 / Windows Server 2016</span></span>
    * `win10-x64`
    * `win10-x86`
    * `win10-arm`
    * `win10-arm64`

## <a name="linux-rids"></a><span data-ttu-id="b51bc-146">Linux RID</span><span class="sxs-lookup"><span data-stu-id="b51bc-146">Linux RIDs</span></span>

* <span data-ttu-id="b51bc-147">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="b51bc-147">Red Hat Enterprise Linux</span></span>
    * `rhel.7-x64`
* <span data-ttu-id="b51bc-148">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="b51bc-148">Ubuntu</span></span>
    * `ubuntu.14.04-x64`
    * `ubuntu.14.10-x64`
    * `ubuntu.15.04-x64`
    * `ubuntu.15.10-x64`
    * `ubuntu.16.04-x64`
    * `ubuntu.16.10-x64`
* <span data-ttu-id="b51bc-149">CentOS</span><span class="sxs-lookup"><span data-stu-id="b51bc-149">CentOS</span></span>
    * `centos.7-x64`
* <span data-ttu-id="b51bc-150">Debian</span><span class="sxs-lookup"><span data-stu-id="b51bc-150">Debian</span></span>
    * `debian.8-x64`
* <span data-ttu-id="b51bc-151">Fedora</span><span class="sxs-lookup"><span data-stu-id="b51bc-151">Fedora</span></span>
    * `fedora.23-x64`
    * `fedora.24-x64`
* <span data-ttu-id="b51bc-152">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="b51bc-152">OpenSUSE</span></span>
    * `opensuse.13.2-x64`
    * `opensuse.42.1-x64`
* <span data-ttu-id="b51bc-153">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="b51bc-153">Oracle Linux</span></span>
    * `ol.7-x64`
    * `ol.7.0-x64`
    * `ol.7.1-x64`
    * `ol.7.2-x64`
* <span data-ttu-id="b51bc-154">目前支援的 Ubuntu 衍生項目</span><span class="sxs-lookup"><span data-stu-id="b51bc-154">Currently supported Ubuntu derivatives</span></span> 
    * `linuxmint.17-x64`
    * `linuxmint.17.1-x64`
    * `linuxmint.17.2-x64`
    * `linuxmint.17.3-x64`
    * `linuxmint.18-x64`

## <a name="os-x-rids"></a><span data-ttu-id="b51bc-155">OS X RID</span><span class="sxs-lookup"><span data-stu-id="b51bc-155">OS X RIDs</span></span>

* `osx.10.10-x64`
* `osx.10.11-x64`
* `osx.10.12-x64`

