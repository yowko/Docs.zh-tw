---
title: 行為安全性
ms.date: 03/30/2017
ms.assetid: 19710ae3-f197-4d28-ba9d-52e465006819
ms.openlocfilehash: c06c615af773affe9b824c6a862afcbadfb16295
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258734"
---
# <a name="behavior-security"></a>行為安全性

本節包含示範設定服務行為之安全性的範例。  
  
## <a name="in-this-section"></a>本節內容  

 [服務稽核行為](service-auditing-behavior.md)  
 這個範例會示範如何使用 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> 以啟用稽核服務作業期間的安全性事件。  
  
 [成員資格和角色提供者](membership-and-role-provider.md)  
 這個範例會示範服務如何使用 ASP.NET 成員資格和角色提供者來驗證和授權用戶端。  
  
 [授權存取服務作業](authorizing-access-to-service-operations.md)  
 這個範例會示範如何使用， [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) 以允許使用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 屬性來授權存取服務作業。  
  
 [模擬用戶端](impersonating-the-client.md)  
 這個範例會示範如何在服務端模擬呼叫者應用程式，以便讓服務能夠代表該呼叫端存取系統資源。
