---
title: .NET Standard 的新功能
description: 本文摘要說明 .NET Standard 的每個新版本中的新功能和增強功能。
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.prod: dotnet-whatsnew
ms.openlocfilehash: 299477a7375381fa7f8064562e2a68e221944a05
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817170"
---
# <a name="whats-new-in-net-standard"></a><span data-ttu-id="1fa81-103">.NET Standard 的新功能</span><span class="sxs-lookup"><span data-stu-id="1fa81-103">What's new in .NET Standard</span></span>

<span data-ttu-id="1fa81-104">.NET Standard 是正式規格，可定義一組已建立版本的 Api，這些 Api 必須可在符合該標準版本的 .NET 執行上使用。</span><span class="sxs-lookup"><span data-stu-id="1fa81-104">.NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="1fa81-105">.NET Standard 是以程式庫開發人員為目標。</span><span class="sxs-lookup"><span data-stu-id="1fa81-105">.NET Standard is targeted at library developers.</span></span> <span data-ttu-id="1fa81-106">以 .NET Standard 版本為目標的程式庫可以用於任何支援該標準的版本之 .NET Framework、.NET Core 或 Xamarin 實作。</span><span class="sxs-lookup"><span data-stu-id="1fa81-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="1fa81-107">當您選取 .NET Core 工作負載時，.NET Standard 會隨附于 .NET Core SDK 和 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="1fa81-107">.NET Standard is included with the .NET Core SDK, as well as with Visual Studio when you select the .NET Core workload.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="1fa81-108">支援的 .NET 實作</span><span class="sxs-lookup"><span data-stu-id="1fa81-108">Supported .NET implementations</span></span>

<span data-ttu-id="1fa81-109">下列 .NET 部署支援 .NET Standard 2.0：</span><span class="sxs-lookup"><span data-stu-id="1fa81-109">.NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="1fa81-110">.NET Core 2.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="1fa81-110">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="1fa81-111">.NET Framework 4.6.1 或更新版本</span><span class="sxs-lookup"><span data-stu-id="1fa81-111">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="1fa81-112">Mono 5.4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="1fa81-112">Mono 5.4 or later</span></span>
- <span data-ttu-id="1fa81-113">Xamarin.iOS 10.14 或更新版本</span><span class="sxs-lookup"><span data-stu-id="1fa81-113">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="1fa81-114">Xamarin.Mac 3.8 或更新版本</span><span class="sxs-lookup"><span data-stu-id="1fa81-114">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="1fa81-115">Xamarin.Android 8.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="1fa81-115">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="1fa81-116">通用 Windows 平台 10.0.16299 或更新版本</span><span class="sxs-lookup"><span data-stu-id="1fa81-116">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-net-standard-20"></a><span data-ttu-id="1fa81-117">.NET Standard 2.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="1fa81-117">What's new in .NET Standard 2.0</span></span>

<span data-ttu-id="1fa81-118">.NET Standard 2.0 包含下列新功能：</span><span class="sxs-lookup"><span data-stu-id="1fa81-118">.NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="1fa81-119">一組大幅擴充的 API</span><span class="sxs-lookup"><span data-stu-id="1fa81-119">A vastly expanded set of APIs</span></span>

<span data-ttu-id="1fa81-120">在1.6 版中，.NET Standard 包含相對較小的 Api 子集。</span><span class="sxs-lookup"><span data-stu-id="1fa81-120">Through version 1.6, .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="1fa81-121">其中所排除的許多 Api 通常用於 .NET Framework 或 Xamarin 中。</span><span class="sxs-lookup"><span data-stu-id="1fa81-121">Among those excluded were many APIs that were commonly used in .NET Framework or Xamarin.</span></span> <span data-ttu-id="1fa81-122">這讓開發變得複雜，因為當開發人員開發以多個 .NET 實作為目標的應用程式和程式庫時，他們必須尋找熟悉的 API 之合適替代方案。</span><span class="sxs-lookup"><span data-stu-id="1fa81-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="1fa81-123">.NET Standard 2.0 藉由新增超過20000個 Api （比舊版標準的 .NET Standard 1.6）來解決這項限制。</span><span class="sxs-lookup"><span data-stu-id="1fa81-123">.NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="1fa81-124">如需已新增至 .NET Standard 2.0 的 Api 清單，請參閱 [.NET Standard 2.0 與 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)。</span><span class="sxs-lookup"><span data-stu-id="1fa81-124">For a list of the APIs that have been added to .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="1fa81-125">一些新增到 .NET Standard 2.0 中 <xref:System> 命名空間的項目包括：</span><span class="sxs-lookup"><span data-stu-id="1fa81-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="1fa81-126"><xref:System.AppDomain> 類別的支援。</span><span class="sxs-lookup"><span data-stu-id="1fa81-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="1fa81-127">從 <xref:System.Array> 類別中其他成員使用陣列的更好之支援。</span><span class="sxs-lookup"><span data-stu-id="1fa81-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="1fa81-128">從 <xref:System.Attribute> 類別中其他成員使用屬性的更好之支援。</span><span class="sxs-lookup"><span data-stu-id="1fa81-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="1fa81-129"><xref:System.DateTime> 值的更好之行事曆支援和其他格式選項。</span><span class="sxs-lookup"><span data-stu-id="1fa81-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="1fa81-130">其他 <xref:System.Decimal> 四捨五入功能。</span><span class="sxs-lookup"><span data-stu-id="1fa81-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="1fa81-131"><xref:System.Environment> 類別中的其他功能。</span><span class="sxs-lookup"><span data-stu-id="1fa81-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="1fa81-132">增強透過 <xref:System.GC> 類別的記憶體回收行程的控制。</span><span class="sxs-lookup"><span data-stu-id="1fa81-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="1fa81-133">增強 <xref:System.String> 類別中字串比較、列舉和正規化的支援。</span><span class="sxs-lookup"><span data-stu-id="1fa81-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="1fa81-134">支援日光節約調整和 <xref:System.TimeZoneInfo.AdjustmentRule> 與 <xref:System.TimeZoneInfo.TransitionTime> 類別中的轉換時間。</span><span class="sxs-lookup"><span data-stu-id="1fa81-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="1fa81-135">大幅增強 <xref:System.Type> 類別中的功能。</span><span class="sxs-lookup"><span data-stu-id="1fa81-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="1fa81-136">藉由新增包含 <xref:System.Runtime.Serialization.SerializationInfo> 和 <xref:System.Runtime.Serialization.StreamingContext> 參數的例外狀況建構函式，提供例外狀況物件還原序列化更好的支援。</span><span class="sxs-lookup"><span data-stu-id="1fa81-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="1fa81-137">針對 .NET Framework 程式庫的支援</span><span class="sxs-lookup"><span data-stu-id="1fa81-137">Support for .NET Framework libraries</span></span>

