---
title: "行為安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19710ae3-f197-4d28-ba9d-52e465006819
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# 行為安全性
本節包含示範設定服務行為之安全性的範例。  
  
## 在本節中  
 [服務稽核行為](../../../../docs/framework/wcf/samples/service-auditing-behavior.md)  
 這個範例會示範如何使用 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> 以啟用稽核服務作業期間的安全性事件。  
  
 [成員資格和角色提供者](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)  
 這個範例會示範服務如何使用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 成員資格和角色提供者來驗證及授權用戶端。  
  
 [授權存取服務作業](../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 這個範例會示範如何使用 [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)來啟用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 屬性的使用，以授權存取服務作業。  
  
 [模擬用戶端](../../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 這個範例會示範如何在服務端模擬呼叫者應用程式，以便讓服務能夠代表該呼叫端存取系統資源。