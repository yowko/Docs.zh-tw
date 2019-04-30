---
title: 發行中繼資料端點
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 143a46ce18a0d9dee89bbbffac9be9a467e951df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955151"
---
# <a name="publishing-metadata-endpoints"></a>發行中繼資料端點
Windows Communication Foundation (WCF) 服務會發行中繼資料發行一個或多個中繼資料端點。 發行服務中繼資料會使用標準化的通訊協定 (例如 WS-MetadataExchange (MEX) 和 HTTP/GET 要求) 來提供中繼資料。 中繼資料端點與其他服務端點相似的地方，在於都有位址、繫結和合約，並且能夠透過組態或程式碼新增至服務主機。 若要啟用發行中繼資料端點，您必須將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 服務行為新增至服務。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：發行服務，使用組態檔的中繼資料](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 示範如何設定 WCF 服務發行中繼資料，讓用戶端可以擷取中繼資料使用 Ws-metadataexchange 或 HTTP/GET 要求使用`?wsdl`查詢字串。  
  
 [如何：發行服務，使用程式碼的中繼資料](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 示範如何啟用 WCF 服務程式碼中的中繼資料發行，讓用戶端可以擷取中繼資料使用 Ws-metadataexchange 或 HTTP/GET 要求使用`?wsdl`查詢字串。  
  
## <a name="see-also"></a>另請參閱

- [發行中繼資料](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
