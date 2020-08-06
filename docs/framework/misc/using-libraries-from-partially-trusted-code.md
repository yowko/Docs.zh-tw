---
title: 從部分受信任程式碼使用程式庫
description: 瞭解如何從部分信任的程式碼使用程式庫。 使用 AllowPartiallyTrustedCallersAttribute 屬性呼叫共用的 managed 程式庫。
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
ms.openlocfilehash: 38d9c7c7239c849041683525895293a281e3e10f
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855721"
---
# <a name="using-libraries-from-partially-trusted-code"></a><span data-ttu-id="a6d85-104">從部分受信任程式碼使用程式庫</span><span class="sxs-lookup"><span data-stu-id="a6d85-104">Using Libraries from Partially Trusted Code</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> <span data-ttu-id="a6d85-105">本主題說明強式名稱元件的行為，並且只適用于[層級 1](security-transparent-code-level-1.md)元件。</span><span class="sxs-lookup"><span data-stu-id="a6d85-105">This topic addresses the behavior of strong-named assemblies and applies only to [Level 1](security-transparent-code-level-1.md) assemblies.</span></span> <span data-ttu-id="a6d85-106">[安全性透明的程式碼、](security-transparent-code-level-2.md) .NET Framework 4 或更新版本中的層級2元件不會受到強式名稱的影響。</span><span class="sxs-lookup"><span data-stu-id="a6d85-106">[Security-Transparent Code, Level 2](security-transparent-code-level-2.md) assemblies in the .NET Framework 4 or later are not affected by strong names.</span></span> <span data-ttu-id="a6d85-107">如需安全性系統變更的詳細資訊，請參閱[安全性變更](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)。</span><span class="sxs-lookup"><span data-stu-id="a6d85-107">For more information about changes to the security system, see [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="a6d85-108">從其主機或沙箱獲得低於完全信任的應用程式不允許呼叫共用 Managed 程式庫，除非程式庫撰寫者透過使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 來特別允許它們。</span><span class="sxs-lookup"><span data-stu-id="a6d85-108">Applications that receive less than full trust from their host or sandbox are not allowed to call shared managed libraries unless the library writer specifically allows them to through the use of the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="a6d85-109">因此，應用程式撰寫者必須知道有些程式庫將無法從部分信任的內容使用它們。</span><span class="sxs-lookup"><span data-stu-id="a6d85-109">Therefore, application writers must be aware that some libraries will not be available to them from a partially trusted context.</span></span> <span data-ttu-id="a6d85-110">根據預設，在部分信任的[沙箱](how-to-run-partially-trusted-code-in-a-sandbox.md)中執行且不在完全信任元件清單中的所有程式碼，都是部分信任的。</span><span class="sxs-lookup"><span data-stu-id="a6d85-110">By default, all code that executes in a partial-trust [sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md) and is not in the list of full-trust assemblies is partially trusted.</span></span> <span data-ttu-id="a6d85-111">如果您不希望從部分信任的內容中執行您的程式碼，或由部分信任程式碼呼叫您的程式碼，不必顧慮這一節中的資訊。</span><span class="sxs-lookup"><span data-stu-id="a6d85-111">If you do not expect your code to be executed from a partially trusted context or to be called by partially trusted code, you do not have to be concerned about the information in this section.</span></span> <span data-ttu-id="a6d85-112">不過，如果您撰寫的程式碼必須與部分信任的程式碼互動，或從部分信任的內容操作，則應該考慮下列因素：</span><span class="sxs-lookup"><span data-stu-id="a6d85-112">However, if you write code that must interact with partially trusted code or operate from a partially trusted context, you should consider the following factors:</span></span>  
  
- <span data-ttu-id="a6d85-113">程式庫必須使用強式名稱簽署，才能由多個應用程式共用。</span><span class="sxs-lookup"><span data-stu-id="a6d85-113">Libraries must be signed with a strong name in order to be shared by multiple applications.</span></span> <span data-ttu-id="a6d85-114">強式名稱可讓您的程式碼放入全域組件快取，或加入沙箱環境 <xref:System.AppDomain> 的完全信任清單中，並允許取用者驗證行動程式碼的特定部分確實來自您。</span><span class="sxs-lookup"><span data-stu-id="a6d85-114">Strong names allow your code to be placed in the global assembly cache or added to the full-trust list of a sandboxing <xref:System.AppDomain>, and allow consumers to verify that a particular piece of mobile code actually originates from you.</span></span>  
  
- <span data-ttu-id="a6d85-115">根據預設，強式名稱[層級 1](security-transparent-code-level-1.md)共用程式庫會自動執行完全信任的隱含[LinkDemand](link-demands.md) ，而不需要程式庫撰寫者執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="a6d85-115">By default, strong-named [Level 1](security-transparent-code-level-1.md) shared libraries perform an implicit [LinkDemand](link-demands.md) for full trust automatically, without the library writer having to do anything.</span></span>  
  
