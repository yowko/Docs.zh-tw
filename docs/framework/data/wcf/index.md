---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 017fe2177cf824d461b4c51ea805f75b6ddbe064
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779995"
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5

WCF Data Services （之前稱為 "ADO.NET 資料服務"）是 .NET Framework 的元件，可讓您建立使用[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]的服務，透過 Web 或內部網路公開及取用資料，方法是使用[具像狀態的語義傳輸（REST）](https://go.microsoft.com/fwlink/?LinkId=113919)。 OData 會將資料公開為可由 URI 定址的資源。 資料是使用 GET、PUT、POST 和 DELETE 的標準 HTTP 動作來存取及變更。 OData 會使用[實體資料模型](../adonet/entity-data-model.md)的實體關聯性慣例，將資源公開為與關聯相關的實體集。

WCF Data Services 使用 OData 通訊協定來定址及更新資源。 如此一來，您就可以從任何支援 OData 的用戶端存取這些服務。 OData 可讓您使用已知的傳輸格式來要求和寫入資源的資料：Atom，這是一組在 AJAX 應用程式中廣泛使用的文字型資料交換格式，用來以 XML 交換和更新資料的標準，以及 JavaScript 物件標記法（JSON）。

WCF Data Services 可以將源自各種來源的資料公開為 OData 摘要。 Visual Studio 工具可讓您使用 ADO.NET Entity Framework 資料模型，更輕鬆地建立以 OData 為基礎的服務。 您也可以根據 common language runtime （CLR）類別，甚至是晚期繫結或不具類型的資料來建立 OData 摘要。

WCF Data Services 也包含一組用戶端程式庫，一個用於一般 .NET Framework 用戶端應用程式，另一個則特別針對 Silverlight 應用程式。 當您從 .NET Framework 和 Silverlight 等環境存取 OData 摘要時，這些用戶端程式庫可提供以物件為基礎的程式設計模型。

## <a name="where-should-i-start"></a>我該從哪裡開始？

根據您的興趣而定，請考慮在下列其中一個主題中開始使用 WCF Data Services。

我想直接開始

- [快速入門](quickstart-wcf-data-services.md)

- [快速入門](getting-started-with-wcf-data-services.md)

- [Silverlight 快速入門](https://go.microsoft.com/fwlink/?LinkID=192782)

- [適用於 Windows Phone 開發的 Silverlight 快速入門](https://go.microsoft.com/fwlink/?LinkID=214535)

只顯示一些程式碼 。

- [快速入門](quickstart-wcf-data-services.md)

- [如何：執行資料服務查詢](how-to-execute-data-service-queries-wcf-data-services.md)

- [如何：將資料系結至 Windows Presentation Foundation 元素](bind-data-to-wpf-elements-wcf-data-services.md)

我想要深入瞭解 OData 。

- [白皮書OData 簡介](https://go.microsoft.com/fwlink/?LinkId=220867)

- [開放式資料通訊協定網站](https://go.microsoft.com/fwlink/?LinkID=184554)

- [ODataSDK](https://go.microsoft.com/fwlink/?LinkID=185248)

- [OData常見問題集](https://go.microsoft.com/fwlink/?LinkId=185867)

我想要觀賞一些影片 。

- [WCF Data Services 初學者指南](https://go.microsoft.com/fwlink/?LinkId=220864)

- [WCF Data Services 開發人員視訊](https://go.microsoft.com/fwlink/?LinkId=220861)

- [OData開發人員網站](https://go.microsoft.com/fwlink/?LinkId=185866)

我想要查看端對端範例 。

- [MSDN 範例庫上的 WCF Data Services 文件範例](https://go.microsoft.com/fwlink/?LinkID=220865)

- [MSDN 範例庫上的其他 WCF Data Services 範例](https://go.microsoft.com/fwlink/?LinkId=220866)

- [ODataSDK](https://go.microsoft.com/fwlink/?LinkID=185248)

如何與 Visual Studio 整合？

- [產生資料服務用戶端程式庫](generating-the-data-service-client-library-wcf-data-services.md)

- [建立資料服務](creating-the-data-service.md)

- [Entity Framework 提供者](entity-framework-provider-wcf-data-services.md)

可使用哪些功能？

- [概觀](wcf-data-services-overview.md)

- [白皮書OData 簡介](https://go.microsoft.com/fwlink/?LinkId=220867)

- [應用程式案例](application-scenarios-wcf-data-services.md)

我想要使用 Silverlight 。

- [Silverlight 快速入門](https://go.microsoft.com/fwlink/?LinkID=192782)

- [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)

- [Silverlight 使用者入門](https://go.microsoft.com/fwlink/?LinkId=148366)

我想要使用 LINQ 。

- [查詢資料服務](querying-the-data-service-wcf-data-services.md)

- [LINQ 考量](linq-considerations-wcf-data-services.md)

- [如何：執行資料服務查詢](how-to-execute-data-service-queries-wcf-data-services.md)

我還需要一些其他資訊 。

- [WCF Data Services 小組部落格](https://go.microsoft.com/fwlink/?LinkID=150511)

- [資源](wcf-data-services-resources.md)

- [WCF Data Services 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=220868)

- [開放式資料通訊協定網站](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a>本節內容

[概觀](wcf-data-services-overview.md)

提供 WCF Data Services 中可用的特性和功能的總覽。

[5.0 WCF Data Services 的新功能](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))

描述 WCF Data Services 中的新功能，以及新 OData 功能的支援。

[快速入門](getting-started-with-wcf-data-services.md)

描述如何使用 WCF Data Services 公開和取用 OData 摘要。

[定義 WCF Data Services](defining-wcf-data-services.md)

描述如何建立和設定會公開 OData 摘要的資料服務。

[WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)

描述如何使用用戶端程式庫，從 .NET Framework 用戶端應用程式取用 OData 摘要。

## <a name="see-also"></a>另請參閱

- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919) (具像狀態傳輸 (REST))
