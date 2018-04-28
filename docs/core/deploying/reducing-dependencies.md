---
title: 減少與 project.json 的封裝相依性
description: 撰寫以 project.json 為基礎的程式庫時，請降低套件相依性。
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 647d850c1629cddc1584a2044174838930b2fb1d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="ef769-103">減少與 project.json 的封裝相依性</span><span class="sxs-lookup"><span data-stu-id="ef769-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="ef769-104">本文涵蓋撰寫 `project.json` 程式庫時，您需要了解的降低封裝相依性的內容。</span><span class="sxs-lookup"><span data-stu-id="ef769-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="ef769-105">在本文的最後，您會了解如何撰寫程式庫，令它只使用需要的相依性。</span><span class="sxs-lookup"><span data-stu-id="ef769-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span> 

## <a name="why-its-important"></a><span data-ttu-id="ef769-106">為何重要</span><span class="sxs-lookup"><span data-stu-id="ef769-106">Why it's Important</span></span>

<span data-ttu-id="ef769-107">.NET Core 是由 NuGet 封裝組成的產品。</span><span class="sxs-lookup"><span data-stu-id="ef769-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="ef769-108">必要的封裝是 [.NETStandard.Library 中繼封裝](https://www.nuget.org/packages/NETStandard.Library) \(英文\)，由 NuGet 封裝組成的其他封裝。</span><span class="sxs-lookup"><span data-stu-id="ef769-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span>  <span data-ttu-id="ef769-109">它提供的一組封裝，保證都能在多個 .NET 實作上運作，例如 .NET Framework、.NET Core 和 Xamarin/Mono。</span><span class="sxs-lookup"><span data-stu-id="ef769-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core and Xamarin/Mono.</span></span>

<span data-ttu-id="ef769-110">不過，您的程式庫有極大的可能不會使用其包含的每個單一封裝。</span><span class="sxs-lookup"><span data-stu-id="ef769-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="ef769-111">在撰寫程式庫並透過 NuGet 散發時，最佳的作法是將相依性「修剪」至實際使用的封裝。</span><span class="sxs-lookup"><span data-stu-id="ef769-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="ef769-112">這會減少 NuGet 封裝的整體使用量。</span><span class="sxs-lookup"><span data-stu-id="ef769-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="ef769-113">作法</span><span class="sxs-lookup"><span data-stu-id="ef769-113">How to do it</span></span>

<span data-ttu-id="ef769-114">目前沒有任何修剪封裝參考的正式 `dotnet` 命令。</span><span class="sxs-lookup"><span data-stu-id="ef769-114">Currently, there is no official `dotnet` command which trims package references.</span></span>  <span data-ttu-id="ef769-115">您必須改以手動作業。</span><span class="sxs-lookup"><span data-stu-id="ef769-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="ef769-116">一般程序如下所示︰</span><span class="sxs-lookup"><span data-stu-id="ef769-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="ef769-117">參考您 `project.json` 的 `dependencies` 區段的 `NETStandard.Library` 版本 `1.6.0`。</span><span class="sxs-lookup"><span data-stu-id="ef769-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="ef769-118">從命令列使用 `dotnet restore` ([請參閱附註](#dotnet-restore-note)) 還原套件。</span><span class="sxs-lookup"><span data-stu-id="ef769-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="ef769-119">檢查 `project.lock.json` 檔案，找出 `NETSTandard.Library` 區段。</span><span class="sxs-lookup"><span data-stu-id="ef769-119">Inspect the `project.lock.json` file and find the `NETSTandard.Library` section.</span></span>  <span data-ttu-id="ef769-120">它在靠近檔案開頭處。</span><span class="sxs-lookup"><span data-stu-id="ef769-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="ef769-121">複製 `dependencies` 下列出的所有封裝。</span><span class="sxs-lookup"><span data-stu-id="ef769-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="ef769-122">移除 `.NETStandard.Library` 參考，並以複製的封裝取而代之。</span><span class="sxs-lookup"><span data-stu-id="ef769-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="ef769-123">移除您不需要的封裝參考。</span><span class="sxs-lookup"><span data-stu-id="ef769-123">Remove references to packages you don't need.</span></span>


