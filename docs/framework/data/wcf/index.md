---
title: WCF Data Services 4.5
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b6b9ddd27422c09f21833548634afd7945afa89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] (之前稱為 "ADO.NET Data Services") 是 .NET Framework 的一個元件，可讓您建立使用[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]的服務來透過 Web 或內部網路公開及取用資料，其方式是使用[具像狀態傳輸 (REST)](http://go.microsoft.com/fwlink/?LinkId=113919) 的語意。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 會將資料公開為可由 URI 定址的資源。 資料是使用 GET、PUT、POST 和 DELETE 的標準 HTTP 動作來存取及變更。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 會運用[實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)的實體關聯慣例，將資源公開為依關聯性相關的實體集。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會使用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 通訊協定來定址及更新資源。 您可以透過這個方式來從任何支援 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 的用戶端存取這些服務。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 可讓您使用以下知名的傳輸格式來要求資料，並將其寫入至資源：Atom (以 XML 格式交換與更新資料的一組標準) 以及 JavaScript 物件標記法 (JSON) (在 AJAX 應用程式中廣泛使用的文字型資料交換格式)。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可將來自各種不同來源的資料公開為 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。 Visual Studio 工具可讓您輕鬆地建立以 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 為基礎的服務，其方式是使用 ADO.NET Entity Framework 資料模型。 您也可以根據 Common Language Runtime (CLR) 類別以及甚至是晚期繫結或不具類型的資料來建立 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 也包含用戶端程式庫集，其中一個程式庫適用於一般 .NET Framework 用戶端應用程式，而另一個則是針對以 Silverlight 為基礎的應用程式。 當您從類似 .NET Framework 和 Silverlight 等環境存取 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要時，這些用戶端程式庫可提供以物件為基礎的程式設計模型。  
  
## <a name="where-should-i-start"></a>我該從哪裡開始？  
 視您最感興趣的項目而定，您可以考慮從下列其中一個主題開始學習 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]。  
  
 我想直接開始  
 -   [快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [快速入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [Silverlight 快速入門](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [適用於 Windows Phone 開發的 Silverlight 快速入門](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 我只想查看某些程式碼  
 -   [快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [如何：執行資料服務查詢](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [如何：將資料繫結至 Windows Presentation Foundation 項目](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 我想要進一步了解 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]  
 -   [白皮書：OData 簡介](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [開放式資料通訊協定網站](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [OData：SDK](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [OData：常見問題集](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 我想觀看某些影片  
 -   [WCF Data Services 初學者指南](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [WCF Data Services 開發人員視訊](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [OData：開發人員網站](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 我想要查看端對端的範例程式  
 -   [MSDN 範例庫上的 WCF Data Services 文件範例](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [MSDN 範例庫上的其他 WCF Data Services 範例](http://go.microsoft.com/fwlink/?LinkId=220866)  
  
-   [OData：SDK](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 如何與 Visual Studio 整合？  
 -   [產生資料服務用戶端程式庫](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [建立資料服務](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [Entity Framework 提供者](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 可使用哪些功能？  
 -   [概觀](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [白皮書：OData 簡介](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [應用程式案例](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 我想使用 Silverlight  
 -   [Silverlight 快速入門](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [Silverlight 使用者入門](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 我想建立 Windows Phone 應用程式…  
 -   [適用於 Windows Phone 開發的 Silverlight 快速入門](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [適用於 Windows Phone 的開放式資料通訊協定 (OData) 用戶端](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 我想使用 LINQ  
 -   [查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [LINQ 考量](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [如何：執行資料服務查詢](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 我仍然需要一些詳細資訊  
 -   [WCF Data Services 小組部落格](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [資源](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [WCF Data Services 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [開放式資料通訊協定網站](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a>本節內容  
 [概觀](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 提供 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 中可取得之特性與功能的概觀。  
  
 [WCF Data Services 的新功能](http://msdn.microsoft.com/en-us/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 描述 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 的新功能以及新 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 功能的支援。  
  
 [快速入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 描述如何使用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 來公開及取用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 摘要。  
  
 [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 描述如何建立及設定可公開 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的資料服務。  
  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 描述如何使用用戶端程式庫，從 .NET Framework 用戶端應用程式取用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。  
  
## <a name="see-also"></a>請參閱  
 [Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919) (具像狀態傳輸 (REST))
