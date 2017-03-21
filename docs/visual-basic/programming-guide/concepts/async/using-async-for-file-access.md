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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e0e548989b1d2c32b9faf5ce0dd90ae371dfc028
ms.lasthandoff: 03/13/2017

---
# <a name="using-async-for-file-access-visual-basic"></a>使用非同步方式存取檔案 (Visual Basic)
您可以使用非同步功能來存取檔案。 使用 Async 功能，您就可以呼叫非同步方法，而不需要使用回呼或將您的程式碼分散到多種方法或 Lambda 運算式上。 若要讓同步程式碼變成非同步，您只要呼叫非同步方法，而不是同步方法呼叫，並加入幾個關鍵字到程式碼。  
  
 您可以考慮加入檔案存取呼叫非同步的原因如下︰  
  
-   非同步可讓 UI 應用程式回應速度更快因為 UI 執行緒啟動作業可以執行其他工作。 如果 UI 執行緒必須執行的程式碼的時間較長 （例如，超過 50 毫秒為單位），直到 I/O 完成且在 UI 執行緒可以再次處理鍵盤和滑鼠輸入和其他事件，可能會凍結 UI。  
  
-   非同步提升 ASP.NET 的延展性和其他伺服器應用程式，藉由減少執行緒。 如果應用程式會使用專用的執行緒，每個回應，同時處理一千個要求所需一千個執行緒。 非同步作業通常不需要使用一個執行緒等待期間。 結尾簡短地使用現有的 I/O 完成執行緒。  
  
-   檔案存取作業的延遲可能會在目前的情況下很低，但延遲可能會大幅增加未來。 例如，檔案可能會移至世界各地的伺服器。  
  
-   加入使用 Async 功能的額外負荷很小。  
  
-   以平行方式時，可以輕鬆地執行非同步工作。  
  
## <a name="running-the-examples"></a>執行範例  
 若要執行本主題中的範例，您可以建立**WPF 應用程式**或**Windows Form 應用程式**，然後新增**按鈕**。 在按鈕的`Click`事件，每個範例中新增的第一個方法的呼叫。  
  
 在下列範例中，包括下列`Imports`陳述式。  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>使用 FileStream 類別  
 在這個主題使用範例<xref:System.IO.FileStream>類別，有一個選項，會造成作業系統層級發生的非同步 I/O。</xref:System.IO.FileStream> 您可以藉由使用此選項，避免封鎖執行緒集區執行緒，在許多情況下。 若要啟用此選項，您指定`useAsync=true`或`options=FileOptions.Asynchronous`建構函式呼叫引數。  
  
 您無法使用此選項<xref:System.IO.StreamReader>，而<xref:System.IO.StreamWriter>如果您開啟它們直接藉由指定檔案路徑。</xref:System.IO.StreamWriter> </xref:System.IO.StreamReader> 不過，使用此選項，如果您提供給他們<xref:System.IO.Stream>，<xref:System.IO.FileStream>類別開啟。</xref:System.IO.FileStream> </xref:System.IO.Stream> 請注意，非同步呼叫 UI 應用程式中更快速即使執行緒集區執行緒遭到封鎖，因為 UI 執行緒未在等待時封鎖。  
  
## <a name="writing-text"></a>寫入文字  
 下列範例會將文字寫入檔案。 在每個 await 陳述式，方法會立即結束。 檔案 I/O 完成時，此方法會繼續在 await 陳述式後面的陳述式。 請注意，async 修飾詞使用 await 陳述式的方法定義中。  
  
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
  
 原始範例有陳述式`Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`，也就是下列兩個陳述式的縮減︰  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 第一個陳述式傳回的工作，並造成檔案啟動的處理。 與 await 第二個陳述式會立即結束，並傳回不同的工作的方法。 檔案稍後處理完成時，執行會傳回 await 後面的陳述式。 如需詳細資訊，請參閱[非同步程式 (Visual Basic) 中的控制流程](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)。  
  
## <a name="reading-text"></a>讀取文字  
 下列範例會從檔案讀取文字。 文字是經過緩衝處理，在此情況下，放入<xref:System.Text.StringBuilder>.</xref:System.Text.StringBuilder> 不像在先前範例中，等候評估產生的值。 <xref:System.IO.Stream.ReadAsync%2A>方法會傳回<xref:System.Threading.Tasks.Task>\< <xref:System.Int32>>，因此等候的評估會產生`Int32`值 (`numRead`) 在作業完成之後。</xref:System.Int32> </xref:System.Threading.Tasks.Task> </xref:System.IO.Stream.ReadAsync%2A> 如需詳細資訊，請參閱[非同步傳回類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。  
  
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
  
## <a name="parallel-asynchronous-io"></a>平行非同步 I/O  
 下列範例會示範平行處理，藉由撰寫 10 個文字檔案。 針對每個檔案，<xref:System.IO.Stream.WriteAsync%2A>方法傳回的工作，然後加入工作清單。</xref:System.IO.Stream.WriteAsync%2A> `Await Task.WhenAll(tasks)`陳述式結束方法，並繼續處理檔案時的方法內的所有工作完成。  
  
 範例會關閉所有<xref:System.IO.FileStream>執行個體在`Finally`封鎖在工作完成後。</xref:System.IO.FileStream> 如果每個`FileStream`改為建立`Imports`陳述式，`FileStream`可能在工作完成之前的處置。  
  
 請注意，任何效能提升幾乎完全從平行處理和非同步處理。 非同步功能的優點是它不會佔用多個執行緒，並不會佔用使用者介面執行緒。  
  
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
  
 當使用<xref:System.IO.Stream.WriteAsync%2A>和<xref:System.IO.Stream.ReadAsync%2A>方法，您可以指定<xref:System.Threading.CancellationToken>，可用來取消作業的中間資料流。</xref:System.Threading.CancellationToken> </xref:System.IO.Stream.ReadAsync%2A> </xref:System.IO.Stream.WriteAsync%2A> 如需詳細資訊，請參閱[微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)和[Managed 執行緒中的取消](http://msdn.microsoft.com/library/eea11fe5-d8b0-4314-bb5d-8a58166fb1c3)。  
  
## <a name="see-also"></a>另請參閱  
 [非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [非同步方法的傳回類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)   
 [非同步程式 (Visual Basic) 中的控制流程](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
