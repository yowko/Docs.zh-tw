---
title: WCF 資料服務概觀
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: 6f085f87286aa5af4a3c2aaf2b74c9bf19023356
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899434"
---
# <a name="wcf-data-services-overview"></a>WCF 資料服務概觀

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

## <a name="overview"></a>概觀

WCF Data Services 使用開放式資料通訊協定 (OData) ，讓 Web 或內部網路的資料服務建立和取用。 OData 可讓您將資料公開為可由 Uri 定址的資源。 這可讓您使用具像狀態傳輸 (REST) 的語意存取及變更資料，尤其是標準 HTTP 動作，例如 GET、PUT、POST 和 DELETE。 本主題概述 OData 定義的模式和做法，以及 WCF Data Services 所提供的功能，以利用以 .NET Framework 為基礎的應用程式中的 OData。  
  
## <a name="address-data-as-resources"></a>將資料定址為資源  

 OData 會將資料公開為可由 URI 定址的資源。 資源路徑會根據實體資料模型的實體-關聯性慣例來建構。 在此模型中，實體代表應用程式定義域中的資料運算單位，例如客戶、訂單、項目及產品。 如需詳細資訊，請參閱 [實體資料模型](../adonet/entity-data-model.md)。  
  
 在 OData 中，您會將實體資源定址為包含實體類型實例的實體集。 例如，URI 會傳回與 `https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` 客戶相關的資料服務的所有訂單，其 `Northwind` `CustomerID` 值為 `ALFKI.`  
  
 查詢運算式可讓您針對資源執行傳統查詢運算，例如篩選、排序和分頁。 例如，URI `https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` 會篩選資源，只傳回運費超過 $50 美元的訂單。 如需詳細資訊，請參閱 [存取資料服務資源](accessing-data-service-resources-wcf-data-services.md)。  
  
## <a name="interoperable-data-access"></a>可互通的資料存取  

 OData 建基於標準網際網路通訊協定，可讓資料服務與不使用 .NET Framework 的應用程式互通。 由於您可以使用標準 URI 來定址資料，因此應用程式可以使用具像狀態傳輸 (REST) 的語意存取及變更資料，尤其是標準 HTTP 動詞命令，例如 GET、PUT、POST 和 DELETE。 這樣能讓您從任何用戶端存取這些服務 (這些用戶端需可剖析及存取透過標準 HTTP 通訊協定傳輸的資料)。  
  
