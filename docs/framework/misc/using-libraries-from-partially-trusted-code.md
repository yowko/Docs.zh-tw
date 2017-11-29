---
title: "從部分受信任程式碼使用程式庫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7a452370df7c18f3e3f0190a14979099152485f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-libraries-from-partially-trusted-code"></a><span data-ttu-id="868a7-102">從部分受信任程式碼使用程式庫</span><span class="sxs-lookup"><span data-stu-id="868a7-102">Using Libraries from Partially Trusted Code</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  <span data-ttu-id="868a7-103">本主題說明強式名稱組件的行為，並且只適用於[層級 1](../../../docs/framework/misc/security-transparent-code-level-1.md)組件。</span><span class="sxs-lookup"><span data-stu-id="868a7-103">This topic addresses the behavior of strong-named assemblies and applies only to [Level 1](../../../docs/framework/misc/security-transparent-code-level-1.md) assemblies.</span></span> <span data-ttu-id="868a7-104">[安全性透明程式碼，層級 2](../../../docs/framework/misc/security-transparent-code-level-2.md)中的組件[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]或更新版本不受強式名稱。</span><span class="sxs-lookup"><span data-stu-id="868a7-104">[Security-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) assemblies in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] or later are not affected by strong names.</span></span> <span data-ttu-id="868a7-105">如需安全性系統變更的詳細資訊，請參閱[安全性變更](../../../docs/framework/security/security-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="868a7-105">For more information about changes to the security system, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="868a7-106">應用程式獲得低於完全信任從其主機或沙箱不允許呼叫共用 managed 程式庫，除非程式庫撰寫者特別允許它們使用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="868a7-106">Applications that receive less than full trust from their host or sandbox are not allowed to call shared managed libraries unless the library writer specifically allows them to through the use of the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="868a7-107">因此，應用程式撰寫者必須知道有些程式庫將無法從部分信任的內容使用它們。</span><span class="sxs-lookup"><span data-stu-id="868a7-107">Therefore, application writers must be aware that some libraries will not be available to them from a partially trusted context.</span></span> <span data-ttu-id="868a7-108">根據預設，所有的程式碼中執行部分信任[沙箱](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)並不是處於完整信任組件清單為部分信任。</span><span class="sxs-lookup"><span data-stu-id="868a7-108">By default, all code that executes in a partial-trust [sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) and is not in the list of full-trust assemblies is partially trusted.</span></span> <span data-ttu-id="868a7-109">如果您不希望從部分信任的內容中執行您的程式碼，或由部分信任程式碼呼叫您的程式碼，不必顧慮這一節中的資訊。</span><span class="sxs-lookup"><span data-stu-id="868a7-109">If you do not expect your code to be executed from a partially trusted context or to be called by partially trusted code, you do not have to be concerned about the information in this section.</span></span> <span data-ttu-id="868a7-110">不過，如果您撰寫的程式碼必須與部分信任的程式碼互動，或從部分信任的內容操作，則應該考慮下列因素：</span><span class="sxs-lookup"><span data-stu-id="868a7-110">However, if you write code that must interact with partially trusted code or operate from a partially trusted context, you should consider the following factors:</span></span>  
  
-   <span data-ttu-id="868a7-111">程式庫必須使用強式名稱簽署，才能由多個應用程式共用。</span><span class="sxs-lookup"><span data-stu-id="868a7-111">Libraries must be signed with a strong name in order to be shared by multiple applications.</span></span> <span data-ttu-id="868a7-112">強式名稱可讓您的程式碼放入全域組件快取，或加入沙箱環境 <xref:System.AppDomain> 的完全信任清單中，並允許取用者驗證行動程式碼的特定部分確實來自您。</span><span class="sxs-lookup"><span data-stu-id="868a7-112">Strong names allow your code to be placed in the global assembly cache or added to the full-trust list of a sandboxing <xref:System.AppDomain>, and allow consumers to verify that a particular piece of mobile code actually originates from you.</span></span>  
  
-   <span data-ttu-id="868a7-113">根據預設，強式名稱[層級 1](../../../docs/framework/misc/security-transparent-code-level-1.md)共用程式庫執行隱含[LinkDemand](../../../docs/framework/misc/link-demands.md)完全信任，而不執行任何動作的程式庫撰寫者。</span><span class="sxs-lookup"><span data-stu-id="868a7-113">By default, strong-named [Level 1](../../../docs/framework/misc/security-transparent-code-level-1.md) shared libraries perform an implicit [LinkDemand](../../../docs/framework/misc/link-demands.md) for full trust automatically, without the library writer having to do anything.</span></span>  
  
-   <span data-ttu-id="868a7-114">如果呼叫端沒有完全信任，但仍嘗試呼叫這類程式庫，執行階段會擲回 <xref:System.Security.SecurityException>，且不允許呼叫端連結程式庫。</span><span class="sxs-lookup"><span data-stu-id="868a7-114">If a caller does not have full trust but still tries to call such a library, the runtime throws a <xref:System.Security.SecurityException> and the caller is not allowed to link to the library.</span></span>  
  
-   <span data-ttu-id="868a7-115">若要停用自動**LinkDemand**並避免擲回的例外狀況，您可以**AllowPartiallyTrustedCallersAttribute**共用組件範圍上的屬性程式庫。</span><span class="sxs-lookup"><span data-stu-id="868a7-115">In order to disable the automatic **LinkDemand** and prevent the exception from being thrown, you can place the **AllowPartiallyTrustedCallersAttribute** attribute on the assembly scope of a shared library.</span></span> <span data-ttu-id="868a7-116">此屬性允許從部分信任的 Managed 程式碼呼叫您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="868a7-116">This attribute allows your libraries to be called from partially trusted managed code.</span></span>  
  
-   <span data-ttu-id="868a7-117">以這個屬性被授權存取程式庫的部分信任程式碼，仍受限於 <xref:System.AppDomain> 定義的其他限制。</span><span class="sxs-lookup"><span data-stu-id="868a7-117">Partially trusted code that is granted access to a library with this attribute is still subject to further restrictions defined by the <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="868a7-118">沒有任何程式設計的方式，部分信任的程式碼呼叫的程式庫，並沒有**AllowPartiallyTrustedCallersAttribute**屬性。</span><span class="sxs-lookup"><span data-stu-id="868a7-118">There is no programmatic way for partially trusted code to call a library that does not have the **AllowPartiallyTrustedCallersAttribute** attribute.</span></span>  
  
 <span data-ttu-id="868a7-119">私用特定應用程式的程式庫不需要強式名稱或**AllowPartiallyTrustedCallersAttribute**屬性，並不能由應用程式外的可能惡意程式碼參考。</span><span class="sxs-lookup"><span data-stu-id="868a7-119">Libraries that are private to a specific application do not require a strong name or the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be referenced by potentially malicious code outside the application.</span></span> <span data-ttu-id="868a7-120">這類程式碼受到保護可避免部分信任的行動程式碼有意或無意地誤用，而不需要開發人員執行任何額外的動作。</span><span class="sxs-lookup"><span data-stu-id="868a7-120">Such code is protected against intentional or unintentional misuse by partially trusted mobile code without the developer having to do anything extra.</span></span>  
  
 <span data-ttu-id="868a7-121">針對下列程式碼類型，您應該考慮明確地啟用部分信任程式碼的使用：</span><span class="sxs-lookup"><span data-stu-id="868a7-121">You should consider explicitly enabling use by partially trusted code for the following types of code:</span></span>  
  
-   <span data-ttu-id="868a7-122">程式碼已經過努力測試是否有安全性弱點，且符合中所述的指導方針[安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="868a7-122">Code that has been diligently tested for security vulnerabilities and is in compliance with the guidelines described in [Secure Coding Guidelines](../../../docs/standard/security/secure-coding-guidelines.md).</span></span>  
  
-   <span data-ttu-id="868a7-123">專為部分信任案例撰寫的強式名稱程式碼程式庫。</span><span class="sxs-lookup"><span data-stu-id="868a7-123">Strong-named code libraries that are specifically written for partially trusted scenarios.</span></span>  
  
-   <span data-ttu-id="868a7-124">使用強式名稱簽署，且將由從網際網路下載的程式碼呼叫的任何元件 (不論部分或完全信任)。</span><span class="sxs-lookup"><span data-stu-id="868a7-124">Any components (whether partially or fully trusted) signed with a strong name that will be called by code that is downloaded from the Internet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="868a7-125">.NET Framework 類別庫中的某些類別沒有**AllowPartiallyTrustedCallersAttribute**屬性，而且無法由部分信任程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="868a7-125">Some classes in the .NET Framework class library do not have the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be called by partially trusted code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="868a7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="868a7-126">See Also</span></span>  
 [<span data-ttu-id="868a7-127">程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="868a7-127">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
