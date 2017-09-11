---
title: "C# 程式結構 - C# 語言教學課程"
description: "了解 C# 程式的基本建置區塊"
keywords: .NET .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8d8f443f8458cd392c75e9787e612ca1cc3518c7
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="program-structure"></a><span data-ttu-id="361d6-104">程式結構</span><span class="sxs-lookup"><span data-stu-id="361d6-104">Program Structure</span></span>

<span data-ttu-id="361d6-105">C# 語言的重要組織概念如下：程式、命名空間、型別、成員及組件。</span><span class="sxs-lookup"><span data-stu-id="361d6-105">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="361d6-106">C# 程式包含一個或多個原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="361d6-106">C# programs consist of one or more source files.</span></span> <span data-ttu-id="361d6-107">程式宣告型別，其中包含成員並可以依據命名空間分組。</span><span class="sxs-lookup"><span data-stu-id="361d6-107">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="361d6-108">類別和介面都是型別的範例。</span><span class="sxs-lookup"><span data-stu-id="361d6-108">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="361d6-109">欄位、方法、屬性及事件都是成員的範例。</span><span class="sxs-lookup"><span data-stu-id="361d6-109">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="361d6-110">在編譯 C# 語言時，會將它們實際封裝為組件。</span><span class="sxs-lookup"><span data-stu-id="361d6-110">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="361d6-111">組件通常具有副檔名 `.exe` 或 `.dll`，其分別在於實作「應用程式」或「程式庫」。</span><span class="sxs-lookup"><span data-stu-id="361d6-111">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="361d6-112">此範例會在名為 `Acme.Collections` 的命名空間中，宣告稱為 `Stack` 的類別：</span><span class="sxs-lookup"><span data-stu-id="361d6-112">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

<span data-ttu-id="361d6-113">[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]</span><span class="sxs-lookup"><span data-stu-id="361d6-113">[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]</span></span>

<span data-ttu-id="361d6-114">此類別的完整名稱是 `Acme.Collections.Stack`。</span><span class="sxs-lookup"><span data-stu-id="361d6-114">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="361d6-115">該類別包含數個成員︰一個名為 `top` 的欄位、兩個名為 `Push` 和 `Pop` 的方法以及名為 `Entry` 的巢狀類別。</span><span class="sxs-lookup"><span data-stu-id="361d6-115">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="361d6-116">`Entry` 類別更包含三個成員︰一個名為 `next` 的欄位、一個名為 `data` 的欄位以及建構函式。</span><span class="sxs-lookup"><span data-stu-id="361d6-116">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="361d6-117">假設此範例的原始程式碼儲存在檔案 `acme.cs`，命令列</span><span class="sxs-lookup"><span data-stu-id="361d6-117">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```
csc /t:library acme.cs
```

<span data-ttu-id="361d6-118">會將範例編譯為程式庫 (不需要 `Main` 進入點的程式碼)，並產生名為 `acme.dll` 的組件。</span><span class="sxs-lookup"><span data-stu-id="361d6-118">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="361d6-119">上述範例使用 `csc` 做為命令列 C# 編譯器。</span><span class="sxs-lookup"><span data-stu-id="361d6-119">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="361d6-120">此編譯器是 Windows 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="361d6-120">This compiler is a windows executable.</span></span> <span data-ttu-id="361d6-121">若要在其他平台上使用 C#，您應該使用 .NET core 的工具。</span><span class="sxs-lookup"><span data-stu-id="361d6-121">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="361d6-122">.NET Core 生態系統會使用 `dotnet` CLI 管理命令列組建。</span><span class="sxs-lookup"><span data-stu-id="361d6-122">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="361d6-123">這包括管理相依性，以及叫用 C# 編譯器。</span><span class="sxs-lookup"><span data-stu-id="361d6-123">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="361d6-124">如需有關 .NET Core 所支援平台上那些工具的完整說明 ，請參閱[本教學課程](../../core/tutorials/using-with-xplat-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="361d6-124">See [this tutorial](../../core/tutorials/using-with-xplat-cli.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="361d6-125">組件包含的可執行程式碼採用中繼語言 (IL) 指令形式，而符號資訊採用中繼資料形式。</span><span class="sxs-lookup"><span data-stu-id="361d6-125">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="361d6-126">執行前，組件中的 IL 程式碼會由 .NET 通用語言執行平台的 Just-In-Time (JIT) 編譯器自動轉換為處理器特定程式碼。</span><span class="sxs-lookup"><span data-stu-id="361d6-126">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="361d6-127">由於組件是包含程式碼和中繼資料的功能自我描述單位，所以不需要提供 C# 中的 `#include` 指示詞和標頭檔。</span><span class="sxs-lookup"><span data-stu-id="361d6-127">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="361d6-128">特定組件中所包含的公用型別和成員只能在編譯程式時，使用 C# 程式來參考該組件。</span><span class="sxs-lookup"><span data-stu-id="361d6-128">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="361d6-129">例如，此程式使用來自 `acme.dll` 組件的 `Acme.Collections.Stack` 類別︰</span><span class="sxs-lookup"><span data-stu-id="361d6-129">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

<span data-ttu-id="361d6-130">[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]</span><span class="sxs-lookup"><span data-stu-id="361d6-130">[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]</span></span>

<span data-ttu-id="361d6-131">如果程式儲存在檔案 `example.cs` 中，編譯 `example.cs` 時，可以使用編譯器的 /r 選項來參考 acme.dll 組件︰</span><span class="sxs-lookup"><span data-stu-id="361d6-131">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```
csc /r:acme.dll example.cs
```

<span data-ttu-id="361d6-132">這樣會建立名為 `example.exe` 可執行檔組件，執行時會產生以下輸出︰</span><span class="sxs-lookup"><span data-stu-id="361d6-132">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```
100
10
1
```

<span data-ttu-id="361d6-133">C# 允許以數個原始程式檔儲存程式的原始程式文字。</span><span class="sxs-lookup"><span data-stu-id="361d6-133">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="361d6-134">編譯有多檔案的 C# 程式時，所有原始程式檔都會一起處理，而原始程式檔可以隨意地互相參考。概念上，就如同將所有原始程式檔都串連成一個大型檔案，然後再進行處理。</span><span class="sxs-lookup"><span data-stu-id="361d6-134">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="361d6-135">C# 中不再需要向前宣告，原因是在極少數的例外狀況中，宣告順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="361d6-135">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="361d6-136">C# 不會限制原始程式檔只能宣告一個公用型別，也不會要求原始程式檔符合原始程式檔中所宣告的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="361d6-136">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="361d6-137">[上一頁](index.md)
[下一頁](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="361d6-137">[Previous](index.md)
[Next](types-and-variables.md)</span></span>

