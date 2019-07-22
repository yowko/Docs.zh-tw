---
title: 使用非同步方式存取檔案 (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 6ca47157575ef4569a43f334dae4f99a1986a7ce
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68330945"
---
# <a name="using-async-for-file-access-c"></a>使用非同步方式存取檔案 (C#)
您可以使用非同步功能來存取檔案。 使用非同步功能，您就可以呼叫非同步方法，而不需要使用回呼或將您的程式碼分散到多種方法或 Lambda 運算式上。 若要讓同步程式碼變成非同步，只要呼叫非同步方法 (而不是同步方法)，然後將幾個關鍵字新增至程式碼即可。  
  
 您可能會基於下列原因將非同步功能新增至檔案存取呼叫：  
  
- 非同步功能可讓 UI 應用程式回應速度更快，因為啟動作業的 UI 執行緒可以執行其他工作。 如果 UI 執行緒必須執行相當耗時的程式碼 (例如超過 50 毫秒)，UI 可能會凍結到 I/O 完成，之後 UI 執行緒就可以再次處理鍵盤和滑鼠輸入以及其他事件。  
  
- 非同步功能藉由降低對執行緒的需求，來改善 ASP.NET 及其他伺服器架構應用程式的延展性。 如果應用程式針對每個回應使用專用執行緒，並同時處理一千個要求，則需要一千個執行緒。 非同步作業在等候期間通常不需要使用執行緒。 它們可能會在結束時短暫使用現有的 I/O 完成執行緒。  
  
- 檔案存取作業的延遲在目前情況下可能很低，但未來可能會大幅增加。 例如，檔案可能會移至世界各地的伺服器。  
  
- 使用非同步功能所增加的額外負荷很小。  
  
- 您可以輕鬆地同時執行多個非同步工作。  
  
## <a name="running-the-examples"></a>執行範例  
 為了執行本主題中的範例，您可以建立 **WPF 應用程式**或 **Windows Forms 應用程式**，然後新增一個**按鈕**。 在按鈕的 `Click` 事件中，新增呼叫至每個範例中的第一個方法。  
  
 在下列範例中，加入下列 `using` 陳述式。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>使用 FileStream 類別  
 本主題中的範例使用 <xref:System.IO.FileStream> 類別，其所包含的一個選項會導致在作業系統層級發生非同步 I/O。 您可以在許多情況下，使用此選項來避免封鎖 ThreadPool 執行緒。 若要啟用此選項，請在建構函式呼叫中指定 `useAsync=true` 或 `options=FileOptions.Asynchronous` 引數。  
  
 如果您藉由指定檔案路徑來直接開啟它們，就無法搭配使用這個選項與 <xref:System.IO.StreamReader> 和 <xref:System.IO.StreamWriter>。 不過，如果您提供它們已開啟 <xref:System.IO.FileStream> 類別的 <xref:System.IO.Stream>，則可以使用此選項。 請注意，即使已封鎖 ThreadPool 執行緒，非同步呼叫在 UI 應用程式中還是更快，因為在等候期間不會封鎖 UI 執行緒。  
  
## <a name="writing-text"></a>寫入文字  
 下列範例會將文字寫入檔案。 在每個 await 陳述式中，此方法會立即結束。 當檔案 I/O 完成時，此方法會在 await 陳述式後面的陳述式繼續進行。 請注意，使用 await 陳述式的方法定義中會有 async 修飾詞。  
  
```csharp  
public async Task ProcessWriteAsync()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 原始範例具有陳述式 `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`，這是下列兩個陳述式的縮減：  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 第一個陳述式會傳回一個工作並開始處理檔案。 第二個陳述式具有 await，會立即結束方法並傳回其他工作。 稍後完成處理檔案之後，則會回到 await 後面的陳述式繼續執行。 如需詳細資訊，請參閱[非同步程式中的控制流程 (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)。  
  
## <a name="reading-text"></a>讀取文字  
 下列範例會從檔案讀取文字。 此文字已經過緩衝處理，在本例中已置於 <xref:System.Text.StringBuilder>。 不同於上一個範例，await 的評估會產生一個值。 <xref:System.IO.Stream.ReadAsync%2A> 方法會傳回 <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>，因此在作業完成之後，await 的評估會產生 `Int32` 值 (`numRead`)。 如需詳細資訊，請參閱[非同步方法的傳回型別 (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)。  
  
```csharp  
public async Task ProcessReadAsync()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="parallel-asynchronous-io"></a>平行非同步 I/O  
 下列範例示範如何平行處理寫入 10 個文字檔的作業。 針對每個檔案，<xref:System.IO.Stream.WriteAsync%2A> 方法會傳回一個工作，此工作之後會新增至工作清單。 `await Task.WhenAll(tasks);` 陳述式會在所有工作的檔案處理完成時結束方法，並在方法內繼續進行。  
  
 此範例會在工作完成之後，關閉 `finally` 區塊中的所有 <xref:System.IO.FileStream> 執行個體。 如果改為在 `using` 陳述式中建立每個 `FileStream`，`FileStream` 可能會在工作完成前就被處置。  
  
 請注意，任何效能提升幾乎完全來自平行處理，而不是非同步處理。 非同步的優點在於不會佔用多個執行緒，而且不會佔用使用者介面執行緒。  
  
```csharp  
public async Task ProcessWriteMultAsync()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 使用 <xref:System.IO.Stream.WriteAsync%2A> 和 <xref:System.IO.Stream.ReadAsync%2A> 方法時，您可以指定 <xref:System.Threading.CancellationToken>，這可用來在中途取消作業。 如需詳細資訊，請參閱[微調非同步應用程式 (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) 和 [Managed 執行緒中的取消作業](../../../../standard/threading/cancellation-in-managed-threads.md)。  
  
## <a name="see-also"></a>另請參閱

- [使用 Async 和 Await 進行非同步程式設計 (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [非同步方法的傳回型別 (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [非同步程式中的控制流程 (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
