---
title: 行為安全性
ms.date: 03/30/2017
ms.assetid: 19710ae3-f197-4d28-ba9d-52e465006819
ms.openlocfilehash: 5d09fcc2068133b3bb302850a647a2539ab07ee3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575585"
---
# <a name="behavior-security"></a><span data-ttu-id="a4f60-102">行為安全性</span><span class="sxs-lookup"><span data-stu-id="a4f60-102">Behavior Security</span></span>
<span data-ttu-id="a4f60-103">本節包含示範設定服務行為之安全性的範例。</span><span class="sxs-lookup"><span data-stu-id="a4f60-103">This section includes samples that demonstrate configuring security for service behaviors.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4f60-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="a4f60-104">In This Section</span></span>  
 [<span data-ttu-id="a4f60-105">服務稽核行為</span><span class="sxs-lookup"><span data-stu-id="a4f60-105">Service Auditing Behavior</span></span>](service-auditing-behavior.md)  
 <span data-ttu-id="a4f60-106">這個範例會示範如何使用 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> 以啟用稽核服務作業期間的安全性事件。</span><span class="sxs-lookup"><span data-stu-id="a4f60-106">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span>  
  
 [<span data-ttu-id="a4f60-107">成員資格和角色提供者</span><span class="sxs-lookup"><span data-stu-id="a4f60-107">Membership and Role Provider</span></span>](membership-and-role-provider.md)  
 <span data-ttu-id="a4f60-108">這個範例會示範服務如何使用 ASP.NET 成員資格和角色提供者來驗證及授權用戶端。</span><span class="sxs-lookup"><span data-stu-id="a4f60-108">This sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 [<span data-ttu-id="a4f60-109">授權存取服務作業</span><span class="sxs-lookup"><span data-stu-id="a4f60-109">Authorizing Access to Service Operations</span></span>](authorizing-access-to-service-operations.md)  
 <span data-ttu-id="a4f60-110">這個範例會示範如何使用來啟用屬性的使用，以授與 [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) <xref:System.Security.Permissions.PrincipalPermissionAttribute> 服務作業的存取權。</span><span class="sxs-lookup"><span data-stu-id="a4f60-110">This sample demonstrates how to use the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span>  
  
 [<span data-ttu-id="a4f60-111">模擬用戶端</span><span class="sxs-lookup"><span data-stu-id="a4f60-111">Impersonating the Client</span></span>](impersonating-the-client.md)  
 <span data-ttu-id="a4f60-112">這個範例會示範如何在服務端模擬呼叫者應用程式，以便讓服務能夠代表該呼叫端存取系統資源。</span><span class="sxs-lookup"><span data-stu-id="a4f60-112">This sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>
