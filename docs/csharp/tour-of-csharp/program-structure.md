---
title: C# 程式結構 - C# 語言教學課程
description: 了解 C# 程式的基本建置區塊
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c09c11a4dd957b29b2adb7aaa8d68a50f30620b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156827"
---
# <a name="program-structure"></a><span data-ttu-id="09e2c-103">程式結構</span><span class="sxs-lookup"><span data-stu-id="09e2c-103">Program Structure</span></span>

<span data-ttu-id="09e2c-104">C# 語言的重要組織概念如下：程式\*\*\*\*\*\*、命名空間\*\*\*\*\*\*、型別\*\*\*\*\*\*、成員\*\*\*\*\*\* 及組件\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="09e2c-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="09e2c-105">C# 程式包含一個或多個原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="09e2c-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="09e2c-106">程式宣告型別，其中包含成員並可以依據命名空間分組。</span><span class="sxs-lookup"><span data-stu-id="09e2c-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="09e2c-107">類別和介面都是型別的範例。</span><span class="sxs-lookup"><span data-stu-id="09e2c-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="09e2c-108">欄位、方法、屬性及事件都是成員的範例。</span><span class="sxs-lookup"><span data-stu-id="09e2c-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="09e2c-109">編譯 C# 程式時，它們將物理打包到程式集中。</span><span class="sxs-lookup"><span data-stu-id="09e2c-109">When C# programs are compiled, they're physically packaged into assemblies.</span></span> <span data-ttu-id="09e2c-110">組件通常具有副檔名 `.exe` 或 `.dll`，其分別在於實作「應用程式」\*\*\*\*\*\* 或「程式庫」\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="09e2c-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="09e2c-111">可以使用 以下命令創建名為*acme*的`dotnet new`庫專案：</span><span class="sxs-lookup"><span data-stu-id="09e2c-111">You can create a library project named *acme* using the `dotnet new` command:</span></span>

```console
dotnet new classlib -o acme
```

<span data-ttu-id="09e2c-112">在該專案中，聲明命名空間中`Stack`名為 的類： `Acme.Collections`</span><span class="sxs-lookup"><span data-stu-id="09e2c-112">In that project, declare a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="09e2c-113">此類別的完整名稱是 `Acme.Collections.Stack`。</span><span class="sxs-lookup"><span data-stu-id="09e2c-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="09e2c-114">該類別包含數個成員︰一個名為 `top` 的欄位、兩個名為 `Push` 和 `Pop` 的方法以及名為 `Entry` 的巢狀類別。</span><span class="sxs-lookup"><span data-stu-id="09e2c-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="09e2c-115">`Entry` 類別更包含三個成員︰一個名為 `next` 的欄位、一個名為 `data` 的欄位以及建構函式。</span><span class="sxs-lookup"><span data-stu-id="09e2c-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="09e2c-116">命令：</span><span class="sxs-lookup"><span data-stu-id="09e2c-116">The command:</span></span>

```console
dotnet build
```

<span data-ttu-id="09e2c-117">會將範例編譯為程式庫 (不需要 `Main` 進入點的程式碼)，並產生名為 `acme.dll` 的組件。</span><span class="sxs-lookup"><span data-stu-id="09e2c-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

<span data-ttu-id="09e2c-118">組件包含的可執行程式碼採用中繼語言 (IL) 指令形式，而符號資訊採用中繼資料形式。</span><span class="sxs-lookup"><span data-stu-id="09e2c-118">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="09e2c-119">在執行之前，.NET 通用語言運行時的及時 （JIT） 編譯器將程式集中的 IL 代碼轉換為特定于處理器的代碼。</span><span class="sxs-lookup"><span data-stu-id="09e2c-119">Before it's executed, the Just-In-Time (JIT) compiler of .NET Common Language Runtime converts the IL code in an assembly to processor-specific code.</span></span>

<span data-ttu-id="09e2c-120">由於程式集是包含代碼和中繼資料的自描述功能單元，因此不需要 C# 中的`#include`指令和標標頭檔。</span><span class="sxs-lookup"><span data-stu-id="09e2c-120">Because an assembly is a self-describing unit of functionality containing both code and metadata, there's no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="09e2c-121">特定組件中所包含的公用型別和成員只能在編譯程式時，使用 C# 程式來參考該組件。</span><span class="sxs-lookup"><span data-stu-id="09e2c-121">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="09e2c-122">例如，此程式使用來自 `acme.dll` 組件的 `Acme.Collections.Stack` 類別︰</span><span class="sxs-lookup"><span data-stu-id="09e2c-122">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="09e2c-123">前一個程式專案的*csproj*檔必須包含 C# 編譯器的引用節點，以解決對程式集中的類的`acme.dll`引用：</span><span class="sxs-lookup"><span data-stu-id="09e2c-123">The *csproj* file for the preceding program's project must include a reference node for the C# compiler to resolve references to the classes in the `acme.dll` assembly:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

<span data-ttu-id="09e2c-124">添加後，`dotnet build`創建名為 的`example.exe`可執行程式集，該程式集在運行時生成輸出：</span><span class="sxs-lookup"><span data-stu-id="09e2c-124">After that addition, `dotnet build` creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="09e2c-125">C# 允許以數個原始程式檔儲存程式的原始程式文字。</span><span class="sxs-lookup"><span data-stu-id="09e2c-125">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="09e2c-126">編譯有多檔案的 C# 程式時，所有原始程式檔都會一起處理，而原始程式檔可以隨意地互相參考。概念上，就如同將所有原始程式檔都串連成一個大型檔案，然後再進行處理。</span><span class="sxs-lookup"><span data-stu-id="09e2c-126">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="09e2c-127">C# 中從來不需要轉發聲明，因為除了少數例外情況外，聲明順序微不足道。</span><span class="sxs-lookup"><span data-stu-id="09e2c-127">Forward declarations are never needed in C# because, with few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="09e2c-128">C# 不會限制原始程式檔只能宣告一個公用型別，也不會要求原始程式檔符合原始程式檔中所宣告的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="09e2c-128">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="09e2c-129">[上一個](index.md)
>[下一個](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="09e2c-129">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
