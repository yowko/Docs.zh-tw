---
title: 發行中繼資料端點
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 4c6ac81f0c97415dc21ff3346178dd1e9936b7a5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319900"
---
# <a name="publishing-metadata-endpoints"></a>發行中繼資料端點
Windows Communication Foundation （WCF）服務會藉由發佈一或多個中繼資料端點來發行中繼資料。 發行服務中繼資料會使用標準化的通訊協定 (例如 WS-MetadataExchange (MEX) 和 HTTP/GET 要求) 來提供中繼資料。 中繼資料端點與其他服務端點相似的地方，在於都有位址、繫結和合約，並且能夠透過組態或程式碼新增至服務主機。 若要啟用發行中繼資料端點，您必須將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 服務行為新增至服務。  
  
## <a name="in-this-section"></a>本章節內容  
 [如何：使用組態檔發行服務的中繼資料](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 示範如何設定 WCF 服務以發行中繼資料，讓用戶端可以使用透過 ws-metadataexchange 或 HTTP/GET 要求來抓取中繼資料，方法是使用 `?wsdl` 查詢字串。  
  
 [如何：使用程式碼發行服務的中繼資料](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 示範如何在程式碼中啟用 WCF 服務的中繼資料發行，讓用戶端可以使用透過 ws-metadataexchange 或 HTTP/GET 要求，使用 `?wsdl` 查詢字串來抓取中繼資料。  
  
## <a name="see-also"></a>請參閱

- [發行中繼資料](./feature-details/publishing-metadata.md)
