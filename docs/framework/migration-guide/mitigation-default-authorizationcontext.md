---
title: "風險降低：預設的 AuthorizationContext"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 48363d0f8e515b703e49761a763379566e217844
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-default-authorizationcontext"></a><span data-ttu-id="886ae-102">風險降低：預設的 AuthorizationContext</span><span class="sxs-lookup"><span data-stu-id="886ae-102">Mitigation: Default AuthorizationContext</span></span>
<span data-ttu-id="886ae-103">使用 `null``authorizationPolicies` 引數呼叫 <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> 所傳回的 <xref:System.IdentityModel.Policy.AuthorizationContext> 實作，已變更其在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中的實作。</span><span class="sxs-lookup"><span data-stu-id="886ae-103">The implementation of the <xref:System.IdentityModel.Policy.AuthorizationContext> returned by a call to the <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> with a `null``authorizationPolicies` argument has changed its implementation in the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].</span></span>  
  
## <a name="impact"></a><span data-ttu-id="886ae-104">影響</span><span class="sxs-lookup"><span data-stu-id="886ae-104">Impact</span></span>  
 <span data-ttu-id="886ae-105">在少數情況下，使用自訂驗證的 WCF 應用程式，在行為上可能會有些許差異。</span><span class="sxs-lookup"><span data-stu-id="886ae-105">In rare cases, WCF apps that use custom authentication may see behavioral differences.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="886ae-106">緩和</span><span class="sxs-lookup"><span data-stu-id="886ae-106">Mitigation</span></span>  
 <span data-ttu-id="886ae-107">您可使用下列兩種方式之一還原舊有的行為：</span><span class="sxs-lookup"><span data-stu-id="886ae-107">You can restore the previous behavior in either of two ways:</span></span>  
  
-   <span data-ttu-id="886ae-108">以 .NET Framework 4.6 之前的舊版為目標，重新編譯您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="886ae-108">Recompile your app to target an earlier version of the .NET Framework than 4.6.</span></span> <span data-ttu-id="886ae-109">對於裝載在 IIS 上的服務，請使用 `<httpRuntime targetFramework="x.x" />` 項目，將目標設為舊版 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="886ae-109">For IIS-hosted services, use the `<httpRuntime targetFramework="x.x" />` element to target an earlier version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="886ae-110">將下列行加入 app.config 檔案中的 `<appSettings>` 區段：</span><span class="sxs-lookup"><span data-stu-id="886ae-110">Add the following line to the `<appSettings>` section of your app.config file:</span></span>  
  
    ```xml  
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="886ae-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="886ae-111">See Also</span></span>  
 [<span data-ttu-id="886ae-112">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="886ae-112">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

