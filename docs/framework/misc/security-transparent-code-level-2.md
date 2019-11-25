---
title: 安全性透明的程式碼，層級 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea782b346f6c53664a8aeb736c7d7a4509d83985
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974936"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="42492-102">安全性透明的程式碼，層級 2</span><span class="sxs-lookup"><span data-stu-id="42492-102">Security-Transparent Code, Level 2</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="42492-103">層級2透明度是在 .NET Framework 4 中引進。</span><span class="sxs-lookup"><span data-stu-id="42492-103">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="42492-104">此模型的三個原則是透明程式碼、安全性安全關鍵程式碼和安全性關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="42492-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="42492-105">透明程式碼，包括以完全信任執行的程式碼，只可以呼叫其他透明程式碼或安全性安全關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="42492-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="42492-106">它只能執行定義域之部分信任權限集合 (如果存在的話) 所允許的動作。</span><span class="sxs-lookup"><span data-stu-id="42492-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="42492-107">透明程式碼無法進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="42492-107">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="42492-108">執行 <xref:System.Security.CodeAccessPermission.Assert%2A> 或提高權限。</span><span class="sxs-lookup"><span data-stu-id="42492-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="42492-109">包含不安全或無法驗證的程式碼。</span><span class="sxs-lookup"><span data-stu-id="42492-109">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="42492-110">直接呼叫關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="42492-110">Directly call critical code.</span></span>

  - <span data-ttu-id="42492-111">呼叫機器碼或含有 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性的程式碼。</span><span class="sxs-lookup"><span data-stu-id="42492-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="42492-112">呼叫 <xref:System.Security.Permissions.SecurityAction.LinkDemand> 所保護的成員。</span><span class="sxs-lookup"><span data-stu-id="42492-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="42492-113">繼承自關鍵類型。</span><span class="sxs-lookup"><span data-stu-id="42492-113">Inherit from critical types.</span></span>

  <span data-ttu-id="42492-114">此外，透明方法無法覆寫關鍵虛擬方法或實作關鍵介面方法。</span><span class="sxs-lookup"><span data-stu-id="42492-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="42492-115">安全關鍵程式碼受到完全信任，但是可由透明程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="42492-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="42492-116">它會公開完全信任程式碼的有限介面區；正確性和安全性驗證會在安全關鍵程式碼中進行。</span><span class="sxs-lookup"><span data-stu-id="42492-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="42492-117">雖然安全性關鍵程式碼可以呼叫任何程式碼，而且受到完全信任，但是無法由透明程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="42492-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="42492-118">使用範例和行為</span><span class="sxs-lookup"><span data-stu-id="42492-118">Usage Examples and Behaviors</span></span>

<span data-ttu-id="42492-119">若要指定 .NET Framework 4 規則（層級2透明度），請針對元件使用下列注釋：</span><span class="sxs-lookup"><span data-stu-id="42492-119">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="42492-120">若要鎖定 .NET Framework 2.0 規則 (層級 1 透明度)，請使用下列註釋：</span><span class="sxs-lookup"><span data-stu-id="42492-120">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="42492-121">如果您沒有標注元件，預設會使用 .NET Framework 4 規則。</span><span class="sxs-lookup"><span data-stu-id="42492-121">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="42492-122">不過，建議的最佳作法是使用 <xref:System.Security.SecurityRulesAttribute> 屬性，而不是根據預設值。</span><span class="sxs-lookup"><span data-stu-id="42492-122">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="42492-123">組件範圍的註釋</span><span class="sxs-lookup"><span data-stu-id="42492-123">Assembly-wide Annotation</span></span>

