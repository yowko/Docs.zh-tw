---
title: 宣告與拒絕資源的存取
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: 2c903d5b5aa520b9c79fb8b36912324feaf9a432
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264917"
---
# <a name="claims-and-denying-access-to-resources"></a>宣告與拒絕資源的存取

Windows Communication Foundation (WCF) 支援以宣告為基礎的授權機制。 就像根據宣告的存在而允許存取資源，系統也經常會根據宣告的存在而拒絕存取資源。 這類系統應該在尋找會導致允許存取的宣告之前，先檢查 <xref:System.IdentityModel.Policy.AuthorizationContext> 是否有會導致拒絕存取的宣告。  
  
 例如，系統可能只會在任何人擁有類型為 `Age`、權限為 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 且資源值為 `Under 21` 的宣告，而此身分識別又同時擁有類型為 `Name`、權限為 <xref:System.IdentityModel.Claims.Rights.Identity%2A> 且資源值為 `Mallory` 的宣告時，才拒絕該人員對資源的存取。 換句話說，此系統會拒絕低於 21 歲的任何人的存取，而在名稱為 Mallory 時授與存取。 為了正確地實作這項語意，這時先尋找 `Age` 宣告並判斷年齡是否低於 21 歲是非常重要的步驟。 否則，如果 Mallory 低於 21 歲，這時可能就只會根據 `Name` 宣告基礎來授與資源的存取。  
  
## <a name="see-also"></a>另請參閱

- [使用身分識別模型來管理宣告與授權](managing-claims-and-authorization-with-the-identity-model.md)
- [宣告與權杖](claims-and-tokens.md)
