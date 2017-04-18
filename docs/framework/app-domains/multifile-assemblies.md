---
title: "多檔案組件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "組件 [.NET Framework], 多檔案"
  - "組件資訊清單, 多檔案組件"
  - "程式碼模組"
  - "命令列編譯器"
  - "編譯組件"
  - "組件的進入點"
  - "多檔案組件"
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 多檔案組件
您可以使用命令列編譯器或 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 搭配 Visual C\+\+ 建立多檔案組件。  組件的檔案必須包含組件資訊清單。  啟動應用程式的組件必須同時含有進入點，例如 Main 或 WinMain 方法。  
  
 例如，假設您的應用程式包含 Client.cs 和 Stringer.cs 這兩個模組。  Stringer.cs 會建立 `myStringer` 命名空間，而 Client.cs 中的程式碼會參考這個命名空間。  Client.cs 包含 `Main` 方法，這個方法是應用程式的進入點。  在這個範例中，您將編譯兩個程式碼模組，然後建立第三個可啟動應用程式的檔案，其中含有組件資訊清單。  組件資訊清單同時參考 `Client` 和 `Stringer` 模組。  
  
> [!NOTE]
>  即使組件擁有多重程式碼模組，多檔案組件仍可僅擁有一個進入點。  
  
 您可能想要建立多檔案組件，原因如下：  
  
-   您想要結合使用不同語言撰寫的模組。  這是建立多檔案組件最常見的理由。  
  
-   您想要將很少使用的型別放入只有在需要時才下載的模組中，以便最佳化應用程式的下載。  
  
    > [!NOTE]
    >  如果您要建立將使用 Internet Explorer 和 `<object>` 標記下載的應用程式，則您必須建立多檔案組件。  在這個案例中，您將建立一個有別於您的程式碼模組的檔案，該檔案中僅含有組件資訊清單。  Internet Explorer 會先下載組件資訊清單，然後建立背景工作執行緒 \(Worker Thread\) 來下載所有其他必要的模組或組件。  當含有組件資訊清單的檔案下載完成後，Internet Explorer 將不會回應使用者輸入。  如果含有組件資訊清單的檔案越小，Internet Explorer 不回應的時間就越短。  
  
-   您可以結合數個開發人員所撰寫的程式碼模組。  雖然每個開發人員都可以將每個程式碼模組編譯到一個組件裡，這個動作會使某些型別公開地公開出來，但如果模組分散放置到多個檔案組件中，這些型別就不會公開出來。  
  
 建立組件後，您可以簽署含有組件資訊清單的檔案 \(並藉此可簽署組件\)，或者您可以為檔案 \(和組件\) 指定強式名稱並將它放入全域組件快取。  
  
## 請參閱  
 [如何：建置多檔案組件](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)   
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)