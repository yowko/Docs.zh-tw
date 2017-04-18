---
title: "如何：從字串中讀取字元 | Microsoft Docs"
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
  - "從字串讀取字元"
  - "資料流，從字串讀取字元"
  - "I/O [.NET Framework]，從字串讀取字元"
  - "讀取資料，字串"
  - "資料流，從字串讀取字元"
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：從字串中讀取字元
下列程式碼範例將示範如何同步和非同步從字串讀取字元。  
  
## 範例  
 這個範例會從字串陣列中同步讀取 13 個字元，並顯示這些字元。  在開始第六個元素的陣列讀取字串中的剩餘字元，然後顯示陣列的內容。  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## 範例  
 下一個範例會從 <xref:System.Windows.Controls.TextBox> 控制項非同步讀取所有字元，並將它們存在陣列中。  它會以非同步方式在分行符號後面跟著另一行並將每一個字母或空白字元 <xref:System.Windows.Controls.TextBlock> 給控制項。  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## 請參閱  
 <xref:System.IO.StringReader>   
 <xref:System.IO.StringReader.Read%2A?displayProperty=fullName>   
 [非同步檔案 I\/O](../../../docs/standard/io/非同步檔案-i-o.md)   
 [NIB: How to: Create a Directory Listing](http://msdn.microsoft.com/zh-tw/4d2772b1-b991-4532-a8a6-6ef733277e69)   
 [如何：讀取和寫入新建立的資料檔案](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)   
 [如何：開啟並附加至記錄檔](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)   
 [如何：從檔案讀取文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)   
 [如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)   
 [如何：將字元寫入至字串](../../../docs/standard/io/how-to-write-characters-to-a-string.md)   
 [檔案和資料流 I\/O](../../../docs/standard/io/index.md)