<span data-ttu-id="42492-124">下列規則適用於在組件層級使用屬性：</span><span class="sxs-lookup"><span data-stu-id="42492-124">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="42492-125">無屬性：如果您沒有指定任何屬性，執行階段就會將所有程式碼解譯為安全性關鍵的，但是安全性關鍵違反繼承規則的程式碼除外 (例如，在覆寫或實作透明虛擬或介面方法時)。</span><span class="sxs-lookup"><span data-stu-id="42492-125">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="42492-126">在這些情況下，這些方法都是安全關鍵方法。</span><span class="sxs-lookup"><span data-stu-id="42492-126">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="42492-127">不指定屬性會導致 Common Language Runtime 為您決定透明度規則。</span><span class="sxs-lookup"><span data-stu-id="42492-127">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="42492-128">`SecurityTransparent`：所有程式碼都是透明的；整個組件將不會進行任何需要權限或不安全的作業。</span><span class="sxs-lookup"><span data-stu-id="42492-128">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="42492-129">`SecurityCritical`：這個組件中類型所引入的所有程式碼都是關鍵的；所有其他程式碼則為透明的。</span><span class="sxs-lookup"><span data-stu-id="42492-129">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="42492-130">這個案例與不指定任何屬性很相似；不過，Common Language Runtime 不會自動決定透明度規則。</span><span class="sxs-lookup"><span data-stu-id="42492-130">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="42492-131">例如，如果您覆寫虛擬或抽象方法，或是實作介面方法，則根據預設，該方法為透明的。</span><span class="sxs-lookup"><span data-stu-id="42492-131">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="42492-132">您必須明確將此方法加註為 `SecurityCritical` 或 `SecuritySafeCritical`；否則，系統將在載入時擲回 <xref:System.TypeLoadException>。</span><span class="sxs-lookup"><span data-stu-id="42492-132">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="42492-133">當基底類別和衍生類別都位於相同的組件時，這項規則也適用。</span><span class="sxs-lookup"><span data-stu-id="42492-133">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="42492-134">`AllowPartiallyTrustedCallers` (僅限層級 2)：所有程式碼都預設為透明的。</span><span class="sxs-lookup"><span data-stu-id="42492-134">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="42492-135">不過，個別的類型和成員可以有其他屬性。</span><span class="sxs-lookup"><span data-stu-id="42492-135">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="42492-136">下表比較層級2與層級1的元件層級行為。</span><span class="sxs-lookup"><span data-stu-id="42492-136">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="42492-137">Assembly 屬性</span><span class="sxs-lookup"><span data-stu-id="42492-137">Assembly attribute</span></span>|<span data-ttu-id="42492-138">階層 2</span><span class="sxs-lookup"><span data-stu-id="42492-138">Level 2</span></span>|<span data-ttu-id="42492-139">階層 1</span><span class="sxs-lookup"><span data-stu-id="42492-139">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="42492-140">部分信任組件無屬性</span><span class="sxs-lookup"><span data-stu-id="42492-140">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="42492-141">根據預設，類型和成員為透明的，但是可能為安全性關鍵或安全性安全關鍵的。</span><span class="sxs-lookup"><span data-stu-id="42492-141">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="42492-142">所有類型和成員皆為透明的。</span><span class="sxs-lookup"><span data-stu-id="42492-142">All types and members are transparent.</span></span>|
|<span data-ttu-id="42492-143">無屬性</span><span class="sxs-lookup"><span data-stu-id="42492-143">No attribute</span></span>|<span data-ttu-id="42492-144">不指定屬性會導致 Common Language Runtime 為您決定透明度規則。</span><span class="sxs-lookup"><span data-stu-id="42492-144">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="42492-145">所有類型和成員都是安全性關鍵的，但是安全性關鍵違反繼承規則的程式碼除外。</span><span class="sxs-lookup"><span data-stu-id="42492-145">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="42492-146">在完全信任的組件上 (位於全域組件快取中或在 `AppDomain` 中識別為完全信任)，所有類型都是透明的，而且所有成員都是安全性安全關鍵的。</span><span class="sxs-lookup"><span data-stu-id="42492-146">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="42492-147">所有類型和成員皆為透明的。</span><span class="sxs-lookup"><span data-stu-id="42492-147">All types and members are transparent.</span></span>|<span data-ttu-id="42492-148">所有類型和成員皆為透明的。</span><span class="sxs-lookup"><span data-stu-id="42492-148">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="42492-149">不適用。</span><span class="sxs-lookup"><span data-stu-id="42492-149">Not applicable.</span></span>|<span data-ttu-id="42492-150">所有類型和成員皆為安全性關鍵的。</span><span class="sxs-lookup"><span data-stu-id="42492-150">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="42492-151">這個組件中之類型所引入的所有程式碼都是關鍵的；所有其他程式碼則為透明的。</span><span class="sxs-lookup"><span data-stu-id="42492-151">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="42492-152">如果您覆寫虛擬或抽象方法，或是實作介面方法，就必須明確將此方法加註為 `SecurityCritical` 或 `SecuritySafeCritical`。</span><span class="sxs-lookup"><span data-stu-id="42492-152">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="42492-153">所有程式碼都預設為透明的。</span><span class="sxs-lookup"><span data-stu-id="42492-153">All code defaults to transparent.</span></span> <span data-ttu-id="42492-154">不過，個別的類型和成員可以有其他屬性。</span><span class="sxs-lookup"><span data-stu-id="42492-154">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="42492-155">類型和成員註釋</span><span class="sxs-lookup"><span data-stu-id="42492-155">Type and Member Annotation</span></span>