OData 會定義一組 Atom 發行通訊協定 (AtomPub) 的延伸模組。 它可支援採用多種資料格式的 HTTP 要求和回應，配合各種用戶端應用程式和平台。 OData 摘要可代表 Atom、JavaScript 物件標記法 (JSON) 和純 XML 格式的資料。 雖然 Atom 是預設格式，但是摘要的格式會在 HTTP 要求的標頭中指定。 如需詳細資訊，請參閱 [odata： Atom 格式](https://www.odata.org/documentation/odata-version-2-0/atom-format/) 和 [Odata： JSON 格式](https://www.odata.org/documentation/odata-version-2-0/json-format/)。  
  
 當您將資料發佈為 OData 摘要時，WCF Data Services 會依賴其他現有的網際網路設備來進行快取和驗證等作業。 為了達成此目的，WCF Data Services 與現有的裝載應用程式和服務整合，例如 ASP.NET、Windows Communication Foundation (WCF) 和 Internet Information Services (IIS) 。  
  
## <a name="storage-independence"></a>儲存獨立性  

 雖然會根據實體關聯性模型來定址資源，但無論基礎資料來源為何，WCF Data Services 都會公開 OData 摘要。 當 WCF Data Services 接受 URI 識別之資源的 HTTP 要求時，會將要求還原序列化，並將該要求的標記法傳遞給 WCF Data Services 提供者。 此提供者會將要求轉譯為特定資料來源格式，並且在基礎資料來源執行該要求。 WCF Data Services 藉由分隔概念模型來定址 OData 所規定的資源與基礎資料來源的特定架構，以達到儲存體獨立性。  
  
 WCF Data Services 與 ADO.NET Entity Framework 整合，可讓您建立公開關系型資料的資料服務。 您可以使用實體資料模型工具建立以實體形式包含可定址資源的資料模型，同時定義此模型和基礎資料庫中資料表的對應。 如需詳細資訊，請參閱 [Entity Framework 提供者](entity-framework-provider-wcf-data-services.md)。  
  
 WCF Data Services 也可讓您建立資料服務，以公開任何會傳回介面之執行的資料結構 <xref:System.Linq.IQueryable%601> 。 這可讓您建立公開 .NET Framework 型別資料的資料服務。 若您同時實作 <xref:System.Data.Services.IUpdatable> 介面，則亦支援建立、更新及刪除作業。 如需詳細資訊，請參閱 [反映提供者](reflection-provider-wcf-data-services.md)。  
  
 如需 WCF Data Services 如何與這些資料提供者整合的圖例，請參閱本主題稍後的架構圖表。  
  
## <a name="custom-business-logic"></a>自訂商務邏輯  

 WCF Data Services 可讓您輕鬆地透過服務作業和攔截器，將自訂商務邏輯新增至資料服務。 服務作業是在伺服器上定義的方法，而 URI 可透過與資料資源相同的格式來定址這些方法。 服務作業也使用查詢運算式語法來篩選、排序及分頁作業所傳回的資料。 例如，URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` 代表呼叫 Northwind 資料服務中名為 `GetOrdersByCity` 的服務作業，該服務會傳回來自 London 客戶的訂單，同時傳回按 `OrderDate` 排序的分頁結果。 如需詳細資訊，請參閱 [服務作業](service-operations-wcf-data-services.md)。  
  
 攔截器可讓您依照資料服務將自訂應用程式邏輯整合至要求或回應訊息的處理。 在指定的實體集上進行查詢、插入、更新或刪除動作時，系統就會呼叫攔截器。 然後，攔截器可能會更改資料、強制執行授權原則，甚至結束作業。 您必須針對資料服務所公開的特定實體集，明確地註冊攔截器方法。 如需詳細資訊，請參閱 [攔截](interceptors-wcf-data-services.md)器。  
  
## <a name="client-libraries"></a>用戶端程式庫  

 OData 會定義一組統一模式，以便與資料服務互動。 此模式能讓您根據這些服務建立可重複使用的元件，例如可簡化資料服務取用程序的用戶端程式庫。  
  
 WCF Data Services 包含 .NET Framework 型和 Silverlight 用戶端應用程式的用戶端程式庫。 這些用戶端程式庫可讓您利用 .NET Framework 物件與資料服務互動。 它們也支援以物件為基礎的查詢和 LINQ 查詢、載入相關物件、變更追蹤以及識別解析。 如需詳細資訊，請參閱 [WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)。  
  
 除了 .NET Framework 和 Silverlight 隨附的 OData 用戶端程式庫之外，還有其他用戶端程式庫可讓您在用戶端應用程式中使用 OData 摘要，例如 PHP、AJAX 和 JAVA 應用程式。 如需 OData SDK 的詳細資訊，請參閱 [ODATA sdk-範例程式碼](https://www.odata.org/ecosystem/#sdk)。
  
## <a name="architecture-overview"></a>架構概觀  

 下圖說明在啟用 OData 的用戶端程式庫中公開 OData 摘要以及使用這些摘要的 WCF Data Services 架構：  
  
 ![顯示 WCF Data Services 架構圖表的螢幕擷取畫面。](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>另請參閱

- [WCF Data Services 4.5](index.md)
- [快速入門](getting-started-with-wcf-data-services.md)
- [定義 WCF 資料服務](defining-wcf-data-services.md)
- [存取資料服務資源 (WCF 資料服務)](/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [WCF 資料服務用戶端程式庫](wcf-data-services-client-library.md)
- [Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm) (具像狀態傳輸 (REST))
