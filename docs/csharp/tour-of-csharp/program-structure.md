---
title: C# 程式結構 - C# 語言教學課程
description: 了解 C# 程式的基本建置區塊
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 828146ba509daf9427e6dd1a4ebf3ad747ac7c39
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159113"
---
# <a name="program-structure"></a><span data-ttu-id="ccc2b-103">程式結構</span><span class="sxs-lookup"><span data-stu-id="ccc2b-103">Program Structure</span></span>

<span data-ttu-id="ccc2b-104">C# 語言的重要組織概念如下：程式、命名空間、型別、成員及組件。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="ccc2b-105">C# 程式包含一個或多個原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="ccc2b-106">程式宣告型別，其中包含成員並可以依據命名空間分組。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="ccc2b-107">類別和介面都是型別的範例。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="ccc2b-108">欄位、方法、屬性及事件都是成員的範例。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="ccc2b-109">程式C#在編譯時，會實際封裝到元件中。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-109">When C# programs are compiled, they're physically packaged into assemblies.</span></span> <span data-ttu-id="ccc2b-110">組件通常具有副檔名 `.exe` 或 `.dll`，其分別在於實作「應用程式」或「程式庫」。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="ccc2b-111">您可以使用 `dotnet new` 命令，建立名為*acme*的程式庫專案：</span><span class="sxs-lookup"><span data-stu-id="ccc2b-111">You can create a library project named *acme* using the `dotnet new` command:</span></span>

```console
dotnet new classlib -o acme
```

<span data-ttu-id="ccc2b-112">在該專案中，于名為 `Acme.Collections`的命名空間中，宣告名為 `Stack` 的類別：</span><span class="sxs-lookup"><span data-stu-id="ccc2b-112">In that project, declare a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="ccc2b-113">此類別的完整名稱是 `Acme.Collections.Stack`。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="ccc2b-114">該類別包含數個成員︰一個名為 `top` 的欄位、兩個名為 `Push` 和 `Pop` 的方法以及名為 `Entry` 的巢狀類別。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="ccc2b-115">`Entry` 類別更包含三個成員︰一個名為 `next` 的欄位、一個名為 `data` 的欄位以及建構函式。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="ccc2b-116">命令：</span><span class="sxs-lookup"><span data-stu-id="ccc2b-116">The command:</span></span>

```console
dotnet build 
```

<span data-ttu-id="ccc2b-117">會將範例編譯為程式庫 (不需要 `Main` 進入點的程式碼)，並產生名為 `acme.dll` 的組件。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

<span data-ttu-id="ccc2b-118">組件包含的可執行程式碼採用中繼語言 (IL) 指令形式，而符號資訊採用中繼資料形式。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-118">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="ccc2b-119">在執行之前，.NET 通用語言執行平臺的即時（JIT）編譯器會將元件中的 IL 程式碼轉換成處理器特定程式碼。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-119">Before it's executed, the Just-In-Time (JIT) compiler of .NET Common Language Runtime converts the IL code in an assembly to processor-specific code.</span></span>

<span data-ttu-id="ccc2b-120">因為元件是包含程式碼和中繼資料的自我描述功能單位，所以中C#不需要 `#include` 指示詞和標頭檔。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-120">Because an assembly is a self-describing unit of functionality containing both code and metadata, there's no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="ccc2b-121">特定組件中所包含的公用型別和成員只能在編譯程式時，使用 C# 程式來參考該組件。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-121">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="ccc2b-122">例如，此程式使用來自 `Acme.Collections.Stack` 組件的 `acme.dll` 類別︰</span><span class="sxs-lookup"><span data-stu-id="ccc2b-122">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="ccc2b-123">前述程式專案的 *.csproj*檔案必須包含參考節點， C#編譯器才能解析 `acme.dll` 元件中類別的參考：</span><span class="sxs-lookup"><span data-stu-id="ccc2b-123">The *csproj* file for the preceding program's project must include a reference node for the C# compiler to resolve references to the classes in the `acme.dll` assembly:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

<span data-ttu-id="ccc2b-124">在該新增之後，`dotnet build` 會建立名為 `example.exe`的可執行元件，在執行時，會產生輸出：</span><span class="sxs-lookup"><span data-stu-id="ccc2b-124">After that addition, `dotnet build` creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="ccc2b-125">C# 允許以數個原始程式檔儲存程式的原始程式文字。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-125">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="ccc2b-126">編譯有多檔案的 C# 程式時，所有原始程式檔都會一起處理，而原始程式檔可以隨意地互相參考。概念上，就如同將所有原始程式檔都串連成一個大型檔案，然後再進行處理。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-126">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="ccc2b-127">中C#永遠不需要向前宣告，因為只有少數例外狀況，宣告順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-127">Forward declarations are never needed in C# because, with few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="ccc2b-128">C# 不會限制原始程式檔只能宣告一個公用型別，也不會要求原始程式檔符合原始程式檔中所宣告的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="ccc2b-128">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ccc2b-129">[上一頁](index.md)
>[下一頁](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="ccc2b-129">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
