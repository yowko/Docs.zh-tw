---
title: "組件繫結重新導向安全性使用權限"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1bd25dd0444c428e000371abe494e62b258eaa63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="b8364-102">組件繫結重新導向安全性使用權限</span><span class="sxs-lookup"><span data-stu-id="b8364-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="b8364-103">在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。</span><span class="sxs-lookup"><span data-stu-id="b8364-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="b8364-104">這適用於 .NET Framework 組件和協力廠商組件的重新導向。</span><span class="sxs-lookup"><span data-stu-id="b8364-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="b8364-105">藉由設定授與權<xref:System.Security.Permissions.SecurityPermissionFlag>加上旗標上<xref:System.Security.Permissions.SecurityPermission>。</span><span class="sxs-lookup"><span data-stu-id="b8364-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="b8364-106">根據預設，managed 組件具有任何權限。</span><span class="sxs-lookup"><span data-stu-id="b8364-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="b8364-107">安全性權限會授與信任的區域 （本機電腦） 和內部網路區域中執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8364-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="b8364-108">網際網路區域中執行的應用程式絕對禁止執行組件繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="b8364-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="b8364-109">如果由元件發行者的發行者原則檔中或在電腦組態檔由系統管理員所控制的方式執行組件重新導向，則不需要權限。</span><span class="sxs-lookup"><span data-stu-id="b8364-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="b8364-110">不過，需要的權限來明確忽略發行者原則使用的應用程式[ \<p 套用 ="否"/ >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)應用程式組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="b8364-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="b8364-111">下表顯示的預設安全性設定**方式是**旗標。</span><span class="sxs-lookup"><span data-stu-id="b8364-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="b8364-112">區域</span><span class="sxs-lookup"><span data-stu-id="b8364-112">Zone</span></span>|<span data-ttu-id="b8364-113">設定的方式是旗標</span><span class="sxs-lookup"><span data-stu-id="b8364-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="b8364-114">受信任的區域 （本機電腦）</span><span class="sxs-lookup"><span data-stu-id="b8364-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="b8364-115">**ON**</span><span class="sxs-lookup"><span data-stu-id="b8364-115">**ON**</span></span>|  
|<span data-ttu-id="b8364-116">內部網路區域</span><span class="sxs-lookup"><span data-stu-id="b8364-116">Intranet Zone</span></span>|<span data-ttu-id="b8364-117">**ON**</span><span class="sxs-lookup"><span data-stu-id="b8364-117">**ON**</span></span>|  
|<span data-ttu-id="b8364-118">網際網路區域</span><span class="sxs-lookup"><span data-stu-id="b8364-118">Internet Zone</span></span>|<span data-ttu-id="b8364-119">**關閉**</span><span class="sxs-lookup"><span data-stu-id="b8364-119">**OFF**</span></span>|  
|<span data-ttu-id="b8364-120">不受信任的區域</span><span class="sxs-lookup"><span data-stu-id="b8364-120">Untrusted zones</span></span>|<span data-ttu-id="b8364-121">**關閉**</span><span class="sxs-lookup"><span data-stu-id="b8364-121">**OFF**</span></span>|  
  
 <span data-ttu-id="b8364-122">系統管理員可以變更這些安全性設定，以支援或限制特定電腦的特定案例。</span><span class="sxs-lookup"><span data-stu-id="b8364-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="b8364-123">沒有變更工具**方式是**旗標預設值，從設定系統管理員必須手動編輯使用者的電腦上的 Security.config 檔。</span><span class="sxs-lookup"><span data-stu-id="b8364-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8364-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="b8364-124">See Also</span></span>  
 [<span data-ttu-id="b8364-125">發行者原則檔和-並存執行</span><span class="sxs-lookup"><span data-stu-id="b8364-125">Publisher Policy Files and Side-by-Side Execution</span></span>](http://msdn.microsoft.com/en-us/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [<span data-ttu-id="b8364-126">如何：啟用和停用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="b8364-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="b8364-127">並存執行</span><span class="sxs-lookup"><span data-stu-id="b8364-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
