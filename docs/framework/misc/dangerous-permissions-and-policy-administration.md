---
title: 危險使用權限和原則管理
description: 請參閱 .NET 中各種危險許可權的連結。 這些許可權應該只提供給值得信任的程式碼，而且只有在必要時才會授與。
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
ms.openlocfilehash: ba3d47dc445e4b368f57d59d735fc331f5d6de81
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281611"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="d486a-104">危險使用權限和原則管理</span><span class="sxs-lookup"><span data-stu-id="d486a-104">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="d486a-105">.NET Framework 為幾個受保護作業提供了使用權限，這些受保護作業也可能會讓安全性系統受到危害。</span><span class="sxs-lookup"><span data-stu-id="d486a-105">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="d486a-106">您只能在必要時將這些危險的使用權限授與給可靠的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d486a-106">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="d486a-107">如果將這些使用權限授與給惡意程式碼，通常就沒有任何方法可以抵禦這些惡意程式碼。</span><span class="sxs-lookup"><span data-stu-id="d486a-107">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d486a-108">在 .NET Framework 4 中，.NET Framework 安全性模型和術語的重大變更。</span><span class="sxs-lookup"><span data-stu-id="d486a-108">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="d486a-109">如需這些變更的詳細資訊，請參閱[安全性變更](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)。</span><span class="sxs-lookup"><span data-stu-id="d486a-109">For more information about these changes, see [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="d486a-110">下表說明危險的使用權限。</span><span class="sxs-lookup"><span data-stu-id="d486a-110">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="d486a-111">權限</span><span class="sxs-lookup"><span data-stu-id="d486a-111">Permission</span></span>|<span data-ttu-id="d486a-112">潛在風險</span><span class="sxs-lookup"><span data-stu-id="d486a-112">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="d486a-113">允許 Managed 程式碼呼叫進入 Unmanaged 程式碼，後者通常具有危險。</span><span class="sxs-lookup"><span data-stu-id="d486a-113">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="d486a-114">不用進行驗證，程式碼就可以執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="d486a-114">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="d486a-115">失效的辨識項可以騙過安全性原則。</span><span class="sxs-lookup"><span data-stu-id="d486a-115">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="d486a-116">修改安全性原則的能力可以使安全性停用。</span><span class="sxs-lookup"><span data-stu-id="d486a-116">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="d486a-117">使用序列化可能會規避存取範圍機制。</span><span class="sxs-lookup"><span data-stu-id="d486a-117">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="d486a-118">如需詳細資訊，請參閱 [安全性和序列化](security-and-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="d486a-118">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="d486a-119">設定目前主體的能力可以欺騙以角色為基礎的安全性。</span><span class="sxs-lookup"><span data-stu-id="d486a-119">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="d486a-120">執行緒的操作有危險，因為安全性狀態與執行緒有關聯。</span><span class="sxs-lookup"><span data-stu-id="d486a-120">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="d486a-121">可以使用私用成員使存取範圍機制無效。</span><span class="sxs-lookup"><span data-stu-id="d486a-121">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d486a-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="d486a-122">See also</span></span>

- [<span data-ttu-id="d486a-123">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="d486a-123">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
