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
# <a name="names-of-classes-structs-and-interfaces"></a>類別、結構和介面的名稱
The naming guidelines that follow apply to general type naming.

 ✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.

 This distinguishes type names from methods, which are named with verb phrases.

 ✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.

 Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.

 ❌ DO NOT give class names a prefix (e.g., "C").

 ✔️ CONSIDER ending the name of derived classes with the name of the base class.

 This is very readable and explains the relationship clearly. Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`. However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.

 ✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.

 For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names. As with other type names, avoid abbreviations.

 ✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.

## <a name="names-of-generic-type-parameters"></a>Names of Generic Type Parameters
 Generics were added to .NET Framework 2.0. The feature introduced a new kind of identifier called *type parameter*.

 ✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.

 ✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️ DO prefix descriptive type parameter names with `T`.

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.

 For example, a parameter constrained to `ISession` might be called `TSession`.

## <a name="names-of-common-types"></a>Names of Common Types
 ✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.

|基底類型|Derived/Implementing Type Guideline|
|---------------|------------------------------------------|
|`System.Attribute`|✔️ DO add the suffix "Attribute" to names of custom attribute classes.|
|`System.Delegate`|✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.<br /><br /> ✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.<br /><br /> ❌ DO NOT add the suffix "Delegate" to a delegate.|
|`System.EventArgs`|✔️ DO add the suffix "EventArgs."|
|`System.Enum`|❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.<br /><br /> ❌ DO NOT add the suffix "Enum" or "Flag."|
|`System.Exception`|✔️ DO add the suffix "Exception."|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️ DO add the suffix "Dictionary." Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️ DO add the suffix "Collection."|
|`System.IO.Stream`|✔️ DO add the suffix "Stream."|
|`CodeAccessPermission IPermission`|✔️ DO add the suffix "Permission."|

## <a name="naming-enumerations"></a>Naming Enumerations
 Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.). However, there are additional guidelines that apply specifically to enums.

 ✔️ DO use a singular type name for an enumeration unless its values are bit fields.

 ✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.

 ❌ DO NOT use an "Enum" suffix in enum type names.

 ❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.

 ❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).

 *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