<span data-ttu-id="ef769-124">您可以下列方法之一，找出不需要的封裝︰</span><span class="sxs-lookup"><span data-stu-id="ef769-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="ef769-125">試驗與錯誤。</span><span class="sxs-lookup"><span data-stu-id="ef769-125">Trial and error.</span></span>  <span data-ttu-id="ef769-126">這牽涉到移除封裝、還原、查看程式庫是否仍在編譯，以及重複此程序。</span><span class="sxs-lookup"><span data-stu-id="ef769-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="ef769-127">使用諸如 [ILSpy](http://ilspy.net) 或 [.NET 反射程式](http://www.red-gate.com/products/dotnet-development/reflector)等工具預覽參考，查看程式碼實際使用的參考。</span><span class="sxs-lookup"><span data-stu-id="ef769-127">Using a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span>  <span data-ttu-id="ef769-128">接著移除與所用類型不對應的封裝。</span><span class="sxs-lookup"><span data-stu-id="ef769-128">You can then remove packages which don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="ef769-129">範例</span><span class="sxs-lookup"><span data-stu-id="ef769-129">Example</span></span> 

<span data-ttu-id="ef769-130">假設您撰寫的程式庫提供了泛型集合類型的額外功能。</span><span class="sxs-lookup"><span data-stu-id="ef769-130">Imagine that you wrote a library which provided additional functionality to generic collection types.</span></span>  <span data-ttu-id="ef769-131">這類程式庫需要依賴如 `System.Collections` 的封裝，但可能完全不依賴如 `System.Net.Http` 的封裝。</span><span class="sxs-lookup"><span data-stu-id="ef769-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span>  <span data-ttu-id="ef769-132">如此，將封裝相依性修剪至此程式庫所需就很好！</span><span class="sxs-lookup"><span data-stu-id="ef769-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="ef769-133">若要修剪此程式庫，您可以從 `project.json` 檔案開始，將參考加入 `NETStandard.Library` 版本 `1.6.0`。</span><span class="sxs-lookup"><span data-stu-id="ef769-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="ef769-134">接下來，使用 `dotnet restore` ([請參閱附註](#dotnet-restore-note)) 還原套件、檢查 `project.lock.json` 檔案，找出所有還原的 `NETSTandard.Library` 套件。</span><span class="sxs-lookup"><span data-stu-id="ef769-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETSTandard.Library`.</span></span>

<span data-ttu-id="ef769-135">以下是以 `netstandard1.0` 為目標時，`project.lock.json` 檔案中相關區段的樣貌：</span><span class="sxs-lookup"><span data-stu-id="ef769-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

<span data-ttu-id="ef769-136">接下來，將封裝參考複製到程式庫 `project.json` 檔案的 `dependencies` 區段，取代 `NETStandard.Library` 參考︰</span><span class="sxs-lookup"><span data-stu-id="ef769-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

<span data-ttu-id="ef769-137">這是很大數量的封裝，其中有許多對擴充集合類型完全沒必要。</span><span class="sxs-lookup"><span data-stu-id="ef769-137">That's quite a lot of packages, many of which which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="ef769-138">您可以手動移除封裝，或使用 [ILSpy](http://ilspy.net) 或 [.NET 反射程式](http://www.red-gate.com/products/dotnet-development/reflector)等工具識別程式碼實際使用的封裝。</span><span class="sxs-lookup"><span data-stu-id="ef769-138">You can either remove packages manually or use a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="ef769-139">修剪過的封裝可能看起來像這樣︰</span><span class="sxs-lookup"><span data-stu-id="ef769-139">Here's what a trimmed package could look like:</span></span>

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="ef769-140">現在，它的使用量比之前依賴 `NETStandard.Library` 中繼封裝時小。</span><span class="sxs-lookup"><span data-stu-id="ef769-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]