---
title: 發行中繼資料
description: 瞭解 WCF 服務如何藉由發佈一或多個中繼資料端點來發行中繼資料，並使用標準通訊協定來提供中繼資料。
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
ms.openlocfilehash: 3ea2377870a37e7dee6f4253503d70167d021a0d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244726"
---
# <a name="publishing-metadata"></a>發行中繼資料

Windows Communication Foundation (WCF) 服務會發佈一個或多個中繼資料端點來發行中繼資料。 發行服務中繼資料會使用標準化的通訊協定 (例如 WS-MetadataExchange (MEX) 和 HTTP/GET 要求) 來提供中繼資料。 中繼資料端點與其他服務端點相似的地方，在於兩者都有位址、繫結程序和合約，並且能夠透過組態或命令式程式碼新增至服務主機。  
  
## <a name="publishing-metadata-endpoints"></a>發行中繼資料端點  

 若要發佈 WCF 服務的中繼資料端點，您必須先將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 服務行為加入至服務。 加入 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> 執行個體可讓您的服務公開中繼資料端點。 一旦您加入 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> 服務行為之後，就可以接著公開支援 MEX 通訊協定或回應 HTTP/GET 要求的中繼資料端點。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> 會使用 <xref:System.ServiceModel.Description.WsdlExporter> 匯出服務中所有服務端點的中繼資料。 如需從服務匯出中繼資料的詳細資訊，請參閱 [匯出和匯入中繼資料](exporting-and-importing-metadata.md)。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> 會加入 <xref:System.ServiceModel.Description.ServiceMetadataExtension> 執行個體做為服務主機的延伸。 <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> 為中繼資料發行通訊協定提供實作。 您也可以藉由存取 <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> 屬性，使用 <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> 在執行階段取得服務的中繼資料。  
  
### <a name="mex-metadata-endpoints"></a>MEX 中繼資料端點  

 若要加入使用 MEX 通訊協定的中繼資料端點，請將服務端點加入至使用 `IMetadataExchange` 服務合約的服務主機。 WCF 包含 <xref:System.ServiceModel.Description.IMetadataExchange> 具有此服務合約名稱的介面，您可以將其作為 WCF 程式設計模型的一部分。 WS-MetadataExchange 端點或 MEX 端點可以使用靜態處理站方法在類別上公開的四個預設系結中的其中一個， <xref:System.ServiceModel.Description.MetadataExchangeBindings> 以符合 WCF 工具（例如 Svcutil.exe）所使用的預設系結。 您也可以使用自己的自訂繫結設定 MEX 中繼資料端點。  
  
### <a name="http-get-metadata-endpoints"></a>HTTP GET 中繼資料端點  

 若要將中繼資料端點加入至回應 HTTP/GET 要求的服務，請將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> 上的 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> 屬性設為 `true`。 您也可以將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> 上的 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> 屬性設為 `true`，以設定使用 HTTPS 的中繼資料端點。  
  
## <a name="in-this-section"></a>本節內容  

 [作法：使用組態檔發行服務的中繼資料](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 示範如何設定 WCF 服務來發行中繼資料，讓用戶端可以使用 WS-MetadataExchange 或使用查詢字串的 HTTP/GET 要求來取得中繼資料 `?wsdl` 。  
  
 [作法：使用程式碼發行服務的中繼資料](how-to-publish-metadata-for-a-service-using-code.md)  
 示範如何在程式碼中啟用 WCF 服務的中繼資料發行，讓用戶端可以使用 WS-MetadataExchange 或使用查詢字串的 HTTP/GET 要求來取得中繼資料 `?wsdl` 。  
  
## <a name="reference"></a>參考  

 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>另請參閱

- [匯出和匯入中繼資料](exporting-and-importing-metadata.md)
