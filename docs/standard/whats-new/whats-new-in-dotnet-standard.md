---
title: "在.NET 標準最新消息"
ms.custom: updateeachrelease
ms.date: 11/08/2017
ms.prod: .net
ms.topic: article
ms.technology: dotnet-standard
ms.##devlang: dotnet
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e938c009b79af3b2f36094bbb74f4d38baeeac0b
ms.sourcegitcommit: 281070dee88db86ec3bb4634d5f558d1a4e159dd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2017
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="a79de-102">在.NET 標準最新消息</span><span class="sxs-lookup"><span data-stu-id="a79de-102">What's new in the .NET Standard</span></span>

<span data-ttu-id="a79de-103">.NET 標準會定義一組版本必須符合標準的該版本的.NET 實作應用程式開發介面的型式規格。</span><span class="sxs-lookup"><span data-stu-id="a79de-103">The .NET Standard is a formal specification that defines a versioned set of APIs which must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="a79de-104">.NET Standard 是以程式庫開發人員為目標。</span><span class="sxs-lookup"><span data-stu-id="a79de-104">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="a79de-105">以.NET 標準的版本為目標的程式庫可以用於任何支援的標準版的.NET Framework 中，.NET Core 或 Xamarin 實作。</span><span class="sxs-lookup"><span data-stu-id="a79de-105">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="a79de-106">.NET 標準的最新版本為 2.0。</span><span class="sxs-lookup"><span data-stu-id="a79de-106">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="a79de-107">它是為了搭配.NET Core 2.0 SDK，以及 Visual Studio 2017 版本 15.3 與安裝的.NET Core 工作負載。</span><span class="sxs-lookup"><span data-stu-id="a79de-107">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="a79de-108">支援的.NET 實作</span><span class="sxs-lookup"><span data-stu-id="a79de-108">Supported .NET implementations</span></span>

<span data-ttu-id="a79de-109">標準.NET 2.0 支援下列.NET 實作：</span><span class="sxs-lookup"><span data-stu-id="a79de-109">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="a79de-110">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="a79de-110">.NET Core 2.0</span></span>
- <span data-ttu-id="a79de-111">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="a79de-111">.NET Framework 4.6.1</span></span>
- <span data-ttu-id="a79de-112">單聲道 5.4</span><span class="sxs-lookup"><span data-stu-id="a79de-112">Mono 5.4</span></span>
- <span data-ttu-id="a79de-113">Xamarin.iOS 10.14</span><span class="sxs-lookup"><span data-stu-id="a79de-113">Xamarin.iOS 10.14</span></span>
- <span data-ttu-id="a79de-114">Xamarin.Mac 3.8</span><span class="sxs-lookup"><span data-stu-id="a79de-114">Xamarin.Mac 3.8</span></span>
- <span data-ttu-id="a79de-115">Xamarin.Android 8.0</span><span class="sxs-lookup"><span data-stu-id="a79de-115">Xamarin.Android 8.0</span></span>
- <span data-ttu-id="a79de-116">通用 Windows 平台 10.0.16299</span><span class="sxs-lookup"><span data-stu-id="a79de-116">Universal Windows Platform 10.0.16299</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="a79de-117">標準.NET 2.0 中最新消息</span><span class="sxs-lookup"><span data-stu-id="a79de-117">What's new in the .NET Standard 2.0</span></span>
 
<span data-ttu-id="a79de-118">標準.NET 2.0 包含下列新功能：</span><span class="sxs-lookup"><span data-stu-id="a79de-118">The .NET Standard 2.0 includes the following new features:</span></span>

<span data-ttu-id="a79de-119">**一組大幅擴充的應用程式開發介面**</span><span class="sxs-lookup"><span data-stu-id="a79de-119">**A vastly expanded set of APIs**</span></span>

<span data-ttu-id="a79de-120">1.6 版中，透過.NET 標準包含應用程式開發介面相當小的子集。</span><span class="sxs-lookup"><span data-stu-id="a79de-120">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="a79de-121">當中排除的許多常用的.NET Framework 或 Xamarin 中使用應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="a79de-121">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="a79de-122">這讓事情更加開發，因為它需要開發人員在他們所開發的應用程式和程式庫的目標多個.NET 實作時，會尋找合適的熟悉的應用程式開發介面的取代。</span><span class="sxs-lookup"><span data-stu-id="a79de-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="a79de-123">標準.NET 2.0 藉由新增超過 20,000 多個應用程式開發介面比可用的.NET 標準 1.6，舊版的標準解決這項限制。</span><span class="sxs-lookup"><span data-stu-id="a79de-123">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="a79de-124">如需已新增至.NET 標準 2.0 Api，請參閱[.NET 標準 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)。</span><span class="sxs-lookup"><span data-stu-id="a79de-124">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span> 

