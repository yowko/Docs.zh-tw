---
title: 安全性透明的程式碼，層級1
description: 請參閱層級1透明度程式碼模型、透明度屬性和安全性透明度範例。
ms.date: 03/30/2017
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
ms.openlocfilehash: c44fe3339f3bf24d266fa97487868ce090d51bb1
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309090"
---
# <a name="security-transparent-code-level-1"></a><span data-ttu-id="f4a94-103">安全性透明的程式碼，層級1</span><span class="sxs-lookup"><span data-stu-id="f4a94-103">Security-Transparent Code, Level 1</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="f4a94-104">透明度可協助開發人員撰寫更安全的 .NET Framework 程式庫，該程式庫會向部分信任的程式碼公開功能。</span><span class="sxs-lookup"><span data-stu-id="f4a94-104">Transparency helps developers write more secure .NET Framework libraries that expose functionality to partially trusted code.</span></span> <span data-ttu-id="f4a94-105">層級 1 透明度是在 .NET Framework 2.0 版中所引入的，而且主要只在 Microsoft 中使用。</span><span class="sxs-lookup"><span data-stu-id="f4a94-105">Level 1 transparency was introduced in the .NET Framework version 2.0 and was primarily used only within Microsoft.</span></span> <span data-ttu-id="f4a94-106">從 .NET Framework 4 開始，您可以使用[層級2透明度](security-transparent-code-level-2.md)。</span><span class="sxs-lookup"><span data-stu-id="f4a94-106">Starting with the .NET Framework 4, you can use [level 2 transparency](security-transparent-code-level-2.md).</span></span> <span data-ttu-id="f4a94-107">不過，仍然保留層級 1 透明度，讓您可以識別必須以舊版安全性規則來執行的舊版程式碼。</span><span class="sxs-lookup"><span data-stu-id="f4a94-107">However, level 1 transparency has been retained so that you can identify legacy code that must run with the earlier security rules.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f4a94-108">您應該僅針對相容性指定層級 1 透明度；也就是說，您應該僅針對使用 .NET Framework 3.5 或更早版本 (使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 或沒有使用透明度模型) 所開發的程式碼指定層級 1。</span><span class="sxs-lookup"><span data-stu-id="f4a94-108">You should specify level 1 transparency for compatibility only; that is, specify level 1 only for code that was developed with the .NET Framework 3.5 or earlier that uses the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> or does not use the transparency model.</span></span> <span data-ttu-id="f4a94-109">例如，對於允許來自部分信任呼叫端 (APTCA) 之呼叫的 .NET Framework 2.0 組件，請使用層級 1 透明度。</span><span class="sxs-lookup"><span data-stu-id="f4a94-109">For example, use level 1 transparency for .NET Framework 2.0 assemblies that allow calls from partially trusted callers (APTCA).</span></span> <span data-ttu-id="f4a94-110">針對 .NET Framework 4 所開發的程式碼，請一律使用層級2透明度。</span><span class="sxs-lookup"><span data-stu-id="f4a94-110">For code that is developed for the .NET Framework 4, always use level 2 transparency.</span></span>  
  
 <span data-ttu-id="f4a94-111">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="f4a94-111">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="f4a94-112">層級 1 透明度模型</span><span class="sxs-lookup"><span data-stu-id="f4a94-112">The Level 1 Transparency Model</span></span>](#the_level_1_transparency_model)  
  
- [<span data-ttu-id="f4a94-113">透明度屬性</span><span class="sxs-lookup"><span data-stu-id="f4a94-113">Transparency Attributes</span></span>](#transparency_attributes)  
  
- [<span data-ttu-id="f4a94-114">安全性透明度範例</span><span class="sxs-lookup"><span data-stu-id="f4a94-114">Security Transparency Examples</span></span>](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>
## <a name="the-level-1-transparency-model"></a><span data-ttu-id="f4a94-115">層級 1 透明度模型</span><span class="sxs-lookup"><span data-stu-id="f4a94-115">The Level 1 Transparency Model</span></span>  
 <span data-ttu-id="f4a94-116">當您使用層級 1 透明度時，就是使用將程式碼分為安全性透明、安全性安全關鍵和安全性關鍵方法的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="f4a94-116">When you use Level 1 transparency, you are using a security model that separates code into security-transparent, security-safe-critical, and security-critical methods.</span></span>  
  
 <span data-ttu-id="f4a94-117">您可以將整個組件、組件中的某些類別，或是類別中的某些方法標記為安全性透明。</span><span class="sxs-lookup"><span data-stu-id="f4a94-117">You can mark a whole assembly, some classes in an assembly, or some methods in a class as security-transparent.</span></span> <span data-ttu-id="f4a94-118">安全性透明程式碼無法提高權限。</span><span class="sxs-lookup"><span data-stu-id="f4a94-118">Security-transparent code cannot elevate privileges.</span></span> <span data-ttu-id="f4a94-119">這項限制有三個後果：</span><span class="sxs-lookup"><span data-stu-id="f4a94-119">This restriction has three consequences:</span></span>  
  
- <span data-ttu-id="f4a94-120">安全性透明的程式碼無法執行 <xref:System.Security.Permissions.SecurityAction.Assert> 動作。</span><span class="sxs-lookup"><span data-stu-id="f4a94-120">Security-transparent code cannot perform <xref:System.Security.Permissions.SecurityAction.Assert> actions.</span></span>  
  
- <span data-ttu-id="f4a94-121">由安全性程式碼所滿足的任何連結要求，都會變成完整的要求。</span><span class="sxs-lookup"><span data-stu-id="f4a94-121">Any link demand that would be satisfied by security-transparent code becomes a full demand.</span></span>  
  
- <span data-ttu-id="f4a94-122">必須在安全性透明程式碼中執行的任何不安全 (無法驗證) 的程式碼，都會導致 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> 安全性權限的完整要求。</span><span class="sxs-lookup"><span data-stu-id="f4a94-122">Any unsafe (unverifiable) code that must execute in security-transparent code causes a full demand for the <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> security permission.</span></span>  
  
 <span data-ttu-id="f4a94-123">這些規則是在執行期間由 Common Language Runtime (CLR) 強制執行。</span><span class="sxs-lookup"><span data-stu-id="f4a94-123">These rules are enforced during execution by the common language runtime (CLR).</span></span> <span data-ttu-id="f4a94-124">安全性透明程式碼會將它所回呼的程式碼之所有安全性需求傳遞給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="f4a94-124">Security-transparent code passes all the security requirements of the code it calls back to its callers.</span></span> <span data-ttu-id="f4a94-125">流經安全性透明程式碼的需求，無法提高權限。</span><span class="sxs-lookup"><span data-stu-id="f4a94-125">Demands that flow through the security-transparent code cannot elevate privileges.</span></span> <span data-ttu-id="f4a94-126">如果低度信任的應用程式呼叫安全性透明程式碼，並產生高權限的需求，則此需求會流回低度信任程式碼且失敗。</span><span class="sxs-lookup"><span data-stu-id="f4a94-126">If a low-trust application calls security-transparent code and causes a demand for high privilege, the demand will flow back to the low-trust code and fail.</span></span> <span data-ttu-id="f4a94-127">安全性透明程式碼無法停止此需求，因為它不能執行判斷提示動作。</span><span class="sxs-lookup"><span data-stu-id="f4a94-127">The security-transparent code cannot stop the demand because it cannot perform assert actions.</span></span> <span data-ttu-id="f4a94-128">從完全信任程式碼呼叫的同一個安全性透明程式碼，會產生成功的需求。</span><span class="sxs-lookup"><span data-stu-id="f4a94-128">The same security-transparent code called from full-trust code results in a successful demand.</span></span>  
  
 <span data-ttu-id="f4a94-129">安全性關鍵和安全性透明相反。</span><span class="sxs-lookup"><span data-stu-id="f4a94-129">Security-critical is the opposite of security-transparent.</span></span> <span data-ttu-id="f4a94-130">安全性關鍵程式碼是以完全信任方式執行，而且可以執行所有需要權限的作業。</span><span class="sxs-lookup"><span data-stu-id="f4a94-130">Security-critical code executes with full trust and can perform all privileged operations.</span></span> <span data-ttu-id="f4a94-131">安全性安全關鍵程式碼是通過廣泛安全性稽核的特權程式碼，可以確認該程式碼不會允許部分信任的呼叫端使用沒有存取權限的資源。</span><span class="sxs-lookup"><span data-stu-id="f4a94-131">Security-safe-critical code is privileged code that has been through an extensive security audit to confirm that it does not allow partially trusted callers to use resources they do not have permission to access.</span></span>  
  
 <span data-ttu-id="f4a94-132">您必須明確套用透明度。</span><span class="sxs-lookup"><span data-stu-id="f4a94-132">You have to apply transparency explicitly.</span></span> <span data-ttu-id="f4a94-133">處理資料操作與邏輯的大部分程式碼通常可以標記為安全性透明，而執行權限提高的小部分程式碼則可標記為安全性關鍵或安全性安全關鍵。</span><span class="sxs-lookup"><span data-stu-id="f4a94-133">The majority of your code that handles data manipulation and logic can typically be marked as security-transparent, whereas the lesser amount of code that performs elevations of privileges is marked as security-critical or security-safe-critical.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f4a94-134">層級 1 透明度受限於組件範圍；這在組件之間沒有強制執行。</span><span class="sxs-lookup"><span data-stu-id="f4a94-134">Level 1 transparency is limited to assembly scope; it is not enforced between assemblies.</span></span> <span data-ttu-id="f4a94-135">層級 1 透明度主要用於 Microsoft 內部進行安全性稽核。</span><span class="sxs-lookup"><span data-stu-id="f4a94-135">Level 1 transparency was primarily used within Microsoft for security audit purposes.</span></span> <span data-ttu-id="f4a94-136">層級 1 組件內的安全性關鍵類型和成員可以由其他組件中的安全性透明程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="f4a94-136">Security-critical types and members within a level 1 assembly can be accessed by security-transparent code in other assemblies.</span></span> <span data-ttu-id="f4a94-137">請務必在所有層級 1 安全性關鍵類型和成員中執行完全信任的連結要求。</span><span class="sxs-lookup"><span data-stu-id="f4a94-137">It is important that you perform link demands for full trust in all your level 1 security-critical types and members.</span></span> <span data-ttu-id="f4a94-138">安全性安全關鍵類型和成員還必須確認，對於由類型或成員所存取的受保護資源，呼叫端必須擁有權限。</span><span class="sxs-lookup"><span data-stu-id="f4a94-138">Security-safe-critical types and members must also confirm that callers have permissions for protected resources that are accessed by the type or member.</span></span>  
  
 <span data-ttu-id="f4a94-139">為了與舊版 .NET Framework 回溯相容，會將所有未以透明度屬性標註的成員視為安全性安全關鍵。</span><span class="sxs-lookup"><span data-stu-id="f4a94-139">For backward compatibility with earlier versions of the .NET Framework, all members that are not annotated with transparency attributes are considered to be security-safe-critical.</span></span> <span data-ttu-id="f4a94-140">會將所有未標註的類型都視為透明。</span><span class="sxs-lookup"><span data-stu-id="f4a94-140">All types that are not annotated are considered to be transparent.</span></span> <span data-ttu-id="f4a94-141">沒有任何靜態分析規則可以用來驗證透明度。</span><span class="sxs-lookup"><span data-stu-id="f4a94-141">There are no static analysis rules to validate transparency.</span></span> <span data-ttu-id="f4a94-142">因此，您可能需要在執行階段偵錯透明度錯誤。</span><span class="sxs-lookup"><span data-stu-id="f4a94-142">Therefore, you may need to debug transparency errors at run time.</span></span>  
  
<a name="transparency_attributes"></a>
## <a name="transparency-attributes"></a><span data-ttu-id="f4a94-143">透明度屬性</span><span class="sxs-lookup"><span data-stu-id="f4a94-143">Transparency Attributes</span></span>  
 <span data-ttu-id="f4a94-144">下表說明您可以用來標註程式碼透明度的三個屬性。</span><span class="sxs-lookup"><span data-stu-id="f4a94-144">The following table describes the three attributes that you use to annotate your code for transparency.</span></span>  
  
|<span data-ttu-id="f4a94-145">屬性</span><span class="sxs-lookup"><span data-stu-id="f4a94-145">Attribute</span></span>|<span data-ttu-id="f4a94-146">描述</span><span class="sxs-lookup"><span data-stu-id="f4a94-146">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|<span data-ttu-id="f4a94-147">僅在該組件層級受允許。</span><span class="sxs-lookup"><span data-stu-id="f4a94-147">Allowed only at the assembly level.</span></span> <span data-ttu-id="f4a94-148">將該組件中的所有類型和成員都識別為安全性透明。</span><span class="sxs-lookup"><span data-stu-id="f4a94-148">Identifies all types and members in the assembly as security-transparent.</span></span> <span data-ttu-id="f4a94-149">該組件不能包含任何安全性關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="f4a94-149">The assembly cannot contain any security-critical code.</span></span>|  
|<xref:System.Security.SecurityCriticalAttribute>|<span data-ttu-id="f4a94-150">在無 <xref:System.Security.SecurityCriticalAttribute.Scope%2A> 屬性的組件層級使用時，根據預設，會將組件中的所有程式碼識別為安全性透明，但也表示該組件可能包含安全性關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="f4a94-150">When used at the assembly level without the <xref:System.Security.SecurityCriticalAttribute.Scope%2A> property, identifies all code in the assembly as security-transparent by default, but indicates that the assembly may contain security-critical code.</span></span><br /><br /> <span data-ttu-id="f4a94-151">在類別層級使用時，會將類別或方法識別為安全性關鍵，而不是識別類別的成員。</span><span class="sxs-lookup"><span data-stu-id="f4a94-151">When used at the class level, identifies the class or method as security-critical, but not the members of the class.</span></span> <span data-ttu-id="f4a94-152">若要將所有成員都設成安全性關鍵，請將 <xref:System.Security.SecurityCriticalAttribute.Scope%2A> 屬性設為 <xref:System.Security.SecurityCriticalScope.Everything>。 </span><span class="sxs-lookup"><span data-stu-id="f4a94-152">To make all the members security-critical, set the <xref:System.Security.SecurityCriticalAttribute.Scope%2A> property to <xref:System.Security.SecurityCriticalScope.Everything>.</span></span><br /><br /> <span data-ttu-id="f4a94-153">在成員層級使用時，該屬性只適用於該成員。</span><span class="sxs-lookup"><span data-stu-id="f4a94-153">When used at the member level, the attribute applies only to that member.</span></span><br /><br /> <span data-ttu-id="f4a94-154">已識別為安全性關鍵的類別或成員可以執行權限提高。</span><span class="sxs-lookup"><span data-stu-id="f4a94-154">The class or member identified as security-critical can perform elevations of privilege.</span></span> <span data-ttu-id="f4a94-155">**重要事項：** 在層級1透明度中，從元件外部呼叫安全性關鍵類型和成員時，會將其視為安全性安全關鍵。</span><span class="sxs-lookup"><span data-stu-id="f4a94-155">**Important:**  In level 1 transparency, security-critical types and members are treated as security-safe-critical when they are called from outside the assembly.</span></span> <span data-ttu-id="f4a94-156">您應該使用完全信任的連結要求來保護安全性關鍵類型和成員，以避免未經授權的權限提高。</span><span class="sxs-lookup"><span data-stu-id="f4a94-156">You should protect security-critical types and members with a link demand for full trust to avoid unauthorized elevation of privilege.</span></span>|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|<span data-ttu-id="f4a94-157">識別可以由組件中安全性透明程式碼存取的安全性關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="f4a94-157">Identifies security-critical code that can be accessed by security-transparent code in the assembly.</span></span> <span data-ttu-id="f4a94-158">否則安全性透明程式碼無法存取相同組件中的私用或內部安全性關鍵成員。</span><span class="sxs-lookup"><span data-stu-id="f4a94-158">Otherwise, security-transparent code cannot access private or internal security-critical members in the same assembly.</span></span> <span data-ttu-id="f4a94-159">這麼做會影響安全性關鍵程式碼，並可能造成非預期的權限提高。</span><span class="sxs-lookup"><span data-stu-id="f4a94-159">Doing so would influence security-critical code and make unexpected elevations of privilege possible.</span></span> <span data-ttu-id="f4a94-160">安全性安全關鍵程式碼應該經過嚴密的安全性稽核。</span><span class="sxs-lookup"><span data-stu-id="f4a94-160">Security-safe-critical code should undergo a rigorous security audit.</span></span> <span data-ttu-id="f4a94-161">**注意：** 安全性安全關鍵類型和成員必須驗證呼叫端的許可權，以判斷呼叫端是否具有存取受保護資源的授權。</span><span class="sxs-lookup"><span data-stu-id="f4a94-161">**Note:**  Security-safe-critical types and members must validate the permissions of callers to determine whether the caller has authority to access protected resources.</span></span>|  
  
 <span data-ttu-id="f4a94-162"><xref:System.Security.SecuritySafeCriticalAttribute> 屬性可以讓安全性透明程式碼存取相同組件中安全性關鍵的成員。</span><span class="sxs-lookup"><span data-stu-id="f4a94-162">The <xref:System.Security.SecuritySafeCriticalAttribute> attribute enables security-transparent code to access security-critical members in the same assembly.</span></span> <span data-ttu-id="f4a94-163">請考慮將組件中的安全性透明及安全性關鍵程式碼區分成兩個組件。</span><span class="sxs-lookup"><span data-stu-id="f4a94-163">Consider the security-transparent and security-critical code in your assembly as separated into two assemblies.</span></span> <span data-ttu-id="f4a94-164">安全性透明程式碼無法查看安全性關鍵程式碼的私用或內部成員。</span><span class="sxs-lookup"><span data-stu-id="f4a94-164">The security-transparent code would not be able to see the private or internal members of the security-critical code.</span></span> <span data-ttu-id="f4a94-165">此外，安全性關鍵程式碼一般是為了存取公用介面而受稽核的。</span><span class="sxs-lookup"><span data-stu-id="f4a94-165">Additionally, the security-critical code is generally audited for access to its public interface.</span></span> <span data-ttu-id="f4a94-166">您可能不希望私用或內部狀態在組件外還能存取；您可能想要讓狀態保持隔離。</span><span class="sxs-lookup"><span data-stu-id="f4a94-166">You would not expect a private or internal state to be accessible outside the assembly; you would want to keep the state isolated.</span></span> <span data-ttu-id="f4a94-167"><xref:System.Security.SecuritySafeCriticalAttribute> 屬性會維護安全性透明與安全性關鍵程式碼之間的狀態隔離，但是可在必要時提供覆寫隔離的功能。</span><span class="sxs-lookup"><span data-stu-id="f4a94-167">The <xref:System.Security.SecuritySafeCriticalAttribute> attribute maintains the isolation of state between security-transparent and security-critical code while providing the ability to override the isolation when it is necessary.</span></span> <span data-ttu-id="f4a94-168">安全性透明程式碼無法存取私用或內部安全性關鍵程式碼，除非那些成員已經以 <xref:System.Security.SecuritySafeCriticalAttribute> 標記。</span><span class="sxs-lookup"><span data-stu-id="f4a94-168">Security-transparent code cannot access private or internal security-critical code unless those members have been marked with <xref:System.Security.SecuritySafeCriticalAttribute>.</span></span> <span data-ttu-id="f4a94-169">套用 <xref:System.Security.SecuritySafeCriticalAttribute> 之前，請先將成員視為已公開並加以稽核。</span><span class="sxs-lookup"><span data-stu-id="f4a94-169">Before applying the <xref:System.Security.SecuritySafeCriticalAttribute>, audit that member as if it were publicly exposed.</span></span>  
  
### <a name="assembly-wide-annotation"></a><span data-ttu-id="f4a94-170">組件範圍的註釋</span><span class="sxs-lookup"><span data-stu-id="f4a94-170">Assembly-wide Annotation</span></span>  
 <span data-ttu-id="f4a94-171">下表說明在組件層級中使用安全性屬性的效果。</span><span class="sxs-lookup"><span data-stu-id="f4a94-171">The following table describes the effects of using security attributes at the assembly level.</span></span>  
  
|<span data-ttu-id="f4a94-172">組件屬性</span><span class="sxs-lookup"><span data-stu-id="f4a94-172">Assembly attribute</span></span>|<span data-ttu-id="f4a94-173">組件狀態</span><span class="sxs-lookup"><span data-stu-id="f4a94-173">Assembly state</span></span>|  
|------------------------|--------------------|  
|<span data-ttu-id="f4a94-174">部分信任組件無屬性</span><span class="sxs-lookup"><span data-stu-id="f4a94-174">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="f4a94-175">所有類型和成員皆為透明的。</span><span class="sxs-lookup"><span data-stu-id="f4a94-175">All types and members are transparent.</span></span>|  
|<span data-ttu-id="f4a94-176">在完全信任組件上沒有屬性 (在全域組件快取中或在 `AppDomain` 中識別為完全信任)</span><span class="sxs-lookup"><span data-stu-id="f4a94-176">No attribute on a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`)</span></span>|<span data-ttu-id="f4a94-177">所有類型為透明，且所有成員為安全性安全關鍵。</span><span class="sxs-lookup"><span data-stu-id="f4a94-177">All types are transparent and all members are security-safe-critical.</span></span>|  
|`SecurityTransparent`|<span data-ttu-id="f4a94-178">所有類型和成員皆為透明的。</span><span class="sxs-lookup"><span data-stu-id="f4a94-178">All types and members are transparent.</span></span>|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="f4a94-179">所有類型和成員皆為安全性關鍵的。</span><span class="sxs-lookup"><span data-stu-id="f4a94-179">All types and members are security-critical.</span></span>|  
|`SecurityCritical`|<span data-ttu-id="f4a94-180">所有程式碼都預設為透明的。</span><span class="sxs-lookup"><span data-stu-id="f4a94-180">All code defaults to transparent.</span></span> <span data-ttu-id="f4a94-181">不過，個別的類型和成員可以有其他屬性。</span><span class="sxs-lookup"><span data-stu-id="f4a94-181">However, individual types and members can have other attributes.</span></span>|  
  
<a name="security_transparency_examples"></a>
## <a name="security-transparency-examples"></a><span data-ttu-id="f4a94-182">安全性透明度範例</span><span class="sxs-lookup"><span data-stu-id="f4a94-182">Security Transparency Examples</span></span>  
 <span data-ttu-id="f4a94-183">若要使用 .NET Framework 2.0 透明度規則 (層級 1 透明度)，請使用下列組件註釋：</span><span class="sxs-lookup"><span data-stu-id="f4a94-183">To use the .NET Framework 2.0 transparency rules (level 1 transparency), use the following assembly annotation:</span></span>  
  
```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 <span data-ttu-id="f4a94-184">如果您要使整個組件透明，來表示該組件不含任何關鍵程式碼，而且在任何情況下都不提高權限，則可以使用下列屬性將透明度明確地加入該組件：</span><span class="sxs-lookup"><span data-stu-id="f4a94-184">If you want to make a whole assembly transparent to indicate that the assembly does not contain any critical code and does not elevate privileges in any way, you can explicitly add transparency to the assembly with the following attribute:</span></span>  
  
```csharp  
[assembly: SecurityTransparent]  
```  
  
 <span data-ttu-id="f4a94-185">如果您要混合相同組件中的關鍵及透明程式碼，則可以使用 <xref:System.Security.SecurityCriticalAttribute> 屬性標記該組件，表示該組件可以包含關鍵程式碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f4a94-185">If you want to mix critical and transparent code in the same assembly, start by marking the assembly with the <xref:System.Security.SecurityCriticalAttribute> attribute to indicate that the assembly can contain critical code, as follows:</span></span>  
  
```csharp  
[assembly: SecurityCritical]  
```  
  
 <span data-ttu-id="f4a94-186">如果您要執行安全性關鍵動作，則必須以另一個 <xref:System.Security.SecurityCriticalAttribute> 屬性明確地標記將執行關鍵動作的程式碼，如下列程式碼範例所示：</span><span class="sxs-lookup"><span data-stu-id="f4a94-186">If you want to perform security-critical actions, you must explicitly mark the code that will perform the critical action with another <xref:System.Security.SecurityCriticalAttribute> attribute, as shown in the following code example:</span></span>  
  
```csharp  
[assembly: SecurityCritical]  
public class A  
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
  
 <span data-ttu-id="f4a94-187">除了 `Critical` 方法 (明確標記為安全性關鍵) 之外，前述程式碼是透明程式碼。</span><span class="sxs-lookup"><span data-stu-id="f4a94-187">The previous code is transparent except for the `Critical` method, which is explicitly marked as security-critical.</span></span> <span data-ttu-id="f4a94-188">即使有組件層級 <xref:System.Security.SecurityCriticalAttribute> 屬性，透明度仍是預設的設定。</span><span class="sxs-lookup"><span data-stu-id="f4a94-188">Transparency is the default setting, even with the assembly-level <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4a94-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4a94-189">See also</span></span>

- [<span data-ttu-id="f4a94-190">安全性透明的程式碼，層級 2</span><span class="sxs-lookup"><span data-stu-id="f4a94-190">Security-Transparent Code, Level 2</span></span>](security-transparent-code-level-2.md)
- [<span data-ttu-id="f4a94-191">安全性變更</span><span class="sxs-lookup"><span data-stu-id="f4a94-191">Security Changes</span></span>](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
