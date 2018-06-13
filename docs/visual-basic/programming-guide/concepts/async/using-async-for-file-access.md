---
title: 使用非同步方式存取檔案 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: e12eaa57d0f7186e9d281b89ec3abd26280e12ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644221"
---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="84770-102">使用非同步方式存取檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84770-102">Using Async for File Access (Visual Basic)</span></span>
<span data-ttu-id="84770-103">您可以使用非同步功能，以存取檔案。</span><span class="sxs-lookup"><span data-stu-id="84770-103">You can use the Async feature to access files.</span></span> <span data-ttu-id="84770-104">使用 Async 功能，您就可以呼叫非同步方法，而不需要使用回呼或將您的程式碼分散到多種方法或 Lambda 運算式上。</span><span class="sxs-lookup"><span data-stu-id="84770-104">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="84770-105">若要讓同步程式碼變成非同步，只要呼叫非同步方法 (而不是同步方法)，然後將幾個關鍵字新增至程式碼即可。</span><span class="sxs-lookup"><span data-stu-id="84770-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="84770-106">您可能會基於下列原因將非同步功能新增至檔案存取呼叫：</span><span class="sxs-lookup"><span data-stu-id="84770-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="84770-107">非同步功能可讓 UI 應用程式回應速度更快，因為啟動作業的 UI 執行緒可以執行其他工作。</span><span class="sxs-lookup"><span data-stu-id="84770-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="84770-108">如果 UI 執行緒必須執行相當耗時的程式碼 (例如超過 50 毫秒)，UI 可能會凍結到 I/O 完成，之後 UI 執行緒就可以再次處理鍵盤和滑鼠輸入以及其他事件。</span><span class="sxs-lookup"><span data-stu-id="84770-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="84770-109">非同步功能藉由降低對執行緒的需求，來改善 ASP.NET 及其他伺服器架構應用程式的延展性。</span><span class="sxs-lookup"><span data-stu-id="84770-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="84770-110">如果應用程式針對每個回應使用專用執行緒，並同時處理一千個要求，則需要一千個執行緒。</span><span class="sxs-lookup"><span data-stu-id="84770-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="84770-111">非同步作業在等候期間通常不需要使用執行緒。</span><span class="sxs-lookup"><span data-stu-id="84770-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="84770-112">它們可能會在結束時短暫使用現有的 I/O 完成執行緒。</span><span class="sxs-lookup"><span data-stu-id="84770-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="84770-113">檔案存取作業的延遲在目前情況下可能很低，但未來可能會大幅增加。</span><span class="sxs-lookup"><span data-stu-id="84770-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="84770-114">例如，檔案可能會移至世界各地的伺服器。</span><span class="sxs-lookup"><span data-stu-id="84770-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="84770-115">使用非同步功能所增加的額外負荷很小。</span><span class="sxs-lookup"><span data-stu-id="84770-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="84770-116">您可以輕鬆地同時執行多個非同步工作。</span><span class="sxs-lookup"><span data-stu-id="84770-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="84770-117">執行範例</span><span class="sxs-lookup"><span data-stu-id="84770-117">Running the Examples</span></span>  
 <span data-ttu-id="84770-118">為了執行本主題中的範例，您可以建立 **WPF 應用程式**或 **Windows Forms 應用程式**，然後新增一個**按鈕**。</span><span class="sxs-lookup"><span data-stu-id="84770-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="84770-119">在按鈕的 `Click` 事件中，新增呼叫至每個範例中的第一個方法。</span><span class="sxs-lookup"><span data-stu-id="84770-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="84770-120">在下列範例中，加入下列 `Imports` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="84770-120">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="84770-121">使用 FileStream 類別</span><span class="sxs-lookup"><span data-stu-id="84770-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="84770-122">本主題中的範例使用 <xref:System.IO.FileStream> 類別，其所包含的一個選項會導致在作業系統層級發生非同步 I/O。</span><span class="sxs-lookup"><span data-stu-id="84770-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="84770-123">您可以在許多情況下，使用此選項來避免封鎖 ThreadPool 執行緒。</span><span class="sxs-lookup"><span data-stu-id="84770-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="84770-124">若要啟用此選項，請在建構函式呼叫中指定 `useAsync=true` 或 `options=FileOptions.Asynchronous` 引數。</span><span class="sxs-lookup"><span data-stu-id="84770-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="84770-125">如果您藉由指定檔案路徑來直接開啟它們，就無法搭配使用這個選項與 <xref:System.IO.StreamReader> 和 <xref:System.IO.StreamWriter>。</span><span class="sxs-lookup"><span data-stu-id="84770-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="84770-126">不過，如果您提供它們已開啟 <xref:System.IO.FileStream> 類別的 <xref:System.IO.Stream>，則可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="84770-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="84770-127">請注意，即使已封鎖 ThreadPool 執行緒，非同步呼叫在 UI 應用程式中還是更快，因為在等候期間不會封鎖 UI 執行緒。</span><span class="sxs-lookup"><span data-stu-id="84770-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="84770-128">寫入文字</span><span class="sxs-lookup"><span data-stu-id="84770-128">Writing Text</span></span>  
 <span data-ttu-id="84770-129">下列範例會將文字寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="84770-129">The following example writes text to a file.</span></span> <span data-ttu-id="84770-130">在每個 await 陳述式中，此方法會立即結束。</span><span class="sxs-lookup"><span data-stu-id="84770-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="84770-131">當檔案 I/O 完成時，此方法會在 await 陳述式後面的陳述式繼續進行。</span><span class="sxs-lookup"><span data-stu-id="84770-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="84770-132">請注意，使用 await 陳述式的方法定義中會有 async 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="84770-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```vb  
