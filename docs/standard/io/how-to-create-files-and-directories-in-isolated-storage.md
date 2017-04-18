---
title: "如何：在隔離儲存區中建立檔案和目錄 | Microsoft Docs"
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
  - "目錄 [.NET Framework]，隔離儲存區"
  - "檔案 [.NET Framework]，隔離儲存區"
  - "隔離儲存區，建立檔案和目錄"
  - "資料存放區，建立檔案和目錄"
  - "使用隔離儲存區儲存資料，建立檔案和目錄"
  - "存放區，建立檔案和目錄"
  - "使用隔離儲存區儲存資料，建立檔案和目錄"
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：在隔離儲存區中建立檔案和目錄
在您取得存放區之後，您可以建立儲存資料的目錄和檔案。  存放區內，檔案和目錄名稱相對於虛擬檔案系統的根 \(Root\) 來指定。  
  
 如果要建立目錄，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=fullName> 執行個體方法。  如果您指定不存在的目錄的子目錄，兩個目錄皆會被建立。  如果您指定已經存在的目錄，則不需建立目錄，且不會擲回例外狀況。  但是，如果您指定的目錄名稱內含無效字元，則會擲回 <xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外狀況。  
  
 若要建立檔案，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=fullName> 方法。  
  
 在 Windows 作業系統中，隔離儲存區的檔案和目錄名稱不區分大小寫。  如此，如果您建立名為 `ThisFile.txt` 的檔案，並接著建立另一個名為 `THISFILE.TXT` 的檔案，只有一個檔案會被建立。  檔案名稱在顯示的場合保留它原來的大小寫。  
  
## 範例  
 下列程式碼範例說明如何在隔離存放區中建立檔案和目錄。  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## 請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>   
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)