<span data-ttu-id="42492-156">套用至某個類型的安全性屬性也會套用至該類型所引入的成員。</span><span class="sxs-lookup"><span data-stu-id="42492-156">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="42492-157">不過，這些屬性不會套用至基底類別或介面實作的虛擬或抽象覆寫。</span><span class="sxs-lookup"><span data-stu-id="42492-157">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="42492-158">下列規則適用於在類型和成員層級使用屬性：</span><span class="sxs-lookup"><span data-stu-id="42492-158">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="42492-159">`SecurityCritical`：類型或成員是關鍵的，而且只能由完全信任程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="42492-159">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="42492-160">在安全性關鍵類型中引入的方法是關鍵的。</span><span class="sxs-lookup"><span data-stu-id="42492-160">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="42492-161">根據預設，在基底類別或介面中引入，並且在安全性關鍵類別中覆寫或實作的虛擬和抽象方法為透明的。</span><span class="sxs-lookup"><span data-stu-id="42492-161">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="42492-162">它們必須識別為 `SecuritySafeCritical` 或 `SecurityCritical`。</span><span class="sxs-lookup"><span data-stu-id="42492-162">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="42492-163">`SecuritySafeCritical`：類型或成員是安全關鍵的。</span><span class="sxs-lookup"><span data-stu-id="42492-163">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="42492-164">不過，此類型或成員可以從透明 (部分信任) 程式碼呼叫，而且其功能與任何其他關鍵程式碼一樣。</span><span class="sxs-lookup"><span data-stu-id="42492-164">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="42492-165">基於安全性，您必須稽核此程式碼。</span><span class="sxs-lookup"><span data-stu-id="42492-165">The code must be audited for security.</span></span>

## <a name="override-patterns"></a><span data-ttu-id="42492-166">覆寫模式</span><span class="sxs-lookup"><span data-stu-id="42492-166">Override Patterns</span></span>

<span data-ttu-id="42492-167">下表顯示層級 2 透明度所允許的方法覆寫。</span><span class="sxs-lookup"><span data-stu-id="42492-167">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="42492-168">基底虛擬/介面成員</span><span class="sxs-lookup"><span data-stu-id="42492-168">Base virtual/interface member</span></span>|<span data-ttu-id="42492-169">覆寫/介面</span><span class="sxs-lookup"><span data-stu-id="42492-169">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a><span data-ttu-id="42492-170">繼承規則</span><span class="sxs-lookup"><span data-stu-id="42492-170">Inheritance Rules</span></span>

<span data-ttu-id="42492-171">在本節中，下列順序是根據存取和功能指派給 `Transparent`、`Critical` 和 `SafeCritical` 程式碼：</span><span class="sxs-lookup"><span data-stu-id="42492-171">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="42492-172">類型的規則：由左至右執行，存取限制變得更嚴格。</span><span class="sxs-lookup"><span data-stu-id="42492-172">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="42492-173">衍生類型的限制至少必須與基底類型一樣嚴格。</span><span class="sxs-lookup"><span data-stu-id="42492-173">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="42492-174">方法的規則：衍生方法無法變更基底方法的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="42492-174">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="42492-175">就預設行為而言，沒有加上附註的所有衍生方法都是 `Transparent`。</span><span class="sxs-lookup"><span data-stu-id="42492-175">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="42492-176">如果覆寫方法沒有明確標註為 `SecurityCritical`，關鍵類型的衍生物會導致系統擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42492-176">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="42492-177">下表顯示允許的類型繼承模式。</span><span class="sxs-lookup"><span data-stu-id="42492-177">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="42492-178">基底類別</span><span class="sxs-lookup"><span data-stu-id="42492-178">Base class</span></span>|<span data-ttu-id="42492-179">衍生類別可為</span><span class="sxs-lookup"><span data-stu-id="42492-179">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="42492-180">下表顯示不允許的類型繼承模式。</span><span class="sxs-lookup"><span data-stu-id="42492-180">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="42492-181">基底類別</span><span class="sxs-lookup"><span data-stu-id="42492-181">Base class</span></span>|<span data-ttu-id="42492-182">衍生類別不可為</span><span class="sxs-lookup"><span data-stu-id="42492-182">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="42492-183">下表顯示允許的方法繼承模式。</span><span class="sxs-lookup"><span data-stu-id="42492-183">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="42492-184">基底方法</span><span class="sxs-lookup"><span data-stu-id="42492-184">Base method</span></span>|<span data-ttu-id="42492-185">衍生方法可為</span><span class="sxs-lookup"><span data-stu-id="42492-185">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="42492-186">下表顯示不允許的方法繼承模式。</span><span class="sxs-lookup"><span data-stu-id="42492-186">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="42492-187">基底方法</span><span class="sxs-lookup"><span data-stu-id="42492-187">Base method</span></span>|<span data-ttu-id="42492-188">衍生方法不可為</span><span class="sxs-lookup"><span data-stu-id="42492-188">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="42492-189">這些繼承規則適用於層級 2 類型和成員。</span><span class="sxs-lookup"><span data-stu-id="42492-189">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="42492-190">層級 1 組件中的類型可以繼承自層級 2 安全性關鍵類型和成員。</span><span class="sxs-lookup"><span data-stu-id="42492-190">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="42492-191">因此，層級 2 類型和成員必須針對層級 1 繼承者具有不同的繼承要求。</span><span class="sxs-lookup"><span data-stu-id="42492-191">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

