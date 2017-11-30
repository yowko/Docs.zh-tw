---
title: "如何：使用 PLINQ 逐一查看檔案目錄"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 40fd9f64b5702f5205b7817f3de1e0a8709c5a63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-plinq"></a><span data-ttu-id="958ab-102">如何：使用 PLINQ 逐一查看檔案目錄</span><span class="sxs-lookup"><span data-stu-id="958ab-102">How to: Iterate File Directories with PLINQ</span></span>
<span data-ttu-id="958ab-103">此範例示範兩個簡單的方式，來平行化檔案目錄的作業。</span><span class="sxs-lookup"><span data-stu-id="958ab-103">This example shows two simple ways to parallelize operations on file directories.</span></span> <span data-ttu-id="958ab-104">第一個查詢使用<xref:System.IO.Directory.GetFiles%2A>方法來填入的目錄和所有子目錄中的檔案名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="958ab-104">The first query uses the <xref:System.IO.Directory.GetFiles%2A> method to populate an array of file names in a directory and all subdirectories.</span></span> <span data-ttu-id="958ab-105">這個方法不會傳回，直到整個陣列已填入，因此它可能會導致在作業開始時的延遲。</span><span class="sxs-lookup"><span data-stu-id="958ab-105">This method does not return until the entire array is populated, and therefore it can introduce latency at the beginning of the operation.</span></span> <span data-ttu-id="958ab-106">不過，填入陣列之後，PLINQ 可以處理它以平行方式非常快速。</span><span class="sxs-lookup"><span data-stu-id="958ab-106">However, after the array is populated, PLINQ can process it in parallel very quickly.</span></span>  
  
 <span data-ttu-id="958ab-107">第二個查詢會使用靜態<xref:System.IO.Directory.EnumerateDirectories%2A>和<xref:System.IO.DirectoryInfo.EnumerateFiles%2A>開始立即傳回結果的方法。</span><span class="sxs-lookup"><span data-stu-id="958ab-107">The second query uses the static <xref:System.IO.Directory.EnumerateDirectories%2A> and <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> methods which begin returning results immediately.</span></span> <span data-ttu-id="958ab-108">這種方法可以更快時反覆大型目錄樹狀結構中，雖然相較於第一個範例中的處理時間可能取決於許多因素而定。</span><span class="sxs-lookup"><span data-stu-id="958ab-108">This approach can be faster when you are iterating over large directory trees, although the processing time compared to the first example can depend on many factors.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="958ab-109">這些範例為了示範用法，並執行速度可能比不上對應的循序 LINQ to Objects 查詢。</span><span class="sxs-lookup"><span data-stu-id="958ab-109">These examples are intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="958ab-110">提升速度的詳細資訊，請參閱[PLINQ 中的了解加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="958ab-110">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="958ab-111">範例</span><span class="sxs-lookup"><span data-stu-id="958ab-111">Example</span></span>  
 <span data-ttu-id="958ab-112">下列範例會示範如何逐一查看檔案目錄，在簡單的案例時您可以在樹狀目錄中的所有目錄存取、 檔案大小不是非常大，和存取時間皆屬於不顯著。</span><span class="sxs-lookup"><span data-stu-id="958ab-112">The following example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes are not very large, and the access times are not significant.</span></span> <span data-ttu-id="958ab-113">檔案名稱的陣列會在建構時，這種方法牽涉到一段延遲開頭。</span><span class="sxs-lookup"><span data-stu-id="958ab-113">This approach involves a period of latency at the beginning while the array of file names is being constructed.</span></span>  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a><span data-ttu-id="958ab-114">範例</span><span class="sxs-lookup"><span data-stu-id="958ab-114">Example</span></span>  
 <span data-ttu-id="958ab-115">下列範例會示範如何逐一查看檔案目錄，在簡單的案例時您可以在樹狀目錄中的所有目錄存取、 檔案大小不是非常大，和存取時間皆屬於不顯著。</span><span class="sxs-lookup"><span data-stu-id="958ab-115">The following example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes are not very large, and the access times are not significant.</span></span> <span data-ttu-id="958ab-116">這種方法開始速度比前一個範例產生的結果。</span><span class="sxs-lookup"><span data-stu-id="958ab-116">This approach begins producing results faster than the previous example.</span></span>  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 <span data-ttu-id="958ab-117">當使用<xref:System.IO.Directory.GetFiles%2A>，確定您在樹狀目錄中的所有目錄上有足夠的權限。</span><span class="sxs-lookup"><span data-stu-id="958ab-117">When using <xref:System.IO.Directory.GetFiles%2A>, be sure that you have sufficient permissions on all directories in the tree.</span></span> <span data-ttu-id="958ab-118">否則將擲回例外狀況，而且會傳回任何結果。</span><span class="sxs-lookup"><span data-stu-id="958ab-118">Otherwise an exception will be thrown and no results will be returned.</span></span> <span data-ttu-id="958ab-119">當使用<xref:System.IO.Directory.EnumerateDirectories%2A>在 PLINQ 查詢中，會有問題，可讓您在繼續重複執行以正常方式處理 I/O 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="958ab-119">When using the <xref:System.IO.Directory.EnumerateDirectories%2A> in a PLINQ query, it is problematic to handle I/O exceptions in a graceful way that enables you to continue iterating.</span></span> <span data-ttu-id="958ab-120">如果您的程式碼必須處理 I/O 或未經授權的存取例外狀況，那麼您應該考慮中描述的方法[How to： 使用平行類別逐一查看檔案目錄](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md)。</span><span class="sxs-lookup"><span data-stu-id="958ab-120">If your code must handle I/O or unauthorized access exceptions, then you should consider the approach described in [How to: Iterate File Directories with the Parallel Class](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).</span></span>  
  
 <span data-ttu-id="958ab-121">如果 I/O 延遲問題，例如在網路上的檔案 I/O 請考慮使用非同步技術中所述的其中一個[TPL 和傳統.NET Framework 非同步程式設計](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)和此[部落格文章](http://go.microsoft.com/fwlink/?LinkID=186458).</span><span class="sxs-lookup"><span data-stu-id="958ab-121">If I/O latency is an issue, for example with file I/O over a network, consider using one of the asynchronous I/O techniques described in [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) and in this [blog post](http://go.microsoft.com/fwlink/?LinkID=186458).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="958ab-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="958ab-122">See Also</span></span>  
 [<span data-ttu-id="958ab-123">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="958ab-123">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