<span data-ttu-id="1fa81-138">許多程式庫的目標都是 .NET Framework 而不是 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="1fa81-138">Many libraries target .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="1fa81-139">不過，這些程式庫中的大部分呼叫都是包含在 .NET Standard 2.0 中的 Api。</span><span class="sxs-lookup"><span data-stu-id="1fa81-139">However, most of the calls in those libraries are to APIs that are included in .NET Standard 2.0.</span></span> <span data-ttu-id="1fa81-140">從 .NET Standard 2.0 開始，您可以使用 [相容性填充碼](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification)從 .NET Standard 程式庫存取 .NET Framework 程式庫。</span><span class="sxs-lookup"><span data-stu-id="1fa81-140">Starting with .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="1fa81-141">此相容性層級對開發人員是透明的，您不需要執行任何動作就能利用.NET Framework 程式庫。</span><span class="sxs-lookup"><span data-stu-id="1fa81-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="1fa81-142">單一需求是 .NET Framework 類別庫所呼叫的 Api 必須包含在 .NET Standard 2.0 中。</span><span class="sxs-lookup"><span data-stu-id="1fa81-142">The single requirement is that the APIs called by the .NET Framework class library must be included in .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="1fa81-143">Visual Basic 的支援</span><span class="sxs-lookup"><span data-stu-id="1fa81-143">Support for Visual Basic</span></span>

<span data-ttu-id="1fa81-144">您現在可以在 Visual Basic 中開發 .NET Standard 程式庫。</span><span class="sxs-lookup"><span data-stu-id="1fa81-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="1fa81-145">已安裝 .NET Core 工作負載的 Visual Studio 2019 和 Visual Studio 2017 15.3 版或更新版本，包括 .NET Standard 類別庫範本。</span><span class="sxs-lookup"><span data-stu-id="1fa81-145">Visual Studio 2019 and Visual Studio 2017 version 15.3 or later with the .NET Core workload installed include a .NET Standard Class Library template.</span></span> <span data-ttu-id="1fa81-146">對於使用其他開發工具和環境的 Visual Basic 開發人員，您可以使用 [dotnet new](../../core/tools/dotnet-new.md) 命令來建立 .NET Standard 程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="1fa81-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="1fa81-147">如需詳細資訊，請參閱 [.NET Standard 程式庫的工具支援](#tooling-support-for-net-standard-libraries)。</span><span class="sxs-lookup"><span data-stu-id="1fa81-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="1fa81-148">.NET Standard 程式庫的工具支援</span><span class="sxs-lookup"><span data-stu-id="1fa81-148">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="1fa81-149">隨著 .NET Core 2.0 和 .NET Standard 2.0 的發行，Visual Studio 2017 和 [.NET Core CLI](../../core/tools/index.md) 都包含建立 .NET Standard 程式庫的工具支援。</span><span class="sxs-lookup"><span data-stu-id="1fa81-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="1fa81-150">如果您安裝具有 **.Net Core 跨平臺開發** 工作負載的 Visual Studio，您可以使用專案範本來建立 .NET Standard 2.0 程式庫專案，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="1fa81-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="1fa81-151">C#</span><span class="sxs-lookup"><span data-stu-id="1fa81-151">C#</span></span>](#tab/csharp)

![新增 .NET Standard 程式庫專案](./media/std-project-cs.png)

<span data-ttu-id="1fa81-153">如果您使用的是 .NET Core CLI，下列 [dotnet new](../../core/tools/dotnet-new.md) 命令會建立以 .NET Standard 2.0 為目標的類別庫專案：</span><span class="sxs-lookup"><span data-stu-id="1fa81-153">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="1fa81-154">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fa81-154">Visual Basic</span></span>](#tab/vb)

![新增 .NET Standard 程式庫專案](./media/std-project-vb.png)

<span data-ttu-id="1fa81-156">如果您使用的是 .NET Core CLI，下列 [dotnet new](../../core/tools/dotnet-new.md) 命令會建立以 .NET Standard 2.0 為目標的類別庫專案：</span><span class="sxs-lookup"><span data-stu-id="1fa81-156">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="1fa81-157">請參閱</span><span class="sxs-lookup"><span data-stu-id="1fa81-157">See also</span></span>

- [<span data-ttu-id="1fa81-158">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="1fa81-158">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="1fa81-159">.NET Standard 簡介</span><span class="sxs-lookup"><span data-stu-id="1fa81-159">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
- [<span data-ttu-id="1fa81-160">下載 .NET SDK</span><span class="sxs-lookup"><span data-stu-id="1fa81-160">Download the .NET SDK</span></span>](https://dotnet.microsoft.com/download)
