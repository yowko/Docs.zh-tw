---
title: "如何：將字元寫入至字串 | Microsoft Docs"
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
  - "資料流，將字元寫入字串"
  - "將字元寫入字串"
  - "資料流，將字元寫入字串"
  - "I/O [.NET Framework]，將字元寫入字串"
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：將字元寫入至字串
下列程式碼範例會從字元陣列寫入字元同步和非同步輸入字串。  
  
## 範例  
 下列範例會從陣列同步寫入 5 字元資料。  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## 範例  
 下一個範例會從 <xref:System.Windows.Controls.TextBox> 控制項非同步讀取所有字元，並將它們存在陣列中。  它會以非同步方式在分行符號後面跟著另一行並將每一個字母或空白字元 <xref:System.Windows.Controls.TextBlock> 給控制項。  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## 請參閱  
 <xref:System.IO.StringWriter>   
 <xref:System.IO.StringWriter.Write%2A?displayProperty=fullName>   
 <xref:System.Text.StringBuilder>   
 [檔案和資料流 I\/O](../../../docs/standard/io/index.md)   
 [非同步檔案 I\/O](../../../docs/standard/io/非同步檔案-i-o.md)   
 [如何：列舉目錄和檔案](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)   
 [如何：讀取和寫入新建立的資料檔案](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)   
 [如何：開啟並附加至記錄檔](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)   
 [如何：從檔案讀取文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)   
 [如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)   
 [如何：從字串中讀取字元](../../../docs/standard/io/how-to-read-characters-from-a-string.md)