---
title: 組件繫結重新導向安全性使用權限
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e6690a4f11bb1a88e2d77c67ccb29056c8e03f96
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088656"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="29089-102">組件繫結重新導向安全性使用權限</span><span class="sxs-lookup"><span data-stu-id="29089-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="29089-103">在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。</span><span class="sxs-lookup"><span data-stu-id="29089-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="29089-104">這適用於 .NET Framework 組件和協力廠商組件的重新導向。</span><span class="sxs-lookup"><span data-stu-id="29089-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="29089-105">藉由設定授與權限<xref:System.Security.Permissions.SecurityPermissionFlag>加上旗標上<xref:System.Security.Permissions.SecurityPermission>。</span><span class="sxs-lookup"><span data-stu-id="29089-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="29089-106">Managed 組件預設會有任何權限。</span><span class="sxs-lookup"><span data-stu-id="29089-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="29089-107">安全性權限會授與信任的區域 （本機電腦） 和內部網路區域中執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="29089-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="29089-108">在 [網際網路] 區域中執行的應用程式的嚴格禁止執行組件繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="29089-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="29089-109">如果由元件發行者所控制的發行者原則檔中或在電腦組態檔是由系統管理員所控制的方式執行組件重新導向，則不需要的權限。</span><span class="sxs-lookup"><span data-stu-id="29089-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="29089-110">不過，需要的權限來明確忽略發行者原則使用的應用程式[ \<apply ="no"/ >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)應用程式組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="29089-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="29089-111">下表顯示的預設安全性設定**BindingRedirects**旗標。</span><span class="sxs-lookup"><span data-stu-id="29089-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="29089-112">區域</span><span class="sxs-lookup"><span data-stu-id="29089-112">Zone</span></span>|<span data-ttu-id="29089-113">BindingRedirects 旗標設定</span><span class="sxs-lookup"><span data-stu-id="29089-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="29089-114">受信任的區域 （本機電腦）</span><span class="sxs-lookup"><span data-stu-id="29089-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="29089-115">**ON**</span><span class="sxs-lookup"><span data-stu-id="29089-115">**ON**</span></span>|  
|<span data-ttu-id="29089-116">內部網路區域</span><span class="sxs-lookup"><span data-stu-id="29089-116">Intranet Zone</span></span>|<span data-ttu-id="29089-117">**ON**</span><span class="sxs-lookup"><span data-stu-id="29089-117">**ON**</span></span>|  
|<span data-ttu-id="29089-118">網際網路區域</span><span class="sxs-lookup"><span data-stu-id="29089-118">Internet Zone</span></span>|<span data-ttu-id="29089-119">**關閉**</span><span class="sxs-lookup"><span data-stu-id="29089-119">**OFF**</span></span>|  
|<span data-ttu-id="29089-120">不受信任的區域</span><span class="sxs-lookup"><span data-stu-id="29089-120">Untrusted zones</span></span>|<span data-ttu-id="29089-121">**關閉**</span><span class="sxs-lookup"><span data-stu-id="29089-121">**OFF**</span></span>|  
  
 <span data-ttu-id="29089-122">系統管理員可以變更這些安全性設定，以支援或限制特定電腦的特定案例。</span><span class="sxs-lookup"><span data-stu-id="29089-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="29089-123">沒有變更工具**BindingRedirects**旗標設定預設值; 系統管理員必須手動編輯使用者的電腦上的 Security.config 檔。</span><span class="sxs-lookup"><span data-stu-id="29089-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29089-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29089-124">See Also</span></span>  
 [<span data-ttu-id="29089-125">發行者原則檔和並排顯示執行</span><span class="sxs-lookup"><span data-stu-id="29089-125">Publisher Policy Files and Side-by-Side Execution</span></span>](https://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [<span data-ttu-id="29089-126">如何：啟用和停用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="29089-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="29089-127">並存執行</span><span class="sxs-lookup"><span data-stu-id="29089-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
