---
title: "如何：尋找隔離儲存區中的現有檔案和目錄 | Microsoft Docs"
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
  - "存放區，尋找檔案和目錄"
  - "在隔離儲存區檔案中尋找檔案"
  - "目錄 [.NET Framework]，隔離儲存區"
  - "隔離儲存區，尋找檔案和目錄"
  - "使用隔離儲存區儲存資料，尋找檔案和目錄"
  - "檔案 [.NET Framework]，隔離儲存區"
  - "資料存放區，尋找檔案和目錄"
  - "在隔離儲存區檔案中尋找目錄"
  - "使用隔離儲存區儲存資料，尋找檔案和目錄"
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：尋找隔離儲存區中的現有檔案和目錄
若要搜尋在隔離儲存區 \(Isolated Storage\) 的目錄，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=fullName> 方法。  這個方法會使用表示搜尋模式的字串。  您可以在搜尋模式可以使用單一字元 \(?\) 和多重字元 \(\*\) 萬用字元，不過，萬用字元必須出現在名稱的最後一部分。  例如， `directory1/*ect*` 是有效的搜尋字串，不過， `*ect*/directory2` 不是。  
  
 如果要搜尋檔案，請使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=fullName> 方法。  也會套用至 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> 萬用字元的限制搜尋字串適用於 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>。  
  
 這些方法不是遞迴的， <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 類別不在您存放區提供清單中所有目錄或檔案的任何方法。  不過，下列程式碼範例演示遞迴方法。  
  
## 範例  
 下列程式碼範例說明如何在隔離存放區中建立檔案和目錄。  首先，擷取使用者、定義域和組件所隔離的存放區，並放入 `isoStore` 變數中。  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%28System.String%29> 方法是用來設定一些不同的目錄，而?qualifyHint=False&autoUpgrade=TrueIsolatedStorageFileStream<xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29>方法則會在這些目錄中建立一些檔案。  程式碼接著對 `GetAllDirectories` 方法的結果執行迴圈。  這個方法使用 [GetDirectoryNames M:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames\(System.String\)](assetId:///GetDirectoryNames M:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames(System.String)?qualifyHint=False&autoUpgrade=True)來尋找目前目錄中的所有目錄名稱。  這些名稱儲存在陣列中，而 `GetAllDirectories` 接著呼叫它本身，並傳入它所找到的每一個目錄。  結果是陣列中傳回的所有目錄名稱。  接下來，程式碼會呼叫 `GetAllFiles` 方法。  此方法會呼叫 `GetAllDirectories` 找出所有目錄的名稱，接著使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%28System.String%29> 方法，為檔案檢查每個目錄。  結果在陣列中傳回以供顯示。  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## 請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)