---
title: "類別、結構和介面的名稱"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7c76fccec77454cb4551e427e254fe84d9a60299
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="b7596-102">類別、結構和介面的名稱</span><span class="sxs-lookup"><span data-stu-id="b7596-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="b7596-103">遵循的命名指導方針適用於一般類型命名。</span><span class="sxs-lookup"><span data-stu-id="b7596-103">The naming guidelines that follow apply to general type naming.</span></span>  
  
 <span data-ttu-id="b7596-104">**✓ 不要**命名類別與結構名詞或名詞片語，使用 PascalCasing。</span><span class="sxs-lookup"><span data-stu-id="b7596-104">**✓ DO** name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>  
  
 <span data-ttu-id="b7596-105">這個區別型別名稱與命名的動詞片語的方法。</span><span class="sxs-lookup"><span data-stu-id="b7596-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>  
  
 <span data-ttu-id="b7596-106">**✓ 不要**命名介面與形容詞片語，或有時候名詞或名詞片語。</span><span class="sxs-lookup"><span data-stu-id="b7596-106">**✓ DO** name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="b7596-107">名詞和名詞片語應該很少使用，它們可能表示的類型應該是抽象類別，並不是介面。</span><span class="sxs-lookup"><span data-stu-id="b7596-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>  
  
 <span data-ttu-id="b7596-108">**X 不**提供以類別名稱的前置詞 (例如，"C")。</span><span class="sxs-lookup"><span data-stu-id="b7596-108">**X DO NOT** give class names a prefix (e.g., "C").</span></span>  
  
 <span data-ttu-id="b7596-109">**✓ 考慮**名稱的結尾衍生的基底類別名稱的類別。</span><span class="sxs-lookup"><span data-stu-id="b7596-109">**✓ CONSIDER** ending the name of derived classes with the name of the base class.</span></span>  
  
 <span data-ttu-id="b7596-110">這是不易閱讀，而且清楚地說明的關聯性。</span><span class="sxs-lookup"><span data-stu-id="b7596-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="b7596-111">這個程式碼中的某些範例包括： `ArgumentOutOfRangeException`，這是一種的`Exception`，和`SerializableAttribute`，這是一種的`Attribute`。</span><span class="sxs-lookup"><span data-stu-id="b7596-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="b7596-112">不過，請務必使用合理判斷在套用這個指導方針。例如，`Button`類別是一種的`Control`事件，雖然`Control`不會出現在其名稱。</span><span class="sxs-lookup"><span data-stu-id="b7596-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>  
  
 <span data-ttu-id="b7596-113">**✓ 不要**前置詞介面名稱以字母 I，表示型別是介面。</span><span class="sxs-lookup"><span data-stu-id="b7596-113">**✓ DO** prefix interface names with the letter I, to indicate that the type is an interface.</span></span>  
  
 <span data-ttu-id="b7596-114">例如， `IComponent` （描述性名詞） `ICustomAttributeProvider` （名詞片語） 和`IPersistable`（形容詞） 是適當的介面名稱。</span><span class="sxs-lookup"><span data-stu-id="b7596-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="b7596-115">如同其他類型名稱，避免縮寫。</span><span class="sxs-lookup"><span data-stu-id="b7596-115">As with other type names, avoid abbreviations.</span></span>  
  
 <span data-ttu-id="b7596-116">**✓ 不要**確保僅由"I"前置詞上的介面名稱定義在類別是標準的介面實作的一組類別 – 介面時，名稱會不同。</span><span class="sxs-lookup"><span data-stu-id="b7596-116">**✓ DO** ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>  
  
## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="b7596-117">泛型型別參數的名稱</span><span class="sxs-lookup"><span data-stu-id="b7596-117">Names of Generic Type Parameters</span></span>  
 <span data-ttu-id="b7596-118">泛型已新增至.NET Framework 2.0。</span><span class="sxs-lookup"><span data-stu-id="b7596-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="b7596-119">此功能導入了一種新的識別項稱為*型別參數*。</span><span class="sxs-lookup"><span data-stu-id="b7596-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>  
  
 <span data-ttu-id="b7596-120">**✓ 不要**泛型型別參數名稱使用描述性名稱，除非單一字母名稱是完全一目了然，而且專案的描述性名稱不會加入值。</span><span class="sxs-lookup"><span data-stu-id="b7596-120">**✓ DO** name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>  
  
 <span data-ttu-id="b7596-121">**✓ 考慮**使用`T`做為型別參數名稱與一個單一字母的型別參數的類型。</span><span class="sxs-lookup"><span data-stu-id="b7596-121">**✓ CONSIDER** using `T` as the type parameter name for types with one single-letter type parameter.</span></span>  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 <span data-ttu-id="b7596-122">**✓ 不要**描述性型別參數名稱前面加上`T`。</span><span class="sxs-lookup"><span data-stu-id="b7596-122">**✓ DO** prefix descriptive type parameter names with `T`.</span></span>  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 <span data-ttu-id="b7596-123">**✓ 考慮**指出條件約束放在以參數名稱的型別參數上。</span><span class="sxs-lookup"><span data-stu-id="b7596-123">**✓ CONSIDER** indicating constraints placed on a type parameter in the name of the parameter.</span></span>  
  
 <span data-ttu-id="b7596-124">例如，將參數限制為`ISession`可能呼叫`TSession`。</span><span class="sxs-lookup"><span data-stu-id="b7596-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>  
  
## <a name="names-of-common-types"></a><span data-ttu-id="b7596-125">一般型別的名稱</span><span class="sxs-lookup"><span data-stu-id="b7596-125">Names of Common Types</span></span>  
 <span data-ttu-id="b7596-126">**✓ 不要**遵循命名型別衍生自或實作特定的.NET Framework 型別時下, 表中所述的指導方針。</span><span class="sxs-lookup"><span data-stu-id="b7596-126">**✓ DO** follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>  
  
|<span data-ttu-id="b7596-127">基底類型</span><span class="sxs-lookup"><span data-stu-id="b7596-127">Base Type</span></span>|<span data-ttu-id="b7596-128">衍生/實作型別指導方針</span><span class="sxs-lookup"><span data-stu-id="b7596-128">Derived/Implementing Type Guideline</span></span>|  
|---------------|------------------------------------------|  
|`System.Attribute`|<span data-ttu-id="b7596-129">**✓ 不要**加入後置詞"Attribute"的自訂屬性的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="b7596-129">**✓ DO** add the suffix "Attribute" to names of custom attribute classes.</span></span>|  
|`System.Delegate`|<span data-ttu-id="b7596-130">**✓ 不要**將後置詞"事件處理常式 」 新增到事件中所使用的委派的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7596-130">**✓ DO** add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="b7596-131">**✓ 不要**加入後置詞"Callback"名稱的委派以外做為事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b7596-131">**✓ DO** add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="b7596-132">**X 不**委派中加入後置詞 「 委派 」。</span><span class="sxs-lookup"><span data-stu-id="b7596-132">**X DO NOT** add the suffix "Delegate" to a delegate.</span></span>|  
|`System.EventArgs`|<span data-ttu-id="b7596-133">**✓ 不要**加入後置詞"EventArgs。 」</span><span class="sxs-lookup"><span data-stu-id="b7596-133">**✓ DO** add the suffix "EventArgs."</span></span>|  
|`System.Enum`|<span data-ttu-id="b7596-134">**X 不**衍生自這個類別使用改為您的語言支援的關鍵字; 例如，在 C# 中，使用`enum`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b7596-134">**X DO NOT** derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="b7596-135">**X 不**加入後置詞 「 列舉 」 或 「 旗標。 」</span><span class="sxs-lookup"><span data-stu-id="b7596-135">**X DO NOT** add the suffix "Enum" or "Flag."</span></span>|  
|`System.Exception`|<span data-ttu-id="b7596-136">**✓ 不要**加入後置詞 「 例外狀況 」。</span><span class="sxs-lookup"><span data-stu-id="b7596-136">**✓ DO** add the suffix "Exception."</span></span>|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="b7596-137">**✓ 不要**加入後置詞"字典。</span><span class="sxs-lookup"><span data-stu-id="b7596-137">**✓ DO** add the suffix "Dictionary."</span></span> <span data-ttu-id="b7596-138">請注意，`IDictionary`特定類型的集合，但這項指導方針的優先順序高於遵循的一般集合導線。</span><span class="sxs-lookup"><span data-stu-id="b7596-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="b7596-139">**✓ 不要**加入後置詞 「 集合 」。</span><span class="sxs-lookup"><span data-stu-id="b7596-139">**✓ DO** add the suffix "Collection."</span></span>|  
|`System.IO.Stream`|<span data-ttu-id="b7596-140">**✓ 不要**加入後置詞"資料流。 」</span><span class="sxs-lookup"><span data-stu-id="b7596-140">**✓ DO** add the suffix "Stream."</span></span>|  
|`CodeAccessPermission IPermission`|<span data-ttu-id="b7596-141">**✓ 不要**加入後置詞 「 權限。 」</span><span class="sxs-lookup"><span data-stu-id="b7596-141">**✓ DO** add the suffix "Permission."</span></span>|  
  