<span data-ttu-id="a79de-125">有些附加的<xref:System>.NET Standard 2.0 中的命名空間包含：</span><span class="sxs-lookup"><span data-stu-id="a79de-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="a79de-126">支援<xref:System.AppDomain>類別。</span><span class="sxs-lookup"><span data-stu-id="a79de-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="a79de-127">更佳的使用中的其他成員的陣列支援<xref:System.Array>類別。</span><span class="sxs-lookup"><span data-stu-id="a79de-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="a79de-128">更佳的使用中的其他成員的屬性支援<xref:System.Attribute>類別。</span><span class="sxs-lookup"><span data-stu-id="a79de-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="a79de-129">支援和其他格式選項更好行事曆<xref:System.DateTime>值。</span><span class="sxs-lookup"><span data-stu-id="a79de-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="a79de-130">其他<xref:System.Decimal>捨入的功能。</span><span class="sxs-lookup"><span data-stu-id="a79de-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="a79de-131">中的其他功能<xref:System.Environment>類別。</span><span class="sxs-lookup"><span data-stu-id="a79de-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="a79de-132">增強透過記憶體回收行程控制<xref:System.GC>類別。</span><span class="sxs-lookup"><span data-stu-id="a79de-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="a79de-133">增強的支援字串比較、 列舉型別，以及在正規化<xref:System.String>類別。</span><span class="sxs-lookup"><span data-stu-id="a79de-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="a79de-134">支援日光節約調整和轉換次數<xref:System.TimeZoneInfo.AdjustmentRule>和<xref:System.TimeZoneInfo.TransitionTime>類別。</span><span class="sxs-lookup"><span data-stu-id="a79de-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="a79de-135">中的功能中大幅增強<xref:System.Type>類別。</span><span class="sxs-lookup"><span data-stu-id="a79de-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="a79de-136">加強支援還原序列化的例外狀況物件所加入的例外狀況建構函式<xref:System.Runtime.Serialization.SerializationInfo>和<xref:System.Runtime.Serialization.StreamingContext>參數。</span><span class="sxs-lookup"><span data-stu-id="a79de-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

<span data-ttu-id="a79de-137">**.NET Framework 程式庫支援**</span><span class="sxs-lookup"><span data-stu-id="a79de-137">**Support for .NET Framework libraries**</span></span>

<span data-ttu-id="a79de-138">非常龐大的大部分程式庫的目標.NET Framework，而不是標準.NET。</span><span class="sxs-lookup"><span data-stu-id="a79de-138">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="a79de-139">不過，大部分的這些文件庫中的呼叫會隨附的.NET 標準 2.0 api。</span><span class="sxs-lookup"><span data-stu-id="a79de-139">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="a79de-140">從.NET 標準 2.0 開始，您可以存取.NET Framework 程式庫從.NET 標準程式庫使用[相容性填充碼](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification)。</span><span class="sxs-lookup"><span data-stu-id="a79de-140">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="a79de-141">此相容性層級而言是透明開發人員;您沒有執行任何動作來充分利用.NET Framework 程式庫。</span><span class="sxs-lookup"><span data-stu-id="a79de-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="a79de-142">一個需求是.NET Framework 類別庫所呼叫之 Api 都必須包含在標準.NET 2.0。</span><span class="sxs-lookup"><span data-stu-id="a79de-142">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

<span data-ttu-id="a79de-143">**適用於 Visual Basic 的支援**</span><span class="sxs-lookup"><span data-stu-id="a79de-143">**Support for Visual Basic**</span></span>

<span data-ttu-id="a79de-144">您現在可以開發在 Visual Basic 中的.NET 標準程式庫。</span><span class="sxs-lookup"><span data-stu-id="a79de-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="a79de-145">適用於 Visual Basic 開發人員使用 Visual Studio 2017 版本 15.3 或更新版本安裝的.NET Core 工作負載，Visual Studio 現在包含.NET 標準的類別庫範本。</span><span class="sxs-lookup"><span data-stu-id="a79de-145">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="a79de-146">使用其他開發工具和環境的 Visual Basic 開發人員，您可以使用[dotnet 新](../../core/tools/dotnet-new.md)命令建立的.NET 標準程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="a79de-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="a79de-147">如需詳細資訊，請參閱[工具支援的.NET 標準程式庫](#tooling)。</span><span class="sxs-lookup"><span data-stu-id="a79de-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling).</span></span>

<span data-ttu-id="a79de-148"><a name="tooling" />**工具支援的.NET 標準程式庫**</span><span class="sxs-lookup"><span data-stu-id="a79de-148"><a name="tooling" />**Tooling support for .NET Standard libraries**</span></span>

<span data-ttu-id="a79de-149">版的.NET Core 2.0 和.NET Standard 2.0 中，這兩個 Visual Studio 2017 和[.NET Core 命令列介面 (CLI)](../../core/tools/index.md)包含工具支援建立.NET 標準程式庫。</span><span class="sxs-lookup"><span data-stu-id="a79de-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span> 

<span data-ttu-id="a79de-150">如果您安裝 Visual Studio 中以**.NET Core 跨平台開發**工作負載，您可以建立的.NET 標準 2.0 程式庫專案所使用的專案範本，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="a79de-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows.</span></span> 

# <a name="ctabcsharp"></a>[<span data-ttu-id="a79de-151">C#</span><span class="sxs-lookup"><span data-stu-id="a79de-151">C#</span></span>](#tab/csharp)
![加入新.NET 標準程式庫專案](./media/std-project-cs.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="a79de-153">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a79de-153">Visual Basic</span></span>](#tab/visual-basic)
<a name="add-new-net-standard-library-projectmediastd-project-vbpng"></a>![加入新.NET 標準程式庫專案](./media/std-project-vb.png)
---

<span data-ttu-id="a79de-155">如果您使用.NET 核心 CLI 下列[dotnet 新](../../core/tools/dotnet-new.md)命令會建立以.NET 標準 2.0 為目標的類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="a79de-155">If you are using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0.</span></span>

```csharp
dotnet new classlib
```
```vb
dotnet new classlib -lang vb
```
  
## <a name="see-also"></a><span data-ttu-id="a79de-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a79de-156">See Also</span></span>
<span data-ttu-id="a79de-157">[.NET 標準](../net-standard.md)
[導入.NET 標準](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span><span class="sxs-lookup"><span data-stu-id="a79de-157">[.NET Standard](../net-standard.md)
[Introducing .NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span></span>
