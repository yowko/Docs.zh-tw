---
title: "如何：讀取和寫入離儲存區中的檔案 | Microsoft Docs"
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
  - "使用隔離儲存區儲存資料, 讀取和寫入至檔案"
  - "資料存放區, 讀取和寫入至檔案"
  - "檔案, 隔離儲存區"
  - "隔離儲存區, 讀取和寫入至檔案"
  - "讀取資料"
  - "在存放區中讀取檔案"
  - "存放區, 讀取和寫入至檔案"
  - "使用隔離儲存區來儲存資料, 讀取和寫入至檔案"
  - "在存放區中寫入至檔案"
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：讀取和寫入離儲存區中的檔案
讀取或寫入在隔離存放區的檔案時，使用資料流讀取器 \(<xref:System.IO.StreamReader>物件\) 或資料流寫入器 \(<xref:System.IO.StreamWriter>物件\)的<xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>。  
  
## 範例  
 下列程式碼範例會取得隔離的存放區並檢查名為 TestStore.txt 的檔案是否出現在存放區中。  如果不存在，則會建立檔案和寫入「Hello 隔離儲存區 \(Isolated Storage\)」寫入檔案。  如果 TestStore.txt 已經存在，範例程式碼會從檔案中讀取。  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## 請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>   
 <xref:System.IO.FileMode?displayProperty=fullName>   
 <xref:System.IO.FileAccess?displayProperty=fullName>   
 <xref:System.IO.StreamReader?displayProperty=fullName>   
 <xref:System.IO.StreamWriter?displayProperty=fullName>   
 [檔案和資料流 I\/O](../../../docs/standard/io/index.md)   
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)