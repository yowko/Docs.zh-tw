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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400593"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="6856e-102">類別、結構和介面的名稱</span><span class="sxs-lookup"><span data-stu-id="6856e-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="6856e-103">以下命名準則適用于常規類型命名。</span><span class="sxs-lookup"><span data-stu-id="6856e-103">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="6856e-104">✔️使用 PascalCasing 命名類和帶有名詞或名詞短語的結構。</span><span class="sxs-lookup"><span data-stu-id="6856e-104">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="6856e-105">這將類型名稱與用動詞短語命名的方法區分開來。</span><span class="sxs-lookup"><span data-stu-id="6856e-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="6856e-106">✔️使用形容詞短語，或偶爾使用名詞或名詞短語進行命名介面。</span><span class="sxs-lookup"><span data-stu-id="6856e-106">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="6856e-107">名詞和名詞短語應很少使用，它們可能表示類型應為抽象類別，而不是介面。</span><span class="sxs-lookup"><span data-stu-id="6856e-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="6856e-108">❌不要給類名首碼（例如，"C"）。</span><span class="sxs-lookup"><span data-stu-id="6856e-108">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="6856e-109">✔️考慮用基類的名稱結束派生類的名稱。</span><span class="sxs-lookup"><span data-stu-id="6856e-109">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="6856e-110">這是非常可讀的，並清楚地解釋了這種關係。</span><span class="sxs-lookup"><span data-stu-id="6856e-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="6856e-111">代碼中這方面的一些示例是： `ArgumentOutOfRangeException`，這是一種`Exception`，和`SerializableAttribute`，是 一`Attribute`種 。</span><span class="sxs-lookup"><span data-stu-id="6856e-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="6856e-112">但是，在適用本準則時，必須運用合理的判斷;例如，`Button`類是一種`Control`事件，儘管`Control`未出現在其名稱中。</span><span class="sxs-lookup"><span data-stu-id="6856e-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="6856e-113">✔️ DO 首碼介面名稱與字母 I，以指示類型是介面。</span><span class="sxs-lookup"><span data-stu-id="6856e-113">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="6856e-114">例如，（`IComponent`描述性名詞）、（`ICustomAttributeProvider`名詞短語）和`IPersistable`（形容詞）是適當的介面名稱。</span><span class="sxs-lookup"><span data-stu-id="6856e-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="6856e-115">與其他類型名稱一樣，請避免縮寫。</span><span class="sxs-lookup"><span data-stu-id="6856e-115">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="6856e-116">✔️，在定義類介面對時，確保名稱僅與介面名稱上的"I"首碼不同，其中類是介面的標準實現。</span><span class="sxs-lookup"><span data-stu-id="6856e-116">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="6856e-117">泛型型別參數的名稱</span><span class="sxs-lookup"><span data-stu-id="6856e-117">Names of Generic Type Parameters</span></span>
 <span data-ttu-id="6856e-118">泛型已添加到 .NET 框架 2.0 中。</span><span class="sxs-lookup"><span data-stu-id="6856e-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="6856e-119">該功能引入了一種稱為*類型參數*的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6856e-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="6856e-120">✔️ DO 名稱泛型型別參數（帶有描述性名稱）除非單字母名稱完全不言自明，並且描述性名稱不會增加值。</span><span class="sxs-lookup"><span data-stu-id="6856e-120">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="6856e-121">✔️考慮使用`T`具有單字母類型參數的類型作為類型參數名稱。</span><span class="sxs-lookup"><span data-stu-id="6856e-121">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="6856e-122">✔️ DO 首碼描述性`T`類型參數名稱。</span><span class="sxs-lookup"><span data-stu-id="6856e-122">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="6856e-123">✔️考慮指示在參數名稱中對類型參數放置的約束。</span><span class="sxs-lookup"><span data-stu-id="6856e-123">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="6856e-124">例如，約束到`ISession`的參數可能稱為`TSession`。</span><span class="sxs-lookup"><span data-stu-id="6856e-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="6856e-125">常見類型的名稱</span><span class="sxs-lookup"><span data-stu-id="6856e-125">Names of Common Types</span></span>
 <span data-ttu-id="6856e-126">✔️命名派生自某些 .NET 框架類型或實現某些 .NET 框架類型時，請遵循下表中描述的準則。</span><span class="sxs-lookup"><span data-stu-id="6856e-126">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="6856e-127">基底類型</span><span class="sxs-lookup"><span data-stu-id="6856e-127">Base Type</span></span>|<span data-ttu-id="6856e-128">派生/實現類型指南</span><span class="sxs-lookup"><span data-stu-id="6856e-128">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="6856e-129">✔️DO將尾碼"屬性"添加到自訂屬性類的名稱中。</span><span class="sxs-lookup"><span data-stu-id="6856e-129">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="6856e-130">✔️DO將尾碼"事件處理常式"添加到事件中使用的委託名稱中。</span><span class="sxs-lookup"><span data-stu-id="6856e-130">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="6856e-131">✔️將尾碼"回檔"添加到用作事件處理常式的委託名稱以外的委託名稱中。</span><span class="sxs-lookup"><span data-stu-id="6856e-131">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="6856e-132">❌不要將尾碼"委託"添加到委託。</span><span class="sxs-lookup"><span data-stu-id="6856e-132">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="6856e-133">✔️添加尾碼"事件阿格"。</span><span class="sxs-lookup"><span data-stu-id="6856e-133">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="6856e-134">❌不要從此類派生;因此，請勿從此類派生。改用語言支援的關鍵字;例如，在 C# 中，`enum`使用 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6856e-134">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="6856e-135">❌請勿添加尾碼"枚舉"或"標記"。</span><span class="sxs-lookup"><span data-stu-id="6856e-135">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="6856e-136">✔️添加尾碼"異常"。</span><span class="sxs-lookup"><span data-stu-id="6856e-136">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="6856e-137">✔️添加尾碼"字典"。</span><span class="sxs-lookup"><span data-stu-id="6856e-137">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="6856e-138">請注意，`IDictionary`這是特定類型的集合，但此準則優先于以下更常規的集合準則。</span><span class="sxs-lookup"><span data-stu-id="6856e-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="6856e-139">✔️添加尾碼"集合"。</span><span class="sxs-lookup"><span data-stu-id="6856e-139">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="6856e-140">✔️添加尾碼"流"。</span><span class="sxs-lookup"><span data-stu-id="6856e-140">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="6856e-141">✔️添加尾碼"許可權"。</span><span class="sxs-lookup"><span data-stu-id="6856e-141">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="6856e-142">命名枚舉</span><span class="sxs-lookup"><span data-stu-id="6856e-142">Naming Enumerations</span></span>
 <span data-ttu-id="6856e-143">枚舉類型（也稱為枚舉）的名稱通常應遵循標準類型命名規則（PascalCasing 等）。</span><span class="sxs-lookup"><span data-stu-id="6856e-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="6856e-144">但是，還有其他特別適用于枚舉的準則。</span><span class="sxs-lookup"><span data-stu-id="6856e-144">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="6856e-145">✔️DO使用單一類型名稱進行枚舉，除非其值為位欄位。</span><span class="sxs-lookup"><span data-stu-id="6856e-145">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="6856e-146">✔️DO使用複數類型名稱進行枚舉，其中位欄位為值，也稱為標誌枚舉。</span><span class="sxs-lookup"><span data-stu-id="6856e-146">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="6856e-147">❌請勿在枚舉類型名稱中使用"枚舉"尾碼。</span><span class="sxs-lookup"><span data-stu-id="6856e-147">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="6856e-148">❌請勿在枚舉類型名稱中使用"標記"或"標記"尾碼。</span><span class="sxs-lookup"><span data-stu-id="6856e-148">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="6856e-149">❌請勿在枚舉值名稱上使用首碼（例如，ADO 枚舉的"ad"，富文本枚舉的"rtf"等）。</span><span class="sxs-lookup"><span data-stu-id="6856e-149">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="6856e-150">*部分© 2005， 2009 微軟公司.保留擁有權利。*</span><span class="sxs-lookup"><span data-stu-id="6856e-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="6856e-151">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="6856e-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="6856e-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6856e-152">See also</span></span>

- [<span data-ttu-id="6856e-153">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="6856e-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="6856e-154">命名方針</span><span class="sxs-lookup"><span data-stu-id="6856e-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