## <a name="additional-information-and-rules"></a><span data-ttu-id="42492-192">其他資訊和規則</span><span class="sxs-lookup"><span data-stu-id="42492-192">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="42492-193">LinkDemand 支援</span><span class="sxs-lookup"><span data-stu-id="42492-193">LinkDemand Support</span></span>

<span data-ttu-id="42492-194">層級 2 透明度模型會將 <xref:System.Security.Permissions.SecurityAction.LinkDemand> 取代成 <xref:System.Security.SecurityCriticalAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="42492-194">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="42492-195">在舊版 (層級 1) 程式碼中，<xref:System.Security.Permissions.SecurityAction.LinkDemand> 可自動視為 <xref:System.Security.Permissions.SecurityAction.Demand>。</span><span class="sxs-lookup"><span data-stu-id="42492-195">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="42492-196">反射</span><span class="sxs-lookup"><span data-stu-id="42492-196">Reflection</span></span>

<span data-ttu-id="42492-197">叫用關鍵方法或讀取關鍵欄位就會觸發完全信任的要求 (就如同您叫用私用方法或欄位一樣)。</span><span class="sxs-lookup"><span data-stu-id="42492-197">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="42492-198">因此，完全信任程式碼可以叫用關鍵方法，而部分信任程式碼則無法叫用。</span><span class="sxs-lookup"><span data-stu-id="42492-198">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="42492-199">已加入下列屬性至 <xref:System.Reflection> 命名空間來識別類型、方法或欄位是否為 `SecurityCritical`、`SecuritySafeCritical`，或 `SecurityTransparent`：<xref:System.Type.IsSecurityCritical%2A>、<xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> 和 <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>。</span><span class="sxs-lookup"><span data-stu-id="42492-199">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="42492-200">您可以使用這些屬性來判斷透明度，方法是使用反映，而非檢查屬性是否存在。</span><span class="sxs-lookup"><span data-stu-id="42492-200">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="42492-201">透明度規則很複雜，而且檢查屬性是否存在可能不足夠。</span><span class="sxs-lookup"><span data-stu-id="42492-201">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="42492-202">`SafeCritical` 方法會傳回 <xref:System.Type.IsSecurityCritical%2A> 和 <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>的 `true`，因為 `SafeCritical` 確實很重要（其功能與關鍵程式碼相同，但可從透明程式碼呼叫）。</span><span class="sxs-lookup"><span data-stu-id="42492-202">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="42492-203">動態方法會繼承它們所附加之目標模組的透明度，但是不會繼承類型的透明度 (如果它們附加至類型的話)。</span><span class="sxs-lookup"><span data-stu-id="42492-203">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="42492-204">在完全信任中略過驗證</span><span class="sxs-lookup"><span data-stu-id="42492-204">Skip Verification in Full Trust</span></span>

<span data-ttu-id="42492-205">若為完全信任的透明組件，您就可以在 <xref:System.Security.SecurityRulesAttribute> 屬性中，將 <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> 屬性設定為 `true`，藉以略過驗證：</span><span class="sxs-lookup"><span data-stu-id="42492-205">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="42492-206"><xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> 屬性預設為 `false`，因此這個屬性必須設定為 `true`，才能略過驗證。</span><span class="sxs-lookup"><span data-stu-id="42492-206">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="42492-207">您應該僅針對最佳化目的進行此作業。</span><span class="sxs-lookup"><span data-stu-id="42492-207">This should be done for optimization purposes only.</span></span> <span data-ttu-id="42492-208">您應該使用[PEVerify 工具](../tools/peverify-exe-peverify-tool.md)中的 [`transparent`] 選項，確保元件中的透明程式碼是可驗證的。</span><span class="sxs-lookup"><span data-stu-id="42492-208">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42492-209">請參閱</span><span class="sxs-lookup"><span data-stu-id="42492-209">See also</span></span>

- [<span data-ttu-id="42492-210">安全性透明的程式碼，層級1</span><span class="sxs-lookup"><span data-stu-id="42492-210">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="42492-211">安全性變更</span><span class="sxs-lookup"><span data-stu-id="42492-211">Security Changes</span></span>](../security/security-changes.md)
