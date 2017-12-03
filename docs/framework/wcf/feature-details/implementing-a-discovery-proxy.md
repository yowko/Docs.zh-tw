---
title: "實作探索 Proxy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 98affacf611ad31c7c3f8a93ff5793279a42a128
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="implementing-a-discovery-proxy"></a>實作探索 Proxy
本節說明實作探索 Proxy 的必要步驟。 探索 Proxy 是一項獨立的服務，包含服務的儲存機制。 用戶端可以查詢探索 Proxy 來尋找 Proxy 感知的可探索服務。 Proxy 中如何填入服務的方式完全取決於實作器。 例如，探索 Proxy 可以連接至現有服務儲存機制，並且使資訊成為可探索，系統管理員可以使用管理 API 將可探索的服務加入至 Proxy，或是探索 Proxy 可以使用公告功能更新其內部快取。  
  
 WCF 實作提供的基底類別可讓您輕鬆建置 Proxy。 您可以利用這些 API 在現有儲存機制之上建置探索 Proxy。  
  
 此處實作的探索 Proxy 就像其他 WCF 服務一般，也就是說，您也可以讓探索 Proxy 成為可探索，並且讓用戶端尋找其端點。  
  
## <a name="in-this-section"></a>本章節內容  
 [如何： 實作探索 Proxy](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 說明如何實作探索 Proxy。  
  
 [如何： 實作使用探索 Proxy 註冊的可探索服務](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 說明如何實作於探索 Proxy 註冊的可探索 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。  
  
 [如何： 實作使用探索 Proxy 來尋找服務的用戶端應用程式](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 說明如何實作使用探索 Proxy 搜尋服務的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端應用程式。  
  
 [如何： 測試探索 Proxy](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 說明如何測試前三個主題中撰寫的程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [WCF 探索](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [如何： 以程式設計方式將探索能力加入至 WCF 服務和用戶端](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
