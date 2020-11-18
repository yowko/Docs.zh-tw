---
title: 以角色為基礎的安全性
ms.date: 07/15/2020
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET]
- security [.NET], role-based
- permissions [.NET], principals
- authentication [.NET], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
ms.openlocfilehash: a03cda3aac06cc247818ccea5c61c673225d7929
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824131"
---
# <a name="role-based-security"></a><span data-ttu-id="e0da7-102">以角色為基礎的安全性</span><span class="sxs-lookup"><span data-stu-id="e0da7-102">Role-Based Security</span></span>

<span data-ttu-id="e0da7-103">角色通常用在財務和商務應用程式中以強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="e0da7-103">Roles are often used in financial or business applications to enforce policy.</span></span> <span data-ttu-id="e0da7-104">例如，應用程式可能會根據提出要求的使用者是否為指定角色的成員，而限制正在處理之交易的大小。</span><span class="sxs-lookup"><span data-stu-id="e0da7-104">For example, an application might impose limits on the size of the transaction being processed depending on whether the user making the request is a member of a specified role.</span></span> <span data-ttu-id="e0da7-105">職員可能具有授權，可以處理小於指定臨界值的交易，監督員可能有更高的限制，而副總裁可能有再更高的限制 (或根本沒有限制)。</span><span class="sxs-lookup"><span data-stu-id="e0da7-105">Clerks might have authorization to process transactions that are less than a specified threshold, supervisors might have a higher limit, and vice-presidents might have a still higher limit (or no limit at all).</span></span> <span data-ttu-id="e0da7-106">以角色為基礎的安全性也可用於應用程式需要多重許可才能完成動作之時。</span><span class="sxs-lookup"><span data-stu-id="e0da7-106">Role-based security can also be used when an application requires multiple approvals to complete an action.</span></span> <span data-ttu-id="e0da7-107">這樣的情況可能是採購系統，任何員工可以產生採購要求，但只有採購人員可以將該要求轉換成可以傳送給供應商的訂單。</span><span class="sxs-lookup"><span data-stu-id="e0da7-107">Such a case might be a purchasing system in which any employee can generate a purchase request, but only a purchasing agent can convert that request into a purchase order that can be sent to a supplier.</span></span>  
  
 <span data-ttu-id="e0da7-108">.NET 以角色為基礎的安全性可透過建立主體相關資訊來支援授權，而此主體是從關聯的身分識別（可供目前的執行緒使用）所構成。</span><span class="sxs-lookup"><span data-stu-id="e0da7-108">.NET role-based security supports authorization by making information about the principal, which is constructed from an associated identity, available to the current thread.</span></span> <span data-ttu-id="e0da7-109">識別 (以及它協助定義的主體) 可以是根據 Windows 帳戶，或者是與 Windows 帳戶無關的自訂識別。</span><span class="sxs-lookup"><span data-stu-id="e0da7-109">The identity (and the principal it helps to define) can be either based on a Windows account or be a custom identity unrelated to a Windows account.</span></span> <span data-ttu-id="e0da7-110">.NET 應用程式可以根據主體的身分識別或角色成員資格，或兩者進行授權決策。</span><span class="sxs-lookup"><span data-stu-id="e0da7-110">.NET applications can make authorization decisions based on the principal's identity or role membership, or both.</span></span> <span data-ttu-id="e0da7-111">角色是在安全性方面具有相同權限之主體的命名集 (例如櫃員或經理)。</span><span class="sxs-lookup"><span data-stu-id="e0da7-111">A role is a named set of principals that have the same privileges with respect to security (such as a teller or a manager).</span></span> <span data-ttu-id="e0da7-112">主體可以是一個或多個角色的成員。</span><span class="sxs-lookup"><span data-stu-id="e0da7-112">A principal can be a member of one or more roles.</span></span> <span data-ttu-id="e0da7-113">因此，應用程式可以使用角色成員資格，來判斷主體是否已獲授權執行要求的動作。</span><span class="sxs-lookup"><span data-stu-id="e0da7-113">Therefore, applications can use role membership to determine whether a principal is authorized to perform a requested action.</span></span>  
  
 <span data-ttu-id="e0da7-114">為了讓代碼啟用安全性更容易使用且一致，.NET 以角色為基礎的安全性所提供的 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> 物件，可讓 common language runtime 以類似于代碼啟用安全性檢查的方式來執行授權。</span><span class="sxs-lookup"><span data-stu-id="e0da7-114">To provide ease of use and consistency with code access security, .NET role-based security provides <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> objects that enable the common language runtime to perform authorization in a way that is similar to code access security checks.</span></span> <span data-ttu-id="e0da7-115"><xref:System.Security.Permissions.PrincipalPermission> 類別代表主體必須符合，而且同時與宣告式和命令式安全性檢查相容的識別或角色。</span><span class="sxs-lookup"><span data-stu-id="e0da7-115">The <xref:System.Security.Permissions.PrincipalPermission> class represents the identity or role that the principal must match and is compatible with both declarative and imperative security checks.</span></span> <span data-ttu-id="e0da7-116">您也可以直接存取主體的識別資訊，並視需要在程式碼中執行角色和識別檢查。</span><span class="sxs-lookup"><span data-stu-id="e0da7-116">You can also access a principal's identity information directly and perform role and identity checks in your code when needed.</span></span>  
  
 <span data-ttu-id="e0da7-117">.NET 提供以角色為基礎的安全性支援，其具有彈性且可擴充，足以滿足各式各樣應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="e0da7-117">.NET provides role-based security support that is flexible and extensible enough to meet the needs of a wide spectrum of applications.</span></span> <span data-ttu-id="e0da7-118">您可以選擇與現有的驗證基礎結構 (例如 COM + 1.0 服務) 交互操作，或建立自訂驗證系統。</span><span class="sxs-lookup"><span data-stu-id="e0da7-118">You can choose to interoperate with existing authentication infrastructures, such as COM+ 1.0 Services, or to create a custom authentication system.</span></span> <span data-ttu-id="e0da7-119">以角色為基礎的安全性特別適合用於 ASP.NET Web 應用程式，它們主要是在伺服器上進行處理。</span><span class="sxs-lookup"><span data-stu-id="e0da7-119">Role-based security is particularly well-suited for use in ASP.NET Web applications, which are processed primarily on the server.</span></span> <span data-ttu-id="e0da7-120">不過，您可以在用戶端或伺服器上使用 .NET 角色型安全性。</span><span class="sxs-lookup"><span data-stu-id="e0da7-120">However, .NET role-based security can be used on either the client or the server.</span></span>  
  
 <span data-ttu-id="e0da7-121">閱讀本節之前，請確定您瞭解 [重要安全性概念](key-security-concepts.md)中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="e0da7-121">Before reading this section, make sure that you understand the material presented in [Key Security Concepts](key-security-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0da7-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="e0da7-122">See also</span></span>
  
- [<span data-ttu-id="e0da7-123">Principal 和 Identity 物件</span><span class="sxs-lookup"><span data-stu-id="e0da7-123">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="e0da7-124">重要的安全性概念</span><span class="sxs-lookup"><span data-stu-id="e0da7-124">Key Security Concepts</span></span>](key-security-concepts.md)
- <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
- [<span data-ttu-id="e0da7-125">ASP.NET Core 安全性</span><span class="sxs-lookup"><span data-stu-id="e0da7-125">ASP.NET Core Security</span></span>](/aspnet/core/security/)
