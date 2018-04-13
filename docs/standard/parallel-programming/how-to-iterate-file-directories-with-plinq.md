---
title: 如何：使用 PLINQ 逐一查看檔案目錄
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ddd3b509b7c0c35f1c4edea99cb5a4ec6c1ac18e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-iterate-file-directories-with-plinq"></a><span data-ttu-id="b54cc-102">如何：使用 PLINQ 逐一查看檔案目錄</span><span class="sxs-lookup"><span data-stu-id="b54cc-102">How to: Iterate File Directories with PLINQ</span></span>
<span data-ttu-id="b54cc-103">此範例示範兩個簡單的方式來平行處理檔案目錄的作業。</span><span class="sxs-lookup"><span data-stu-id="b54cc-103">This example shows two simple ways to parallelize operations on file directories.</span></span> <span data-ttu-id="b54cc-104">第一個查詢使用 <xref:System.IO.Directory.GetFiles%2A> 方法來填入目錄和所有子目錄中的檔案名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="b54cc-104">The first query uses the <xref:System.IO.Directory.GetFiles%2A> method to populate an array of file names in a directory and all subdirectories.</span></span> <span data-ttu-id="b54cc-105">這個方法在整個陣列填入之前不會傳回，因此在作業開始時可能會延遲。</span><span class="sxs-lookup"><span data-stu-id="b54cc-105">This method does not return until the entire array is populated, and therefore it can introduce latency at the beginning of the operation.</span></span> <span data-ttu-id="b54cc-106">不過，在填入陣列之後，PLINQ 可以平行方式非常快速地處理它。</span><span class="sxs-lookup"><span data-stu-id="b54cc-106">However, after the array is populated, PLINQ can process it in parallel very quickly.</span></span>  
  
 <span data-ttu-id="b54cc-107">第二個查詢使用靜態 <xref:System.IO.Directory.EnumerateDirectories%2A> 和 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> 方法，會立即開始傳回結果。</span><span class="sxs-lookup"><span data-stu-id="b54cc-107">The second query uses the static <xref:System.IO.Directory.EnumerateDirectories%2A> and <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> methods which begin returning results immediately.</span></span> <span data-ttu-id="b54cc-108">逐一查看大型的目錄樹狀時，這種方法的執行速度更快，然而相較於第一個範例，處理時間可能取決於許多因素。</span><span class="sxs-lookup"><span data-stu-id="b54cc-108">This approach can be faster when you are iterating over large directory trees, although the processing time compared to the first example can depend on many factors.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b54cc-109">這些範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。</span><span class="sxs-lookup"><span data-stu-id="b54cc-109">These examples are intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="b54cc-110">如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="b54cc-110">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b54cc-111">範例</span><span class="sxs-lookup"><span data-stu-id="b54cc-111">Example</span></span>  
 <span data-ttu-id="b54cc-112">下列範例示範在簡單案例中，當您可以存取樹狀中的所有目錄時應如何逐一查檔案目錄，檔案大小不是非常大，且存取時間不是很長。</span><span class="sxs-lookup"><span data-stu-id="b54cc-112">The following example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes are not very large, and the access times are not significant.</span></span> <span data-ttu-id="b54cc-113">此方法一開始由於正在建構檔案名稱陣列，會有一段時間的延遲。</span><span class="sxs-lookup"><span data-stu-id="b54cc-113">This approach involves a period of latency at the beginning while the array of file names is being constructed.</span></span>  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a><span data-ttu-id="b54cc-114">範例</span><span class="sxs-lookup"><span data-stu-id="b54cc-114">Example</span></span>  
 <span data-ttu-id="b54cc-115">下列範例示範在簡單案例中，當您可以存取樹狀中的所有目錄時應如何逐一查檔案目錄，檔案大小不是非常大，且存取時間不是很長。</span><span class="sxs-lookup"><span data-stu-id="b54cc-115">The following example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes are not very large, and the access times are not significant.</span></span> <span data-ttu-id="b54cc-116">此方法開始產生結果的速度會比上一個範例快。</span><span class="sxs-lookup"><span data-stu-id="b54cc-116">This approach begins producing results faster than the previous example.</span></span>  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 <span data-ttu-id="b54cc-117">使用 <xref:System.IO.Directory.GetFiles%2A> 時，請確定您有足夠的權限可以存取樹狀中的所有目錄。</span><span class="sxs-lookup"><span data-stu-id="b54cc-117">When using <xref:System.IO.Directory.GetFiles%2A>, be sure that you have sufficient permissions on all directories in the tree.</span></span> <span data-ttu-id="b54cc-118">否則將會擲回例外狀況，而且不會傳回任何結果。</span><span class="sxs-lookup"><span data-stu-id="b54cc-118">Otherwise an exception will be thrown and no results will be returned.</span></span> <span data-ttu-id="b54cc-119">在 PLINQ 查詢中使用 <xref:System.IO.Directory.EnumerateDirectories%2A> 時，要以可讓您繼續逐一查看的正常方式處理 I/O 例外狀況會有困難。</span><span class="sxs-lookup"><span data-stu-id="b54cc-119">When using the <xref:System.IO.Directory.EnumerateDirectories%2A> in a PLINQ query, it is problematic to handle I/O exceptions in a graceful way that enables you to continue iterating.</span></span> <span data-ttu-id="b54cc-120">如果您的程式碼必須處理 I/O 或未經授權的存取例外狀況，您應該考慮[如何：使用平行類別逐一查看檔案目錄](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md)中描述的方法。</span><span class="sxs-lookup"><span data-stu-id="b54cc-120">If your code must handle I/O or unauthorized access exceptions, then you should consider the approach described in [How to: Iterate File Directories with the Parallel Class](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).</span></span>  
  
 <span data-ttu-id="b54cc-121">如果 I/O 延遲會造成問題，例如在網路上處理檔案 I/O，請考慮使用 [TPL 和傳統 .NET Framework 非同步程式設計](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)和這篇[部落格文章](http://go.microsoft.com/fwlink/?LinkID=186458)中所述的其中一項非同步 I/O 技術。</span><span class="sxs-lookup"><span data-stu-id="b54cc-121">If I/O latency is an issue, for example with file I/O over a network, consider using one of the asynchronous I/O techniques described in [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) and in this [blog post](http://go.microsoft.com/fwlink/?LinkID=186458).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b54cc-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="b54cc-122">See Also</span></span>  
 [<span data-ttu-id="b54cc-123">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="b54cc-123">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
