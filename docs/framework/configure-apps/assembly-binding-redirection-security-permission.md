---
title: 組件繫結重新導向安全性使用權限
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: b59689e78f901637674c0a1df28ed74411e8e7c7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "69921379"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="ae1ce-102">組件繫結重新導向安全性使用權限</span><span class="sxs-lookup"><span data-stu-id="ae1ce-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="ae1ce-103">在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。</span><span class="sxs-lookup"><span data-stu-id="ae1ce-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="ae1ce-104">這適用於 .NET Framework 組件和協力廠商組件的重新導向。</span><span class="sxs-lookup"><span data-stu-id="ae1ce-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="ae1ce-105">許可權是藉由在上設定旗標來授與 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> 。</span><span class="sxs-lookup"><span data-stu-id="ae1ce-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="ae1ce-106">受控元件預設沒有任何許可權。</span><span class="sxs-lookup"><span data-stu-id="ae1ce-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="ae1ce-107">安全性許可權會授與在 [信任的區域（本機電腦）] 和 [內部網路] 區域中執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ae1ce-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="ae1ce-108">在網際網路區域中執行的應用程式，絕對不會被禁止執行元件系結重新導向。</span><span class="sxs-lookup"><span data-stu-id="ae1ce-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="ae1ce-109">如果在元件發行者所控制的發行者原則檔中，或在系統管理員所控制的電腦設定檔中執行元件重新導向，則不需要許可權。</span><span class="sxs-lookup"><span data-stu-id="ae1ce-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="ae1ce-110">不過，應用程式必須具備許可權，才能使用 [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) 應用程式佈建檔中的元素明確忽略發行者原則。</span><span class="sxs-lookup"><span data-stu-id="ae1ce-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="ae1ce-111">下表顯示**BindingRedirects**旗標的預設安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ae1ce-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="ae1ce-112">區域</span><span class="sxs-lookup"><span data-stu-id="ae1ce-112">Zone</span></span>|<span data-ttu-id="ae1ce-113">BindingRedirects 旗標設定</span><span class="sxs-lookup"><span data-stu-id="ae1ce-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="ae1ce-114">信任的區域（本機電腦）</span><span class="sxs-lookup"><span data-stu-id="ae1ce-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="ae1ce-115">**ON**</span><span class="sxs-lookup"><span data-stu-id="ae1ce-115">**ON**</span></span>|  
|<span data-ttu-id="ae1ce-116">內部網路區域</span><span class="sxs-lookup"><span data-stu-id="ae1ce-116">Intranet Zone</span></span>|<span data-ttu-id="ae1ce-117">**ON**</span><span class="sxs-lookup"><span data-stu-id="ae1ce-117">**ON**</span></span>|  
|<span data-ttu-id="ae1ce-118">網際網路區域</span><span class="sxs-lookup"><span data-stu-id="ae1ce-118">Internet Zone</span></span>|<span data-ttu-id="ae1ce-119">**OFF**</span><span class="sxs-lookup"><span data-stu-id="ae1ce-119">**OFF**</span></span>|  
|<span data-ttu-id="ae1ce-120">不受信任的區域</span><span class="sxs-lookup"><span data-stu-id="ae1ce-120">Untrusted zones</span></span>|<span data-ttu-id="ae1ce-121">**OFF**</span><span class="sxs-lookup"><span data-stu-id="ae1ce-121">**OFF**</span></span>|  
  
 <span data-ttu-id="ae1ce-122">系統管理員可以變更這些安全性設定，以支援或限制指定電腦上的特定案例。</span><span class="sxs-lookup"><span data-stu-id="ae1ce-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="ae1ce-123">沒有任何工具可變更**BindingRedirects**旗標設定的預設值;系統管理員必須手動編輯使用者電腦上的安全 .config 檔案。</span><span class="sxs-lookup"><span data-stu-id="ae1ce-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae1ce-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae1ce-124">See also</span></span>

- <span data-ttu-id="ae1ce-125">[發行者原則檔和並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ae1ce-125">[Publisher Policy Files and Side-by-Side Execution](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="ae1ce-126">作法：啟用和停用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="ae1ce-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="ae1ce-127">並存執行</span><span class="sxs-lookup"><span data-stu-id="ae1ce-127">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
