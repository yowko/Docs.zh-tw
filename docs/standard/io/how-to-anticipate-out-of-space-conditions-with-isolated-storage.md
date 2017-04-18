---
title: "如何：預期隔離儲存區發生空間不足的情況 | Microsoft Docs"
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
  - "資料存放區，配額"
  - "隔離儲存區，配額"
  - "使用的隔離儲存區之數量"
  - "使用的隔離儲存區之限制"
  - "存放區，配額"
  - "存放區，空間不足的情況"
  - "使用隔離儲存區儲存資料，配額"
  - "使用隔離儲存區儲存資料，配額"
  - "隔離儲存區中剩餘的空間"
  - "資料存放區，空間不足的情況"
  - "使用隔離儲存區儲存資料，空間不足的情況"
  - "隔離儲存區的配額"
  - "隔離儲存區，空間不足的情況"
  - "使用隔離儲存區儲存資料，空間不足的情況"
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：預期隔離儲存區發生空間不足的情況
使用隔離儲存區的程式碼受限於指定隔離儲存區檔案和目錄所存在資料區間最大大小的[隔離儲存區的配額](../../../docs/standard/io/isolated-storage.md#quotas)。  這個值由安全性原則定義，並可由系統管理員設定。  如果嘗試寫入資料時超過最大容許大小，將會擲回 <xref:System.IO.IsolatedStorage.IsolatedStorageException>，且作業失敗。  這樣有助於防止惡意的拒絕服務攻擊，以免造成應用程式因為資料儲存區被填滿而拒絕要求。  
  
 為了幫助您判斷某個寫入嘗試是否可能會因此失敗，<xref:System.IO.IsolatedStorage.IsolatedStorage> 類別提供了三個唯讀屬性：<xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A> 和 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>。  這些屬性可以用來判斷對存放區的寫入是否超出存放區的最大容許大小。  當您使用這些屬性時，請記得隔離儲存區可並行存取；因此，如果要計算儲存區的剩餘數量，在您嘗試寫入存放區前，可能又會消耗掉一些儲存空間。  不過，您可以使用存放區的最大大小來協助判斷在可用的儲存區是否會到達上限。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> 屬性取決於來自組件的辨識項才能正確運作。  因此，您應該擷取這個屬性只使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>或 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法建立的 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件。  以任何其他方式建立的 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件 \(例如，從 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> 方法傳回的物件\) 將不會傳回正確的最大值。  
  
## 範例  
 下列程式碼範例會取得隔離的存放區、建立幾個檔案，並且擷取 <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> 屬性。  剩餘空間將以位元組為單位回報。  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## 請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)   
 [如何：取得離儲存區的存放區](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)