---
title: "如何：使用平行類別逐一查看檔案目錄"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: parallel loops, how to iterate directories
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c21aadf70eaccafc8c8ec9c4efefff1c66abc6b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a><span data-ttu-id="6c6a2-102">如何：使用平行類別逐一查看檔案目錄</span><span class="sxs-lookup"><span data-stu-id="6c6a2-102">How to: Iterate File Directories with the Parallel Class</span></span>
<span data-ttu-id="6c6a2-103">在許多情況下，檔案反覆項目是可以輕鬆平行處理作業。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-103">In many cases, file iteration is an operation that can be easily parallelized.</span></span> <span data-ttu-id="6c6a2-104">本主題[How to： 使用 PLINQ 逐一查看檔案目錄](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)示範許多案例中執行這項工作的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-104">The topic [How to: Iterate File Directories with PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) shows the easiest way to perform this task for many scenarios.</span></span> <span data-ttu-id="6c6a2-105">不過，當您的程式碼有許多類型的存取檔案系統時可能發生的例外狀況處理，可能會發生的複雜性。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-105">However, complications can arise when your code has to deal with the many types of exceptions that can arise when accessing the file system.</span></span> <span data-ttu-id="6c6a2-106">下列範例會顯示問題的其中一個方法。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-106">The following example shows one approach to the problem.</span></span> <span data-ttu-id="6c6a2-107">它會使用堆疊為基礎的反覆項目來周遊所有檔案和資料夾下指定的目錄，並且它可讓您的程式碼來攔截並處理各種例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-107">It uses a stack-based iteration to traverse all files and folders under a specified directory, and it enables your code to catch and handle various exceptions.</span></span> <span data-ttu-id="6c6a2-108">當然，您處理的例外狀況的方法是由您決定。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-108">Of course, the way that you handle the exceptions is up to you.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c6a2-109">範例</span><span class="sxs-lookup"><span data-stu-id="6c6a2-109">Example</span></span>  
 <span data-ttu-id="6c6a2-110">下列範例會循序逐一查看目錄，但是以平行方式處理檔案。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-110">The following example iterates the directories sequentially, but processes the files in parallel.</span></span> <span data-ttu-id="6c6a2-111">這可能是最好的方法時，您有大型的檔案到目錄比率。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-111">This is probably the best approach when you have a large file-to-directory ratio.</span></span> <span data-ttu-id="6c6a2-112">它也可平行處理的目錄反覆項目，並以循序方式存取每個檔案。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-112">It is also possible to parallelize the directory iteration, and access each file sequentially.</span></span> <span data-ttu-id="6c6a2-113">可能不是有效平行處理這兩個迴圈，除非您特別的目標有大量處理器的電腦。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-113">It is probably not efficient to parallelize both loops unless you are specifically targeting a machine with a large number of processors.</span></span> <span data-ttu-id="6c6a2-114">不過，如同所有的情況下，您應該測試您的應用程式，徹底地判斷最佳的方法。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-114">However, as in all cases, you should test your application thoroughly to determine the best approach.</span></span>  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 <span data-ttu-id="6c6a2-115">在此範例中，檔案 I/O 是以同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-115">In this example, the file I/O is performed synchronously.</span></span> <span data-ttu-id="6c6a2-116">當處理大型檔案或低速網路連線，它可能會比以非同步方式存取的檔案。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-116">When dealing with large files or slow network connections, it might be preferable to access the files asynchronously.</span></span> <span data-ttu-id="6c6a2-117">您可以將非同步 I/O 技術結合平行反覆項目。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-117">You can combine asynchronous I/O techniques with parallel iteration.</span></span> <span data-ttu-id="6c6a2-118">如需詳細資訊，請參閱 [TPL 和傳統 .NET Framework 非同步程式設計](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-118">For more information, see [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).</span></span>  
  
 <span data-ttu-id="6c6a2-119">這個範例會使用本機 `fileCount` 變數維護已處理檔案的總數。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-119">The example uses the local `fileCount` variable to maintain a count of the total number of files processed.</span></span> <span data-ttu-id="6c6a2-120">由於可能會有多個工作同時存取這個變數，因此會透過呼叫 <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> 方法同步處理其存取。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-120">Because the variable might be accessed concurrently by multiple tasks, access to it is synchronized by calling the <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="6c6a2-121">請注意，如果例外狀況會擲回主執行緒，而啟動的執行緒<xref:System.Threading.Tasks.Parallel.ForEach%2A>方法可能會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-121">Note that if an exception is thrown on the main thread, the threads that are started by the <xref:System.Threading.Tasks.Parallel.ForEach%2A> method might continue to run.</span></span> <span data-ttu-id="6c6a2-122">若要停止這些執行緒，可以在您的例外狀況處理常式中設定布林值變數，並檢查它在平行迴圈的每個反覆項目上的值。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-122">To stop these threads, you can set a Boolean variable in your exception handlers, and check its value on each iteration of the parallel loop.</span></span> <span data-ttu-id="6c6a2-123">如果此值會指出已擲回的例外狀況，使用<xref:System.Threading.Tasks.ParallelLoopState>停止或中斷迴圈的變數。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-123">If the value indicates that an exception has been thrown, use the <xref:System.Threading.Tasks.ParallelLoopState> variable to stop or break from the loop.</span></span> <span data-ttu-id="6c6a2-124">如需詳細資訊，請參閱[如何： 停止或中斷 Parallel.For 迴圈](http://msdn.microsoft.com/en-us/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)。</span><span class="sxs-lookup"><span data-stu-id="6c6a2-124">For more information, see [How to: Stop or Break from a Parallel.For Loop](http://msdn.microsoft.com/en-us/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c6a2-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c6a2-125">See Also</span></span>  
 [<span data-ttu-id="6c6a2-126">資料平行處理原則</span><span class="sxs-lookup"><span data-stu-id="6c6a2-126">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
