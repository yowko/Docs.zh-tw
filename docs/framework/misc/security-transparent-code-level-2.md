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
ms.openlocfilehash: 61a436efe3e3af7ce4aa50afe242838b1cd8941e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206062"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="56d89-102">安全性透明的程式碼，層級 2</span><span class="sxs-lookup"><span data-stu-id="56d89-102">Security-Transparent Code, Level 2</span></span>

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="56d89-103">層級2透明度是在 .NET Framework 4 中引進。</span><span class="sxs-lookup"><span data-stu-id="56d89-103">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="56d89-104">此模型的三個原則是透明程式碼、安全性安全關鍵程式碼和安全性關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="56d89-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="56d89-105">透明程式碼，包括以完全信任執行的程式碼，只可以呼叫其他透明程式碼或安全性安全關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="56d89-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="56d89-106">它只能執行定義域之部分信任權限集合 (如果存在的話) 所允許的動作。</span><span class="sxs-lookup"><span data-stu-id="56d89-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="56d89-107">透明程式碼無法進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="56d89-107">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="56d89-108">執行 <xref:System.Security.CodeAccessPermission.Assert%2A> 或提高權限。</span><span class="sxs-lookup"><span data-stu-id="56d89-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="56d89-109">包含不安全或無法驗證的程式碼。</span><span class="sxs-lookup"><span data-stu-id="56d89-109">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="56d89-110">直接呼叫關鍵程式碼。</span><span class="sxs-lookup"><span data-stu-id="56d89-110">Directly call critical code.</span></span>

  - <span data-ttu-id="56d89-111">呼叫機器碼或含有 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性的程式碼。</span><span class="sxs-lookup"><span data-stu-id="56d89-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="56d89-112">呼叫 <xref:System.Security.Permissions.SecurityAction.LinkDemand> 所保護的成員。</span><span class="sxs-lookup"><span data-stu-id="56d89-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="56d89-113">繼承自關鍵類型。</span><span class="sxs-lookup"><span data-stu-id="56d89-113">Inherit from critical types.</span></span>

  <span data-ttu-id="56d89-114">此外，透明方法無法覆寫關鍵虛擬方法或實作關鍵介面方法。</span><span class="sxs-lookup"><span data-stu-id="56d89-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="56d89-115">安全關鍵程式碼受到完全信任，但是可由透明程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="56d89-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="56d89-116">它會公開完全信任程式碼的有限介面區；正確性和安全性驗證會在安全關鍵程式碼中進行。</span><span class="sxs-lookup"><span data-stu-id="56d89-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="56d89-117">雖然安全性關鍵程式碼可以呼叫任何程式碼，而且受到完全信任，但是無法由透明程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="56d89-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

<span data-ttu-id="56d89-118">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="56d89-118">This topic contains the following sections:</span></span>

