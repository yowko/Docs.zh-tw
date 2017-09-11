---
title: "如何︰ 使用 Task.WhenAll (Visual Basic) 來擴充非同步逐步解說 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 91cecc84899c9a87307ed5799485ec60ef341e65
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a><span data-ttu-id="d235e-102">如何︰ 使用 Task.WhenAll (Visual Basic) 來擴充非同步逐步解說</span><span class="sxs-lookup"><span data-stu-id="d235e-102">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>
<span data-ttu-id="d235e-103">您可以改善效能的非同步方案中[逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)使用<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>方法。</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d235e-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="d235e-104">這個方法以非同步方式等候多個非同步作業，表示為工作的集合。</span><span class="sxs-lookup"><span data-stu-id="d235e-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="d235e-105">您可能已經注意到在這個逐步解說的網站下載不同的速率。</span><span class="sxs-lookup"><span data-stu-id="d235e-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="d235e-106">有時網站是非常緩慢，這會延遲所有剩餘的下載。</span><span class="sxs-lookup"><span data-stu-id="d235e-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="d235e-107">當您執行您建置的非同步方案逐步解說中，您可以結束程式輕鬆地如果不想等待，但更好的選項會啟動一次的所有下載並讓更快下載繼續而不需等待的延遲。</span><span class="sxs-lookup"><span data-stu-id="d235e-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="d235e-108">您套用`Task.WhenAll`的工作集合的方法。</span><span class="sxs-lookup"><span data-stu-id="d235e-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="d235e-109">應用程式的`WhenAll`傳回集合中的每項工作完成之前未完成的單一工作。</span><span class="sxs-lookup"><span data-stu-id="d235e-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="d235e-110">若要平行執行，就會出現的工作，但沒有其他執行緒會建立。</span><span class="sxs-lookup"><span data-stu-id="d235e-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="d235e-111">工作可以依任何順序完成。</span><span class="sxs-lookup"><span data-stu-id="d235e-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d235e-112">下列程序說明中的非同步應用程式的擴充功能[逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="d235e-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="d235e-113">您可以開發應用程式以完成這個逐步解說，或下載的程式碼來[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)。</span><span class="sxs-lookup"><span data-stu-id="d235e-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
>   
>  <span data-ttu-id="d235e-114">若要執行此範例，您必須安裝 Visual Studio 2012 或更新版本安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="d235e-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="d235e-115">若要新增 Task.WhenAll GetURLContentsAsync 解決方案</span><span class="sxs-lookup"><span data-stu-id="d235e-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1.  <span data-ttu-id="d235e-116">新增`ProcessURLAsync`開發中的第一個應用程式的方法[逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="d235e-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="d235e-117">如果您已下載的程式碼[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)，開啟 AsyncWalkthrough 專案，然後再新增`ProcessURLAsync`MainWindow.xaml.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="d235e-117">If you downloaded the code from  [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="d235e-118">如果您完成逐步解說開發的程式碼，加入`ProcessURLAsync`應用程式，其中包含`GetURLContentsAsync`方法。</span><span class="sxs-lookup"><span data-stu-id="d235e-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="d235e-119">此應用程式的 MainWindow.xaml.vb 檔是 「 完整程式碼範例從逐步解說 > 一節的第一個範例。</span><span class="sxs-lookup"><span data-stu-id="d235e-119">The MainWindow.xaml.vb file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="d235e-120">`ProcessURLAsync`方法會彙總的主體中的動作`For Each`迴圈`SumPageSizesAsync`在原始的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="d235e-120">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="d235e-121">此方法以非同步方式為位元組陣列，指定網站的內容下載然後並顯示傳回的位元組陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="d235e-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="d235e-122">註解化或刪除`For Each`迴圈`SumPageSizesAsync`，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="d235e-122">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
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
  
3.  <span data-ttu-id="d235e-123">建立工作的集合。</span><span class="sxs-lookup"><span data-stu-id="d235e-123">Create a collection of tasks.</span></span> <span data-ttu-id="d235e-124">下列程式碼定義[查詢](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)，程式執行時<xref:System.Linq.Enumerable.ToArray%2A>方法建立的每個網站的內容下載工作的集合。</xref:System.Linq.Enumerable.ToArray%2A></span><span class="sxs-lookup"><span data-stu-id="d235e-124">The following code defines a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="d235e-125">當評估查詢時，會啟動工作。</span><span class="sxs-lookup"><span data-stu-id="d235e-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="d235e-126">將下列程式碼加入至方法`SumPageSizesAsync`宣告後`urlList`。</span><span class="sxs-lookup"><span data-stu-id="d235e-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="d235e-127">套用`Task.WhenAll`至集合的工作， `downloadTasks`。</span><span class="sxs-lookup"><span data-stu-id="d235e-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="d235e-128">`Task.WhenAll`傳回已完成的工作集合中的所有工作完成的單一工作。</span><span class="sxs-lookup"><span data-stu-id="d235e-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="d235e-129">在下列範例中，`Await`運算式等候完成的單一工作`WhenAll`傳回。</span><span class="sxs-lookup"><span data-stu-id="d235e-129">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="d235e-130">運算式評估為整數，其中每個整數是下載網站的長度的陣列。</span><span class="sxs-lookup"><span data-stu-id="d235e-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="d235e-131">加入下列程式碼以`SumPageSizesAsync`，只是您在上一個步驟中加入的程式碼後面。</span><span class="sxs-lookup"><span data-stu-id="d235e-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="d235e-132">最後，使用<xref:System.Linq.Enumerable.Sum%2A>方法，以計算所有網站的長度總和。</xref:System.Linq.Enumerable.Sum%2A></span><span class="sxs-lookup"><span data-stu-id="d235e-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="d235e-133">將下列行加入`SumPageSizesAsync`。</span><span class="sxs-lookup"><span data-stu-id="d235e-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="d235e-134">若要新增 Task.WhenAll HttpClient.GetByteArrayAsync 解決方案</span><span class="sxs-lookup"><span data-stu-id="d235e-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1.  <span data-ttu-id="d235e-135">加入下列版本`ProcessURLAsync`開發中的第二個應用程式[逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="d235e-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="d235e-136">如果您已下載的程式碼[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)，開啟 AsyncWalkthrough_HttpClient 專案，然後再新增`ProcessURLAsync`MainWindow.xaml.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="d235e-136">If you downloaded the code from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="d235e-137">如果您完成逐步解說開發的程式碼，加入`ProcessURLAsync`應用程式使用`HttpClient.GetByteArrayAsync`方法。</span><span class="sxs-lookup"><span data-stu-id="d235e-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="d235e-138">此應用程式的 MainWindow.xaml.vb 檔是 「 完整程式碼範例從逐步解說 > 一節中的第二個範例。</span><span class="sxs-lookup"><span data-stu-id="d235e-138">The MainWindow.xaml.vb file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="d235e-139">`ProcessURLAsync`方法會彙總的主體中的動作`For Each`迴圈`SumPageSizesAsync`在原始的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="d235e-139">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="d235e-140">此方法以非同步方式為位元組陣列，指定網站的內容下載然後並顯示傳回的位元組陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="d235e-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="d235e-141">唯一差別`ProcessURLAsync`在先前程序中的方法是使用<xref:System.Net.Http.HttpClient>執行個體， `client`。</xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="d235e-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="d235e-142">註解化或刪除`For Each`迴圈`SumPageSizesAsync`，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="d235e-142">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
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
  
3.  <span data-ttu-id="d235e-143">定義[查詢](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)，程式執行時<xref:System.Linq.Enumerable.ToArray%2A>方法建立的每個網站的內容下載工作的集合。</xref:System.Linq.Enumerable.ToArray%2A></span><span class="sxs-lookup"><span data-stu-id="d235e-143">Define a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="d235e-144">當評估查詢時，會啟動工作。</span><span class="sxs-lookup"><span data-stu-id="d235e-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="d235e-145">將下列程式碼加入至方法`SumPageSizesAsync`宣告後`client`和`urlList`。</span><span class="sxs-lookup"><span data-stu-id="d235e-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="d235e-146">接下來，套用`Task.WhenAll`至集合的工作， `downloadTasks`。</span><span class="sxs-lookup"><span data-stu-id="d235e-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="d235e-147">`Task.WhenAll`傳回已完成的工作集合中的所有工作完成的單一工作。</span><span class="sxs-lookup"><span data-stu-id="d235e-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="d235e-148">在下列範例中，`Await`運算式等候完成的單一工作`WhenAll`傳回。</span><span class="sxs-lookup"><span data-stu-id="d235e-148">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="d235e-149">完成時，`Await`運算式評估為整數，其中每個整數是下載網站的長度的陣列。</span><span class="sxs-lookup"><span data-stu-id="d235e-149">When complete, the `Await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="d235e-150">加入下列程式碼以`SumPageSizesAsync`，只是您在上一個步驟中加入的程式碼後面。</span><span class="sxs-lookup"><span data-stu-id="d235e-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="d235e-151">最後，使用<xref:System.Linq.Enumerable.Sum%2A>方法來取得所有網站的長度總和。</xref:System.Linq.Enumerable.Sum%2A></span><span class="sxs-lookup"><span data-stu-id="d235e-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="d235e-152">將下列行加入`SumPageSizesAsync`。</span><span class="sxs-lookup"><span data-stu-id="d235e-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="d235e-153">若要測試 Task.WhenAll 解決方案</span><span class="sxs-lookup"><span data-stu-id="d235e-153">To test the Task.WhenAll solutions</span></span>  
  
-   <span data-ttu-id="d235e-154">其中一個解決方案中，選擇 F5 鍵以執行程式，然後選擇**啟動** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d235e-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="d235e-155">輸出應該類似的輸出中的非同步方案[逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="d235e-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="d235e-156">但是請注意，網站會出現在不同的順序每次。</span><span class="sxs-lookup"><span data-stu-id="d235e-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d235e-157">範例</span><span class="sxs-lookup"><span data-stu-id="d235e-157">Example</span></span>  
 <span data-ttu-id="d235e-158">下列程式碼顯示使用專案的擴充`GetURLContentsAsync`方法，從 web 下載內容。</span><span class="sxs-lookup"><span data-stu-id="d235e-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="d235e-159">範例</span><span class="sxs-lookup"><span data-stu-id="d235e-159">Example</span></span>  
 <span data-ttu-id="d235e-160">下列程式碼顯示擴充方法會使用專案`HttpClient.GetByteArrayAsync`從 web 下載內容。</span><span class="sxs-lookup"><span data-stu-id="d235e-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d235e-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d235e-161">See Also</span></span>  
 <span data-ttu-id="d235e-162"><xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName></xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d235e-162"><xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName></span></span>   
<span data-ttu-id="d235e-163"> [逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)</span><span class="sxs-lookup"><span data-stu-id="d235e-163"> [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)</span></span>
