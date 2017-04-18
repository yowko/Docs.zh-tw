---
title: "如何：列舉隔離儲存區的存放區 | Microsoft Docs"
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
  - "列舉存放區"
  - "使用隔離儲存區的資料儲存區，列舉存放區"
  - "使用隔離儲存區儲存資料，列舉存放區"
  - "存放區，列舉"
  - "隔離儲存區，列舉存放區"
  - "資料存放區，列舉"
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：列舉隔離儲存區的存放區
您可以使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=fullName> 靜態方法 ，列舉目前使用者所有的隔離存放區。  這個方法會使用 <xref:System.IO.IsolatedStorage.IsolatedStorageScope> 值並傳回 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 列舉值。  如果要列舉存放區，您必須具有將 <xref:System.Security.Permissions.IsolatedStorageContainment> 值指定為 AdministerIsolatedStorageByUser 的 <xref:System.Security.Permissions.IsolatedStorageFilePermission>。  如果您只使用 <xref:System.IO.IsolatedStorage.IsolatedStorageScope> 值的 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> 方法，它會傳回陣列為目前使用者定義的 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件。  
  
## 範例  
 您可以使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> 方法，下列程式碼範例會取得使用者和組件所隔離的存放區，建立一些檔案，並擷取這些檔案。  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## 請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)