- [<span data-ttu-id="56d89-119">使用方式範例和行為</span><span class="sxs-lookup"><span data-stu-id="56d89-119">Usage Examples and Behaviors</span></span>](#examples)

- [<span data-ttu-id="56d89-120">覆寫模式</span><span class="sxs-lookup"><span data-stu-id="56d89-120">Override Patterns</span></span>](#override)

- [<span data-ttu-id="56d89-121">繼承規則</span><span class="sxs-lookup"><span data-stu-id="56d89-121">Inheritance Rules</span></span>](#inheritance)

- [<span data-ttu-id="56d89-122">其他資訊和規則</span><span class="sxs-lookup"><span data-stu-id="56d89-122">Additional Information and Rules</span></span>](#additional)

<a name="examples"></a>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="56d89-123">使用範例和行為</span><span class="sxs-lookup"><span data-stu-id="56d89-123">Usage Examples and Behaviors</span></span>

<span data-ttu-id="56d89-124">若要指定 .NET Framework 4 規則 (層級2透明度), 請針對元件使用下列注釋:</span><span class="sxs-lookup"><span data-stu-id="56d89-124">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="56d89-125">若要鎖定 .NET Framework 2.0 規則 (層級 1 透明度)，請使用下列註釋：</span><span class="sxs-lookup"><span data-stu-id="56d89-125">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="56d89-126">如果您沒有標注元件, 預設會使用 .NET Framework 4 規則。</span><span class="sxs-lookup"><span data-stu-id="56d89-126">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="56d89-127">不過, 建議的最佳作法是使用<xref:System.Security.SecurityRulesAttribute>屬性, 而不是根據預設值。</span><span class="sxs-lookup"><span data-stu-id="56d89-127">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="56d89-128">組件範圍的註釋</span><span class="sxs-lookup"><span data-stu-id="56d89-128">Assembly-wide Annotation</span></span>

<span data-ttu-id="56d89-129">下列規則適用於在組件層級使用屬性：</span><span class="sxs-lookup"><span data-stu-id="56d89-129">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="56d89-130">無屬性:如果您未指定任何屬性, 則執行時間會將所有程式碼解釋為安全性關鍵, 但安全性關鍵違反繼承規則 (例如, 覆寫或執行透明的虛擬或介面方法時)。</span><span class="sxs-lookup"><span data-stu-id="56d89-130">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="56d89-131">在這些情況下，這些方法都是安全關鍵方法。</span><span class="sxs-lookup"><span data-stu-id="56d89-131">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="56d89-132">不指定屬性會導致 Common Language Runtime 為您決定透明度規則。</span><span class="sxs-lookup"><span data-stu-id="56d89-132">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="56d89-133">`SecurityTransparent`：所有程式碼都是透明的;整個元件不會執行任何特殊許可權或不安全的動作。</span><span class="sxs-lookup"><span data-stu-id="56d89-133">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="56d89-134">`SecurityCritical`：這個組件中之類型所引入的所有程式碼都是關鍵的；所有其他程式碼則為透明的。</span><span class="sxs-lookup"><span data-stu-id="56d89-134">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="56d89-135">這個案例與不指定任何屬性很相似；不過，Common Language Runtime 不會自動決定透明度規則。</span><span class="sxs-lookup"><span data-stu-id="56d89-135">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="56d89-136">例如，如果您覆寫虛擬或抽象方法，或是實作介面方法，則根據預設，該方法為透明的。</span><span class="sxs-lookup"><span data-stu-id="56d89-136">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="56d89-137">您必須明確將此方法加註為 `SecurityCritical` 或 `SecuritySafeCritical`；否則，系統將在載入時擲回 <xref:System.TypeLoadException>。</span><span class="sxs-lookup"><span data-stu-id="56d89-137">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="56d89-138">當基底類別和衍生類別都位於相同的組件時，這項規則也適用。</span><span class="sxs-lookup"><span data-stu-id="56d89-138">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="56d89-139">`AllowPartiallyTrustedCallers`(僅限層級 2):所有程式碼都預設為透明的。</span><span class="sxs-lookup"><span data-stu-id="56d89-139">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="56d89-140">不過，個別的類型和成員可以有其他屬性。</span><span class="sxs-lookup"><span data-stu-id="56d89-140">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="56d89-141">下表比較層級2與層級1的元件層級行為。</span><span class="sxs-lookup"><span data-stu-id="56d89-141">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="56d89-142">Assembly 屬性</span><span class="sxs-lookup"><span data-stu-id="56d89-142">Assembly attribute</span></span>|<span data-ttu-id="56d89-143">層級 2</span><span class="sxs-lookup"><span data-stu-id="56d89-143">Level 2</span></span>|<span data-ttu-id="56d89-144">層級 1</span><span class="sxs-lookup"><span data-stu-id="56d89-144">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="56d89-145">部分信任組件無屬性</span><span class="sxs-lookup"><span data-stu-id="56d89-145">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="56d89-146">根據預設，類型和成員為透明的，但是可能為安全性關鍵或安全性安全關鍵的。</span><span class="sxs-lookup"><span data-stu-id="56d89-146">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="56d89-147">所有類型和成員皆為透明的。</span><span class="sxs-lookup"><span data-stu-id="56d89-147">All types and members are transparent.</span></span>|
|<span data-ttu-id="56d89-148">無屬性</span><span class="sxs-lookup"><span data-stu-id="56d89-148">No attribute</span></span>|<span data-ttu-id="56d89-149">不指定屬性會導致 Common Language Runtime 為您決定透明度規則。</span><span class="sxs-lookup"><span data-stu-id="56d89-149">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="56d89-150">所有類型和成員都是安全性關鍵的，但是安全性關鍵違反繼承規則的程式碼除外。</span><span class="sxs-lookup"><span data-stu-id="56d89-150">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="56d89-151">在完全信任的組件上 (位於全域組件快取中或在 `AppDomain` 中識別為完全信任)，所有類型都是透明的，而且所有成員都是安全性安全關鍵的。</span><span class="sxs-lookup"><span data-stu-id="56d89-151">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="56d89-152">所有類型和成員皆為透明的。</span><span class="sxs-lookup"><span data-stu-id="56d89-152">All types and members are transparent.</span></span>|<span data-ttu-id="56d89-153">所有類型和成員皆為透明的。</span><span class="sxs-lookup"><span data-stu-id="56d89-153">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="56d89-154">不適用。</span><span class="sxs-lookup"><span data-stu-id="56d89-154">Not applicable.</span></span>|<span data-ttu-id="56d89-155">所有類型和成員皆為安全性關鍵的。</span><span class="sxs-lookup"><span data-stu-id="56d89-155">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="56d89-156">這個組件中之類型所引入的所有程式碼都是關鍵的；所有其他程式碼則為透明的。</span><span class="sxs-lookup"><span data-stu-id="56d89-156">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="56d89-157">如果您覆寫虛擬或抽象方法，或是實作介面方法，就必須明確將此方法加註為 `SecurityCritical` 或 `SecuritySafeCritical`。</span><span class="sxs-lookup"><span data-stu-id="56d89-157">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="56d89-158">所有程式碼都預設為透明的。</span><span class="sxs-lookup"><span data-stu-id="56d89-158">All code defaults to transparent.</span></span> <span data-ttu-id="56d89-159">不過，個別的類型和成員可以有其他屬性。</span><span class="sxs-lookup"><span data-stu-id="56d89-159">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="56d89-160">類型和成員註釋</span><span class="sxs-lookup"><span data-stu-id="56d89-160">Type and Member Annotation</span></span>

<span data-ttu-id="56d89-161">套用至某個類型的安全性屬性也會套用至該類型所引入的成員。</span><span class="sxs-lookup"><span data-stu-id="56d89-161">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="56d89-162">不過，這些屬性不會套用至基底類別或介面實作的虛擬或抽象覆寫。</span><span class="sxs-lookup"><span data-stu-id="56d89-162">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="56d89-163">下列規則適用於在類型和成員層級使用屬性：</span><span class="sxs-lookup"><span data-stu-id="56d89-163">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="56d89-164">`SecurityCritical`：類型或成員是非常重要的, 而且只能由完全信任程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="56d89-164">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="56d89-165">在安全性關鍵類型中引入的方法是關鍵的。</span><span class="sxs-lookup"><span data-stu-id="56d89-165">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="56d89-166">根據預設，在基底類別或介面中引入，並且在安全性關鍵類別中覆寫或實作的虛擬和抽象方法為透明的。</span><span class="sxs-lookup"><span data-stu-id="56d89-166">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="56d89-167">它們必須識別為 `SecuritySafeCritical` 或 `SecurityCritical`。</span><span class="sxs-lookup"><span data-stu-id="56d89-167">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="56d89-168">`SecuritySafeCritical`：類型或成員是安全關鍵的。</span><span class="sxs-lookup"><span data-stu-id="56d89-168">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="56d89-169">不過，此類型或成員可以從透明 (部分信任) 程式碼呼叫，而且其功能與任何其他關鍵程式碼一樣。</span><span class="sxs-lookup"><span data-stu-id="56d89-169">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="56d89-170">基於安全性，您必須稽核此程式碼。</span><span class="sxs-lookup"><span data-stu-id="56d89-170">The code must be audited for security.</span></span>

[<span data-ttu-id="56d89-171">回到頁首</span><span class="sxs-lookup"><span data-stu-id="56d89-171">Back to top</span></span>](#top)

<a name="override"></a>

## <a name="override-patterns"></a><span data-ttu-id="56d89-172">覆寫模式</span><span class="sxs-lookup"><span data-stu-id="56d89-172">Override Patterns</span></span>

<span data-ttu-id="56d89-173">下表顯示層級 2 透明度所允許的方法覆寫。</span><span class="sxs-lookup"><span data-stu-id="56d89-173">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="56d89-174">基底虛擬/介面成員</span><span class="sxs-lookup"><span data-stu-id="56d89-174">Base virtual/interface member</span></span>|<span data-ttu-id="56d89-175">覆寫/介面</span><span class="sxs-lookup"><span data-stu-id="56d89-175">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

[<span data-ttu-id="56d89-176">回到頁首</span><span class="sxs-lookup"><span data-stu-id="56d89-176">Back to top</span></span>](#top)

<a name="inheritance"></a>

## <a name="inheritance-rules"></a><span data-ttu-id="56d89-177">繼承規則</span><span class="sxs-lookup"><span data-stu-id="56d89-177">Inheritance Rules</span></span>

<span data-ttu-id="56d89-178">在本節中，下列順序是根據存取和功能指派給 `Transparent`、`Critical` 和 `SafeCritical` 程式碼：</span><span class="sxs-lookup"><span data-stu-id="56d89-178">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="56d89-179">類型的規則:從左至右, 存取權會變得更嚴格。</span><span class="sxs-lookup"><span data-stu-id="56d89-179">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="56d89-180">衍生類型的限制至少必須與基底類型一樣嚴格。</span><span class="sxs-lookup"><span data-stu-id="56d89-180">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="56d89-181">方法的規則:衍生的方法無法變更基底方法的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="56d89-181">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="56d89-182">就預設行為而言，沒有加上附註的所有衍生方法都是 `Transparent`。</span><span class="sxs-lookup"><span data-stu-id="56d89-182">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="56d89-183">如果覆寫方法沒有明確標註為 `SecurityCritical`，關鍵類型的衍生物會導致系統擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="56d89-183">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="56d89-184">下表顯示允許的類型繼承模式。</span><span class="sxs-lookup"><span data-stu-id="56d89-184">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="56d89-185">基底類別</span><span class="sxs-lookup"><span data-stu-id="56d89-185">Base class</span></span>|<span data-ttu-id="56d89-186">衍生類別可為</span><span class="sxs-lookup"><span data-stu-id="56d89-186">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="56d89-187">下表顯示不允許的類型繼承模式。</span><span class="sxs-lookup"><span data-stu-id="56d89-187">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="56d89-188">基底類別</span><span class="sxs-lookup"><span data-stu-id="56d89-188">Base class</span></span>|<span data-ttu-id="56d89-189">衍生類別不可為</span><span class="sxs-lookup"><span data-stu-id="56d89-189">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="56d89-190">下表顯示允許的方法繼承模式。</span><span class="sxs-lookup"><span data-stu-id="56d89-190">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="56d89-191">基底方法</span><span class="sxs-lookup"><span data-stu-id="56d89-191">Base method</span></span>|<span data-ttu-id="56d89-192">衍生方法可為</span><span class="sxs-lookup"><span data-stu-id="56d89-192">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="56d89-193">下表顯示不允許的方法繼承模式。</span><span class="sxs-lookup"><span data-stu-id="56d89-193">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="56d89-194">基底方法</span><span class="sxs-lookup"><span data-stu-id="56d89-194">Base method</span></span>|<span data-ttu-id="56d89-195">衍生方法不可為</span><span class="sxs-lookup"><span data-stu-id="56d89-195">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="56d89-196">這些繼承規則適用於層級 2 類型和成員。</span><span class="sxs-lookup"><span data-stu-id="56d89-196">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="56d89-197">層級 1 組件中的類型可以繼承自層級 2 安全性關鍵類型和成員。</span><span class="sxs-lookup"><span data-stu-id="56d89-197">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="56d89-198">因此，層級 2 類型和成員必須針對層級 1 繼承者具有不同的繼承要求。</span><span class="sxs-lookup"><span data-stu-id="56d89-198">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

[<span data-ttu-id="56d89-199">回到頁首</span><span class="sxs-lookup"><span data-stu-id="56d89-199">Back to top</span></span>](#top)

<a name="additional"></a>

## <a name="additional-information-and-rules"></a><span data-ttu-id="56d89-200">其他資訊和規則</span><span class="sxs-lookup"><span data-stu-id="56d89-200">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="56d89-201">LinkDemand 支援</span><span class="sxs-lookup"><span data-stu-id="56d89-201">LinkDemand Support</span></span>

<span data-ttu-id="56d89-202">層級 2 透明度模型會將 <xref:System.Security.Permissions.SecurityAction.LinkDemand> 取代成 <xref:System.Security.SecurityCriticalAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="56d89-202">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="56d89-203">在舊版 (層級 1) 程式碼中，<xref:System.Security.Permissions.SecurityAction.LinkDemand> 可自動視為 <xref:System.Security.Permissions.SecurityAction.Demand>。</span><span class="sxs-lookup"><span data-stu-id="56d89-203">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="56d89-204">反射</span><span class="sxs-lookup"><span data-stu-id="56d89-204">Reflection</span></span>

<span data-ttu-id="56d89-205">叫用關鍵方法或讀取關鍵欄位就會觸發完全信任的要求 (就如同您叫用私用方法或欄位一樣)。</span><span class="sxs-lookup"><span data-stu-id="56d89-205">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="56d89-206">因此，完全信任程式碼可以叫用關鍵方法，而部分信任程式碼則無法叫用。</span><span class="sxs-lookup"><span data-stu-id="56d89-206">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="56d89-207">已加入下列屬性至 <xref:System.Reflection> 命名空間來識別類型、方法或欄位是否為 `SecurityCritical`、`SecuritySafeCritical`，或 `SecurityTransparent`：<xref:System.Type.IsSecurityCritical%2A>、<xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> 和 <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>。</span><span class="sxs-lookup"><span data-stu-id="56d89-207">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="56d89-208">您可以使用這些屬性來判斷透明度，方法是使用反映，而非檢查屬性是否存在。</span><span class="sxs-lookup"><span data-stu-id="56d89-208">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="56d89-209">透明度規則很複雜，而且檢查屬性是否存在可能不足夠。</span><span class="sxs-lookup"><span data-stu-id="56d89-209">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="56d89-210">`SafeCritical` 方法會<xref:System.Type.IsSecurityCritical%2A>傳回和的,因為<xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>確實相當重要(其功能與關鍵程式碼相同,不過可從透明程式`SafeCritical`代碼呼叫)。 `true`</span><span class="sxs-lookup"><span data-stu-id="56d89-210">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="56d89-211">動態方法會繼承它們所附加之目標模組的透明度，但是不會繼承類型的透明度 (如果它們附加至類型的話)。</span><span class="sxs-lookup"><span data-stu-id="56d89-211">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="56d89-212">在完全信任中略過驗證</span><span class="sxs-lookup"><span data-stu-id="56d89-212">Skip Verification in Full Trust</span></span>

<span data-ttu-id="56d89-213">若為完全信任的透明組件，您就可以在 <xref:System.Security.SecurityRulesAttribute> 屬性中，將 <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> 屬性設定為 `true`，藉以略過驗證：</span><span class="sxs-lookup"><span data-stu-id="56d89-213">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="56d89-214"><xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> 屬性預設為 `false`，因此這個屬性必須設定為 `true`，才能略過驗證。</span><span class="sxs-lookup"><span data-stu-id="56d89-214">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="56d89-215">您應該僅針對最佳化目的進行此作業。</span><span class="sxs-lookup"><span data-stu-id="56d89-215">This should be done for optimization purposes only.</span></span> <span data-ttu-id="56d89-216">您應該使用`transparent` [PEVerify 工具](../tools/peverify-exe-peverify-tool.md)中的選項, 確保元件中的透明程式碼是可驗證的。</span><span class="sxs-lookup"><span data-stu-id="56d89-216">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="56d89-217">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56d89-217">See also</span></span>

- [<span data-ttu-id="56d89-218">安全性透明的程式碼, 層級1</span><span class="sxs-lookup"><span data-stu-id="56d89-218">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="56d89-219">安全性變更</span><span class="sxs-lookup"><span data-stu-id="56d89-219">Security Changes</span></span>](../security/security-changes.md)
