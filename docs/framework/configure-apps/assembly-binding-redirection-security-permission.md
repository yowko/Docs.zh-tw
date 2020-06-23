---
title: 組件繫結重新導向安全性使用權限
description: 瞭解 .NET 中的應用程式佈建檔中明確元件系結重新導向所需的安全性許可權。
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: a8596bcac4efb0aea07efcfde6726d8bbf148c24
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105087"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="2174b-103">組件繫結重新導向安全性使用權限</span><span class="sxs-lookup"><span data-stu-id="2174b-103">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="2174b-104">在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。</span><span class="sxs-lookup"><span data-stu-id="2174b-104">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="2174b-105">這適用於 .NET Framework 組件和協力廠商組件的重新導向。</span><span class="sxs-lookup"><span data-stu-id="2174b-105">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="2174b-106">許可權是藉由在上設定旗標來授與 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> 。</span><span class="sxs-lookup"><span data-stu-id="2174b-106">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="2174b-107">受控元件預設沒有任何許可權。</span><span class="sxs-lookup"><span data-stu-id="2174b-107">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="2174b-108">安全性許可權會授與在 [信任的區域（本機電腦）] 和 [內部網路] 區域中執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2174b-108">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="2174b-109">在網際網路區域中執行的應用程式，絕對不會被禁止執行元件系結重新導向。</span><span class="sxs-lookup"><span data-stu-id="2174b-109">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="2174b-110">如果在元件發行者所控制的發行者原則檔中，或在系統管理員所控制的電腦設定檔中執行元件重新導向，則不需要許可權。</span><span class="sxs-lookup"><span data-stu-id="2174b-110">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="2174b-111">不過，應用程式必須具備許可權，才能使用 [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) 應用程式佈建檔中的元素明確忽略發行者原則。</span><span class="sxs-lookup"><span data-stu-id="2174b-111">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="2174b-112">下表顯示**BindingRedirects**旗標的預設安全性設定。</span><span class="sxs-lookup"><span data-stu-id="2174b-112">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="2174b-113">區域</span><span class="sxs-lookup"><span data-stu-id="2174b-113">Zone</span></span>|<span data-ttu-id="2174b-114">BindingRedirects 旗標設定</span><span class="sxs-lookup"><span data-stu-id="2174b-114">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="2174b-115">信任的區域（本機電腦）</span><span class="sxs-lookup"><span data-stu-id="2174b-115">Trusted Zone (local machine)</span></span>|<span data-ttu-id="2174b-116">**ON**</span><span class="sxs-lookup"><span data-stu-id="2174b-116">**ON**</span></span>|  
|<span data-ttu-id="2174b-117">內部網路區域</span><span class="sxs-lookup"><span data-stu-id="2174b-117">Intranet Zone</span></span>|<span data-ttu-id="2174b-118">**ON**</span><span class="sxs-lookup"><span data-stu-id="2174b-118">**ON**</span></span>|  
|<span data-ttu-id="2174b-119">網際網路區域</span><span class="sxs-lookup"><span data-stu-id="2174b-119">Internet Zone</span></span>|<span data-ttu-id="2174b-120">**OFF**</span><span class="sxs-lookup"><span data-stu-id="2174b-120">**OFF**</span></span>|  
|<span data-ttu-id="2174b-121">不受信任的區域</span><span class="sxs-lookup"><span data-stu-id="2174b-121">Untrusted zones</span></span>|<span data-ttu-id="2174b-122">**OFF**</span><span class="sxs-lookup"><span data-stu-id="2174b-122">**OFF**</span></span>|  
  
 <span data-ttu-id="2174b-123">系統管理員可以變更這些安全性設定，以支援或限制指定電腦上的特定案例。</span><span class="sxs-lookup"><span data-stu-id="2174b-123">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="2174b-124">沒有任何工具可變更**BindingRedirects**旗標設定的預設值;系統管理員必須手動編輯使用者電腦上的 Security.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="2174b-124">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2174b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2174b-125">See also</span></span>

- <span data-ttu-id="2174b-126">[發行者原則檔和並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2174b-126">[Publisher Policy Files and Side-by-Side Execution](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="2174b-127">作法：啟用和停用自動繫結重新導向</span><span class="sxs-lookup"><span data-stu-id="2174b-127">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="2174b-128">並存執行</span><span class="sxs-lookup"><span data-stu-id="2174b-128">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
