---
title: 類別、結構和介面的名稱
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
ms.openlocfilehash: 2c528348c0e84037a80df9797c56f03b51c73adc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727794"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="4c4ed-102">類別、結構和介面的名稱</span><span class="sxs-lookup"><span data-stu-id="4c4ed-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="4c4ed-103">The naming guidelines that follow apply to general type naming.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-103">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="4c4ed-104">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-104">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="4c4ed-105">This distinguishes type names from methods, which are named with verb phrases.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="4c4ed-106">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-106">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="4c4ed-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="4c4ed-108">❌ DO NOT give class names a prefix (e.g., "C").</span><span class="sxs-lookup"><span data-stu-id="4c4ed-108">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="4c4ed-109">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-109">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="4c4ed-110">This is very readable and explains the relationship clearly.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="4c4ed-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="4c4ed-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="4c4ed-113">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-113">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="4c4ed-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="4c4ed-115">As with other type names, avoid abbreviations.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-115">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="4c4ed-116">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-116">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="4c4ed-117">Names of Generic Type Parameters</span><span class="sxs-lookup"><span data-stu-id="4c4ed-117">Names of Generic Type Parameters</span></span>
 <span data-ttu-id="4c4ed-118">Generics were added to .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="4c4ed-119">The feature introduced a new kind of identifier called *type parameter*.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="4c4ed-120">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-120">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="4c4ed-121">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-121">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="4c4ed-122">✔️ DO prefix descriptive type parameter names with `T`.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-122">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="4c4ed-123">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-123">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="4c4ed-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="4c4ed-125">Names of Common Types</span><span class="sxs-lookup"><span data-stu-id="4c4ed-125">Names of Common Types</span></span>
 <span data-ttu-id="4c4ed-126">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-126">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="4c4ed-127">基底類型</span><span class="sxs-lookup"><span data-stu-id="4c4ed-127">Base Type</span></span>|<span data-ttu-id="4c4ed-128">Derived/Implementing Type Guideline</span><span class="sxs-lookup"><span data-stu-id="4c4ed-128">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="4c4ed-129">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-129">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="4c4ed-130">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-130">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="4c4ed-131">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-131">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="4c4ed-132">❌ DO NOT add the suffix "Delegate" to a delegate.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-132">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="4c4ed-133">✔️ DO add the suffix "EventArgs."</span><span class="sxs-lookup"><span data-stu-id="4c4ed-133">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="4c4ed-134">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-134">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="4c4ed-135">❌ DO NOT add the suffix "Enum" or "Flag."</span><span class="sxs-lookup"><span data-stu-id="4c4ed-135">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="4c4ed-136">✔️ DO add the suffix "Exception."</span><span class="sxs-lookup"><span data-stu-id="4c4ed-136">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="4c4ed-137">✔️ DO add the suffix "Dictionary."</span><span class="sxs-lookup"><span data-stu-id="4c4ed-137">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="4c4ed-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="4c4ed-139">✔️ DO add the suffix "Collection."</span><span class="sxs-lookup"><span data-stu-id="4c4ed-139">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="4c4ed-140">✔️ DO add the suffix "Stream."</span><span class="sxs-lookup"><span data-stu-id="4c4ed-140">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="4c4ed-141">✔️ DO add the suffix "Permission."</span><span class="sxs-lookup"><span data-stu-id="4c4ed-141">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="4c4ed-142">Naming Enumerations</span><span class="sxs-lookup"><span data-stu-id="4c4ed-142">Naming Enumerations</span></span>
 <span data-ttu-id="4c4ed-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span><span class="sxs-lookup"><span data-stu-id="4c4ed-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="4c4ed-144">However, there are additional guidelines that apply specifically to enums.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-144">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="4c4ed-145">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-145">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="4c4ed-146">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-146">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="4c4ed-147">❌ DO NOT use an "Enum" suffix in enum type names.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-147">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="4c4ed-148">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span><span class="sxs-lookup"><span data-stu-id="4c4ed-148">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="4c4ed-149">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span><span class="sxs-lookup"><span data-stu-id="4c4ed-149">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="4c4ed-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="4c4ed-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="4c4ed-151">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="4c4ed-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="4c4ed-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="4c4ed-152">See also</span></span>

- [<span data-ttu-id="4c4ed-153">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="4c4ed-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="4c4ed-154">命名方針</span><span class="sxs-lookup"><span data-stu-id="4c4ed-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
