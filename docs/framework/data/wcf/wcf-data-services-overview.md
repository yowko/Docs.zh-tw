---
title: "WCF Data Services 概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "HTML"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "WCF Data Services"
  - "WCF Data Services, 關於"
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# WCF Data Services 概觀
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可讓您使用 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 來建立及取用 Web 或內部網路的資料服務。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 可讓您將資料公開為可由 URI 定址的資源。  這可讓您使用具像狀態傳輸 \(REST\) 的語意來存取和變更資料，明確的說，就是 GET、PUT、POST 和 DELETE 的標準 HTTP 動詞命令。本主題提供 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 所定義的模式和實務概觀，以及 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 所提供的功能，以使用 .NET Framework 架構應用程式中的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]。  
  
## 將資料定址為資源  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 會將資料公開為可由 URI 定址的資源。資源路徑會根據實體資料模型的實體\-關聯性慣例來建構。  在此模型中，實體代表應用程式定義域中的資料運算單位，例如客戶、訂單、項目及產品。  如需詳細資訊，請參閱[實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)。  
  
 在 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 中，您將實體資源定址為包含實體型別執行個體的實體集。  例如，`http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` URI 會傳回取自 `Northwind` 資料服務的所有訂單，它們是與 `CustomerID` 值為 `ALFKI.` 的客戶相關之訂單。  
  
 查詢運算式可讓您針對資源執行傳統查詢運算，例如篩選、排序和分頁。  例如，URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` 會篩選資源，只傳回運費超過 $50 美元的訂單。  如需詳細資訊，請參閱[存取資料服務資源](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)。  
  
## 可互通的資料存取  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 會根據標準網際網路通訊協定來建置，使資料服務能夠與不使用 .NET Framework 的應用程式互通。  由於您可以使用標準 URI 來定址資料，因此應用程式可以使用具像狀態傳輸 \(REST\) 的語意存取及變更資料，尤其是標準 HTTP 動詞命令，例如 GET、PUT、POST 和 DELETE。  這樣能讓您從任何用戶端存取這些服務 \(這些用戶端需可剖析及存取透過標準 HTTP 通訊協定傳輸的資料\)。  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 會定義 Atom 發行通訊協定 \(AtomPub\) 的一組延伸。它可支援採用多種資料格式的 HTTP 要求和回應，配合各種用戶端應用程式和平台。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要可以表示 Atom、JavaScript 物件標記法 \(JSON\) 和單純 XML 格式的資料。  雖然 Atom 是預設格式，但是摘要的格式會在 HTTP 要求的標頭中指定。  如需詳細資訊，請參閱 [OData：Atom 格式](http://go.microsoft.com/fwlink/?LinkID=185794)和 [OData：JSON 格式](http://go.microsoft.com/fwlink/?LinkID=185795)。  
  
 將資料發行為 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要時，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會依賴其他現有的網際網路機能進行此類作業 \(例如快取和驗證\)。  為了完成這項作業，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會與現有的裝載應用程式和服務整合，例如 ASP.NET、Windows Communication Foundation \(WCF\) 和 Internet Information Services \(IIS\)。  
  
## 儲存獨立性  
 雖然資源是根據實體\-關聯性模型定址，但是 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會公開 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要，而不管基礎資料來源為何。在 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 接受 URI 識別之資源的 HTTP 要求後，會還原序列化此要求，並將該要求的表示方式傳遞至 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 提供者。  此提供者會將要求轉譯為特定資料來源格式，並且在基礎資料來源執行該要求。[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會將定址資源的概念模型 \([!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 所規定\) 與基礎資料來源的特定結構描述區隔開來，以達到儲存獨立性。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 整合 ADO.NET Entity Framework，可讓您建立公開關聯式資料的資料服務。  您可以使用實體資料模型工具建立以實體形式包含可定址資源的資料模型，同時定義此模型和基礎資料庫中資料表的對應。  如需詳細資訊，請參閱[Entity Framework 提供者](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 也可讓您建立資料服務，以公開會傳回 <xref:System.Linq.IQueryable%601> 介面實作的任何資料結構。  這可讓您建立公開 .NET Framework 型別資料的資料服務。  若您同時實作 <xref:System.Data.Services.IUpdatable> 介面，則亦支援建立、更新及刪除作業。  如需詳細資訊，請參閱[反映提供者](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)。  
  
 如需 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 如何與這些資料提供者整合的說明，請參閱本主題稍後的架構圖。  
  
## 自訂商務邏輯  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可讓您透過服務作業和攔截器，輕鬆地將自訂商務邏輯加入資料服務中。  服務作業是在伺服器上定義的方法，而 URI 可透過與資料資源相同的格式來定址這些方法。  服務作業也可以使用查詢運算式語法來篩選、排序和分頁作業所傳回的資料。例如，URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` 表示在 Northwind 資料服務上呼叫名稱為 `GetOrdersByCity` 的服務作業，而且這個資料服務會針對 London 的客戶，傳回 `OrderDate` 所排序之分頁結果的順序。  如需詳細資訊，請參閱[服務作業](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)。  
  
 攔截器可讓您依照資料服務將自訂應用程式邏輯整合至要求或回應訊息的處理。  在指定的實體集上進行查詢、插入、更新或刪除動作時，系統就會呼叫攔截器。  然後，攔截器可能會更改資料、強制執行授權原則，甚至結束作業。  您必須針對資料服務所公開的特定實體集，明確地註冊攔截器方法。  如需詳細資訊，請參閱[攔截器](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)。  
  
## 用戶端程式庫  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 定義一組用於與資料服務互動的統一模式。  此模式能讓您根據這些服務建立可重複使用的元件，例如可簡化資料服務取用程序的用戶端程式庫。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 所包含的用戶端程式庫，適用於以 .NET Framework 和 Silverlight 為基礎的用戶端應用程式。  這些用戶端程式庫可讓您利用 .NET Framework 物件與資料服務互動。  它們也支援以物件為基礎的查詢和 LINQ 查詢、載入相關物件、變更追蹤以及識別解析。如需詳細資訊，請參閱[WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)。  
  
 除了 .NET Framework 和 Silverlight 所隨附的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 用戶端程式庫以外，也有其他用戶端程式庫可讓您在用戶端應用程式中取用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要，例如 PHP、AJAX 和 Java 應用程式。  如需詳細資訊，請參閱 [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796)。  
  
## 架構概觀  
 下圖說明用來公開 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 架構以及如何在具有 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 功能的用戶端程式庫中使用這些摘要：  
  
 ![WCF 資料服務架構圖表](../../../../docs/framework/data/wcf/media/astoriaservicearch.gif "AstoriaServiceArch")  
  
## 請參閱  
 [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)   
 [使用者入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)   
 [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [Accessing a Data Service \(WCF Data Services\)](http://msdn.microsoft.com/zh-tw/1e54a2b9-2ec6-4002-b8f8-c1d8df37c350)   
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [具像狀態傳輸 \(REST\)](http://go.microsoft.com/fwlink/?LinkId=113919)