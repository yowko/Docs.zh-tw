---
title: 發行中繼資料端點
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 5be27a72c87d95e36a5b283e7930ba0a5191a5a1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249757"
---
# <a name="publishing-metadata-endpoints"></a>發行中繼資料端點

Windows Communication Foundation (WCF) 服務會發佈一個或多個中繼資料端點來發行中繼資料。 發行服務中繼資料會使用標準化的通訊協定 (例如 WS-MetadataExchange (MEX) 和 HTTP/GET 要求) 來提供中繼資料。 中繼資料端點與其他服務端點相似的地方，在於都有位址、繫結和合約，並且能夠透過組態或程式碼新增至服務主機。 若要啟用發行中繼資料端點，您必須將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 服務行為新增至服務。  
  
## <a name="in-this-section"></a>本節內容  

 [作法：使用組態檔發行服務的中繼資料](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 示範如何設定 WCF 服務來發行中繼資料，讓用戶端可以使用 WS-MetadataExchange 或使用查詢字串的 HTTP/GET 要求來取得中繼資料 `?wsdl` 。  
  
 [作法：使用程式碼發行服務的中繼資料](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 示範如何在程式碼中啟用 WCF 服務的中繼資料發行，讓用戶端可以使用 WS-MetadataExchange 或使用查詢字串的 HTTP/GET 要求來取得中繼資料 `?wsdl` 。  
  
## <a name="see-also"></a>另請參閱

- [發行中繼資料](./feature-details/publishing-metadata.md)
