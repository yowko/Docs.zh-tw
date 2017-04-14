---
title: "如何：取得離儲存區的存放區 | Microsoft Docs"
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
  - "存放區，取得"
  - "使用隔離儲存區儲存資料，取得存放區"
  - "隔離儲存區，取得存放區"
  - "資料存放區，取得"
  - "使用隔離儲存區儲存資料，取得存放區"
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
caps.latest.revision: 19
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：取得離儲存區的存放區
存放區公開資料區間內的虛擬檔案系統。  <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 類別提供互動的幾種方法可與隔離存放區溝通。  為了建立並擷取存放區，<xref:System.IO.IsolatedStorage.IsolatedStorageFile> 提供三個靜態方法。  
  
-   呼叫 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> 會傳回使用者和組件隔離的儲存區。  
  
-   呼叫 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> 會傳回定義域和組件隔離的儲存區。  
  
     兩個方法擷取屬於程式碼所呼叫的存放區。  
  
-   靜態方法 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 會傳回隔離存放區 \(這是透過傳回範圍參數組合所指定的\)。  
  
 下列程式碼範例擷取使用者、定義域和組件所隔離的存放區。  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法可以用來指定存放區應該與漫遊使用者設定檔一起漫遊。  如需如何完成此工作的詳細資訊，請參閱 [隔離的類型](../../../docs/standard/io/types-of-isolation.md)。  
  
 自不同組件內取得的隔離存放區在預設狀況中為不同的存放區。  您可以傳入不同組件或定義域辨識項當做 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法的最後兩個參數，來存取不同組件或定義域的存放區。  這需要使用權限，根據應用程式定義域識別來存取隔離儲存區。  如需詳細資訊，請參閱 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法多載。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>和 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法傳回 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件。  為了協助您決定哪一個隔離類型最適合您的情況，請參閱[隔離的類型](../../../docs/standard/io/types-of-isolation.md)。  一旦您擁有隔離儲存區檔案物件，您即可使用隔離儲存區方法去讀取、寫入、建立和刪除檔案和檔案目錄。  
  
 沒有機制可以防止程式碼傳遞 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 至本身沒有充分存取權取得存放區的程式碼。  只有取得 <xref:System.IO.IsolatedStorage.IsolatedStorage> 物件的參考時 \(通常在 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> 或 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法中\)，才會檢查定義域和組件識別與隔離儲存區使用權限。  因此，保護 <xref:System.IO.IsolatedStorage.IsolatedStorageFile> 物件的參考是使用這些參考的程式碼的責任。  
  
## 範例  
 下列程式碼範例是一個非常簡單的範例，示範取得使用者和組件所隔離存放區的類別。  藉著將 <xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=fullName> 加入至 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> 方法將要傳遞的引數，可以變更程式碼來擷取使用者、定義域和組件所隔離的存放區。  
  
 執行程式碼之後，您可以在命令列輸入 **StoreAdm \/LIST**，確認存放區已建立。  這樣會執行[隔離儲存區管理工具 \(Storeadm.exe\)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md)，並列出使用者的所有目前隔離存放區。  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## 請參閱  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>   
 [隔離儲存區](../../../docs/standard/io/isolated-storage.md)   
 [隔離的類型](../../../docs/standard/io/types-of-isolation.md)   
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)