---
title: "從 Web 瀏覽器存取服務 (WCF Data Services 快速入門) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 從 Web 瀏覽器存取服務 (WCF Data Services 快速入門)
在這個工作中，您將從 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 啟動 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]，並且選擇性停用 Web 瀏覽器中的摘要讀取功能。  接著，您將透過 Web 瀏覽器，將 HTTP GET 要求提交至已公開的資源，以擷取服務定義文件及存取服務資源。  
  
> [!NOTE]
>  根據預設，[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 會在您的電腦上自動指派通訊埠編號給 `localhost` URI。  這項工作會在 URI 範例中使用連接埠號碼 `12345`。  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 如何在 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 專案中設定特定連接埠號碼的詳細資訊，請參閱[建立資料服務](../../../../docs/framework/data/wcf/creating-the-data-service.md)。  
  
### 若要使用 Internet Explorer 要求預設服務文件  
  
1.  在 Internet Explorer 中，選取 \[**工具**\] 功能表的 \[**網際網路選項**\]、按一下 \[**內容**\] 索引標籤、按一下 \[**設定**\]，然後清除 \[**啟動摘要讀取檢視**\]。  
  
     這樣可以確保摘要讀取功能已停用。  如果未停用此功能，Web 瀏覽器會將傳回的 AtomPub 編碼文件視為 XML 摘要，而不會顯示原始的 XML 資料。  
  
    > [!NOTE]
    >  如果您的瀏覽器無法將摘要顯示為原始的 XML 資料，您應該仍然可以將摘要檢視為頁面的原始程式碼。  
  
2.  在 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 中，按 F5 鍵開始偵錯應用程式。  
  
3.  開啟本機電腦上的 Web 瀏覽器。  在位址列中輸入下列 URI：  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     這樣會傳回預設的服務文件，其中包含此資料服務所公開的實體集清單。  
  
### 從 Web 瀏覽器存取實體集資源  
  
1.  在 Web 瀏覽器的位址列中輸入下列 URI：  
  
    ```  
    http://localhost:12345/northwind.svc/Customers  
    ```  
  
     這樣會傳回 Northwind 範例資料庫中的所有客戶。  
  
2.  在 Web 瀏覽器的位址列中輸入下列 URI：  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')  
    ```  
  
     這樣會傳回特定客戶 `ALFKI` 的實體執行個體。  
  
3.  在 Web 瀏覽器的位址列中輸入下列 URI：  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders  
    ```  
  
     這樣會周遊客戶與訂單之間的關聯性，傳回特定客戶 `ALFKI` 的所有訂單。  
  
4.  在 Web 瀏覽器的位址列中輸入下列 URI：  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643  
    ```  
  
     這樣會篩選屬於特定客戶 `ALFKI` 的訂單，因此僅根據所提供的 `OrderID` 值傳回特定訂單。  
  
## 後續步驟  
 您已順利從 Web 瀏覽器存取 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]，且瀏覽器會將 HTTP GET 要求發出至指定的資源。  Web 瀏覽器可讓您輕鬆地實驗要求的定址語法並檢視結果。  不過，此方法通常並不適用於存取實際執行資料服務。  應用程式通常會透過應用程式碼或指令碼語言，與資料服務互動。接下來，您將建立一個用戶端應用程式，此應用程式會使用用戶端程式庫存取資料服務資源，如同它們是 Common Language Runtime \(CLR\) 物件：  
  
 [建立 .NET Framework 用戶端應用程式](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## 請參閱  
 [存取資料服務資源](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)