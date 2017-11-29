---
title: "宣告與拒絕資源的存取"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b94c8b77cd659438ec26129137dd9b8cab056b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="claims-and-denying-access-to-resources"></a>宣告與拒絕資源的存取
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 支援宣告架構的授權機制。 就像根據宣告的存在而允許存取資源，系統也經常會根據宣告的存在而拒絕存取資源。 這類系統應該在尋找會導致允許存取的宣告之前，先檢查 <xref:System.IdentityModel.Policy.AuthorizationContext> 是否有會導致拒絕存取的宣告。  
  
 例如，系統可能只會在任何人擁有類型為 `Age`、權限為 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 且資源值為 `Under 21` 的宣告，而此身分識別又同時擁有類型為 `Name`、權限為 <xref:System.IdentityModel.Claims.Rights.Identity%2A> 且資源值為 `Mallory` 的宣告時，才拒絕該人員對資源的存取。 換句話說，此系統會拒絕低於 21 歲的任何人的存取，而在名稱為 Mallory 時授與存取。 為了正確地實作這項語意，這時先尋找 `Age` 宣告並判斷年齡是否低於 21 歲是非常重要的步驟。 否則，如果 Mallory 低於 21 歲，這時可能就只會根據 `Name` 宣告基礎來授與資源的存取。  
  
## <a name="see-also"></a>另請參閱  
 [管理宣告和授權與身分識別模型](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [宣告與權杖](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
