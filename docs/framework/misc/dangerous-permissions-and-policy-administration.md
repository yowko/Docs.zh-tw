---
title: 危險使用權限和原則管理
description: 請參閱 .NET 中各種危險許可權的連結。 只有在必要時，才應該將這些許可權提供給值得信賴的程式碼。
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
ms.openlocfilehash: a2f4469590fea38924430b07eaf20d49f4dc46e9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556937"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="9c20b-104">危險使用權限和原則管理</span><span class="sxs-lookup"><span data-stu-id="9c20b-104">Dangerous Permissions and Policy Administration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="9c20b-105">.NET Framework 為幾個受保護作業提供了使用權限，這些受保護作業也可能會讓安全性系統受到危害。</span><span class="sxs-lookup"><span data-stu-id="9c20b-105">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="9c20b-106">您只能在必要時將這些危險的使用權限授與給可靠的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9c20b-106">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="9c20b-107">如果將這些使用權限授與給惡意程式碼，通常就沒有任何方法可以抵禦這些惡意程式碼。</span><span class="sxs-lookup"><span data-stu-id="9c20b-107">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c20b-108">在 .NET Framework 4 中，.NET Framework 的安全性模型和術語已經有重要的變更。</span><span class="sxs-lookup"><span data-stu-id="9c20b-108">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="9c20b-109">如需這些變更的詳細資訊，請參閱 [安全性變更](/previous-versions/dotnet/framework/security/security-changes)。</span><span class="sxs-lookup"><span data-stu-id="9c20b-109">For more information about these changes, see [Security Changes](/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="9c20b-110">下表說明危險的使用權限。</span><span class="sxs-lookup"><span data-stu-id="9c20b-110">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="9c20b-111">權限</span><span class="sxs-lookup"><span data-stu-id="9c20b-111">Permission</span></span>|<span data-ttu-id="9c20b-112">潛在風險</span><span class="sxs-lookup"><span data-stu-id="9c20b-112">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="9c20b-113">允許 Managed 程式碼呼叫進入 Unmanaged 程式碼，後者通常具有危險。</span><span class="sxs-lookup"><span data-stu-id="9c20b-113">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="9c20b-114">不用進行驗證，程式碼就可以執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="9c20b-114">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="9c20b-115">失效的辨識項可以騙過安全性原則。</span><span class="sxs-lookup"><span data-stu-id="9c20b-115">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="9c20b-116">修改安全性原則的能力可以使安全性停用。</span><span class="sxs-lookup"><span data-stu-id="9c20b-116">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="9c20b-117">使用序列化可能會規避存取範圍機制。</span><span class="sxs-lookup"><span data-stu-id="9c20b-117">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="9c20b-118">如需詳細資訊，請參閱 [安全性和序列化](security-and-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="9c20b-118">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="9c20b-119">設定目前主體的能力可以欺騙以角色為基礎的安全性。</span><span class="sxs-lookup"><span data-stu-id="9c20b-119">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="9c20b-120">執行緒的操作有危險，因為安全性狀態與執行緒有關聯。</span><span class="sxs-lookup"><span data-stu-id="9c20b-120">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="9c20b-121">可以使用私用成員使存取範圍機制無效。</span><span class="sxs-lookup"><span data-stu-id="9c20b-121">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c20b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c20b-122">See also</span></span>

- [<span data-ttu-id="9c20b-123">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="9c20b-123">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
