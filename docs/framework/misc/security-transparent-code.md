---
title: 安全性透明的程式碼
ms.date: 03/30/2017
helpviewer_keywords:
- transparent code
- security-transparent code
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4e4e472185b3b2ba39393c029bca3966fb5ec4b3
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206049"
---
# <a name="security-transparent-code"></a><span data-ttu-id="6d43d-102">安全性透明的程式碼</span><span class="sxs-lookup"><span data-stu-id="6d43d-102">Security-Transparent Code</span></span>

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="6d43d-103">安全性牽涉到三個互動式的部分：沙箱、權限與強化。</span><span class="sxs-lookup"><span data-stu-id="6d43d-103">Security involves three interacting pieces: sandboxing, permissions, and enforcement.</span></span> <span data-ttu-id="6d43d-104">沙箱是指建立隔離定義域的做法，其中將某些程式碼視為完全信任，且限制其他程式碼為沙箱授權集中的權限。</span><span class="sxs-lookup"><span data-stu-id="6d43d-104">Sandboxing refers to the practice of creating isolated domains where some code is treated as fully trusted and other code is restricted to the permissions in the grant set for the sandbox.</span></span> <span data-ttu-id="6d43d-105">在沙箱授權集內部執行的應用程式程式碼會被視為透明的。也就是說，它無法執行任何可能會影響安全性的作業。</span><span class="sxs-lookup"><span data-stu-id="6d43d-105">The application code that runs within the grant set of the sandbox is considered to be transparent; that is, it cannot perform any operations that can affect security.</span></span> <span data-ttu-id="6d43d-106">沙箱授權集是依照辨識項 (<xref:System.Security.Policy.Evidence> 類別) 決定的。</span><span class="sxs-lookup"><span data-stu-id="6d43d-106">The grant set for the sandbox is determined by evidence (<xref:System.Security.Policy.Evidence> class).</span></span> <span data-ttu-id="6d43d-107">辨識項會識別沙箱所需的特定權限，以及可建立的沙箱種類。</span><span class="sxs-lookup"><span data-stu-id="6d43d-107">Evidence identifies what specific permissions are required by sandboxes, and what kinds of sandboxes can be created.</span></span> <span data-ttu-id="6d43d-108">強化是指讓透明程式碼只能在其授權集內部執行。</span><span class="sxs-lookup"><span data-stu-id="6d43d-108">Enforcement refers to allowing transparent code to execute only within its grant set.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d43d-109">安全性原則是舊版 .NET Framework 中的重要項目。</span><span class="sxs-lookup"><span data-stu-id="6d43d-109">Security policy was a key element in previous versions of the .NET Framework.</span></span> <span data-ttu-id="6d43d-110">從 .NET Framework 4 開始, 安全性原則已經過時。</span><span class="sxs-lookup"><span data-stu-id="6d43d-110">Starting with the .NET Framework 4, security policy is obsolete.</span></span> <span data-ttu-id="6d43d-111">安全性原則的刪除獨立於安全性透明規則。</span><span class="sxs-lookup"><span data-stu-id="6d43d-111">The elimination of security policy is separate from security transparency.</span></span> <span data-ttu-id="6d43d-112">如需這項變更之影響的詳細資訊, 請參閱[代碼啟用安全性原則相容性和遷移](code-access-security-policy-compatibility-and-migration.md)。</span><span class="sxs-lookup"><span data-stu-id="6d43d-112">For information about the effects of this change, see [Code Access Security Policy Compatibility and Migration](code-access-security-policy-compatibility-and-migration.md).</span></span>

<span data-ttu-id="6d43d-113">本主題將詳細描述透明度模型。</span><span class="sxs-lookup"><span data-stu-id="6d43d-113">This topic describes the transparency model in more detail.</span></span> <span data-ttu-id="6d43d-114">它包含以下各節：</span><span class="sxs-lookup"><span data-stu-id="6d43d-114">It contains the following sections:</span></span>

