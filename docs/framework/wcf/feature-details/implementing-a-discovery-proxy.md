---
title: 實作探索 Proxy
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 5d9296d8ba70d4c9e8d8339fa3a032d9c4c62826
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140995"
---
# <a name="implementing-a-discovery-proxy"></a>實作探索 Proxy
本節說明實作探索 Proxy 的必要步驟。 探索 Proxy 是一項獨立的服務，包含服務的儲存機制。 用戶端可以查詢探索 Proxy 來尋找 Proxy 感知的可探索服務。 Proxy 中如何填入服務的方式完全取決於實作器。 例如，探索 Proxy 可以連接至現有服務儲存機制，並且使資訊成為可探索，系統管理員可以使用管理 API 將可探索的服務加入至 Proxy，或是探索 Proxy 可以使用公告功能更新其內部快取。  
  
 WCF 實作提供的基底類別可讓您輕鬆建置 Proxy。 您可以利用這些 API 在現有儲存機制之上建置探索 Proxy。  
  
 此處實作的探索 Proxy 就像其他 WCF 服務一般，也就是說，您也可以讓探索 Proxy 成為可探索，並且讓用戶端尋找其端點。  
  
## <a name="in-this-section"></a>本節內容  
 [HOW TO：實作探索 Proxy](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 說明如何實作探索 Proxy。  
  
 [HOW TO：實作以探索 Proxy 註冊的可探索服務](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 描述如何實作可探索的 WCF 服務會向探索 proxy。  
  
 [HOW TO：實作使用探索 Proxy 的用戶端應用程式來尋找服務](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 描述如何實作使用探索 proxy 搜尋服務的 WCF 用戶端應用程式。  
  
 [HOW TO：測試探索 Proxy](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 說明如何測試前三個主題中撰寫的程式碼。  
  
## <a name="see-also"></a>另請參閱

- [WCF 探索](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)
- [HOW TO：以程式設計方式將探索能力新增至 WCF 服務與用戶端](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
