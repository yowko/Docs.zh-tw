---
title: "使用非同步方式存取檔案 (Visual Basic) |Microsoft 文件"
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
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
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
ms.openlocfilehash: 85f5fe17a012402c406eed972debd1f5889dd393
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="f3442-102">使用非同步方式存取檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3442-102">Using Async for File Access (Visual Basic)</span></span>
<span data-ttu-id="f3442-103">您可以使用非同步功能來存取檔案。</span><span class="sxs-lookup"><span data-stu-id="f3442-103">You can use the Async feature to access files.</span></span> <span data-ttu-id="f3442-104">使用 Async 功能，您就可以呼叫非同步方法，而不需要使用回呼或將您的程式碼分散到多種方法或 Lambda 運算式上。</span><span class="sxs-lookup"><span data-stu-id="f3442-104">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="f3442-105">若要讓同步程式碼變成非同步，您只要呼叫非同步方法，而不是同步方法呼叫，並加入幾個關鍵字到程式碼。</span><span class="sxs-lookup"><span data-stu-id="f3442-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="f3442-106">您可以考慮加入檔案存取呼叫非同步的原因如下︰</span><span class="sxs-lookup"><span data-stu-id="f3442-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="f3442-107">非同步可讓 UI 應用程式回應速度更快因為 UI 執行緒啟動作業可以執行其他工作。</span><span class="sxs-lookup"><span data-stu-id="f3442-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="f3442-108">如果 UI 執行緒必須執行的程式碼的時間較長 （例如，超過 50 毫秒為單位），直到 I/O 完成且在 UI 執行緒可以再次處理鍵盤和滑鼠輸入和其他事件，可能會凍結 UI。</span><span class="sxs-lookup"><span data-stu-id="f3442-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="f3442-109">非同步提升 ASP.NET 的延展性和其他伺服器應用程式，藉由減少執行緒。</span><span class="sxs-lookup"><span data-stu-id="f3442-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="f3442-110">如果應用程式會使用專用的執行緒，每個回應，同時處理一千個要求所需一千個執行緒。</span><span class="sxs-lookup"><span data-stu-id="f3442-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="f3442-111">非同步作業通常不需要使用一個執行緒等待期間。</span><span class="sxs-lookup"><span data-stu-id="f3442-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="f3442-112">結尾簡短地使用現有的 I/O 完成執行緒。</span><span class="sxs-lookup"><span data-stu-id="f3442-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="f3442-113">檔案存取作業的延遲可能會在目前的情況下很低，但延遲可能會大幅增加未來。</span><span class="sxs-lookup"><span data-stu-id="f3442-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="f3442-114">例如，檔案可能會移至世界各地的伺服器。</span><span class="sxs-lookup"><span data-stu-id="f3442-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="f3442-115">加入使用 Async 功能的額外負荷很小。</span><span class="sxs-lookup"><span data-stu-id="f3442-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="f3442-116">以平行方式時，可以輕鬆地執行非同步工作。</span><span class="sxs-lookup"><span data-stu-id="f3442-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="f3442-117">執行範例</span><span class="sxs-lookup"><span data-stu-id="f3442-117">Running the Examples</span></span>  
 <span data-ttu-id="f3442-118">若要執行本主題中的範例，您可以建立**WPF 應用程式**或**Windows Form 應用程式**，然後新增**按鈕**。</span><span class="sxs-lookup"><span data-stu-id="f3442-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="f3442-119">在按鈕的`Click`事件，每個範例中新增的第一個方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f3442-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="f3442-120">在下列範例中，包括下列`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f3442-120">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="f3442-121">使用 FileStream 類別</span><span class="sxs-lookup"><span data-stu-id="f3442-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="f3442-122">在這個主題使用範例<xref:System.IO.FileStream>類別，有一個選項，會造成作業系統層級發生的非同步 I/O。</xref:System.IO.FileStream></span><span class="sxs-lookup"><span data-stu-id="f3442-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="f3442-123">您可以藉由使用此選項，避免封鎖執行緒集區執行緒，在許多情況下。</span><span class="sxs-lookup"><span data-stu-id="f3442-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="f3442-124">若要啟用此選項，您指定`useAsync=true`或`options=FileOptions.Asynchronous`建構函式呼叫引數。</span><span class="sxs-lookup"><span data-stu-id="f3442-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="f3442-125">您無法使用此選項<xref:System.IO.StreamReader>，而<xref:System.IO.StreamWriter>如果您開啟它們直接藉由指定檔案路徑。</xref:System.IO.StreamWriter> </xref:System.IO.StreamReader></span><span class="sxs-lookup"><span data-stu-id="f3442-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="f3442-126">不過，使用此選項，如果您提供給他們<xref:System.IO.Stream>，<xref:System.IO.FileStream>類別開啟。</xref:System.IO.FileStream> </xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="f3442-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="f3442-127">請注意，非同步呼叫 UI 應用程式中更快速即使執行緒集區執行緒遭到封鎖，因為 UI 執行緒未在等待時封鎖。</span><span class="sxs-lookup"><span data-stu-id="f3442-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="f3442-128">寫入文字</span><span class="sxs-lookup"><span data-stu-id="f3442-128">Writing Text</span></span>  
 <span data-ttu-id="f3442-129">下列範例會將文字寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="f3442-129">The following example writes text to a file.</span></span> <span data-ttu-id="f3442-130">在每個 await 陳述式，方法會立即結束。</span><span class="sxs-lookup"><span data-stu-id="f3442-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="f3442-131">檔案 I/O 完成時，此方法會繼續在 await 陳述式後面的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f3442-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="f3442-132">請注意，async 修飾詞使用 await 陳述式的方法定義中。</span><span class="sxs-lookup"><span data-stu-id="f3442-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="f3442-133">原始範例有陳述式`Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`，也就是下列兩個陳述式的縮減︰</span><span class="sxs-lookup"><span data-stu-id="f3442-133">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="f3442-134">第一個陳述式傳回的工作，並造成檔案啟動的處理。</span><span class="sxs-lookup"><span data-stu-id="f3442-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="f3442-135">與 await 第二個陳述式會立即結束，並傳回不同的工作的方法。</span><span class="sxs-lookup"><span data-stu-id="f3442-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="f3442-136">檔案稍後處理完成時，執行會傳回 await 後面的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f3442-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="f3442-137">如需詳細資訊，請參閱[非同步程式 (Visual Basic) 中的控制流程](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)。</span><span class="sxs-lookup"><span data-stu-id="f3442-137">For more information, see  [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="f3442-138">讀取文字</span><span class="sxs-lookup"><span data-stu-id="f3442-138">Reading Text</span></span>  
 <span data-ttu-id="f3442-139">下列範例會從檔案讀取文字。</span><span class="sxs-lookup"><span data-stu-id="f3442-139">The following example reads text from a file.</span></span> <span data-ttu-id="f3442-140">文字是經過緩衝處理，在此情況下，放入<xref:System.Text.StringBuilder>.</xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="f3442-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="f3442-141">不像在先前範例中，等候評估產生的值。</span><span class="sxs-lookup"><span data-stu-id="f3442-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="f3442-142"><xref:System.IO.Stream.ReadAsync%2A>方法會傳回<xref:System.Threading.Tasks.Task>\< <xref:System.Int32>>，因此等候的評估會產生`Int32`值 (`numRead`) 在作業完成之後。</xref:System.Int32> </xref:System.Threading.Tasks.Task> </xref:System.IO.Stream.ReadAsync%2A></span><span class="sxs-lookup"><span data-stu-id="f3442-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="f3442-143">如需詳細資訊，請參閱[非同步傳回類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f3442-143">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="f3442-144">平行非同步 I/O</span><span class="sxs-lookup"><span data-stu-id="f3442-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="f3442-145">下列範例會示範平行處理，藉由撰寫 10 個文字檔案。</span><span class="sxs-lookup"><span data-stu-id="f3442-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="f3442-146">針對每個檔案，<xref:System.IO.Stream.WriteAsync%2A>方法傳回的工作，然後加入工作清單。</xref:System.IO.Stream.WriteAsync%2A></span><span class="sxs-lookup"><span data-stu-id="f3442-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="f3442-147">`Await Task.WhenAll(tasks)`陳述式結束方法，並繼續處理檔案時的方法內的所有工作完成。</span><span class="sxs-lookup"><span data-stu-id="f3442-147">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="f3442-148">範例會關閉所有<xref:System.IO.FileStream>執行個體在`Finally`封鎖在工作完成後。</xref:System.IO.FileStream></span><span class="sxs-lookup"><span data-stu-id="f3442-148">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="f3442-149">如果每個`FileStream`改為建立`Imports`陳述式，`FileStream`可能在工作完成之前的處置。</span><span class="sxs-lookup"><span data-stu-id="f3442-149">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="f3442-150">請注意，任何效能提升幾乎完全從平行處理和非同步處理。</span><span class="sxs-lookup"><span data-stu-id="f3442-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="f3442-151">非同步功能的優點是它不會佔用多個執行緒，並不會佔用使用者介面執行緒。</span><span class="sxs-lookup"><span data-stu-id="f3442-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="f3442-152">當使用<xref:System.IO.Stream.WriteAsync%2A>和<xref:System.IO.Stream.ReadAsync%2A>方法，您可以指定<xref:System.Threading.CancellationToken>，可用來取消作業的中間資料流。</xref:System.Threading.CancellationToken> </xref:System.IO.Stream.ReadAsync%2A> </xref:System.IO.Stream.WriteAsync%2A></span><span class="sxs-lookup"><span data-stu-id="f3442-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="f3442-153">如需詳細資訊，請參閱[微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)和[Managed 執行緒中的取消](http://msdn.microsoft.com/library/eea11fe5-d8b0-4314-bb5d-8a58166fb1c3)。</span><span class="sxs-lookup"><span data-stu-id="f3442-153">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](http://msdn.microsoft.com/library/eea11fe5-d8b0-4314-bb5d-8a58166fb1c3).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3442-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3442-154">See Also</span></span>  
 <span data-ttu-id="f3442-155">[非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="f3442-155">[Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="f3442-156"> [非同步方法的傳回類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span><span class="sxs-lookup"><span data-stu-id="f3442-156"> [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span></span>  
<span data-ttu-id="f3442-157"> [非同步程式 (Visual Basic) 中的控制流程](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)</span><span class="sxs-lookup"><span data-stu-id="f3442-157"> [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)</span></span>
