---
title: "使用用戶端應用程式中的資料服務 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, 用戶端程式庫"
  - "WCF Data Services, 使用者入門"
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 使用用戶端應用程式中的資料服務 (WCF Data Services)
您可以將 URI 提供給 Web 瀏覽器，以存取可公開 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 摘要的服務。  URI 可提供資源的位址，而要求訊息會傳送至這些位址，以存取或變更資源所代表的基礎資料。  瀏覽器會發出 HTTP GET 命令，並且以 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的形式傳回要求的資源。  如需詳細資訊，請參閱[從 Web 瀏覽器存取服務](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)。  
  
 雖然 Web 瀏覽器可用來測試 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務是否會傳回預期的資料，但是同時讓您建立、更新及刪除資料的實際執行 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務通常會以應用程式程式碼或網頁中的指令碼語言來存取。  本主題提供如何從用戶端應用程式存取 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的概觀。  
  
## 使用 REST 語意存取與變更資料  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 有助於確保公開 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要之服務以及取用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要之應用程式之間的互通性。應用程式會在以 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 為基礎的服務中傳送特定 HTTP 動作的要求訊息，以及透過針對應該執行其動作處理實體資源的 URI，存取並變更資料。  當必須提供實體資料時，會在訊息本文中以特定編碼的裝載形式提供。  
  
### HTTP 動作  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 可支援下列 HTTP 動作，在定址資源代表的實體資料上，執行建立、讀取、更新，以及刪除作業：  
  
-   **HTTP GET**：這是從瀏覽器存取資源時的預設動作。  要求訊息中不會提供任何承載，同時會以包含所要求之資料的承載傳回回應方法。  
  
-   **HTTP POST**：在提供的資源中插入新的實體資料。  要插入的資料會於要求訊息的承載中提供。  回應訊息的裝載包含新建立之實體的資料。  其中包括任何自動產生的索引鍵值。  標頭亦包含定址新實體資源的 URI。  
  
-   **HTTP DELETE**：刪除指定資源所代表的實體資料。  要求或回應訊息中不會出現任何承載。  
  
-   **HTTP PUT**：使用要求訊息之裝載中提供的新資料來取代要求之資源中的現有實體資料。  
  
-   **HTTP MERGE** \- 由於只為了變更實體資料而執行刪除再插入資料來源的方式非常缺乏效率，因此 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 引進了新的 HTTP MERGE 動作。  要求訊息的承載包含在定址實體資源中必須變更的屬性。  由於 HTTP 規格中未定義 HTTP MERGE，因此可能需要進行額外處理，才能透過非 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 感知的伺服器來路由傳送 HTTP MERGE 要求。  
  
 如需詳細資訊，請參閱 [OData：作業](http://go.microsoft.com/fwlink/?LinkId=185792)。  
  
### 承載格式  
 若為 HTTP PUT、HTTP POST 或 HTTP MERGE 要求，要求訊息的裝載會包含您傳送至資料服務的實體資料。  承載的內容取決於訊息的資料格式。  所有動作 \(DELETE 除外\) 的 HTTP 回應也包含此類承載。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 支援以下列裝載格式，透過此服務來存取及變更資料：  
  
-   **Atom**：[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 定義為 Atom 發行通訊協定 \(AtomPub\) 之延伸的 XML 型訊息編碼，可透過 HTTP 交換資料以提供 Web 摘要、Podcast、Wiki 及 XML 型網際網路功能。  如需詳細資訊，請參閱 [OData：Atom 格式](http://go.microsoft.com/fwlink/?LinkId=185794)。  
  
-   **JSON**：JavaScript 物件標記法 \(JSON\) 是精簡型的資料交換格式，並以 JavaScript 程式語言子集為基礎。  如需詳細資訊，請參閱 [OData：JSON 格式](http://go.microsoft.com/fwlink/?LinkID=185795)。  
  
 HTTP 要求訊息的標頭中會要求裝載的訊息格式。  如需詳細資訊，請參閱 [OData：作業](http://go.microsoft.com/fwlink/?LinkID=185792)。  
  
## 使用用戶端程式庫存取及變更資料  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 包含用戶端程式庫，能讓您更輕鬆地從以 .NET Framework 和 Silverlight 為基礎的用戶端應用程式取用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。  這些程式庫會簡化 HTTP 訊息的傳送與接收。  他們也會將訊息承載轉譯為代表實體資料的 CLR 物件。  用戶端程式庫具有兩個核心類別：<xref:System.Data.Services.Client.DataServiceContext> 和 <xref:System.Data.Services.Client.DataServiceQuery%601>。  這些類別可讓您查詢資料服務，然後使用傳回的實體資料當做 CLR 物件。  如需詳細資訊，請參閱[WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)與[WCF Data Services \(Silverlight\)](http://msdn.microsoft.com/zh-tw/c0cd9f4b-1372-48e4-9935-c8421239da30)。  
  
 您可以使用 Visual Studio 中的 \[**加入服務參考**\] 對話方塊，將參考加入至資料服務。  此工具會從參考的資料服務要求服務中繼資料，並產生代表資料服務的 <xref:System.Data.Services.Client.DataServiceContext>，同時也會產生代表實體的用戶端資料服務類別。  如需詳細資訊，請參閱[產生資料服務用戶端程式庫](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)。  
  
 有一些程式庫可讓您在其他種類的用戶端應用程式中取用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。  如需詳細資訊，請參閱 [OData SDK](http://go.microsoft.com/fwlink/?LinkId=185796)。  
  
## 請參閱  
 [存取資料服務資源](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)   
 [快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)