## <a name="naming-enumerations"></a><span data-ttu-id="b7596-142">命名列舉型別</span><span class="sxs-lookup"><span data-stu-id="b7596-142">Naming Enumerations</span></span>  
 <span data-ttu-id="b7596-143">一般情況下 （也稱為列舉） 的列舉類型的名稱應該遵循的一般型別命名規則 （PascalCasing 等等）。</span><span class="sxs-lookup"><span data-stu-id="b7596-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="b7596-144">不過，有一些額外的指導方針適用於列舉。</span><span class="sxs-lookup"><span data-stu-id="b7596-144">However, there are additional guidelines that apply specifically to enums.</span></span>  
  
 <span data-ttu-id="b7596-145">**✓ 不要**使用單數的型別名稱的列舉型別，除非其值是位元欄位。</span><span class="sxs-lookup"><span data-stu-id="b7596-145">**✓ DO** use a singular type name for an enumeration unless its values are bit fields.</span></span>  
  
 <span data-ttu-id="b7596-146">**✓ 不要**與位元欄位使用列舉的複數的型別名稱，做為值，也稱為旗標列舉。</span><span class="sxs-lookup"><span data-stu-id="b7596-146">**✓ DO** use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>  
  
 <span data-ttu-id="b7596-147">**X 不**列舉型別名稱中使用的 「 列舉 」 後置詞。</span><span class="sxs-lookup"><span data-stu-id="b7596-147">**X DO NOT** use an "Enum" suffix in enum type names.</span></span>  
  
 <span data-ttu-id="b7596-148">**X 不**使用 」 的旗標 」 或"Flags"尾碼在列舉型別名稱。</span><span class="sxs-lookup"><span data-stu-id="b7596-148">**X DO NOT** use "Flag" or "Flags" suffixes in enum type names.</span></span>  
  
 <span data-ttu-id="b7596-149">**X 不**使用前置詞上的列舉值名稱 (例如，"ad"ADO 列舉。)、"rtf"rtf 文字列舉等等。</span><span class="sxs-lookup"><span data-stu-id="b7596-149">**X DO NOT** use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>  
  
 <span data-ttu-id="b7596-150">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="b7596-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b7596-151">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="b7596-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7596-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7596-152">See Also</span></span>  
 [<span data-ttu-id="b7596-153">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="b7596-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="b7596-154">命名方針</span><span class="sxs-lookup"><span data-stu-id="b7596-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
