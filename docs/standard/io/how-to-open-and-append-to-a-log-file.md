---
title: "如何：開啟並附加至記錄檔 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "記錄檔，開啟"
  - "資料流，開啟及附加至記錄檔"
  - "記錄檔，附加至"
  - "I/O [.NET Framework]，記錄檔"
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：開啟並附加至記錄檔
<xref:System.IO.StreamWriter> 和 <xref:System.IO.StreamReader> 會撰寫字元至資料流，以及讀取資料流中的字元。  下列程式碼範例開啟輸入的 `log.txt` 檔案，或建立檔案 \(如果它不存在\)，並附加資訊至檔案結尾。  接著寫入檔案內容至標準輸出以供顯示。  這個範例有一個替代方法：可以將這項資訊儲存為單一字串或字串陣列，而且 <xref:System.IO.File.WriteAllText%2A> 或 <xref:System.IO.File.WriteAllLines%2A> 方法可用來達成相同的功能。  
  
> [!NOTE]
>  Visual Basic 使用者可選擇使用 <xref:Microsoft.VisualBasic.Logging.Log> 類別或 <xref:Microsoft.VisualBasic.FileIO.FileSystem> 類別所提供的方法和屬性來建立記錄檔，或寫入到記錄檔。  
  
## 範例  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## 請參閱  
 <xref:System.IO.StreamWriter>   
 <xref:System.IO.StreamReader>   
 <xref:System.IO.File.AppendText%2A?displayProperty=fullName>   
 <xref:System.IO.File.OpenText%2A?displayProperty=fullName>   
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName>   
 [如何：列舉目錄和檔案](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)   
 [如何：讀取和寫入新建立的資料檔案](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)   
 [如何：從檔案讀取文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)   
 [如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)   
 [如何：從字串中讀取字元](../../../docs/standard/io/how-to-read-characters-from-a-string.md)   
 [如何：將字元寫入至字串](../../../docs/standard/io/how-to-write-characters-to-a-string.md)   
 [檔案和資料流 I\/O](../../../docs/standard/io/index.md)