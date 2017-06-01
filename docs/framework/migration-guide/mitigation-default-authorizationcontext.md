---
title: "風險降低：預設的 AuthorizationContext | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cfeee63-b148-429a-a7e6-6fe9b0cb7610
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d2cffc531efc0f0be841956d3a09e1ab253d8fbd
ms.contentlocale: zh-tw
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-default-authorizationcontext"></a>風險降低：預設的 AuthorizationContext
使用 `null``authorizationPolicies` 引數呼叫 <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> 所傳回的 <xref:System.IdentityModel.Policy.AuthorizationContext> 實作，已變更其在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中的實作。  
  
## <a name="impact"></a>影響  
 在少數情況下，使用自訂驗證的 WCF 應用程式，在行為上可能會有些許差異。  
  
## <a name="mitigation"></a>緩和  
 您可使用下列兩種方式之一還原舊有的行為：  
  
-   以 .NET Framework 4.6 之前的舊版為目標，重新編譯您的應用程式。 對於裝載在 IIS 上的服務，請使用 `<httpRuntime targetFramework="x.x" />` 項目，將目標設為舊版 .NET Framework。  
  
-   將下列行加入 app.config 檔案中的 `<appSettings>` 區段：  
  
    ```xml  
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
