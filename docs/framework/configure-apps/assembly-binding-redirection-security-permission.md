---
title: 組件繫結重新導向安全性使用權限
description: 瞭解 .NET 中的應用程式佈建檔內明確元件系結重新導向所需的安全性許可權。
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: ea2b735b2c98b588903c4393f21c6b743910854a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552371"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="64cdf-103">組件繫結重新導向安全性使用權限</span><span class="sxs-lookup"><span data-stu-id="64cdf-103">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="64cdf-104">在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。</span><span class="sxs-lookup"><span data-stu-id="64cdf-104">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="64cdf-105">這適用於 .NET Framework 組件和協力廠商組件的重新導向。</span><span class="sxs-lookup"><span data-stu-id="64cdf-105">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="64cdf-106">藉由在上設定旗標來授與許可權 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> 。</span><span class="sxs-lookup"><span data-stu-id="64cdf-106">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="64cdf-107">Managed 元件預設沒有任何許可權。</span><span class="sxs-lookup"><span data-stu-id="64cdf-107">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="64cdf-108">安全性許可權會授與在信任區域 (本機電腦) 和內部網路區域中執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="64cdf-108">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="64cdf-109">在網際網路區域中執行的應用程式，完全禁止執行元件系結重新導向。</span><span class="sxs-lookup"><span data-stu-id="64cdf-109">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="64cdf-110">如果在元件發行者所控制的發行者原則檔中，或由系統管理員所控制的電腦設定檔中執行元件重新導向，則不需要此許可權。</span><span class="sxs-lookup"><span data-stu-id="64cdf-110">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="64cdf-111">但是，應用程式需要許可權，才能使用 [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) 應用程式佈建檔中的專案明確地忽略發行者原則。</span><span class="sxs-lookup"><span data-stu-id="64cdf-111">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="64cdf-112">下表顯示 **BindingRedirects** 旗標的預設安全性設定。</span><span class="sxs-lookup"><span data-stu-id="64cdf-112">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="64cdf-113">區域</span><span class="sxs-lookup"><span data-stu-id="64cdf-113">Zone</span></span>|<span data-ttu-id="64cdf-114">BindingRedirects 旗標設定</span><span class="sxs-lookup"><span data-stu-id="64cdf-114">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="64cdf-115">受信任的區域 (本機電腦) </span><span class="sxs-lookup"><span data-stu-id="64cdf-115">Trusted Zone (local machine)</span></span>|<span data-ttu-id="64cdf-116">**ON**</span><span class="sxs-lookup"><span data-stu-id="64cdf-116">**ON**</span></span>|  
|<span data-ttu-id="64cdf-117">內部網路區域</span><span class="sxs-lookup"><span data-stu-id="64cdf-117">Intranet Zone</span></span>|<span data-ttu-id="64cdf-118">**ON**</span><span class="sxs-lookup"><span data-stu-id="64cdf-118">**ON**</span></span>|  
|<span data-ttu-id="64cdf-119">網際網路區域</span><span class="sxs-lookup"><span data-stu-id="64cdf-119">Internet Zone</span></span>|<span data-ttu-id="64cdf-120">**OFF**</span><span class="sxs-lookup"><span data-stu-id="64cdf-120">**OFF**</span></span>|  
|<span data-ttu-id="64cdf-121">不受信任的區域</span><span class="sxs-lookup"><span data-stu-id="64cdf-121">Untrusted zones</span></span>|<span data-ttu-id="64cdf-122">**OFF**</span><span class="sxs-lookup"><span data-stu-id="64cdf-122">**OFF**</span></span>|  
  
 <span data-ttu-id="64cdf-123">系統管理員可以變更這些安全性設定，以支援或限制指定電腦上的特定案例。</span><span class="sxs-lookup"><span data-stu-id="64cdf-123">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="64cdf-124">沒有從預設值變更 **BindingRedirects** 旗標設定的工具;系統管理員必須手動編輯使用者電腦上的 Security.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="64cdf-124">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64cdf-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64cdf-125">See also</span></span>

- <span data-ttu-id="64cdf-126">[發行者原則檔和並存執行](/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="64cdf-126">[Publisher Policy Files and Side-by-Side Execution](/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="64cdf-127">作法：啟用和停用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="64cdf-127">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="64cdf-128">並存執行</span><span class="sxs-lookup"><span data-stu-id="64cdf-128">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