Public Async Sub ProcessWrite()  
    Dim filePath = "temp2.txt"  
    Dim text = "Hello World" & ControlChars.CrLf  
  
    Await WriteTextAsync(filePath, text)  
End Sub  
  
Private Async Function WriteTextAsync(filePath As String, text As String) As Task  
    Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize:=4096, useAsync:=True)  
  
        Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
    End Using  
End Function  
```  
  
 <span data-ttu-id="84770-133">原始範例具有陳述式 `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`，這是下列兩個陳述式的縮減：</span><span class="sxs-lookup"><span data-stu-id="84770-133">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="84770-134">第一個陳述式會傳回一個工作並開始處理檔案。</span><span class="sxs-lookup"><span data-stu-id="84770-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="84770-135">第二個陳述式具有 await，會立即結束方法並傳回其他工作。</span><span class="sxs-lookup"><span data-stu-id="84770-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="84770-136">稍後完成處理檔案之後，則會回到 await 後面的陳述式繼續執行。</span><span class="sxs-lookup"><span data-stu-id="84770-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="84770-137">如需詳細資訊，請參閱[非同步程式 (Visual Basic) 中的控制流程](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)。</span><span class="sxs-lookup"><span data-stu-id="84770-137">For more information, see  [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="84770-138">讀取文字</span><span class="sxs-lookup"><span data-stu-id="84770-138">Reading Text</span></span>  
 <span data-ttu-id="84770-139">下列範例會從檔案讀取文字。</span><span class="sxs-lookup"><span data-stu-id="84770-139">The following example reads text from a file.</span></span> <span data-ttu-id="84770-140">此文字已經過緩衝處理，在本例中已置於 <xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="84770-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="84770-141">不同於上一個範例，await 的評估會產生一個值。</span><span class="sxs-lookup"><span data-stu-id="84770-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="84770-142"><xref:System.IO.Stream.ReadAsync%2A> 方法會傳回 <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>，因此在作業完成之後，await 的評估會產生 `Int32` 值 (`numRead`)。</span><span class="sxs-lookup"><span data-stu-id="84770-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="84770-143">如需詳細資訊，請參閱[非同步傳回型別 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="84770-143">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
```vb  
Public Async Sub ProcessRead()  
    Dim filePath = "temp2.txt"  
  
    If File.Exists(filePath) = False Then  
        Debug.WriteLine("file not found: " & filePath)  
    Else  
        Try  
            Dim text As String = Await ReadTextAsync(filePath)  
            Debug.WriteLine(text)  
        Catch ex As Exception  
            Debug.WriteLine(ex.Message)  
        End Try  
    End If  
