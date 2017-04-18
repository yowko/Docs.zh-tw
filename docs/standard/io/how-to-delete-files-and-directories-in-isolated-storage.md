---
title: "如何：刪除隔離儲存區中的檔案和目錄 | Microsoft Docs"
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
  - "使用隔離儲存區儲存資料，刪除檔案和目錄"
  - "目錄 [.NET Framework]，隔離儲存區"
  - "檔案 [.NET Framework]，隔離儲存區"
  - "隔離儲存區，刪除檔案和目錄"
  - "資料存放區，刪除檔案和目錄"
  - "存放區，建立檔案和目錄"
  - "刪除隔離階移檔案中的檔案"
  - "使用隔離儲存區儲存資料，刪除檔案和目錄"
  - "刪除隔離階移檔案中的目錄"
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：刪除隔離儲存區中的檔案和目錄
您可以刪除隔離儲存區檔案內的目錄和檔案。  存放區內，檔案和目錄名稱與作業系統相關且由虛擬檔案系統的根 \(Root\)關聯。  不區分大小寫的 Windows 作業系統。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 類別提供兩個執行個體方法以刪除目錄及檔案：?qualifyHint=True&autoUpgrade=True <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> 和?qualifyHint=False&autoUpgrade=True <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>。  如果您嘗試刪除不存在的檔案或目錄，就會擲回 <xref:System.IO.IsolatedStorage.IsolatedStorageException>。  如果您在名稱必須包含萬用字元， <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> 擲回 <xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外狀況和 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> <xref:System.ArgumentException> 擲回例外狀況。  
  
 如果目錄包含任何檔案或子目錄，<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> 方法就會失敗。  您可以使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> 和 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> 方法擷取現有檔案和目錄。  如需搜尋存放區的虛擬檔案系統的詳細資訊，請參閱 [如何：尋找隔離儲存區中的現有檔案和目錄](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)。  
  
## 範例  
 下列程式碼範例建立並接著刪除數個目錄和檔案。  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## 請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=fullName>   
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)