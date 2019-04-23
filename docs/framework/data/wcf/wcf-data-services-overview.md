---
title: WCF 資料服務概觀
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: ca52b725f5fad4b591b95bf6a6dd778c7a72d235
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202035"
---
# <a name="wcf-data-services-overview"></a>WCF 資料服務概觀
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可讓您建立和使用的 Web 或內部的資料服務使用[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 可讓您將資料公開為可由 Uri 定址的資源。 這可讓您使用具像狀態傳輸 (REST) 的語意存取及變更資料，尤其是標準 HTTP 動作，例如 GET、PUT、POST 和 DELETE。 本主題提供 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 所定義的模式和作法概觀以及 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 所提供的功能，以便在 .NET Framework 應用程式中充分利用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]。  
  
## <a name="address-data-as-resources"></a>將資料定址為資源  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 會將資料公開為可由 URI 定址的資源。 資源路徑會根據實體資料模型的實體-關聯性慣例來建構。 在此模型中，實體會代表應用程式定義域中，例如客戶、 訂單、 項目，以及產品的資料運算單位。 如需詳細資訊，請參閱 < [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)。  
  
 在 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 中，您將實體資源定址為包含實體型別執行個體的實體集。 例如，URI`http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders`會傳回所有的訂單`Northwind`的客戶相關的資料服務`CustomerID`值 `ALFKI.`  
  
 查詢運算式可讓您針對資源執行傳統查詢運算，例如篩選、排序和分頁。 例如，URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` 會篩選資源，只傳回運費超過 $50 美元的訂單。 如需詳細資訊，請參閱 <<c0> [ 存取資料服務資源](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)。  
  
## <a name="interoperable-data-access"></a>可互通的資料存取  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 若要讓資料服務的互通性與不使用.NET Framework 的應用程式的標準網際網路通訊協定為基礎。 因為您可以使用標準 Uri 來定址資料，您的應用程式可以存取和變更資料，使用具像狀態傳輸 (REST)，特別是標準 HTTP 動詞命令的語意 GET、 PUT、 POST 和 DELETE。 這樣能讓您從任何用戶端存取這些服務 (這些用戶端需可剖析及存取透過標準 HTTP 通訊協定傳輸的資料)。  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 會定義 Atom 發行通訊協定 (AtomPub) 的一組延伸。 它可支援採用多種資料格式的 HTTP 要求和回應，配合各種用戶端應用程式和平台。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要可以表示 Atom、JavaScript 物件標記法 (JSON) 和單純 XML 格式的資料。 雖然 Atom 是預設格式，但是摘要的格式會在 HTTP 要求的標頭中指定。 如需詳細資訊，請參閱[OData:Atom 格式](https://go.microsoft.com/fwlink/?LinkID=185794)和[OData:JSON 格式](https://go.microsoft.com/fwlink/?LinkID=185795)。  
  
 發行資料時[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]依賴其他現有的網際網路機能進行此類作業，例如快取和驗證。 若要這麼做，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]與現有的裝載應用程式和服務，例如 ASP.NET、 Windows Communication Foundation (WCF) 和 Internet Information Services (IIS) 整合。  
  
## <a name="storage-independence"></a>儲存獨立性  
 雖然會根據實體-關聯性模型定址資源，但無論基礎資料來源為何，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 都會公開 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 接受 URI 識別之資源所傳來的 HTTP 要求後，會將該要求還原序列化，並將該要求的表示法傳遞至 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 提供者。 此提供者會將要求轉譯為特定資料來源格式，並且在基礎資料來源執行該要求。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會將定址資源的概念模型 ([!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 所規定) 與基礎資料來源的特定結構描述區隔開來，以達到儲存獨立性。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 整合 ADO.NET Entity Framework，可讓您建立公開關聯式資料的資料服務。 您可以使用實體資料模型工具建立以實體形式包含可定址資源的資料模型，同時定義此模型和基礎資料庫中資料表的對應。 如需詳細資訊，請參閱 < [Entity Framework 提供者](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 也可讓您建立資料服務公開 （expose） 的實作會傳回任何資料結構<xref:System.Linq.IQueryable%601>介面。 這可讓您建立公開 .NET Framework 型別資料的資料服務。 若您同時實作 <xref:System.Data.Services.IUpdatable> 介面，則亦支援建立、更新及刪除作業。 如需詳細資訊，請參閱 <<c0> [ 反映提供者](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)。  
  
 如需如何以圖例[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]整合這些資料提供者，請參閱本主題稍後的架構圖。  
  
## <a name="custom-business-logic"></a>自訂商務邏輯  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可讓您輕鬆地將自訂商務邏輯加入至資料服務透過服務作義和攔截器。 服務作業是在伺服器上定義的方法，而 URI 可透過與資料資源相同的格式來定址這些方法。 服務作業也使用查詢運算式語法來篩選、排序及分頁作業所傳回的資料。 例如，URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` 代表呼叫 Northwind 資料服務中名為 `GetOrdersByCity` 的服務作業，該服務會傳回來自 London 客戶的訂單，同時傳回按 `OrderDate` 排序的分頁結果。 如需詳細資訊，請參閱 <<c0> [ 服務作業](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)。  
  
 攔截器可讓您依照資料服務將自訂應用程式邏輯整合至要求或回應訊息的處理。 在指定的實體集上進行查詢、插入、更新或刪除動作時，系統就會呼叫攔截器。 然後，攔截器可能會更改資料、強制執行授權原則，甚至結束作業。 您必須針對資料服務所公開的特定實體集，明確地註冊攔截器方法。 如需詳細資訊，請參閱 <<c0> [ 攔截器](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)。  
  
## <a name="client-libraries"></a>用戶端程式庫  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 定義一組用於與資料服務互動的統一模式。 這便有機會來建立可重複使用這些服務，例如輕鬆地使用資料服務的用戶端程式庫為基礎的元件。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 所包含的用戶端程式庫，適用於以 .NET Framework 和 Silverlight 為基礎的用戶端應用程式。 這些用戶端程式庫可讓您利用 .NET Framework 物件與資料服務互動。 它們也支援以物件為基礎的查詢和 LINQ 查詢、載入相關物件、變更追蹤以及識別解析。 如需詳細資訊，請參閱 < [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)。  
  
 除了[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].NET framework 和 Silverlight 所隨附的用戶端程式庫有其他用戶端程式庫可讓您取用[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]中用戶端應用程式，例如 PHP、 AJAX 和 Java 應用程式的摘要。 如需詳細資訊，請參閱 < [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796)。  
  
## <a name="architecture-overview"></a>架構概觀  
 下圖說明[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]架構來公開[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要和中使用這些摘要[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-啟用用戶端程式庫：  
  
 ![顯示 WCF 資料服務架構圖表的螢幕擷取畫面。](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>另請參閱

- [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)
- [快速入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [存取資料服務資源 (WCF Data Services)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919) (具像狀態傳輸 (REST))
