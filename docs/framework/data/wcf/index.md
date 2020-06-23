---
title: WCF Data Services 4.5
description: 深入瞭解 WCF Data Services，這是一種 .NET Framework 元件，支援使用 REST 語義公開及取用資料的服務。
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: ca6b196e8c910f97ead6d1df5b6c0dd6c49c68a4
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247749"
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5

WCF Data Services （之前稱為 "ADO.NET 資料服務"）是 .NET Framework 的元件，可讓您建立使用開放式資料通訊協定（OData）的服務，利用[具像狀態傳輸（REST）](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)的語義，透過 Web 或內部網路公開及取用資料。 OData 會將資料公開為可由 URI 定址的資源。 資料是使用 GET、PUT、POST 和 DELETE 的標準 HTTP 動作來存取及變更。 OData 會使用[實體資料模型](../adonet/entity-data-model.md)的實體關聯性慣例，將資源公開為與關聯相關的實體集。

WCF Data Services 使用 OData 通訊協定來定址及更新資源。 如此一來，您就可以從任何支援 OData 的用戶端存取這些服務。 OData 可讓您使用已知的傳輸格式來要求和寫入資源： Atom （一組以 XML 形式交換和更新資料的標準），以及 JavaScript 物件標記法（JSON），這是在 AJAX 應用程式中廣泛使用的文字型資料交換格式。

WCF Data Services 可以將源自各種來源的資料公開為 OData 摘要。 Visual Studio 工具可讓您使用 ADO.NET Entity Framework 資料模型，更輕鬆地建立以 OData 為基礎的服務。 您也可以根據 common language runtime （CLR）類別，甚至是晚期繫結或不具類型的資料來建立 OData 摘要。

WCF Data Services 也包含一組用戶端程式庫，一個用於一般 .NET Framework 用戶端應用程式，另一個則特別針對 Silverlight 應用程式。 當您從類似 .NET Framework 和 Silverlight 等環境存取 OData 摘要時，這些用戶端程式庫可提供以物件為基礎的程式設計模型。

## <a name="where-should-i-start"></a>我該從哪裡開始？

根據您的興趣而定，請考慮在下列其中一個主題中開始使用 WCF Data Services。

我想直接開始

- [快速入門](quickstart-wcf-data-services.md)

- [快速入門](getting-started-with-wcf-data-services.md)

只顯示一些程式碼 .。。

- [快速入門](quickstart-wcf-data-services.md)

- [如何：執行資料服務查詢](how-to-execute-data-service-queries-wcf-data-services.md)

- [如何：將資料繫結至 Windows Presentation Foundation 項目](bind-data-to-wpf-elements-wcf-data-services.md)

我想要深入瞭解 OData .。。

- [技術白皮書： OData 簡介](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [開放式資料通訊協定網站](https://www.odata.org/)
- [OData：SDK](https://www.odata.org/ecosystem/)

我想要查看端對端範例 .。。

- [WCF Data Services 快速入門](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))
- [OData SDK-範例程式碼](https://www.odata.org/ecosystem/#sdk)

如何與 Visual Studio 整合？

- [產生資料服務用戶端程式庫](generating-the-data-service-client-library-wcf-data-services.md)

- [建立資料服務](creating-the-data-service.md)

- [Entity Framework 提供者](entity-framework-provider-wcf-data-services.md)

用途為何？

- [概觀](wcf-data-services-overview.md)

- [應用程式案例](application-scenarios-wcf-data-services.md)

我想要使用 LINQ .。。

- [查詢資料服務](querying-the-data-service-wcf-data-services.md)

- [LINQ 考量](linq-considerations-wcf-data-services.md)

- [如何：執行資料服務查詢](how-to-execute-data-service-queries-wcf-data-services.md)

我還需要一些其他資訊 .。。

- [WCF Data Services 小組部落格](https://docs.microsoft.com/archive/blogs/astoriateam/)

- [資源](wcf-data-services-resources.md)

## <a name="in-this-section"></a>本節內容

[概觀](wcf-data-services-overview.md)

提供 WCF Data Services 中可用的特性和功能的總覽。

[5.0 WCF Data Services 的新功能](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))

描述 WCF Data Services 中的新功能，以及新 OData 功能的支援。

[快速入門](getting-started-with-wcf-data-services.md)

描述如何使用 WCF Data Services 公開和取用 OData 摘要。

[定義 WCF 資料服務](defining-wcf-data-services.md)

描述如何建立和設定會公開 OData 摘要的資料服務。

[WCF 資料服務用戶端程式庫](wcf-data-services-client-library.md)

描述如何使用用戶端程式庫，從 .NET Framework 用戶端應用程式取用 OData 摘要。

## <a name="see-also"></a>另請參閱

- [Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm) (具像狀態傳輸 (REST))
