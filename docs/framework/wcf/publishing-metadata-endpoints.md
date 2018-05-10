---
title: 發行中繼資料端點
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 42e0f82ca2c669bbde444cf6aac9ce8f0266f783
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="publishing-metadata-endpoints"></a>發行中繼資料端點
Windows Communication Foundation (WCF) 服務發行中繼資料發行一個或多個中繼資料端點。 發行服務中繼資料會使用標準化的通訊協定 (例如 WS-MetadataExchange (MEX) 和 HTTP/GET 要求) 來提供中繼資料。 中繼資料端點與其他服務端點相似的地方，在於都有位址、繫結和合約，並且能夠透過組態或程式碼新增至服務主機。 若要啟用發行中繼資料端點，您必須將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 服務行為新增至服務。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：使用組態檔發行服務的中繼資料](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 示範如何設定 WCF 服務來發行中繼資料，以便讓用戶端可以擷取使用 Ws-metadataexchange 或 HTTP/GET 要求使用的中繼資料`?wsdl`查詢字串。  
  
 [如何：使用程式碼發行服務的中繼資料](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 示範如何讓程式碼中的 WCF 服務的中繼資料發行，好讓用戶端可以擷取使用 Ws-metadataexchange 或 HTTP/GET 要求使用的中繼資料`?wsdl`查詢字串。  
  
## <a name="see-also"></a>另請參閱  
 [發行中繼資料](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
