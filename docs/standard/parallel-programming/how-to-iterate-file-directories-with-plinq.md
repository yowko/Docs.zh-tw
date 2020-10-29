---
title: 作法：使用 PLINQ 逐一查看檔案目錄
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: 5033cc24fce5fc17a950e4797de1ef4071e2b98a
ms.sourcegitcommit: 6d09ae36acba0b0e2ba47999f8f1a725795462a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2020
ms.locfileid: "92925372"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a><span data-ttu-id="1c3b9-102">作法：使用 PLINQ 逐一查看檔案目錄</span><span class="sxs-lookup"><span data-stu-id="1c3b9-102">How to: Iterate File Directories with PLINQ</span></span>

<span data-ttu-id="1c3b9-103">本文說明兩種在檔案目錄上平行處理作業的方式。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-103">This article shows two ways to parallelize operations on file directories.</span></span> <span data-ttu-id="1c3b9-104">第一個查詢使用 <xref:System.IO.Directory.GetFiles%2A> 方法來填入目錄和所有子目錄中的檔案名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-104">The first query uses the <xref:System.IO.Directory.GetFiles%2A> method to populate an array of file names in a directory and all subdirectories.</span></span> <span data-ttu-id="1c3b9-105">此方法可能會在作業開始時引入延遲，因為它不會傳回，直到整個陣列都已填入為止。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-105">This method can introduce latency at the beginning of the operation, because it doesn't return until the entire array is populated.</span></span> <span data-ttu-id="1c3b9-106">不過，在擴展陣列之後，PLINQ 可以快速地平行處理它。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-106">However, after the array is populated, PLINQ can process it in parallel quickly.</span></span>  
  
<span data-ttu-id="1c3b9-107">第二個查詢會使用靜態 <xref:System.IO.Directory.EnumerateDirectories%2A> 和 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> 方法，以立即開始傳回結果。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-107">The second query uses the static <xref:System.IO.Directory.EnumerateDirectories%2A> and <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> methods, which begin returning results immediately.</span></span> <span data-ttu-id="1c3b9-108">當您反復查看大型目錄樹狀結構時，這種方法會更快，但相較于第一個範例，處理時間會視許多因素而定。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-108">This approach can be faster when you're iterating over large directory trees, but the processing time compared to the first example depends on many factors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c3b9-109">這些範例的目的是要示範使用方式，而且執行速度可能會比對等的連續 LINQ to Objects 查詢更快。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-109">These examples are intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="1c3b9-110">如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-110">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="getfiles-example"></a><span data-ttu-id="1c3b9-111">GetFiles 範例</span><span class="sxs-lookup"><span data-stu-id="1c3b9-111">GetFiles example</span></span>

 <span data-ttu-id="1c3b9-112">這個範例示範如何在簡單的案例中，在您可以存取樹狀結構中的所有目錄時，逐一查看檔案目錄、檔案大小不大，而且存取時間不重要。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-112">This example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes aren't large, and the access times are not significant.</span></span> <span data-ttu-id="1c3b9-113">此方法一開始由於正在建構檔案名稱陣列，會有一段時間的延遲。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-113">This approach involves a period of latency at the beginning while the array of file names is being constructed.</span></span>  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="enumeratefiles-example"></a><span data-ttu-id="1c3b9-114">EnumerateFiles 範例</span><span class="sxs-lookup"><span data-stu-id="1c3b9-114">EnumerateFiles example</span></span>

 <span data-ttu-id="1c3b9-115">這個範例示範如何在簡單的案例中，在您可以存取樹狀結構中的所有目錄時，逐一查看檔案目錄、檔案大小不大，而且存取時間不重要。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-115">This example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes aren't large, and the access times are not significant.</span></span> <span data-ttu-id="1c3b9-116">此方法開始產生結果的速度會比上一個範例快。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-116">This approach begins producing results faster than the previous example.</span></span>  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 <span data-ttu-id="1c3b9-117">使用 <xref:System.IO.Directory.GetFiles%2A> 時，請確定您有足夠的權限可以存取樹狀中的所有目錄。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-117">When using <xref:System.IO.Directory.GetFiles%2A>, be sure that you have sufficient permissions on all directories in the tree.</span></span> <span data-ttu-id="1c3b9-118">否則會擲回例外狀況，而且不會傳回任何結果。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-118">Otherwise, an exception will be thrown and no results will be returned.</span></span> <span data-ttu-id="1c3b9-119">在 PLINQ 查詢中使用 <xref:System.IO.Directory.EnumerateDirectories%2A> 時，要以可讓您繼續逐一查看的正常方式處理 I/O 例外狀況會有困難。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-119">When using the <xref:System.IO.Directory.EnumerateDirectories%2A> in a PLINQ query, it is problematic to handle I/O exceptions in a graceful way that enables you to continue iterating.</span></span> <span data-ttu-id="1c3b9-120">如果您的程式碼必須處理 I/O 或未經授權的存取例外狀況，您應該考慮[如何：使用平行類別逐一查看檔案目錄](how-to-iterate-file-directories-with-the-parallel-class.md)中描述的方法。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-120">If your code must handle I/O or unauthorized access exceptions, then you should consider the approach described in [How to: Iterate File Directories with the Parallel Class](how-to-iterate-file-directories-with-the-parallel-class.md).</span></span>  
  
 <span data-ttu-id="1c3b9-121">如果 i/o 延遲是問題（例如透過網路上的檔案 i/o），請考慮使用 [TPL 和傳統 .Net 非同步程式設計](tpl-and-traditional-async-programming.md) 中所述的其中一項非同步 i/o 技術，以及這 [篇 blog 文章](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/)。</span><span class="sxs-lookup"><span data-stu-id="1c3b9-121">If I/O latency is an issue, for example with file I/O over a network, consider using one of the asynchronous I/O techniques described in [TPL and Traditional .NET Asynchronous Programming](tpl-and-traditional-async-programming.md) and in this [blog post](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c3b9-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c3b9-122">See also</span></span>

- [<span data-ttu-id="1c3b9-123">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1c3b9-123">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
