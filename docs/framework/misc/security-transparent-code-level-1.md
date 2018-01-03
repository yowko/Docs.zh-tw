---
title: "安全性透明的程式碼，層級 1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
caps.latest.revision: "32"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd4655524c74175d03191cbf7065177c10e3ddda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="security-transparent-code-level-1"></a><span data-ttu-id="7080b-102">安全性透明的程式碼，層級 1</span><span class="sxs-lookup"><span data-stu-id="7080b-102">Security-Transparent Code, Level 1</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="7080b-103">透明度可協助開發人員撰寫更安全的 .NET Framework 程式庫，該程式庫會向部分信任的程式碼公開功能。</span><span class="sxs-lookup"><span data-stu-id="7080b-103">Transparency helps developers write more secure .NET Framework libraries that expose functionality to partially trusted code.</span></span> <span data-ttu-id="7080b-104">層級 1 透明度是在 .NET Framework 2.0 版中所引入的，而且主要只在 Microsoft 中使用。</span><span class="sxs-lookup"><span data-stu-id="7080b-104">Level 1 transparency was introduced in the .NET Framework version 2.0 and was primarily used only within Microsoft.</span></span> <span data-ttu-id="7080b-105">從開始[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，您可以使用[層級 2 透明度](../../../docs/framework/misc/security-transparent-code-level-2.md)。</span><span class="sxs-lookup"><span data-stu-id="7080b-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use [level 2 transparency](../../../docs/framework/misc/security-transparent-code-level-2.md).</span></span> <span data-ttu-id="7080b-106">不過，層級 1 透明度保留，讓您可以識別必須以舊版安全性規則執行的舊版程式碼。</span><span class="sxs-lookup"><span data-stu-id="7080b-106">However, level 1 transparency has been retained so that you can identify legacy code that must run with the earlier security rules.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7080b-107">您應該僅針對相容性指定層級 1 透明度；也就是說，您應該僅針對使用 .NET Framework 3.5 或更早版本 (使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 或沒有使用透明度模型) 所開發的程式碼指定層級 1。</span><span class="sxs-lookup"><span data-stu-id="7080b-107">You should specify level 1 transparency for compatibility only; that is, specify level 1 only for code that was developed with the .NET Framework 3.5 or earlier that uses the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> or does not use the transparency model.</span></span> <span data-ttu-id="7080b-108">例如，對於允許來自部分信任呼叫端 (APTCA) 之呼叫的 .NET Framework 2.0 組件，請使用層級 1 透明度。</span><span class="sxs-lookup"><span data-stu-id="7080b-108">For example, use level 1 transparency for .NET Framework 2.0 assemblies that allow calls from partially trusted callers (APTCA).</span></span> <span data-ttu-id="7080b-109">對於針對 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 所開發的程式碼，請一律使用層級 2 透明度。</span><span class="sxs-lookup"><span data-stu-id="7080b-109">For code that is developed for the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], always use level 2 transparency.</span></span>  
  
 <span data-ttu-id="7080b-110">此主題包括下列章節：</span><span class="sxs-lookup"><span data-stu-id="7080b-110">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="7080b-111">層級 1 透明度模型</span><span class="sxs-lookup"><span data-stu-id="7080b-111">The Level 1 Transparency Model</span></span>](#the_level_1_transparency_model)  
  
-   [<span data-ttu-id="7080b-112">透明度屬性</span><span class="sxs-lookup"><span data-stu-id="7080b-112">Transparency Attributes</span></span>](#transparency_attributes)  
  
-   [<span data-ttu-id="7080b-113">安全性透明度範例</span><span class="sxs-lookup"><span data-stu-id="7080b-113">Security Transparency Examples</span></span>](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>   
## <a name="the-level-1-transparency-model"></a><span data-ttu-id="7080b-114">層級 1 透明度模型</span><span class="sxs-lookup"><span data-stu-id="7080b-114">The Level 1 Transparency Model</span></span>  
 <span data-ttu-id="7080b-115">當您使用層級 1 透明度時，就是使用將程式碼分為安全性透明、安全性安全關鍵和安全性關鍵方法的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="7080b-115">When you use Level 1 transparency, you are using a security model that separates code into security-transparent, security-safe-critical, and security-critical methods.</span></span>  
  
 <span data-ttu-id="7080b-116">您可以將整個組件、組件中的某些類別，或是類別中的某些方法標記為安全性透明。</span><span class="sxs-lookup"><span data-stu-id="7080b-116">You can mark a whole assembly, some classes in an assembly, or some methods in a class as security-transparent.</span></span> <span data-ttu-id="7080b-117">安全性透明程式碼無法提高權限。</span><span class="sxs-lookup"><span data-stu-id="7080b-117">Security-transparent code cannot elevate privileges.</span></span> <span data-ttu-id="7080b-118">這項限制有三個後果：</span><span class="sxs-lookup"><span data-stu-id="7080b-118">This restriction has three consequences:</span></span>  
  
-   <span data-ttu-id="7080b-119">安全性透明的程式碼無法執行 <xref:System.Security.Permissions.SecurityAction.Assert> 動作。</span><span class="sxs-lookup"><span data-stu-id="7080b-119">Security-transparent code cannot perform <xref:System.Security.Permissions.SecurityAction.Assert> actions.</span></span>  
  
-   <span data-ttu-id="7080b-120">由安全性程式碼所滿足的任何連結要求，都會變成完整的要求。</span><span class="sxs-lookup"><span data-stu-id="7080b-120">Any link demand that would be satisfied by security-transparent code becomes a full demand.</span></span>  
  
-   <span data-ttu-id="7080b-121">必須在安全性透明程式碼中執行的任何不安全 (無法驗證) 的程式碼，都會導致 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> 安全性權限的完整要求。</span><span class="sxs-lookup"><span data-stu-id="7080b-121">Any unsafe (unverifiable) code that must execute in security-transparent code causes a full demand for the <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> security permission.</span></span>  
  
 <span data-ttu-id="7080b-122">這些規則是在執行期間由 Common Language Runtime (CLR) 強制執行。</span><span class="sxs-lookup"><span data-stu-id="7080b-122">These rules are enforced during execution by the common language runtime (CLR).</span></span> <span data-ttu-id="7080b-123">安全性透明程式碼會將它所回呼的程式碼之所有安全性需求傳遞給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="7080b-123">Security-transparent code passes all the security requirements of the code it calls back to its callers.</span></span> <span data-ttu-id="7080b-124">流經安全性透明程式碼的需求，無法提高權限。</span><span class="sxs-lookup"><span data-stu-id="7080b-124">Demands that flow through the security-transparent code cannot elevate privileges.</span></span> <span data-ttu-id="7080b-125">如果低度信任的應用程式呼叫安全性透明程式碼，並產生高權限的需求，則此需求會流回低度信任程式碼且失敗。</span><span class="sxs-lookup"><span data-stu-id="7080b-125">If a low-trust application calls security-transparent code and causes a demand for high privilege, the demand will flow back to the low-trust code and fail.</span></span> <span data-ttu-id="7080b-126">安全性透明程式碼無法停止此需求，因為它不能執行判斷提示動作。</span><span class="sxs-lookup"><span data-stu-id="7080b-126">The security-transparent code cannot stop the demand because it cannot perform assert actions.</span></span> <span data-ttu-id="7080b-127">從完全信任程式碼呼叫的同一個安全性透明程式碼，會產生成功的需求。</span><span class="sxs-lookup"><span data-stu-id="7080b-127">The same security-transparent code called from full-trust code results in a successful demand.</span></span>  
  
 <span data-ttu-id="7080b-128">安全性關鍵和安全性透明相反。</span><span class="sxs-lookup"><span data-stu-id="7080b-128">Security-critical is the opposite of security-transparent.</span></span> <span data-ttu-id="7080b-129">安全性關鍵程式碼是以完全信任方式執行，而且可以執行所有需要權限的作業。</span><span class="sxs-lookup"><span data-stu-id="7080b-129">Security-critical code executes with full trust and can perform all privileged operations.</span></span> <span data-ttu-id="7080b-130">安全性安全關鍵程式碼是通過廣泛安全性稽核的特權程式碼，可以確認該程式碼不會允許部分信任的呼叫端使用沒有存取權限的資源。</span><span class="sxs-lookup"><span data-stu-id="7080b-130">Security-safe-critical code is privileged code that has been through an extensive security audit to confirm that it does not allow partially trusted callers to use resources they do not have permission to access.</span></span>  
  
 <span data-ttu-id="7080b-131">您必須明確套用透明度。</span><span class="sxs-lookup"><span data-stu-id="7080b-131">You have to apply transparency explicitly.</span></span> <span data-ttu-id="7080b-132">處理資料操作與邏輯的大部分程式碼通常可以標記為安全性透明，而執行權限提高的小部分程式碼則可標記為安全性關鍵或安全性安全關鍵。</span><span class="sxs-lookup"><span data-stu-id="7080b-132">The majority of your code that handles data manipulation and logic can typically be marked as security-transparent, whereas the lesser amount of code that performs elevations of privileges is marked as security-critical or security-safe-critical.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7080b-133">層級 1 透明度受限於組件範圍；這在組件之間沒有強制執行。</span><span class="sxs-lookup"><span data-stu-id="7080b-133">Level 1 transparency is limited to assembly scope; it is not enforced between assemblies.</span></span> <span data-ttu-id="7080b-134">層級 1 透明度主要用於 Microsoft 內部進行安全性稽核。</span><span class="sxs-lookup"><span data-stu-id="7080b-134">Level 1 transparency was primarily used within Microsoft for security audit purposes.</span></span> <span data-ttu-id="7080b-135">層級 1 組件內的安全性關鍵類型和成員可以由其他組件中的安全性透明程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="7080b-135">Security-critical types and members within a level 1 assembly can be accessed by security-transparent code in other assemblies.</span></span> <span data-ttu-id="7080b-136">請務必在所有層級 1 安全性關鍵類型和成員中執行完全信任的連結要求。</span><span class="sxs-lookup"><span data-stu-id="7080b-136">It is important that you perform link demands for full trust in all your level 1 security-critical types and members.</span></span> <span data-ttu-id="7080b-137">安全性安全關鍵類型和成員還必須確認，對於由類型或成員所存取的受保護資源，呼叫端必須擁有權限。</span><span class="sxs-lookup"><span data-stu-id="7080b-137">Security-safe-critical types and members must also confirm that callers have permissions for protected resources that are accessed by the type or member.</span></span>  
  
 <span data-ttu-id="7080b-138">為了與舊版 .NET Framework 回溯相容，會將所有未以透明度屬性標註的成員視為安全性安全關鍵。</span><span class="sxs-lookup"><span data-stu-id="7080b-138">For backward compatibility with earlier versions of the .NET Framework, all members that are not annotated with transparency attributes are considered to be security-safe-critical.</span></span> <span data-ttu-id="7080b-139">會將所有未標註的類型都視為透明。</span><span class="sxs-lookup"><span data-stu-id="7080b-139">All types that are not annotated are considered to be transparent.</span></span> <span data-ttu-id="7080b-140">沒有任何靜態分析規則可以用來驗證透明度。</span><span class="sxs-lookup"><span data-stu-id="7080b-140">There are no static analysis rules to validate transparency.</span></span> <span data-ttu-id="7080b-141">因此，您可能需要在執行階段偵錯透明度錯誤。</span><span class="sxs-lookup"><span data-stu-id="7080b-141">Therefore, you may need to debug transparency errors at run time.</span></span>  
  
<a name="transparency_attributes"></a>   
## <a name="transparency-attributes"></a><span data-ttu-id="7080b-142">透明度屬性</span><span class="sxs-lookup"><span data-stu-id="7080b-142">Transparency Attributes</span></span>  
 <span data-ttu-id="7080b-143">下表說明您可以用來標註程式碼透明度的三個屬性。</span><span class="sxs-lookup"><span data-stu-id="7080b-143">The following table describes the three attributes that you use to annotate your code for transparency.</span></span>  
  
|<span data-ttu-id="7080b-144">屬性</span><span class="sxs-lookup"><span data-stu-id="7080b-144">Attribute</span></span>|<span data-ttu-id="7080b-145">描述</span><span class="sxs-lookup"><span data-stu-id="7080b-145">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|<span data-ttu-id="7080b-146">僅在該組件層級受允許。</span><span class="sxs-lookup"><span data-stu-id="7080b-146">Allowed only at the assembly level.</span></span> <span data-ttu-id="7080b-147">將該組件中的所有類型和成員都識別為安全性透明。</span><span class="sxs-lookup"><span data-stu-id="7080b-147">Identifies all types and members in the assembly as security-transparent.</span></span> <span data-ttu-id="7080b-148">該組件不能包含任何安全性關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="7080b-148">The assembly cannot contain any security-critical code.</span></span>|  
|<xref:System.Security.SecurityCriticalAttribute>|<span data-ttu-id="7080b-149">在無 <xref:System.Security.SecurityCriticalAttribute.Scope%2A> 屬性的組件層級使用時，根據預設，會將組件中的所有程式碼識別為安全性透明，但也表示該組件可能包含安全性關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="7080b-149">When used at the assembly level without the <xref:System.Security.SecurityCriticalAttribute.Scope%2A> property, identifies all code in the assembly as security-transparent by default, but indicates that the assembly may contain security-critical code.</span></span><br /><br /> <span data-ttu-id="7080b-150">在類別層級使用時，會將類別或方法識別為安全性關鍵，而不是識別類別的成員。</span><span class="sxs-lookup"><span data-stu-id="7080b-150">When used at the class level, identifies the class or method as security-critical, but not the members of the class.</span></span> <span data-ttu-id="7080b-151">若要將所有成員都設成安全性關鍵，請將 <xref:System.Security.SecurityCriticalAttribute.Scope%2A> 屬性設為 <xref:System.Security.SecurityCriticalScope.Everything>。 </span><span class="sxs-lookup"><span data-stu-id="7080b-151">To make all the members security-critical, set the <xref:System.Security.SecurityCriticalAttribute.Scope%2A> property to <xref:System.Security.SecurityCriticalScope.Everything>.</span></span><br /><br /> <span data-ttu-id="7080b-152">在成員層級使用時，該屬性只適用於該成員。</span><span class="sxs-lookup"><span data-stu-id="7080b-152">When used at the member level, the attribute applies only to that member.</span></span><br /><br /> <span data-ttu-id="7080b-153">已識別為安全性關鍵的類別或成員可以執行權限提高。</span><span class="sxs-lookup"><span data-stu-id="7080b-153">The class or member identified as security-critical can perform elevations of privilege.</span></span> <span data-ttu-id="7080b-154">**重要事項：**層級 1 透明度中安全性關鍵類型和成員的處理為安全性安全關鍵從呼叫外部組件時。</span><span class="sxs-lookup"><span data-stu-id="7080b-154">**Important:**  In level 1 transparency, security-critical types and members are treated as security-safe-critical when they are called from outside the assembly.</span></span> <span data-ttu-id="7080b-155">您應該使用完全信任的連結要求來保護安全性關鍵類型和成員，以避免未經授權的權限提高。</span><span class="sxs-lookup"><span data-stu-id="7080b-155">You should protect security-critical types and members with a link demand for full trust to avoid unauthorized elevation of privilege.</span></span>|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|<span data-ttu-id="7080b-156">識別可以由組件中安全性透明程式碼存取的安全性關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="7080b-156">Identifies security-critical code that can be accessed by security-transparent code in the assembly.</span></span> <span data-ttu-id="7080b-157">否則安全性透明程式碼無法存取相同組件中的私用或內部安全性關鍵成員。</span><span class="sxs-lookup"><span data-stu-id="7080b-157">Otherwise, security-transparent code cannot access private or internal security-critical members in the same assembly.</span></span> <span data-ttu-id="7080b-158">這麼做會影響安全性關鍵程式碼，並可能造成非預期的權限提高。</span><span class="sxs-lookup"><span data-stu-id="7080b-158">Doing so would influence security-critical code and make unexpected elevations of privilege possible.</span></span> <span data-ttu-id="7080b-159">安全性安全關鍵程式碼應該經過嚴密的安全性稽核。</span><span class="sxs-lookup"><span data-stu-id="7080b-159">Security-safe-critical code should undergo a rigorous security audit.</span></span> <span data-ttu-id="7080b-160">**注意：**安全性安全關鍵類型和成員必須驗證呼叫端的權限，以判斷呼叫端是否具有受保護的資源的存取權限。</span><span class="sxs-lookup"><span data-stu-id="7080b-160">**Note:**  Security-safe-critical types and members must validate the permissions of callers to determine whether the caller has authority to access protected resources.</span></span>|  
  
 <span data-ttu-id="7080b-161"><xref:System.Security.SecuritySafeCriticalAttribute> 屬性可以讓安全性透明程式碼存取相同組件中安全性關鍵的成員。</span><span class="sxs-lookup"><span data-stu-id="7080b-161">The <xref:System.Security.SecuritySafeCriticalAttribute> attribute enables security-transparent code to access security-critical members in the same assembly.</span></span> <span data-ttu-id="7080b-162">請考慮將組件中的安全性透明及安全性關鍵程式碼區分成兩個組件。</span><span class="sxs-lookup"><span data-stu-id="7080b-162">Consider the security-transparent and security-critical code in your assembly as separated into two assemblies.</span></span> <span data-ttu-id="7080b-163">安全性透明程式碼無法查看安全性關鍵程式碼的私用或內部成員。</span><span class="sxs-lookup"><span data-stu-id="7080b-163">The security-transparent code would not be able to see the private or internal members of the security-critical code.</span></span> <span data-ttu-id="7080b-164">此外，安全性關鍵程式碼一般是為了存取公用介面而受稽核的。</span><span class="sxs-lookup"><span data-stu-id="7080b-164">Additionally, the security-critical code is generally audited for access to its public interface.</span></span> <span data-ttu-id="7080b-165">您可能不希望私用或內部狀態在組件外還能存取；您可能想要讓狀態保持隔離。</span><span class="sxs-lookup"><span data-stu-id="7080b-165">You would not expect a private or internal state to be accessible outside the assembly; you would want to keep the state isolated.</span></span> <span data-ttu-id="7080b-166"><xref:System.Security.SecuritySafeCriticalAttribute> 屬性會維護安全性透明與安全性關鍵程式碼之間的狀態隔離，但是可在必要時提供覆寫隔離的功能。</span><span class="sxs-lookup"><span data-stu-id="7080b-166">The <xref:System.Security.SecuritySafeCriticalAttribute> attribute maintains the isolation of state between security-transparent and security-critical code while providing the ability to override the isolation when it is necessary.</span></span> <span data-ttu-id="7080b-167">安全性透明程式碼無法存取私用或內部安全性關鍵程式碼，除非那些成員已經以 <xref:System.Security.SecuritySafeCriticalAttribute> 標記。</span><span class="sxs-lookup"><span data-stu-id="7080b-167">Security-transparent code cannot access private or internal security-critical code unless those members have been marked with <xref:System.Security.SecuritySafeCriticalAttribute>.</span></span> <span data-ttu-id="7080b-168">套用 <xref:System.Security.SecuritySafeCriticalAttribute> 之前，請先將成員視為已公開並加以稽核。</span><span class="sxs-lookup"><span data-stu-id="7080b-168">Before applying the <xref:System.Security.SecuritySafeCriticalAttribute>, audit that member as if it were publicly exposed.</span></span>  
  
### <a name="assembly-wide-annotation"></a><span data-ttu-id="7080b-169">組件範圍的註釋</span><span class="sxs-lookup"><span data-stu-id="7080b-169">Assembly-wide Annotation</span></span>  
 <span data-ttu-id="7080b-170">下表說明在組件層級中使用安全性屬性的效果。</span><span class="sxs-lookup"><span data-stu-id="7080b-170">The following table describes the effects of using security attributes at the assembly level.</span></span>  
  
|<span data-ttu-id="7080b-171">Assembly 屬性</span><span class="sxs-lookup"><span data-stu-id="7080b-171">Assembly attribute</span></span>|<span data-ttu-id="7080b-172">組件狀態</span><span class="sxs-lookup"><span data-stu-id="7080b-172">Assembly state</span></span>|  
|------------------------|--------------------|  
|<span data-ttu-id="7080b-173">部分信任組件無屬性</span><span class="sxs-lookup"><span data-stu-id="7080b-173">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="7080b-174">所有類型和成員皆為透明的。</span><span class="sxs-lookup"><span data-stu-id="7080b-174">All types and members are transparent.</span></span>|  
|<span data-ttu-id="7080b-175">在完全信任組件上沒有屬性 (在全域組件快取中或在 `AppDomain` 中識別為完全信任)</span><span class="sxs-lookup"><span data-stu-id="7080b-175">No attribute on a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`)</span></span>|<span data-ttu-id="7080b-176">所有類型為透明，且所有成員為安全性安全關鍵。</span><span class="sxs-lookup"><span data-stu-id="7080b-176">All types are transparent and all members are security-safe-critical.</span></span>|  
|`SecurityTransparent`|<span data-ttu-id="7080b-177">所有類型和成員皆為透明的。</span><span class="sxs-lookup"><span data-stu-id="7080b-177">All types and members are transparent.</span></span>|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="7080b-178">所有類型和成員皆為安全性關鍵的。</span><span class="sxs-lookup"><span data-stu-id="7080b-178">All types and members are security-critical.</span></span>|  
|`SecurityCritical`|<span data-ttu-id="7080b-179">所有程式碼都預設為透明的。</span><span class="sxs-lookup"><span data-stu-id="7080b-179">All code defaults to transparent.</span></span> <span data-ttu-id="7080b-180">不過，個別的類型和成員可以有其他屬性。</span><span class="sxs-lookup"><span data-stu-id="7080b-180">However, individual types and members can have other attributes.</span></span>|  
  
<a name="security_transparency_examples"></a>   
## <a name="security-transparency-examples"></a><span data-ttu-id="7080b-181">安全性透明度範例</span><span class="sxs-lookup"><span data-stu-id="7080b-181">Security Transparency Examples</span></span>  
 <span data-ttu-id="7080b-182">若要使用 .NET Framework 2.0 透明度規則 (層級 1 透明度)，請使用下列組件註釋：</span><span class="sxs-lookup"><span data-stu-id="7080b-182">To use the .NET Framework 2.0 transparency rules (level 1 transparency), use the following assembly annotation:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 <span data-ttu-id="7080b-183">如果您要使整個組件透明，來表示該組件不含任何關鍵程式碼，而且在任何情況下都不提高權限，則可以使用下列屬性將透明度明確地加入該組件：</span><span class="sxs-lookup"><span data-stu-id="7080b-183">If you want to make a whole assembly transparent to indicate that the assembly does not contain any critical code and does not elevate privileges in any way, you can explicitly add transparency to the assembly with the following attribute:</span></span>  
  
```  
[assembly: SecurityTransparent]  
```  
  
 <span data-ttu-id="7080b-184">如果您要混合相同組件中的關鍵及透明程式碼，則可以使用 <xref:System.Security.SecurityCriticalAttribute> 屬性標記該組件，表示該組件可以包含關鍵程式碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7080b-184">If you want to mix critical and transparent code in the same assembly, start by marking the assembly with the <xref:System.Security.SecurityCriticalAttribute> attribute to indicate that the assembly can contain critical code, as follows:</span></span>  
  
```  
[assembly: SecurityCritical]  
```  
  
 <span data-ttu-id="7080b-185">如果您要執行安全性關鍵動作，則必須以另一個 <xref:System.Security.SecurityCriticalAttribute> 屬性明確地標記將執行關鍵動作的程式碼，如下列程式碼範例所示：</span><span class="sxs-lookup"><span data-stu-id="7080b-185">If you want to perform security-critical actions, you must explicitly mark the code that will perform the critical action with another <xref:System.Security.SecurityCriticalAttribute> attribute, as shown in the following code example:</span></span>  
  
```  
[assembly: SecurityCritical]  
Public class A  
{  
    [SecurityCritical]  
    private void Critical()  
    {  
        // critical  
    }  
  
    public int SomeProperty  
    {  
        get {/* transparent */ }  
        set {/* transparent */ }  
    }  
}  
public class B  
{      
    internal string SomeOtherProperty  
    {  
        get { /* transparent */ }  
        set { /* transparent */ }  
    }  
}  
```  
  
 <span data-ttu-id="7080b-186">除了 `Critical` 方法 (明確標記為安全性關鍵) 之外，前述程式碼是透明程式碼。</span><span class="sxs-lookup"><span data-stu-id="7080b-186">The previous code is transparent except for the `Critical` method, which is explicitly marked as security-critical.</span></span> <span data-ttu-id="7080b-187">即使有組件層級 <xref:System.Security.SecurityCriticalAttribute> 屬性，透明度仍是預設的設定。</span><span class="sxs-lookup"><span data-stu-id="7080b-187">Transparency is the default setting, even with the assembly-level <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7080b-188">請參閱</span><span class="sxs-lookup"><span data-stu-id="7080b-188">See Also</span></span>  
 [<span data-ttu-id="7080b-189">安全性透明的程式碼，層級 2</span><span class="sxs-lookup"><span data-stu-id="7080b-189">Security-Transparent Code, Level 2</span></span>](../../../docs/framework/misc/security-transparent-code-level-2.md)  
 [<span data-ttu-id="7080b-190">安全性變更</span><span class="sxs-lookup"><span data-stu-id="7080b-190">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)
