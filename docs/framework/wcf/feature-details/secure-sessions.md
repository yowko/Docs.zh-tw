---
title: 安全工作階段
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: 14
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 068615510d7e1d73ae260441ccef6536ee6ff317
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="secure-sessions"></a>安全工作階段
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 其中一項功能，就是保證按照訊息傳送時的順序來接收訊息的可靠工作階段。 本節中的主題將就建立可靠工作階段時要考量的安全性影響提供說明。 如需可靠工作階段的詳細資訊，請參閱[Sessions<](../../../../docs/framework/wcf/using-sessions.md)。  
  
> [!NOTE]
>  當 Windows XP 需要模擬時，請使用不包含具狀態之安全性內容權杖 (SCT) 的安全工作階段。 當可設定狀態的 SCT 與模擬一起使用時，就會擲回 <xref:System.InvalidOperationException>。 如需詳細資訊，請參閱[不支援的案例](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
|||  
|-|-|  
|[安全對話與安全工作階段](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|安全對話與安全工作階段都是一樣的意思。 本主題將說明安全對話的運作方式，以及此模式的使用時機與原因。|  
|[如何：建立安全工作階段](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|逐步解說建立安全工作階段的基本概念。|  
|[如何：為安全工作階段建立安全性內容權杖](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|逐步解說將維護用戶端狀態及工作階段之 Web 伺服陣列的各項建立步驟。|  
|[安全工作階段的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|描述安全工作階段的特殊考量。|  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>相關章節  
 [工作階段、執行個體與並行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [設計與實作服務](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>另請參閱  
 [如何：啟用訊息偵測重送攻擊](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [重新執行攻擊](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [如何：建立需要工作階段的服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
