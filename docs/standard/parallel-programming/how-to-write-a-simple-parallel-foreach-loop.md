---
title: 使用 Parallel.ForEach 寫入一個簡單的平行程式
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d54f06c1fc774a2e73b3b99a7d5bb24dd8baf3f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835268"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="cb4f7-102">HOW TO：撰寫簡單的 Parallel.ForEach 迴圈</span><span class="sxs-lookup"><span data-stu-id="cb4f7-102">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="cb4f7-103">此範例示範如何使用 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 迴圈來透過 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 資料來源啟用資料平行處理原則。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="cb4f7-104">本文件使用 Lambda 運算式來定義 PLINQ 中的委派。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="cb4f7-105">如果您不熟悉 C# 或 Visual Basic 中的 Lambda 運算式，請參閱 [PLINQ 及 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="cb4f7-106">範例</span><span class="sxs-lookup"><span data-stu-id="cb4f7-106">Example</span></span>

<span data-ttu-id="cb4f7-107">此範例會假設您在 C:\Users\Public\Pictures\Sample Pictures 資料夾中擁有數個 .jpg 檔案，且建立名為 *Modified* 的新子資料夾。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-107">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="cb4f7-108">當您執行範例時，其會旋轉在 *Sample Pictures* 中的各 .jpg 影像，並將其儲存至 *Modified*。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-108">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="cb4f7-109">如有必要，您可以修改這兩個路徑。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-109">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="cb4f7-110"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 迴圈的運作方式類似 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 迴圈。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-110">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="cb4f7-111">迴圈會根據系統環境分割來源集合，及對多個執行緒上的作業進行排程。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-111">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="cb4f7-112">系統上的處理器愈多，平行方法的執行速度愈快。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-112">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="cb4f7-113">對於某些來源集合，循序迴圈的執行速度可能更快，這取決於來源的大小和迴圈執行的作業種類。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-113">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="cb4f7-114">如需效能的詳細資訊，請參閱[資料和工作平行](potential-pitfalls-in-data-and-task-parallelism.md)處理原則中的可能錯誤。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-114">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="cb4f7-115">如需平行迴圈的詳細資訊，請參閱[如何：撰寫簡單的 Parallel.For 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-115">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="cb4f7-116">若要將 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>使用於非泛型集合 ，可使用 <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> 擴充方法將集合轉換成泛型集合，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="cb4f7-116">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="cb4f7-117">您也可以使用平行 LINQ (PLINQ) 來平行處理 <xref:System.Collections.Generic.IEnumerable%601> 資料來源。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-117">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="cb4f7-118">PLINQ 可讓您使用宣告式查詢語法來表示迴圈行為。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-118">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="cb4f7-119">如需詳細資訊，請參閱 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-119">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="cb4f7-120">編譯並執行程式碼</span><span class="sxs-lookup"><span data-stu-id="cb4f7-120">Compile and run the code</span></span>

<span data-ttu-id="cb4f7-121">您可將程式碼編譯為 .NET Framework 的主控台應用程式，或 .NET Core 的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-121">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="cb4f7-122">在 Visual Studio 中，有 Windows Desktop 及 .NET Core 的 Visual Basic 及 C# 主控台應用程式範本。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-122">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="cb4f7-123">從命令列中，您可使用 .NET Core 及其 CLI 工具 (例如 `dotnet new console` 或 `dotnet new console -lang vb`)，或者可建立檔案，然後使用 .NET Framework 應用程式的命令列編譯器。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-123">From the command line, you can use either .NET Core and its CLI tools (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="cb4f7-124">對於 .NET Core 專案，您必須參考 **System.Drawing.Common** NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-124">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="cb4f7-125">在 Visual Studio 中，使用 NuGet 套件管理員來安裝套件。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-125">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="cb4f7-126">或者，您可將參考新增至 \*.csproj 或 \*.vbproj 檔案中的套件：</span><span class="sxs-lookup"><span data-stu-id="cb4f7-126">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>
 
```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="cb4f7-127">若要從命令列執行 .NET Core 主控台應用程式，請從包含您應用程式的資料夾中使用 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-127">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="cb4f7-128">若要從 Visual Studio 執行您的主控台應用程式，請按 **F5**。</span><span class="sxs-lookup"><span data-stu-id="cb4f7-128">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb4f7-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb4f7-129">See also</span></span>

- [<span data-ttu-id="cb4f7-130">資料平行處理原則</span><span class="sxs-lookup"><span data-stu-id="cb4f7-130">Data parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="cb4f7-131">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="cb4f7-131">Parallel programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="cb4f7-132">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="cb4f7-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
