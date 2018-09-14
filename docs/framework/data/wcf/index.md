---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 9ece2fe051855d0fd39556f56a4343ead2c437bc
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527801"
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5

WCF Data Services （先前稱為"ADO.NET Data Services"） 是可讓您建立使用服務的.NET framework 的元件[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]來公開及取用資料透過 Web 或內部網路使用的語意[具像狀態傳輸 (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)。 OData 會將資料公開為可由 URI 定址的資源。 資料是使用 GET、PUT、POST 和 DELETE 的標準 HTTP 動作來存取及變更。 OData 會使用的實體-關聯性慣例[Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)將資源公開為依關聯性相關的實體集。

WCF Data Services 會使用 OData 通訊協定來定址及更新資源。 如此一來，您可以從任何支援 OData 的用戶端存取這些服務。 OData 可讓您要求，並使用已知的傳輸格式將資料寫入資源： Atom，一組交換及更新資料的 XML，以及 JavaScript Object Notation (JSON) 的標準 AJAX 中廣泛使用的文字型資料交換格式應用程式。

WCF 資料服務可以公開為 OData 摘要，來自不同來源的資料。 Visual Studio tools 可讓您更輕鬆地使用 ADO.NET Entity Framework 資料模型建立 OData 為基礎的服務。 您也可以建立根據 common language runtime (CLR) 類別以及甚至是晚期繫結或不具類型資料的 OData 摘要。

WCF Data Services 也包含一組用戶端程式庫，一個用於一般.NET Framework 用戶端應用程式，另一個專門針對以 Silverlight 為基礎的應用程式。 當您存取 OData 摘要的.NET Framework 和 Silverlight 等環境中時，這些用戶端程式庫會提供以物件為基礎的程式設計模型。

## <a name="where-should-i-start"></a>我該從哪裡開始？

根據您感興趣，請考慮開始使用 WCF Data Services 中的下列主題之一。

我想直接開始

-   [快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [快速入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

-   [Silverlight 快速入門](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [適用於 Windows Phone 開發的 Silverlight 快速入門](https://go.microsoft.com/fwlink/?LinkID=214535)

我只想查看某些程式碼...

-   [快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [如何：執行資料服務查詢](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

-   [如何：將資料繫結至 Windows Presentation Foundation 項目](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)

我想要深入了解 OData...

 -   [白皮書：OData 簡介](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [開放式資料通訊協定網站](https://go.microsoft.com/fwlink/?LinkID=184554)

-   [OData：SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

-   [OData：常見問題集](https://go.microsoft.com/fwlink/?LinkId=185867)

我想觀看某些影片...

-   [WCF Data Services 初學者指南](https://go.microsoft.com/fwlink/?LinkId=220864)

-   [WCF Data Services 開發人員視訊](https://go.microsoft.com/fwlink/?LinkId=220861)

-   [OData：開發人員網站](https://go.microsoft.com/fwlink/?LinkId=185866)

我想要查看端對端範例...

-   [MSDN 範例庫上的 WCF Data Services 文件範例](https://go.microsoft.com/fwlink/?LinkID=220865)

-   [MSDN 範例庫上的其他 WCF Data Services 範例](https://go.microsoft.com/fwlink/?LinkId=220866)

-   [OData：SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

如何與 Visual Studio 整合？

-   [產生資料服務用戶端程式庫](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)

-   [建立資料服務](../../../../docs/framework/data/wcf/creating-the-data-service.md)

-   [Entity Framework 提供者](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)

可使用哪些功能？

-   [概觀](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

-   [白皮書：OData 簡介](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [應用程式案例](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)

我想要使用 Silverlight...

-   [Silverlight 快速入門](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)

-   [Silverlight 使用者入門](https://go.microsoft.com/fwlink/?LinkId=148366)

我想要使用 LINQ...

-   [查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)

-   [LINQ 考量](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

-   [如何：執行資料服務查詢](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

我仍然需要一些詳細資訊...

-   [WCF Data Services 小組部落格](https://go.microsoft.com/fwlink/?LinkID=150511)

-   [資源](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

-   [WCF Data Services 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=220868)

-   [開放式資料通訊協定網站](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a>本節內容

 [概觀](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

 提供的功能和 WCF Data Services 中可用功能的概觀。

 [WCF Data Services 的新功能](https://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)

 描述 WCF Data Services 與支援中的 OData 的新功能的新功能。

 [快速入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

 描述如何公開及取用 OData 摘要使用 WCF Data Services。

 [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)

 描述如何建立和設定資料服務公開 OData 摘要。

 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)

 描述如何使用用戶端程式庫來取用 OData 摘要，從.NET Framework 用戶端應用程式。

## <a name="see-also"></a>另請參閱

- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919) (具像狀態傳輸 (REST))