- <span data-ttu-id="a6d85-116">如果呼叫端沒有完全信任，但仍嘗試呼叫這類程式庫，執行階段會擲回 <xref:System.Security.SecurityException>，且不允許呼叫端連結程式庫。</span><span class="sxs-lookup"><span data-stu-id="a6d85-116">If a caller does not have full trust but still tries to call such a library, the runtime throws a <xref:System.Security.SecurityException> and the caller is not allowed to link to the library.</span></span>  
  
- <span data-ttu-id="a6d85-117">若要停用自動**LinkDemand**並防止擲回例外狀況，您可以將**AllowPartiallyTrustedCallersAttribute**屬性放在共用程式庫的元件範圍上。</span><span class="sxs-lookup"><span data-stu-id="a6d85-117">In order to disable the automatic **LinkDemand** and prevent the exception from being thrown, you can place the **AllowPartiallyTrustedCallersAttribute** attribute on the assembly scope of a shared library.</span></span> <span data-ttu-id="a6d85-118">此屬性允許從部分信任的 Managed 程式碼呼叫您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="a6d85-118">This attribute allows your libraries to be called from partially trusted managed code.</span></span>  
  
- <span data-ttu-id="a6d85-119">以這個屬性被授權存取程式庫的部分信任程式碼，仍受限於 <xref:System.AppDomain> 定義的其他限制。</span><span class="sxs-lookup"><span data-stu-id="a6d85-119">Partially trusted code that is granted access to a library with this attribute is still subject to further restrictions defined by the <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="a6d85-120">部分信任的程式碼沒有任何程式設計的方式可呼叫沒有**AllowPartiallyTrustedCallersAttribute**屬性的程式庫。</span><span class="sxs-lookup"><span data-stu-id="a6d85-120">There is no programmatic way for partially trusted code to call a library that does not have the **AllowPartiallyTrustedCallersAttribute** attribute.</span></span>  
  
 <span data-ttu-id="a6d85-121">特定應用程式私用的程式庫不需要強名稱或**AllowPartiallyTrustedCallersAttribute**屬性，而且不能由應用程式外部的潛在惡意程式碼參考。</span><span class="sxs-lookup"><span data-stu-id="a6d85-121">Libraries that are private to a specific application do not require a strong name or the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be referenced by potentially malicious code outside the application.</span></span> <span data-ttu-id="a6d85-122">這類程式碼受到保護可避免部分信任的行動程式碼有意或無意地誤用，而不需要開發人員執行任何額外的動作。</span><span class="sxs-lookup"><span data-stu-id="a6d85-122">Such code is protected against intentional or unintentional misuse by partially trusted mobile code without the developer having to do anything extra.</span></span>  
  
 <span data-ttu-id="a6d85-123">針對下列程式碼類型，您應該考慮明確地啟用部分信任程式碼的使用：</span><span class="sxs-lookup"><span data-stu-id="a6d85-123">You should consider explicitly enabling use by partially trusted code for the following types of code:</span></span>  
  
- <span data-ttu-id="a6d85-124">已針對安全性弱點進行過仔細測試的程式碼，並遵循安全程式碼撰寫[方針](../../standard/security/secure-coding-guidelines.md)中所述的指導方針。</span><span class="sxs-lookup"><span data-stu-id="a6d85-124">Code that has been diligently tested for security vulnerabilities and is in compliance with the guidelines described in [Secure Coding Guidelines](../../standard/security/secure-coding-guidelines.md).</span></span>  
  
- <span data-ttu-id="a6d85-125">專為部分信任案例撰寫的強式名稱程式碼程式庫。</span><span class="sxs-lookup"><span data-stu-id="a6d85-125">Strong-named code libraries that are specifically written for partially trusted scenarios.</span></span>  
  
- <span data-ttu-id="a6d85-126">使用強式名稱簽署，且將由從網際網路下載的程式碼呼叫的任何元件 (不論部分或完全信任)。</span><span class="sxs-lookup"><span data-stu-id="a6d85-126">Any components (whether partially or fully trusted) signed with a strong name that will be called by code that is downloaded from the Internet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6d85-127">.NET Framework Class Library 中的某些類別沒有**AllowPartiallyTrustedCallersAttribute**屬性，而且無法由部分信任的程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="a6d85-127">Some classes in the .NET Framework class library do not have the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be called by partially trusted code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6d85-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6d85-128">See also</span></span>

- [<span data-ttu-id="a6d85-129">代碼啟用安全性</span><span class="sxs-lookup"><span data-stu-id="a6d85-129">Code Access Security</span></span>](code-access-security.md)
