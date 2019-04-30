---
title: 以角色為基礎的安全性
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET Framework]
- security [.NET Framework], role-based
- permissions [.NET Framework], principals
- authentication [.NET Framework], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 596165bfac9c65898448714a4477b7f045bd87d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018576"
---
# <a name="role-based-security"></a><span data-ttu-id="441eb-102">以角色為基礎的安全性</span><span class="sxs-lookup"><span data-stu-id="441eb-102">Role-Based Security</span></span>
<span data-ttu-id="441eb-103">角色通常用在財務和商務應用程式中以強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="441eb-103">Roles are often used in financial or business applications to enforce policy.</span></span> <span data-ttu-id="441eb-104">例如，應用程式可能會根據提出要求的使用者是否為指定角色的成員，而限制正在處理之交易的大小。</span><span class="sxs-lookup"><span data-stu-id="441eb-104">For example, an application might impose limits on the size of the transaction being processed depending on whether the user making the request is a member of a specified role.</span></span> <span data-ttu-id="441eb-105">職員可能具有授權，可以處理小於指定臨界值的交易，監督員可能有更高的限制，而副總裁可能有再更高的限制 (或根本沒有限制)。</span><span class="sxs-lookup"><span data-stu-id="441eb-105">Clerks might have authorization to process transactions that are less than a specified threshold, supervisors might have a higher limit, and vice-presidents might have a still higher limit (or no limit at all).</span></span> <span data-ttu-id="441eb-106">以角色為基礎的安全性也可用於應用程式需要多重許可才能完成動作之時。</span><span class="sxs-lookup"><span data-stu-id="441eb-106">Role-based security can also be used when an application requires multiple approvals to complete an action.</span></span> <span data-ttu-id="441eb-107">這樣的情況可能是採購系統，任何員工可以產生採購要求，但只有採購人員可以將該要求轉換成可以傳送給供應商的訂單。</span><span class="sxs-lookup"><span data-stu-id="441eb-107">Such a case might be a purchasing system in which any employee can generate a purchase request, but only a purchasing agent can convert that request into a purchase order that can be sent to a supplier.</span></span>  
  
 <span data-ttu-id="441eb-108">.NET Framework 以角色為基礎的安全性，是藉由將主體的有關資訊 (這是從關聯的識別所建構) 提供給目前的執行緒，而支援授權。</span><span class="sxs-lookup"><span data-stu-id="441eb-108">.NET Framework role-based security supports authorization by making information about the principal, which is constructed from an associated identity, available to the current thread.</span></span> <span data-ttu-id="441eb-109">識別 (以及它協助定義的主體) 可以是根據 Windows 帳戶，或者是與 Windows 帳戶無關的自訂識別。</span><span class="sxs-lookup"><span data-stu-id="441eb-109">The identity (and the principal it helps to define) can be either based on a Windows account or be a custom identity unrelated to a Windows account.</span></span> <span data-ttu-id="441eb-110">.NET Framework 應用程式可以依據主體的識別及/或角色成員資格，做出授權決策。</span><span class="sxs-lookup"><span data-stu-id="441eb-110">.NET Framework applications can make authorization decisions based on the principal's identity or role membership, or both.</span></span> <span data-ttu-id="441eb-111">角色是在安全性方面具有相同權限之主體的命名集 (例如櫃員或經理)。</span><span class="sxs-lookup"><span data-stu-id="441eb-111">A role is a named set of principals that have the same privileges with respect to security (such as a teller or a manager).</span></span> <span data-ttu-id="441eb-112">主體可以是一個或多個角色的成員。</span><span class="sxs-lookup"><span data-stu-id="441eb-112">A principal can be a member of one or more roles.</span></span> <span data-ttu-id="441eb-113">因此，應用程式可以使用角色成員資格，來判斷主體是否已獲授權執行要求的動作。</span><span class="sxs-lookup"><span data-stu-id="441eb-113">Therefore, applications can use role membership to determine whether a principal is authorized to perform a requested action.</span></span>  
  
 <span data-ttu-id="441eb-114">為了提供程式碼存取安全性的使用方便性和一致性，.NET Framework 以角色為基礎的安全性提供 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> 物件，會讓 Common Language Runtime 能以和程式碼存取安全性檢查類似的方式執行授權。</span><span class="sxs-lookup"><span data-stu-id="441eb-114">To provide ease of use and consistency with code access security, .NET Framework role-based security provides <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> objects that enable the common language runtime to perform authorization in a way that is similar to code access security checks.</span></span> <span data-ttu-id="441eb-115"><xref:System.Security.Permissions.PrincipalPermission> 類別代表主體必須符合，而且同時與宣告式和命令式安全性檢查相容的識別或角色。</span><span class="sxs-lookup"><span data-stu-id="441eb-115">The <xref:System.Security.Permissions.PrincipalPermission> class represents the identity or role that the principal must match and is compatible with both declarative and imperative security checks.</span></span> <span data-ttu-id="441eb-116">您也可以直接存取主體的識別資訊，並視需要在程式碼中執行角色和識別檢查。</span><span class="sxs-lookup"><span data-stu-id="441eb-116">You can also access a principal's identity information directly and perform role and identity checks in your code when needed.</span></span>  
  
 <span data-ttu-id="441eb-117">.NET Framework 提供以角色為基礎的安全性支援，具有足夠的彈性和可擴充性，可滿足廣泛應用程式的需要。</span><span class="sxs-lookup"><span data-stu-id="441eb-117">The .NET Framework provides role-based security support that is flexible and extensible enough to meet the needs of a wide spectrum of applications.</span></span> <span data-ttu-id="441eb-118">您可以選擇與現有的驗證基礎結構 (例如 COM + 1.0 服務) 交互操作，或建立自訂驗證系統。</span><span class="sxs-lookup"><span data-stu-id="441eb-118">You can choose to interoperate with existing authentication infrastructures, such as COM+ 1.0 Services, or to create a custom authentication system.</span></span> <span data-ttu-id="441eb-119">以角色為基礎的安全性特別適合用於 ASP.NET Web 應用程式，它們主要是在伺服器上進行處理。</span><span class="sxs-lookup"><span data-stu-id="441eb-119">Role-based security is particularly well-suited for use in ASP.NET Web applications, which are processed primarily on the server.</span></span> <span data-ttu-id="441eb-120">不過，.NET Framework 以角色為基礎的安全性可以用在用戶端或伺服器上。</span><span class="sxs-lookup"><span data-stu-id="441eb-120">However, .NET Framework role-based security can be used on either the client or the server.</span></span>  
  
 <span data-ttu-id="441eb-121">之前閱讀本節，請確定您已了解中所呈現的題材[重要的安全性概念](../../../docs/standard/security/key-security-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="441eb-121">Before reading this section, make sure that you understand the material presented in [Key Security Concepts](../../../docs/standard/security/key-security-concepts.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="441eb-122">相關主題</span><span class="sxs-lookup"><span data-stu-id="441eb-122">Related Topics</span></span>  
  
|<span data-ttu-id="441eb-123">標題</span><span class="sxs-lookup"><span data-stu-id="441eb-123">Title</span></span>|<span data-ttu-id="441eb-124">描述</span><span class="sxs-lookup"><span data-stu-id="441eb-124">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="441eb-125">Principal 和 Identity 物件</span><span class="sxs-lookup"><span data-stu-id="441eb-125">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)|<span data-ttu-id="441eb-126">說明如何設定和管理 Windows 和泛型識別和主體。</span><span class="sxs-lookup"><span data-stu-id="441eb-126">Explains how to set up and manage both Windows and generic identities and principals.</span></span>|  
|[<span data-ttu-id="441eb-127">重要的安全性概念</span><span class="sxs-lookup"><span data-stu-id="441eb-127">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)|<span data-ttu-id="441eb-128">介紹您在使用 .NET Framework 安全性之前必須了解的基本概念。</span><span class="sxs-lookup"><span data-stu-id="441eb-128">Introduces fundamental concepts you must understand before using .NET Framework security.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="441eb-129">參考資料</span><span class="sxs-lookup"><span data-stu-id="441eb-129">Reference</span></span>  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
