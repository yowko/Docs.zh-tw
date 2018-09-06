---
title: 如何： 使用 Task.WhenAll (Visual Basic) 來擴充非同步逐步解說
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: 650b96926cf66810a93b003b1ebc09ca16212b00
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43778213"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a><span data-ttu-id="7ce6b-102">如何： 使用 Task.WhenAll (Visual Basic) 來擴充非同步逐步解說</span><span class="sxs-lookup"><span data-stu-id="7ce6b-102">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>
<span data-ttu-id="7ce6b-103">您可以改善中非同步方案的效能[逐步解說： 存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)使用<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7ce6b-104">此方法會以非同步方式等候多個非同步作業進行，這些作業是以工作集合來表示。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="7ce6b-105">您在此逐步解說中可能已注意到網站下載的速度各自不同。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="7ce6b-106">有時其中一個網站的速度很慢，而導致所有其餘下載延後執行。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="7ce6b-107">當您執行在此逐步解說中建立的非同步方案時，如果不想要等候，您可以輕鬆地結束程式；但更好的做法是同時啟動所有下載，並讓較快的下載繼續執行而不等候延遲的下載。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="7ce6b-108">您可以將 `Task.WhenAll` 方法套用至工作集合。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="7ce6b-109">套用 `WhenAll` 會傳回未完成的單一工作，直到集合中的所有工作都完成為止。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="7ce6b-110">工作似乎會平行執行，但不會建立其他任何執行緒。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="7ce6b-111">工作可以依任何順序完成。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7ce6b-112">下列程序描述非同步應用程式的開發中的延伸模組[逐步解說： 存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="7ce6b-113">您可以藉由完成此逐步解說，或從[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下載程式碼，來開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
>   
>  <span data-ttu-id="7ce6b-114">若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="7ce6b-115">將 Task.WhenAll 新增至您的 GetURLContentsAsync 方案</span><span class="sxs-lookup"><span data-stu-id="7ce6b-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1.  <span data-ttu-id="7ce6b-116">新增`ProcessURLAsync`方法來開發的第一個應用程式[逐步解說： 存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="7ce6b-117">如果您已下載的程式碼[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)、 開啟 AsyncWalkthrough 專案，然後再新增`ProcessURLAsync`MainWindow.xaml.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="7ce6b-118">如果您藉由完成此逐步解說來開發程式碼，請將 `ProcessURLAsync` 新增至包含 `GetURLContentsAsync` 方法的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="7ce6b-119">此應用程式的 MainWindow.xaml.vb 檔案是 「 完整程式碼範例從逐步解說 > 一節的第一個範例。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-119">The MainWindow.xaml.vb file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="7ce6b-120">`ProcessURLAsync` 方法會合併原始逐步解說中 `SumPageSizesAsync` 之 `For Each` 迴圈主體內的動作。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-120">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="7ce6b-121">此方法會以非同步方式將指定網站的內容下載為位元組陣列，然後顯示並傳回位元組陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="7ce6b-122">將 `SumPageSizesAsync` 中的 `For Each` 迴圈註解化或刪除，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-122">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```vb  
    'Dim total = 0  
    'For Each url In urlList  
  
    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
    '    ' The previous line abbreviates the following two assignment statements.  
  
    '    ' GetURLContentsAsync returns a task. At completion, the task  
    '    ' produces a byte array.  
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
    '    'Dim urlContents As Byte() = Await getContentsTask  
  
    '    DisplayResults(url, urlContents)  
  
    '    ' Update the total.  
    '    total += urlContents.Length  
    'Next  
    ```  
  
3.  <span data-ttu-id="7ce6b-123">建立工作集合。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-123">Create a collection of tasks.</span></span> <span data-ttu-id="7ce6b-124">下列程式碼定義一個[查詢](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)，當 <xref:System.Linq.Enumerable.ToArray%2A> 方法執行此查詢時，會建立工作集合以下載每個網站的內容。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-124">The following code defines a [query](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="7ce6b-125">工作會在評估查詢之後啟動。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="7ce6b-126">將下列程式碼新增至 `urlList` 宣告後面的 `SumPageSizesAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="7ce6b-127">將 `Task.WhenAll` 套用至工作集合 `downloadTasks`。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="7ce6b-128">`Task.WhenAll` 會傳回當工作集合中所有工作完成後才會完成的單一工作。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="7ce6b-129">在下列範例中，`Await` 運算式會等候 `WhenAll` 傳回的單一工作完成。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-129">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="7ce6b-130">此運算式會評估為整數陣列，其中每個整數都是所下載網站的長度。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="7ce6b-131">將下列程式碼新增至 `SumPageSizesAsync`，就在您於上一個步驟中新增的程式碼之後。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="7ce6b-132">最後，使用 <xref:System.Linq.Enumerable.Sum%2A> 方法來計算所有網站的長度總和。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="7ce6b-133">將下列程式碼行新增至 `SumPageSizesAsync`。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="7ce6b-134">將 Task.WhenAll 新增至 HttpClient.GetByteArrayAsync 方案</span><span class="sxs-lookup"><span data-stu-id="7ce6b-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1.  <span data-ttu-id="7ce6b-135">新增下列版本`ProcessURLAsync`第二個應用程式中所開發[逐步解說： 存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="7ce6b-136">如果您已下載的程式碼[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)、 開啟 AsyncWalkthrough_HttpClient 專案，然後再新增`ProcessURLAsync`MainWindow.xaml.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="7ce6b-137">如果您藉由完成此逐步解說來開發程式碼，請將 `ProcessURLAsync` 新增至使用 `HttpClient.GetByteArrayAsync` 方法的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="7ce6b-138">此應用程式的 MainWindow.xaml.vb 檔案是 「 完整程式碼範例從逐步解說 > 一節的第二個範例。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-138">The MainWindow.xaml.vb file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="7ce6b-139">`ProcessURLAsync` 方法會合併原始逐步解說中 `SumPageSizesAsync` 之 `For Each` 迴圈主體內的動作。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-139">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="7ce6b-140">此方法會以非同步方式將指定網站的內容下載為位元組陣列，然後顯示並傳回位元組陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="7ce6b-141">其與上一個步驟中 `ProcessURLAsync` 方法的唯一差別，在於使用了 <xref:System.Net.Http.HttpClient> 執行個體 `client`。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="7ce6b-142">將 `SumPageSizesAsync` 中的 `For Each` 迴圈註解化或刪除，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-142">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```vb  
    'Dim total = 0   
    'For Each url In urlList   
    '    ' GetByteArrayAsync returns a task. At completion, the task   
    '    ' produces a byte array.   
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)   
  
    '    ' The following two lines can replace the previous assignment statement.   
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)   
    '    'Dim urlContents As Byte() = Await getContentsTask   
  
    '    DisplayResults(url, urlContents)   
  
    '    ' Update the total.   
    '    total += urlContents.Length   
    'Next  
    ```  
  
3.  <span data-ttu-id="7ce6b-143">定義一個[查詢](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)，當 <xref:System.Linq.Enumerable.ToArray%2A> 方法執行此查詢時，會建立工作集合以下載每個網站的內容。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-143">Define a [query](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="7ce6b-144">工作會在評估查詢之後啟動。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="7ce6b-145">將下列程式碼新增至 `client` 和 `urlList` 宣告後面的 `SumPageSizesAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="7ce6b-146">接下來，將 `Task.WhenAll` 套用至工作集合 `downloadTasks`。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="7ce6b-147">`Task.WhenAll` 會傳回當工作集合中所有工作完成後才會完成的單一工作。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="7ce6b-148">在下列範例中，`Await` 運算式會等候 `WhenAll` 傳回的單一工作完成。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-148">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="7ce6b-149">完成時，`Await` 運算式會評估為整數陣列，其中每個整數都是所下載網站的長度。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-149">When complete, the `Await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="7ce6b-150">將下列程式碼新增至 `SumPageSizesAsync`，就在您於上一個步驟中新增的程式碼之後。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="7ce6b-151">最後，使用 <xref:System.Linq.Enumerable.Sum%2A> 方法取得所有網站的長度總和。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="7ce6b-152">將下列程式碼行新增至 `SumPageSizesAsync`。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="7ce6b-153">測試 Task.WhenAll 方案</span><span class="sxs-lookup"><span data-stu-id="7ce6b-153">To test the Task.WhenAll solutions</span></span>  
  
-   <span data-ttu-id="7ce6b-154">針對任一方案，選擇 F5 鍵以執行程式，然後選擇 [開始] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="7ce6b-155">輸出看起來應該像中的非同步方案輸出[逐步解說： 存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="7ce6b-156">不過請注意，網站每次出現的順序都不同。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ce6b-157">範例</span><span class="sxs-lookup"><span data-stu-id="7ce6b-157">Example</span></span>  
 <span data-ttu-id="7ce6b-158">下列程式碼顯示專案擴充，其使用 `GetURLContentsAsync` 方法從 Web 下載內容。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.   
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        'Dim total = 0  
        'For Each url In urlList  
  
        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
        '    ' The previous line abbreviates the following two assignment statements.  
  
        '    ' GetURLContentsAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    ' The actions from the foreach loop are moved to this async method.  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                ' CopyToAsync returns a Task, not a Task<T>.  
                Await responseStream.CopyToAsync(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="example"></a><span data-ttu-id="7ce6b-159">範例</span><span class="sxs-lookup"><span data-stu-id="7ce6b-159">Example</span></span>  
 <span data-ttu-id="7ce6b-160">下列程式碼顯示專案擴充，其使用 `HttpClient.GetByteArrayAsync` 方法從 Web 下載內容。</span><span class="sxs-lookup"><span data-stu-id="7ce6b-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        ''<snippet7>  
        'Dim total = 0  
        'For Each url In urlList  
        '    ' GetByteArrayAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    '<snippet31>  
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
        '    '</snippet31>  
  
        '    ' The following two lines can replace the previous assignment statement.  
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://www.msdn.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ce6b-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ce6b-161">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="7ce6b-162">逐步解說：使用 Async 和 Await 存取 Web (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ce6b-162">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
