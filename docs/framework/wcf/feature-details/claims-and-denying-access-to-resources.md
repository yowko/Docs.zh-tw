---
title: "宣告與拒絕資源的存取 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "宣告 [WCF], 拒絕資源的存取"
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 宣告與拒絕資源的存取
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 支援宣告架構的授權機制。就像根據宣告的存在而允許存取資源，系統也經常會根據宣告的存在而拒絕存取資源。這類系統應該在尋找會導致允許存取的宣告之前，先檢查 <xref:System.IdentityModel.Policy.AuthorizationContext> 是否有會導致拒絕存取的宣告。  
  
 例如，系統可能只會在任何人擁有類型為 `Age`、權限為 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 且資源值為 `Under 21` 的宣告，而此身分識別又同時擁有類型為 `Name`、權限為 <xref:System.IdentityModel.Claims.Rights.Identity%2A> 且資源值為 `Mallory` 的宣告時，才拒絕該人員對資源的存取。換句話說，此系統會拒絕低於 21 歲的任何人的存取，而在名稱為 Mallory 時授與存取。為了正確地實作這項語意，這時先尋找 `Age` 宣告並判斷年齡是否低於 21 歲是非常重要的步驟。否則，如果 Mallory 低於 21 歲，這時可能就只會根據 `Name` 宣告基礎來授與資源的存取。  
  
## 請參閱  
 [使用身分識別模型來管理宣告與授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)   
 [宣告與權杖](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)