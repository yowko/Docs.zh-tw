---
title: "HOW TO：建立自訂主體身分識別 | Microsoft Docs"
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
  - "IAuthorizationPolicy"
  - "IPrincipal"
  - "PrincipalPermissionAttribute"
  - "PrincipalPermissionMode"
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HOW TO：建立自訂主體身分識別
<xref:System.Security.Permissions.PrincipalPermissionAttribute> 是控制存取服務方法的宣告式方法。  當使用這個屬性時，<xref:System.ServiceModel.Description.PrincipalPermissionMode> 列舉會指定執行授權檢查的模式。  當這個模式設定為 <xref:System.ServiceModel.Description.PrincipalPermissionMode> 時，可讓使用者指定由 <xref:System.Threading.Thread.CurrentPrincipal%2A> 屬性傳回的自訂 <xref:System.Security.Principal.IPrincipal> 類別。  本主題將示範當使用 <xref:System.ServiceModel.Description.PrincipalPermissionMode> 結合自訂授權原則和自訂主體時的案例。  
  
 如需使用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 的詳細資訊，請參閱 [HOW TO：使用 PrincipalPermissionAttribute 類別來限制存取](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)。  
  
## 範例  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## 編譯程式碼  
 編譯此程式碼需要下列命名空間的參照：  
  
-   <xref:System>  
  
-   <xref:System.Collections.Generic>  
  
-   <xref:System.Security.Permissions>  
  
-   <xref:System.Security.Principal>  
  
-   <xref:System.Threading>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Description>  
  
-   <xref:System.IdentityModel.Claims>  
  
-   <xref:System.IdentityModel.Policy>  
  
## 請參閱  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>   
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>   
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>   
 [HOW TO：使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)   
 [HOW TO：使用 PrincipalPermissionAttribute 類別來限制存取](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)