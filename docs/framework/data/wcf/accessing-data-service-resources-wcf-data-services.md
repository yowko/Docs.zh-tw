---
title: 存取資料服務資源 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, querying
- getting started, WCF Data Services
- querying the data service [WCF Data Service]
- WCF Data Services, getting started
- WCF Data Services, accessing data
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
ms.openlocfilehash: 6a44d61f29fad7fa7d5304deb8b1e329478bc5b4
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202010"
---
# <a name="accessing-data-service-resources-wcf-data-services"></a>存取資料服務資源 (WCF 資料服務)
WCF Data Services 支援開放式資料通訊協定（OData）將您的資料公開為摘要，其中包含可由 Uri 定址的資源。 這些資源會根據[實體資料模型](../adonet/entity-data-model.md)的實體關聯性慣例來表示。 在此模型中，實體代表資料運算單位 (這些資料在應用程式定義域中為資料型別)，例如客戶、訂單、項目及產品。 使用具像狀態傳輸 (REST) 的語意即可存取及變更實體資料，尤其是標準 HTTP 動作，例如 GET、PUT、POST 和 DELETE。  
  
## <a name="addressing-resources"></a>設定資源存取位址  
 在 OData 中，您可以使用 URI 來處理資料模型所公開的任何資料。 例如，下列 URI 會傳回 Customer 實體集的摘要，其中包含 Customer 實體類型之所有執行個體的項目：  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers>
  
 實體還包含稱為實體索引鍵的特殊屬性。 實體索引鍵用於以唯一方式識別實體集中的單一實體。 這樣可以讓您定址實體集中某個實體型別的特殊執行個體。 例如，下列 URI 會傳回 Customer 實體類型之特定執行個體的項目，此執行個體的索引鍵值為 `ALFKI`：  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')>
  
 您也可以個別定址實體執行個體的基本和複雜屬性。 例如，下列 URI 會傳回 XML 項目，其中包含特定 Customer 的 `ContactName` 屬性值：  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName>
  
 當您在之前的 URI 中包含 `$value` 端點時，回應訊息中只會傳回基本屬性的值。 下列範例只會傳回 "Maria Anders" 字串而沒有 XML 項目：  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value>
  
 資料模型中會以關聯性定義實體之間的關係。 這些關聯可讓您定址相關實體，其方式是使用實體執行個體的導覽屬性。 導覽屬性可在多對一關聯性中傳回單一相關實體，或是在一對多關聯性中傳回一組相關實體。 例如，下列 URI 會傳回一個摘要，它是與特定 Customer 相關之所有 Order 的集合：  
  
<https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders>
  
 關聯性 (通常是雙向關聯性) 是由一對導覽屬性來表示。 下列 URI 會傳回特定 Order 實體所屬之 Customer 實體的參考，與之前範例所示的關聯性相反：  
  
<https://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer>
  
 OData 也可以讓您根據查詢運算式的結果來定址資源。 這樣可以讓您根據經過評估的運算式篩選資源集。 例如，下列 URI 會篩選資源，只傳回自 1997 年 9 月 22 日後配送且屬於指定 Customer 的 Orders。  
  
`https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'`
  
 如需詳細資訊，請參閱[OData： URI 慣例](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)。
  
## <a name="system-query-options"></a>系統查詢選項  
 OData 會定義一組系統查詢選項，讓您用來對資源執行傳統的查詢作業，例如篩選、排序和分頁。 例如，下列 URI 會傳回所有實體以及相關實體的集合， `Order` `Order_Detail` 其中的郵遞區號結尾不是 `100` ：  
  
`https://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity`
  
 傳回之摘要中的項目也會依據訂單之 ShipCity 屬性的值來排序。  
  
 WCF Data Services 支援下列 OData 系統查詢選項：  
  
|查詢選項|描述|  
|------------------|-----------------|  
|`$orderby`|在傳回的摘要中定義實體的預設排序次序。 下列查詢會依據縣市和城市來排序傳回的客戶摘要：<br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City>`|  
|`$top`|指定要併入傳回之摘要中的實體數。 下列範例會略過前 10 名客戶，然後傳回接下來的 10 名：<br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`|  
|`$skip`|指定開始傳回摘要中的實體之前所要略過的實體數。 下列範例會略過前 10 名客戶，然後傳回接下來的 10 名：<br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`|  
|`$filter`|定義運算式，根據特定準則來篩選摘要中傳回的實體。 這個查詢選項可支援一組邏輯比較運算子、算術運算子及預先定義的查詢函數，這些是用來評估篩選運算式。 下列範例會傳回郵遞區號不是以 100 結尾的所有訂單：<br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`|  
|`$expand`|指定查詢傳回哪些相關實體。 相關實體會當做摘要或是內嵌項目 (連同查詢傳回的實體) 併入。 下列範例會傳回客戶 'ALFKI' 的訂單，連同每一份訂單的項目詳細資料：<br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`|  
|`$select`|指定投射，可定義要在投射中傳回之實體的屬性。 依預設，實體的所有屬性都會在摘要中傳回。 下列查詢只會傳回 `Customer` 實體的三個屬性：<br /><br /> `https://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`|  
|`$inlinecount`|要求摘要中傳回的實體計數應該要隨附在摘要中。|  
  
## <a name="addressing-relationships"></a>定址關聯性  
 除了定址實體集和實體實例以外，OData 也可以讓您處理代表實體之間關係的關聯。 必須具備此功能，您才能夠建立或變更兩個實體執行個體之間的關聯性，例如，在 Northwind 範例資料庫中的承運者與指定訂單相關。 OData 支援 `$link` 運算子，以明確定址實體之間的關聯。 例如，在 HTTP PUT 要求訊息中，指定以下 URI 將特定訂單的承運者變更為新承運者。  
  
`https://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper`
  
 如需詳細資訊，請 `3.2. Addressing Links between Entries` 參閱[ODATA： URI 慣例](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)中的一節。
  
## <a name="consuming-the-returned-feed"></a>取用傳回的摘要  
 OData 資源的 URI 可讓您定址服務所公開的實體資料。 當您在網頁瀏覽器的 [位址] 欄位中輸入 URI 時，會傳回所要求資源的 OData 摘要標記法。 如需詳細資訊，請參閱[WCF Data Services 快速入門](quickstart-wcf-data-services.md)。 雖然 Web 瀏覽器可用來測試資料服務資源是否會傳回您預期的資料，但實際執行資料服務也可以建立、更新及刪除通常以應用程式程式碼或網頁中的指令碼語言來存取的資料。 如需詳細資訊，請參閱[在用戶端應用程式中使用資料服務](using-a-data-service-in-a-client-application-wcf-data-services.md)。  
  
## <a name="see-also"></a>另請參閱

- [開放式資料通訊協定網站](https://www.odata.org/)
