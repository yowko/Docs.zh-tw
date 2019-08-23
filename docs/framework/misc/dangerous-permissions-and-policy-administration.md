---
title: 危險使用權限和原則管理
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f79fd3e0678fc0bba0d3074904f9ce9460fc6c20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910935"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="89683-102">危險使用權限和原則管理</span><span class="sxs-lookup"><span data-stu-id="89683-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="89683-103">.NET Framework 為幾個受保護作業提供了使用權限，這些受保護作業也可能會讓安全性系統受到危害。</span><span class="sxs-lookup"><span data-stu-id="89683-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="89683-104">您只能在必要時將這些危險的使用權限授與給可靠的程式碼。</span><span class="sxs-lookup"><span data-stu-id="89683-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="89683-105">如果將這些使用權限授與給惡意程式碼，通常就沒有任何方法可以抵禦這些惡意程式碼。</span><span class="sxs-lookup"><span data-stu-id="89683-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89683-106">在 .NET Framework 4 中, .NET Framework 安全性模型和術語的重大變更。</span><span class="sxs-lookup"><span data-stu-id="89683-106">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="89683-107">如需這些變更的詳細資訊, 請參閱[安全性變更](../../../docs/framework/security/security-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="89683-107">For more information about these changes, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="89683-108">下表說明危險的使用權限。</span><span class="sxs-lookup"><span data-stu-id="89683-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="89683-109">權限</span><span class="sxs-lookup"><span data-stu-id="89683-109">Permission</span></span>|<span data-ttu-id="89683-110">潛在風險</span><span class="sxs-lookup"><span data-stu-id="89683-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="89683-111">允許 Managed 程式碼呼叫進入 Unmanaged 程式碼，後者通常具有危險。</span><span class="sxs-lookup"><span data-stu-id="89683-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="89683-112">不用進行驗證，程式碼就可以執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="89683-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="89683-113">失效的辨識項可以騙過安全性原則。</span><span class="sxs-lookup"><span data-stu-id="89683-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="89683-114">修改安全性原則的能力可以使安全性停用。</span><span class="sxs-lookup"><span data-stu-id="89683-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="89683-115">使用序列化可能會規避存取範圍機制。</span><span class="sxs-lookup"><span data-stu-id="89683-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="89683-116">如需詳細資訊，請參閱 [安全性和序列化](../../../docs/framework/misc/security-and-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="89683-116">For details, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="89683-117">設定目前主體的能力可以欺騙以角色為基礎的安全性。</span><span class="sxs-lookup"><span data-stu-id="89683-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="89683-118">執行緒的操作有危險，因為安全性狀態與執行緒有關聯。</span><span class="sxs-lookup"><span data-stu-id="89683-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="89683-119">可以使用私用成員使存取範圍機制無效。</span><span class="sxs-lookup"><span data-stu-id="89683-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89683-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89683-120">See also</span></span>

- [<span data-ttu-id="89683-121">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="89683-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