- [<span data-ttu-id="6d43d-115">透明度模型的用途</span><span class="sxs-lookup"><span data-stu-id="6d43d-115">Purpose of the Transparency Model</span></span>](#purpose)

- [<span data-ttu-id="6d43d-116">指定透明度層級</span><span class="sxs-lookup"><span data-stu-id="6d43d-116">Specifying the Transparency Level</span></span>](#level)

- [<span data-ttu-id="6d43d-117">透明度強制</span><span class="sxs-lookup"><span data-stu-id="6d43d-117">Transparency Enforcement</span></span>](#enforcement)

<a name="purpose"></a>

## <a name="purpose-of-the-transparency-model"></a><span data-ttu-id="6d43d-118">透明度模型的用途</span><span class="sxs-lookup"><span data-stu-id="6d43d-118">Purpose of the Transparency Model</span></span>

<span data-ttu-id="6d43d-119">透明度是一種強化機制，將當做應用程式一部分執行的程式碼與當做基礎結構一部分執行的程式碼分隔。</span><span class="sxs-lookup"><span data-stu-id="6d43d-119">Transparency is an enforcement mechanism that separates code that runs as part of the application from code that runs as part of the infrastructure.</span></span> <span data-ttu-id="6d43d-120">透明度在可以執行授權事項 (例如呼叫機器碼) 的程式碼 (關鍵程式碼) 和不能執行授權事項的程式碼 (透明程式碼) 之間畫出了一條界線。</span><span class="sxs-lookup"><span data-stu-id="6d43d-120">Transparency draws a barrier between code that can do privileged things (critical code), such as calling native code, and code that cannot (transparent code).</span></span> <span data-ttu-id="6d43d-121">透明程式碼可以在其運作的權限集合界限內執行命令，但是無法執行、衍生自關鍵程式碼或包含關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d43d-121">Transparent code can execute commands within the bounds of the permission set it is operating in, but cannot execute, derive from, or contain critical code.</span></span>

<span data-ttu-id="6d43d-122">透明度強化的主要目標是提供簡單、有效率的機制，依據權限來隔離不同程式碼群組。</span><span class="sxs-lookup"><span data-stu-id="6d43d-122">The primary goal of transparency enforcement is to provide a simple, effective mechanism for isolating different groups of code based on privilege.</span></span> <span data-ttu-id="6d43d-123">在沙箱模型的內容中，這些權限群組為完全信任 (也就是不受限制) 或部分信任 (也就是限制為授與沙箱的權限集合)。</span><span class="sxs-lookup"><span data-stu-id="6d43d-123">Within the context of the sandboxing model, these privilege groups are either fully trusted (that is, not restricted) or partially trusted (that is, restricted to the permission set granted to the sandbox).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d43d-124">透明度模型超越了程式碼存取安全性。</span><span class="sxs-lookup"><span data-stu-id="6d43d-124">The transparency model transcends code access security.</span></span> <span data-ttu-id="6d43d-125">透明度是由 Just-In-Time 編譯器強制執行，而且保持有效，不論組件的授權集為何 (包含完全信任)。</span><span class="sxs-lookup"><span data-stu-id="6d43d-125">Transparency is enforced by the just-in-time compiler and remains in effect regardless of the grant set for an assembly, including full trust.</span></span>

<span data-ttu-id="6d43d-126">透明度是在 .NET Framework 2.0 版所引入的，以簡化安全性模型，並且讓您更輕鬆地撰寫和部署安全程式庫與應用程式。</span><span class="sxs-lookup"><span data-stu-id="6d43d-126">Transparency was introduced in the .NET Framework version 2.0 to simplify the security model, and to make it easier to write and deploy secure libraries and applications.</span></span> <span data-ttu-id="6d43d-127">Microsoft Silverlight 中也使用了透明程式碼，以簡化部分信任應用程式的開發。</span><span class="sxs-lookup"><span data-stu-id="6d43d-127">Transparent code is also used in Microsoft Silverlight, to simplify the development of partially trusted applications.</span></span>

> [!NOTE]
> <span data-ttu-id="6d43d-128">當您開發部分信任應用程式時，必須注意目標主機的權限需求。</span><span class="sxs-lookup"><span data-stu-id="6d43d-128">When you develop a partially trusted application, you have to be aware of the permission requirements for your target hosts.</span></span> <span data-ttu-id="6d43d-129">您可以開發使用某些主機不允許之資源的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6d43d-129">You can develop an application that uses resources that are not allowed by some hosts.</span></span> <span data-ttu-id="6d43d-130">雖然這種應用程式在編譯時不會發生任何錯誤，不過在將它載入裝載環境時，就會失敗。</span><span class="sxs-lookup"><span data-stu-id="6d43d-130">This application will compile without error, but will fail when it is loaded into the hosted environment.</span></span> <span data-ttu-id="6d43d-131">如果您已經使用 Visual Studio 開發應用程式，就可以在來自開發環境的部分信任或受限制的權限集合中啟用偵錯。</span><span class="sxs-lookup"><span data-stu-id="6d43d-131">If you have developed your application using Visual Studio, you can enable debugging in partial trust or in a restricted permission set from the development environment.</span></span> <span data-ttu-id="6d43d-132">如需詳細資訊，請參閱[如何：以受限制的權限對 ClickOnce 應用程式進行偵錯](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions)。</span><span class="sxs-lookup"><span data-stu-id="6d43d-132">For more information, see [How to: Debug a ClickOnce Application with Restricted Permissions](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions).</span></span> <span data-ttu-id="6d43d-133">提供給 ClickOnce 應用程式的「計算使用權限」功能也可用於任何部分信任的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6d43d-133">The Calculate Permissions feature provided for ClickOnce applications is also available for any partially trusted application.</span></span>

[<span data-ttu-id="6d43d-134">回到頁首</span><span class="sxs-lookup"><span data-stu-id="6d43d-134">Back to top</span></span>](#top)

<a name="level"></a>

## <a name="specifying-the-transparency-level"></a><span data-ttu-id="6d43d-135">指定透明度層級</span><span class="sxs-lookup"><span data-stu-id="6d43d-135">Specifying the Transparency Level</span></span>

<span data-ttu-id="6d43d-136">組件層級的 <xref:System.Security.SecurityRulesAttribute> 屬性會明確選取該組件將遵循的 <xref:System.Security.SecurityRuleSet> 規則。</span><span class="sxs-lookup"><span data-stu-id="6d43d-136">The assembly-level <xref:System.Security.SecurityRulesAttribute> attribute explicitly selects the <xref:System.Security.SecurityRuleSet> rules that the assembly will follow.</span></span> <span data-ttu-id="6d43d-137">這些規則會在數值層級系統下受組織，其中較高層級表示會比較嚴格地強制執行安全性規則。</span><span class="sxs-lookup"><span data-stu-id="6d43d-137">The rules are organized under a numeric level system, where higher levels mean tighter enforcement of security rules.</span></span>

<span data-ttu-id="6d43d-138">這些層級如下所示：</span><span class="sxs-lookup"><span data-stu-id="6d43d-138">The levels are as follows:</span></span>

- <span data-ttu-id="6d43d-139">層級 2<xref:System.Security.SecurityRuleSet.Level2>() – .NET Framework 4 透明度規則。</span><span class="sxs-lookup"><span data-stu-id="6d43d-139">Level 2 (<xref:System.Security.SecurityRuleSet.Level2>) – the .NET Framework 4 transparency rules.</span></span>

- <span data-ttu-id="6d43d-140">層級 1 (<xref:System.Security.SecurityRuleSet.Level1>) – .NET Framework 2.0 透明度規則。</span><span class="sxs-lookup"><span data-stu-id="6d43d-140">Level 1 (<xref:System.Security.SecurityRuleSet.Level1>) – the .NET Framework 2.0 transparency rules.</span></span>

<span data-ttu-id="6d43d-141">這兩個透明度層級之間的主要差異在於，層級 1 不會針對組件外部的呼叫強制執行透明度規則，而且這主要是為了相容性而使用。</span><span class="sxs-lookup"><span data-stu-id="6d43d-141">The primary difference between the two transparency levels is that level 1 does not enforce transparency rules for calls from outside the assembly and is intended only for compatibility.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d43d-142">您應該僅針對相容性指定層級 1 透明度；也就是說，您應該僅針對使用 .NET Framework 3.5 或更早版本 (使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 屬性或沒有使用透明度模型) 所開發的程式碼指定層級 1。</span><span class="sxs-lookup"><span data-stu-id="6d43d-142">You should specify level 1 transparency for compatibility only; that is, specify level 1 only for code that was developed with the .NET Framework 3.5 or earlier that uses the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute or does not use the transparency model.</span></span> <span data-ttu-id="6d43d-143">例如，對於允許來自部分信任呼叫端 (APTCA) 之呼叫的 .NET Framework 2.0 組件，請使用層級 1 透明度。</span><span class="sxs-lookup"><span data-stu-id="6d43d-143">For example, use level 1 transparency for .NET Framework 2.0 assemblies that allow calls from partially trusted callers (APTCA).</span></span> <span data-ttu-id="6d43d-144">針對 .NET Framework 4 所開發的程式碼, 請一律使用層級2透明度。</span><span class="sxs-lookup"><span data-stu-id="6d43d-144">For code that is developed for the .NET Framework 4, always use level 2 transparency.</span></span>

### <a name="level-2-transparency"></a><span data-ttu-id="6d43d-145">層級 2 透明度</span><span class="sxs-lookup"><span data-stu-id="6d43d-145">Level 2 Transparency</span></span>

<span data-ttu-id="6d43d-146">層級2透明度是在 .NET Framework 4 中引進。</span><span class="sxs-lookup"><span data-stu-id="6d43d-146">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="6d43d-147">此模型的三個原則是透明程式碼、安全性安全關鍵程式碼和安全性關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d43d-147">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="6d43d-148">不論授與給透明程式碼的權限為何 (包含完全信任)，透明程式碼只能呼叫其他透明程式碼或安全性安全關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d43d-148">Transparent code, regardless of the permissions it is granted (including full trust), can call only other transparent code or security-safe-critical code.</span></span> <span data-ttu-id="6d43d-149">如果此程式碼受到部分信任，就只能執行該定義域之權限集合所允許的動作。</span><span class="sxs-lookup"><span data-stu-id="6d43d-149">If the code is partially trusted, it can only perform actions that are allowed by the domain’s permission set.</span></span> <span data-ttu-id="6d43d-150">透明程式碼無法進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="6d43d-150">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="6d43d-151">執行 <xref:System.Security.CodeAccessPermission.Assert%2A> 作業或提高權限。</span><span class="sxs-lookup"><span data-stu-id="6d43d-151">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> operation or elevation of privilege.</span></span>

  - <span data-ttu-id="6d43d-152">包含不安全或無法驗證的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d43d-152">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="6d43d-153">直接呼叫關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d43d-153">Directly call critical code.</span></span>

  - <span data-ttu-id="6d43d-154">呼叫機器碼或含有 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d43d-154">Call native code or code that has the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="6d43d-155">呼叫 <xref:System.Security.Permissions.SecurityAction.LinkDemand> 所保護的成員。</span><span class="sxs-lookup"><span data-stu-id="6d43d-155">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="6d43d-156">繼承自關鍵類型。</span><span class="sxs-lookup"><span data-stu-id="6d43d-156">Inherit from critical types.</span></span>

    <span data-ttu-id="6d43d-157">此外，透明方法無法覆寫關鍵虛擬方法或實作關鍵介面方法。</span><span class="sxs-lookup"><span data-stu-id="6d43d-157">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="6d43d-158">安全性安全關鍵程式碼受到完全信任，但是可由透明程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="6d43d-158">Security-safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="6d43d-159">它會公開完全信任程式碼的有限介面區。</span><span class="sxs-lookup"><span data-stu-id="6d43d-159">It exposes a limited surface area of full-trust code.</span></span> <span data-ttu-id="6d43d-160">正確性和安全性驗證會在安全關鍵程式碼中進行。</span><span class="sxs-lookup"><span data-stu-id="6d43d-160">Correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="6d43d-161">雖然安全性關鍵程式碼可以呼叫任何程式碼，而且受到完全信任，但是無法由透明程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="6d43d-161">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

### <a name="level-1-transparency"></a><span data-ttu-id="6d43d-162">層級 1 透明度</span><span class="sxs-lookup"><span data-stu-id="6d43d-162">Level 1 Transparency</span></span>

<span data-ttu-id="6d43d-163">層級 1 透明度模型是在 .NET Framework 2.0 版中所引入的，可讓開發人員減少受限於安全性稽核的程式碼數量。</span><span class="sxs-lookup"><span data-stu-id="6d43d-163">The level 1 transparency model was introduced in the .NET Framework version 2.0 to enable developers to reduce the amount of code that is subject to a security audit.</span></span> <span data-ttu-id="6d43d-164">雖然層級 1 透明度可公開使用於 2.0 版中，不過它主要是針對安全性稽核的用途，於 Microsoft 中所使用。</span><span class="sxs-lookup"><span data-stu-id="6d43d-164">Although level 1 transparency was publicly available in version 2.0, it was primarily used only within Microsoft for security auditing purposes.</span></span> <span data-ttu-id="6d43d-165">開發人員可以透過註釋宣告哪些類型和成員可以提高安全性和執行其他受信任動作 (安全性關鍵)，以及哪些類型和成員無法執行這些作業 (安全性透明)。</span><span class="sxs-lookup"><span data-stu-id="6d43d-165">Through annotations, developers are able to declare which types and members can perform security elevations and other trusted actions (security-critical) and which cannot (security-transparent).</span></span> <span data-ttu-id="6d43d-166">識別為透明的程式碼不需要高階安全性稽核。</span><span class="sxs-lookup"><span data-stu-id="6d43d-166">Code that is identified as transparent does not require a high degree of security auditing.</span></span> <span data-ttu-id="6d43d-167">層級 1 透明度指出透明度強制執行已限制於組件內部。</span><span class="sxs-lookup"><span data-stu-id="6d43d-167">Level 1 transparency states that the transparency enforcement is limited to within the assembly.</span></span> <span data-ttu-id="6d43d-168">換句話說，識別為安全性關鍵的任何公用類型或成員只在組件內部為安全性關鍵的。</span><span class="sxs-lookup"><span data-stu-id="6d43d-168">In other words, any public types or members that are identified as security-critical are security-critical only within the assembly.</span></span> <span data-ttu-id="6d43d-169">從組件外部呼叫這些類型和成員時，如果您想要針對它們強制執行安全性，就必須使用完全信任的連結要求。</span><span class="sxs-lookup"><span data-stu-id="6d43d-169">If you want to enforce security for those types and members when they are called from outside the assembly, you must use link demands for full trust.</span></span> <span data-ttu-id="6d43d-170">如果您沒有這樣做，就會將公開可見的安全性關鍵類型和成員視為安全性安全關鍵的，而且可由組件外部的部分信任程式碼所呼叫。</span><span class="sxs-lookup"><span data-stu-id="6d43d-170">If you do not, publicly visible security-critical types and members are treated as security-safe-critical and can be called by partially trusted code outside the assembly.</span></span>

<span data-ttu-id="6d43d-171">層級 1 透明度模型具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="6d43d-171">The level 1 transparency model has the following limitations:</span></span>

- <span data-ttu-id="6d43d-172">公用的安全性關鍵類型和成員可從安全性透明程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="6d43d-172">Security-critical types and members that are public are accessible from security-transparent code.</span></span>

- <span data-ttu-id="6d43d-173">透明度註釋只在組件內部強制執行。</span><span class="sxs-lookup"><span data-stu-id="6d43d-173">The transparency annotations are enforced only within an assembly.</span></span>

- <span data-ttu-id="6d43d-174">安全性關鍵類型和成員必須使用連結要求，針對來自組件外部的呼叫強制執行安全性。</span><span class="sxs-lookup"><span data-stu-id="6d43d-174">Security-critical types and members must use link demands to enforce security for calls from outside the assembly.</span></span>

- <span data-ttu-id="6d43d-175">繼承規則不會強制執行。</span><span class="sxs-lookup"><span data-stu-id="6d43d-175">Inheritance rules are not enforced.</span></span>

- <span data-ttu-id="6d43d-176">在完全信任中執行時，透明程式碼有可能會執行有害的事。</span><span class="sxs-lookup"><span data-stu-id="6d43d-176">The potential exists for transparent code to do harmful things when run in full trust.</span></span>

[<span data-ttu-id="6d43d-177">回到頁首</span><span class="sxs-lookup"><span data-stu-id="6d43d-177">Back to top</span></span>](#top)

<a name="enforcement"></a>

## <a name="transparency-enforcement"></a><span data-ttu-id="6d43d-178">透明度強化</span><span class="sxs-lookup"><span data-stu-id="6d43d-178">Transparency Enforcement</span></span>

<span data-ttu-id="6d43d-179">透明度規則會等到計算出透明度之後才會強制執行。</span><span class="sxs-lookup"><span data-stu-id="6d43d-179">Transparency rules are not enforced until transparency is calculated.</span></span> <span data-ttu-id="6d43d-180">此時，如果違反了透明度規則，就會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="6d43d-180">At that time, an <xref:System.InvalidOperationException> is thrown if a transparency rule is violated.</span></span> <span data-ttu-id="6d43d-181">計算透明度的時間取決於多個因素，而且無法預測。</span><span class="sxs-lookup"><span data-stu-id="6d43d-181">The time that transparency is calculated depends on multiple factors and cannot be predicted.</span></span> <span data-ttu-id="6d43d-182">透明度的計算會盡可能延後。</span><span class="sxs-lookup"><span data-stu-id="6d43d-182">It is calculated as late as possible.</span></span> <span data-ttu-id="6d43d-183">在 .NET Framework 4 中, 元件層級的透明度計算會比在 .NET Framework 2.0 中更早發生。</span><span class="sxs-lookup"><span data-stu-id="6d43d-183">In the .NET Framework 4, assembly-level transparency calculation occurs sooner than it does in the .NET Framework 2.0.</span></span> <span data-ttu-id="6d43d-184">唯一能保證的是透明度計算會在需要時發生。</span><span class="sxs-lookup"><span data-stu-id="6d43d-184">The only guarantee is that transparency calculation will occur by the time it is needed.</span></span> <span data-ttu-id="6d43d-185">這與 Just-In-Time (JIT) 編譯器如何變更進行方法之編譯的時間點很類似，也和其如何變更偵測該方法中任何錯誤的時間點很類似。</span><span class="sxs-lookup"><span data-stu-id="6d43d-185">This is similar to how the just-in-time (JIT) compiler can change the point when a method is compiled and any errors in that method are detected.</span></span> <span data-ttu-id="6d43d-186">如果您的程式碼沒有任何透明度錯誤，透明度計算就會是不可見的。</span><span class="sxs-lookup"><span data-stu-id="6d43d-186">Transparency calculation is invisible if your code does not have any transparency errors.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d43d-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d43d-187">See also</span></span>

- [<span data-ttu-id="6d43d-188">安全性透明的程式碼, 層級1</span><span class="sxs-lookup"><span data-stu-id="6d43d-188">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="6d43d-189">安全性透明的程式碼, 層級2</span><span class="sxs-lookup"><span data-stu-id="6d43d-189">Security-Transparent Code, Level 2</span></span>](security-transparent-code-level-2.md)
