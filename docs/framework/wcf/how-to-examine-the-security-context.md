---
title: "HOW TO：檢查安全性內容 | Microsoft Docs"
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
  - "Claimset 類別"
  - "ServiceSecurityContext 類別"
  - "WCF, 安全性"
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# HOW TO：檢查安全性內容
在進行 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務的程式設計時，服務安全性內容可讓您決定用來向服務進行驗證的用戶端認證及宣告的詳細資料。這可藉由使用 <xref:System.ServiceModel.ServiceSecurityContext> 類別的屬性達成。  
  
 例如，您可以使用 <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> 或 <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> 屬性擷取目前用戶端的識別。若要判斷用戶端是否為匿名，請使用 <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> 屬性。  
  
 您也可以透過逐一查看 <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> 屬性中的宣告集合，以判斷代表用戶端所進行的宣告為何。  
  
### 取得目前的安全性內容  
  
-   存取靜態屬性 <xref:System.ServiceModel.ServiceSecurityContext.Current%2A>，取得目前的安全性內容。檢視來自參考之目前內容的任一屬性。  
  
### 判斷呼叫端的識別  
  
1.  列印 <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> 和 <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> 屬性的值。  
  
### 剖析呼叫端的宣告  
  
1.  傳回目前的 <xref:System.IdentityModel.Policy.AuthorizationContext> 類別。使用 <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> 屬性傳回目前的服務安全性內容，然後使用 <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> 屬性傳回 `AuthorizationContext`。  
  
2.  剖析 <xref:System.IdentityModel.Policy.AuthorizationContext> 類別的 <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> 屬性所傳回的 <xref:System.IdentityModel.Claims.ClaimSet> 物件集合。  
  
## 範例  
 以下範例會列印目前安全性內容以及 <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 屬性的 <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> 和 <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> 屬性值、宣告的資源值，以及目前安全性內容中的每一項 <xref:System.IdentityModel.Claims.Claim.Right%2A> 屬性。  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## 編譯程式碼  
 程式碼會使用下列命名空間：  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## 請參閱  
 [保護服務的安全](../../../docs/framework/wcf/securing-services.md)   
 [服務身分識別和驗證](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)