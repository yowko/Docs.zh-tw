---
title: WCF 的安全性考量
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: 796098258601ec5fa208fd8a8060b28c3eeeb4d6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276018"
---
# <a name="security-considerations-in-wcf"></a>WCF 的安全性考量

本節中的主題會列出設計 Windows Communication Foundation (WCF) 應用程式時所要考慮的各種安全性相關專案。  
  
## <a name="in-this-section"></a>本節內容  

 [洩露資訊](information-disclosure.md)  
 討論資訊可能遭到洩漏或受到攻擊的各種方式，以及如何減少這種情況。  
  
 [提高權限](elevation-of-privilege.md)  
 討論提供攻擊者超出初始所授與之使用權限的影響，以及如何減少這種情況。  
  
 [拒絕服務](denial-of-service.md)  
 討論系統無法適當處理訊息時可能發生的情況，以及如何減少這種情況。  
  
 [竄改](tampering.md)  
 討論訊息的更改或傳遞，以及如何減少這種情況。  
  
 [重新執行攻擊](replay-attacks.md)  
 討論當攻擊者複製兩方之間的訊息資料流，並且對其中一方或多方重新執行資料流時可能發生的情況，以及如何減少這種情況。  
  
 [安全工作階段的安全性考量](security-considerations-for-secure-sessions.md)  
 討論在實作安全工作階段時會影響安全性的項目。  
  
 [不支援的案例](unsupported-scenarios.md)  
 列出不支援特定的安全性方面，而且應避免或考量的各種狀況。  
  
## <a name="reference"></a>參考  

 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>相關章節  

 [安全性指引與最佳做法](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a>另請參閱

- [安全性](security.md)
