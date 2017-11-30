---
title: "WCF 的安全性考量"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
caps.latest.revision: "49"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c0af5a5d96f20b2ba5118909a3f0c5ba405bdb11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="security-considerations-in-wcf"></a>WCF 的安全性考量
本節中的主題列出在設計 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式時，要考量的各種安全性相關項目。  
  
## <a name="in-this-section"></a>本章節內容  
 [資訊洩漏](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 討論資訊可能遭到洩漏或受到攻擊的各種方式，以及如何減少這種情況。  
  
 [提高權限](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 討論提供攻擊者超出初始所授與之使用權限的影響，以及如何減少這種情況。  
  
 [阻斷服務](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 討論系統無法適當處理訊息時可能發生的情況，以及如何減少這種情況。  
  
 [遭到竄改](../../../../docs/framework/wcf/feature-details/tampering.md)  
 討論訊息的更改或傳遞，以及如何減少這種情況。  
  
 [重新執行攻擊](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 討論當攻擊者複製兩方之間的訊息資料流，並且對其中一方或多方重新執行資料流時可能發生的情況，以及如何減少這種情況。  
  
 [安全工作階段的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 討論在實作安全工作階段時會影響安全性的項目。  
  
 [不支援的案例](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 列出不支援特定的安全性方面，而且應避免或考量的各種狀況。  
  
## <a name="reference"></a>參考資料  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>相關章節  
 [安全性指導方針和最佳作法](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a>另請參閱  
 [安全性](../../../../docs/framework/wcf/feature-details/security.md)
