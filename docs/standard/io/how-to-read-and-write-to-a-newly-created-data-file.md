---
title: "如何：讀取和寫入新建立的資料檔案 | Microsoft Docs"
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
  - "BinaryReader 類別, 範例"
  - "BinaryWriter 類別, 範例"
  - "I/O [.NET Framework], 讀取資料"
  - "I/O [.NET Framework], 寫入資料"
  - "資料流, 讀寫資料"
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：讀取和寫入新建立的資料檔案
<xref:System.IO.BinaryWriter> 和 <xref:System.IO.BinaryReader?displayProperty=fullName> 類別是用來寫入和讀取資料，而非字元字串。  下列範例示範如何將資料寫入和讀取新的空白檔案資料流 `Test.data`。  在目前目錄中建立資料檔案之後，會建立相關的 <xref:System.IO.BinaryWriter> 和 <xref:System.IO.BinaryReader>，並使用 <xref:System.IO.BinaryWriter> 將 0 至 10 的整數寫入到 `Test.data`，使檔案指標停留在檔案結尾。  將檔案指標設定回起點後，<xref:System.IO.BinaryReader> 會讀出指定的內容。  
  
## 範例  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## 穩固程式設計  
 如果 `Test.data` 已存在於目前目錄中，則會擲回 <xref:System.IO.IOException> 例外狀況。  當您初始化檔案資料流以永遠建立新的檔案時，請使用檔案模式選項 <xref:System.IO.FileMode?displayProperty=fullName> ，以避免擲回例外狀況。  
  
## 請參閱  
 <xref:System.IO.BinaryReader>   
 <xref:System.IO.BinaryWriter>   
 <xref:System.IO.FileStream>   
 <xref:System.IO.FileStream.Seek%2A?displayProperty=fullName>   
 <xref:System.IO.SeekOrigin>   
 [如何：列舉目錄和檔案](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)   
 [如何：開啟並附加至記錄檔](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)   
 [如何：從檔案讀取文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)   
 [如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)   
 [如何：從字串中讀取字元](../../../docs/standard/io/how-to-read-characters-from-a-string.md)   
 [如何：將字元寫入至字串](../../../docs/standard/io/how-to-write-characters-to-a-string.md)   
 [檔案和資料流 I\/O](../../../docs/standard/io/index.md)