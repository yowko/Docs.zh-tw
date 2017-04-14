---
title: "撰寫資料流 | Microsoft Docs"
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
  - "資料流，基底資料流"
  - "I/O [.NET Framework]，撰寫資料流"
  - "Stream 類別，撰寫資料流"
  - "基底資料流"
  - "資料流，支援存放區"
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# 撰寫資料流
支援存放區為儲存媒體，例如磁碟或記憶體。  各個不同的支援存放區都實作它自己的資料流做為 <xref:System.IO.Stream> 類別的實作。  各個資料流類型都對它的指定支援存放區讀取並寫入位元組。  連接至支援存放區的資料流稱為基底資料流。  基底資料流擁有建構函式，其具備連接資料流至支援存放區的必要參數。  例如，<xref:System.IO.FileStream> 具有指定路徑參數的建構函式，這參數可指定檔案將如何為處理序所共用，或諸如此類。  
  
 <xref:System.IO> 類別的設計提供簡化的資料流撰寫方式。  基底資料流可附加至一個或多個傳遞資料流，以提供想要的功能。  讀取器或寫入器可附加至鏈結的結尾，以便能夠輕易讀取或寫入想要的型別。  
  
 下列程式碼範例針對現有的 `MyFile.txt` 建立 **FileStream**，以便緩衝 `MyFile.txt`\(注意，預設的情況下，會緩衝 **FileStream**\)。接下來，會建立 <xref:System.IO.StreamReader> 以從 **FileStream** 讀取字元，後者會傳遞至 **StreamReader** 做為其建構函式引數。  <xref:System.IO.StreamReader.ReadLine%2A> 會讀取直到 <xref:System.IO.StreamReader.Peek%2A> 再也找不到字元為止。  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 下列程式碼範例針對現有的 `MyFile.txt` 建立 **FileStream**，以便緩衝 `MyFile.txt`\(注意，預設的情況下，會緩衝 **FileStream**\)。接下來，會建立 **BinaryReader** 以從 **FileStream** 讀取位元組，後者會傳遞至 **BinaryReader** 做為其建構函式引數。  <xref:System.IO.BinaryReader.ReadByte%2A> 會讀取直到 <xref:System.IO.BinaryReader.PeekChar%2A> 再也找不到位元組為止。  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## 請參閱  
 <xref:System.IO.StreamReader>   
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName>   
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=fullName>   
 <xref:System.IO.FileStream>   
 <xref:System.IO.BinaryReader>   
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=fullName>   
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=fullName>