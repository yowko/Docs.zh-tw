---
title: 裝載資料服務 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: e738fa1feebdd91bdb84484340b31e599d7f5f76
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765568"
---
# <a name="hosting-the-data-service-wcf-data-services"></a>裝載資料服務 (WCF 資料服務)
使用 WCF Data Services，您可以建立資料公開為服務[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]摘要。 這個資料服務會定義為繼承自 <xref:System.Data.Services.DataService%601> 的類別。 這個類別會提供處理要求訊息、 執行更新，針對資料來源，以及產生所需的 OData 回應訊息所需的功能。 不過，無法繫結至資料服務，而且網路通訊端上接聽內送的 HTTP 要求。 對於這個必要的功能而言，資料服務會依賴裝載的元件。

 資料服務主機會代表資料服務執行下列工作：

- 接聽要求，並將這些要求路由傳送到資料服務。

- 為每一個要求建立資料服務的執行個體。

- 要求資料服務處理傳入的要求。

- 代表資料服務傳送回應。

 若要簡化裝載資料服務，WCF Data Services 可整合使用 Windows Communication Foundation (WCF)。 資料服務提供做為資料服務主機中的預設 WCF 實作[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]應用程式。 因此，您可以透過下列其中一個方法來裝載資料服務：

- 在 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式中。

- 在支援自我裝載之 WCF 服務的 Managed 應用程式中。

- 在某個其他自訂資料服務主機中。

## <a name="hosting-a-data-service-in-an-aspnet-application"></a>在 ASP.NET 應用程式中裝載資料服務

當您使用**加入新項目**對話方塊來定義資料服務中的 ASP.NET 應用程式，此工具的 Visual Studio 2015 中的專案中產生兩個新檔案。 第一個檔案的副檔名為 `.svc`，而且它會指示 WCF 執行階段如何具現化資料服務。 以下是此檔案，當您完成時建立的 Northwind 範例資料服務範例[快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):

```
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 這個指示詞會告訴應用程式針對指名的資料服務類別建立服務主機，其方式是使用 <xref:System.Data.Services.DataServiceHostFactory> 類別。

 `.svc` 檔案的程式碼後置頁面包含資料服務本身之實作的類別，如下列 Northwind 範例資料服務所定義：

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 因為資料服務的行為就像 WCF 服務一樣，所以資料服務會與 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 整合並遵循 WCF Web 程式設計模型。 如需詳細資訊，請參閱 < [WCF 服務和 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)並[WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)。

## <a name="self-hosted-wcf-services"></a>自我裝載的 WCF 服務
 它會合併 WCF 實作，因為 WCF Data Services 支援自我裝載的資料服務當做 WCF 服務。 服務可以在任何 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 應用程式中自我裝載，例如在主控台應用程式中。 繼承自 <xref:System.Data.Services.DataServiceHost> 的 <xref:System.ServiceModel.Web.WebServiceHost> 類別是用來具現化特定位址上的資料服務。

 自我裝載可用於開發及測試，因為它可更輕鬆地部署服務以及針對服務進行疑難排解。 但是，這種裝載不會提供 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 或 Internet Information Services (IIS) 所提供的進階裝載和管理功能。 如需詳細資訊，請參閱 <<c0> [ 受管理的應用程式中裝載](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)。

## <a name="defining-a-custom-data-service-host"></a>定義自訂資料服務主機
 如果是 WCF 主機實作太具限制性的情況，您也可以為資料服務定義自訂主機。 實作 <xref:System.Data.Services.IDataServiceHost> 介面的任何類別都可以當做資料服務的網路主機使用。 自訂主機必須實作 <xref:System.Data.Services.IDataServiceHost> 介面，而且必須能夠處理資料服務主機的下列基本責任：

- 為資料服務提供服務根路徑。

- 針對適當的 <xref:System.Data.Services.IDataServiceHost> 成員實作處理要求和回應標頭資訊。

- 處理資料服務所引發的例外狀況。

- 驗證查詢字串中的參數。

## <a name="see-also"></a>另請參閱

- [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [將資料當作服務公開](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
- [設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
