---
title: WCF 的安全性考量
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: 16b3afe9540f3e2953311f602408fce5412be2eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000762"
---
# <a name="security-considerations-in-wcf"></a>WCF 的安全性考量
在本節中的主題列出各種安全性相關的項目設計的 Windows Communication Foundation (WCF) 應用程式時需要考量。  
  
## <a name="in-this-section"></a>本節內容  
 [資訊洩漏](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 討論資訊可能遭到洩漏或受到攻擊的各種方式，以及如何減少這種情況。  
  
 [權限提高](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 討論提供攻擊者超出初始所授與之使用權限的影響，以及如何減少這種情況。  
  
 [阻絕服務](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 討論系統無法適當處理訊息時可能發生的情況，以及如何減少這種情況。  
  
 [竄改](../../../../docs/framework/wcf/feature-details/tampering.md)  
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
 [安全性指引和最佳做法](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a>另請參閱

- [安全性](../../../../docs/framework/wcf/feature-details/security.md)