End Sub  
  
Private Async Function ReadTextAsync(filePath As String) As Task(Of String)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize:=4096, useAsync:=True)  
  
        Dim sb As New StringBuilder  
  
        Dim buffer As Byte() = New Byte(&H1000) {}  
        Dim numRead As Integer  
        numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        While numRead <> 0  
            Dim text As String = Encoding.Unicode.GetString(buffer, 0, numRead)  
            sb.Append(text)  
  
            numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        End While  
  
        Return sb.ToString  
    End Using  
End Function  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="84770-144">平行非同步 I/O</span><span class="sxs-lookup"><span data-stu-id="84770-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="84770-145">下列範例示範如何平行處理寫入 10 個文字檔的作業。</span><span class="sxs-lookup"><span data-stu-id="84770-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="84770-146">針對每個檔案，<xref:System.IO.Stream.WriteAsync%2A> 方法會傳回一個工作，此工作之後會新增至工作清單。</span><span class="sxs-lookup"><span data-stu-id="84770-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="84770-147">`Await Task.WhenAll(tasks)` 陳述式會在所有工作的檔案處理完成時結束方法，並在方法內繼續進行。</span><span class="sxs-lookup"><span data-stu-id="84770-147">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="84770-148">此範例會在工作完成之後，關閉 `Finally` 區塊中的所有 <xref:System.IO.FileStream> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="84770-148">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="84770-149">如果改為在 `Imports` 陳述式中建立每個 `FileStream`，`FileStream` 可能會在工作完成前就被處置。</span><span class="sxs-lookup"><span data-stu-id="84770-149">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="84770-150">請注意，任何效能提升幾乎完全來自平行處理，而不是非同步處理。</span><span class="sxs-lookup"><span data-stu-id="84770-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="84770-151">非同步的優點在於不會佔用多個執行緒，而且不會佔用使用者介面執行緒。</span><span class="sxs-lookup"><span data-stu-id="84770-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```vb  
Public Async Sub ProcessWriteMult()  
    Dim folder = "tempfolder\"  
    Dim tasks As New List(Of Task)  
    Dim sourceStreams As New List(Of FileStream)  
  
    Try  
        For index = 1 To 10  
            Dim text = "In file " & index.ToString & ControlChars.CrLf  
  
            Dim fileName = "thefile" & index.ToString("00") & ".txt"  
            Dim filePath = folder & fileName  
  
            Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
            Dim sourceStream As New FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize:=4096, useAsync:=True)  
  
            Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
            sourceStreams.Add(sourceStream)  
  
            tasks.Add(theTask)  
        Next  
  
        Await Task.WhenAll(tasks)  
    Finally  
        For Each sourceStream As FileStream In sourceStreams  
            sourceStream.Close()  
        Next  
    End Try  
End Sub  
```  
  
 <span data-ttu-id="84770-152">使用 <xref:System.IO.Stream.WriteAsync%2A> 和 <xref:System.IO.Stream.ReadAsync%2A> 方法時，您可以指定 <xref:System.Threading.CancellationToken>，這可用來在中途取消作業。</span><span class="sxs-lookup"><span data-stu-id="84770-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="84770-153">如需詳細資訊，請參閱[微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)和[Managed 執行緒中的取消](../../../../standard/threading/cancellation-in-managed-threads.md)。</span><span class="sxs-lookup"><span data-stu-id="84770-153">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84770-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84770-154">See Also</span></span>  
 [<span data-ttu-id="84770-155">使用 Async 和 Await 進行非同步程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84770-155">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="84770-156">非同步方法的傳回型別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84770-156">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="84770-157">非同步程式中的控制流程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84770-157">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
