---
title: 非同步檔案 I/O
description: 深入瞭解 .NET 中的非同步檔案 i/o。 瞭解非同步方法以簡化非同步作業，例如 System.io.stream.readasync、System.io.stream.writeasync 等等。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
ms.openlocfilehash: aaf722c4af1598b639ffc56e30639e93dbc8a514
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823455"
---
# <a name="asynchronous-file-io"></a>非同步檔案 I/O

非同步作業可讓您執行耗用大量資源的 I/O 作業，而不需要封鎖主執行緒。 這項效能考慮在 Windows 8. x 存放區應用程式或傳統型應用程式中特別重要，因為這種情況下，耗時的串流作業可以封鎖 UI 執行緒，並讓您的應用程式看起來好像無法正常運作。

從 .NET Framework 4.5 開始，i/o 類型包含非同步方法，可簡化非同步作業。 非同步方法在其名稱中包含 `Async` ，例如 <xref:System.IO.Stream.ReadAsync%2A>、 <xref:System.IO.Stream.WriteAsync%2A>、 <xref:System.IO.Stream.CopyToAsync%2A>、 <xref:System.IO.Stream.FlushAsync%2A>、 <xref:System.IO.TextReader.ReadLineAsync%2A>和 <xref:System.IO.TextReader.ReadToEndAsync%2A>。 這些非同步方法會在 Stream 類別上實作 (例如 <xref:System.IO.Stream>、 <xref:System.IO.FileStream>和 <xref:System.IO.MemoryStream>)，以及在用於從資料流讀取或寫入資料流的類別上實作 (例如 <xref:System.IO.TextReader> 和 <xref:System.IO.TextWriter>)。

在 .NET Framework 4 和更早版本中，您必須使用和等 <xref:System.IO.Stream.BeginRead%2A> 方法 <xref:System.IO.Stream.EndRead%2A> 來執行非同步 i/o 作業。 這些方法仍可在目前的 .NET 版本中使用，以支援舊版程式碼;不過，非同步方法可協助您更輕鬆地執行非同步 i/o 作業。

C# 和 Visual Basic 各有兩個進行非同步程式設計的關鍵字：

- `Async` (Visual Basic) 或 `async` (C#) 修飾詞，用來標記包含非同步作業的方法。

- `Await` (Visual Basic) 或 `await` (C#) 運算子，會套用至非同步方法的結果。

若要實作非同步 I/O 作業，請搭配非同步方法使用這些關鍵字，如下列範例所示。 如需詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計 (C#)](../../csharp/programming-guide/concepts/async/index.md) 或[使用 Async 和 Await 進行非同步程式設計 (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)。

下列範例示範如何使用兩個 <xref:System.IO.FileStream> 物件，以非同步方式將檔案從一個目錄複製到另一個目錄。 請注意， <xref:System.Web.UI.WebControls.Button.Click> 控制項的 <xref:System.Windows.Controls.Button> 事件處理常式由於會呼叫非同步方法，因此會以 `async` 修飾詞標記。

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

下一個範例與前一個範例類似，但使用 <xref:System.IO.StreamReader> 和 <xref:System.IO.StreamWriter> 物件以非同步方式讀取及寫入文字檔的內容。

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

下一個範例會顯示程式碼後端檔案和 XAML 檔案，該檔案是用來 <xref:System.IO.Stream> 在 Windows 8. x 存放區應用程式中開啟檔案，並使用類別的實例來讀取其內容 <xref:System.IO.StreamReader> 。 它會使用非同步方法開啟檔案作為資料流並讀取其內容。

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a>請參閱

- <xref:System.IO.Stream>
- [檔案和資料流 I/O](index.md)
- [使用 async 和 await 進行非同步程式設計 (c # ) ](../../csharp/programming-guide/concepts/async/index.md)
- [使用 Async 和 Await 進行非同步程式設計 (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)
