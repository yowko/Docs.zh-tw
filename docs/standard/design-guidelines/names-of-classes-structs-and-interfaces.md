---
title: 類別、結構和介面的名稱
description: 使用這些指導方針來命名類別、結構和介面，作為設計延伸和互動 .NET 程式庫的指引的一部分。
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
ms.openlocfilehash: b9de9329cc8e1bfc47a46523c7119bb3b2c244d8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290210"
---
# <a name="names-of-classes-structs-and-interfaces"></a>類別、結構和介面的名稱
後面的命名指導方針適用于一般類型命名。

 ✔️使用 PascalCasing 來命名具有名詞或名詞片語的類別和結構。

 這會區分方法中的型別名稱，其以動詞片語命名。

 ✔️使用形容詞片語，或偶爾使用名詞或名詞片語來命名介面。

 名詞和名詞片語應該很少使用，而且可能表示該類型應該是抽象類別，而不是介面。

 ❌不要為類別名稱提供前置詞（例如 "C"）。

 ✔️考慮使用基類的名稱來結束衍生類別的名稱。

 這是非常容易閱讀的，並且清楚地說明關聯性。 在程式碼中的一些範例是： `ArgumentOutOfRangeException` ，這是一種 `Exception` 、和 `SerializableAttribute` ，這是一種類型 `Attribute` 。 不過，請務必在套用此指導方針時使用合理的判斷。例如， `Button` 類別是一種 `Control` 事件，但 `Control` 不會出現在其名稱中。

 ✔️在介面名稱前面加上字母 I，表示該類型為介面。

 例如， `IComponent` （描述性名詞）、 `ICustomAttributeProvider` （名詞片語）和 `IPersistable` （形容詞）是適當的介面名稱。 如同其他類型名稱，請避免使用縮寫。

 當您定義類別–介面組（其中類別是介面的標準執行）時，✔️確實會確保介面名稱上的 "I" 前置詞只有名稱不同。

## <a name="names-of-generic-type-parameters"></a>泛型型別參數的名稱
 泛型已加入至 .NET Framework 2.0。 此功能引進了一種稱為「*型別參數*」的新識別碼。

 除非單一字母名稱完全一目了然，而且描述性名稱不會加上值，否則✔️ DO 名稱具有描述性名稱的泛型型別參數。

 ✔️請考慮使用 `T` 做為具有一個單字母類型參數之類型的類型參數名稱。

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️使用在描述性類型參數名稱前面加上 `T` 。

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️，請考慮在參數名稱中指出在類型參數上放置的條件約束。

 例如，受條件約束的參數 `ISession` 可能會被呼叫 `TSession` 。

## <a name="names-of-common-types"></a>一般類型的名稱
 ✔️請遵循下表中所述的指導方針來命名衍生自的型別，或執行特定的 .NET Framework 類型。

|基底類型|衍生/執行類型指導方針|
|---------------|------------------------------------------|
|`System.Attribute`|✔️請將尾碼 "Attribute" 新增至自訂屬性類別的名稱。|
|`System.Delegate`|✔️請將後置詞 "EventHandler" 新增至事件中所使用的委派名稱。<br /><br /> ✔️請將後置詞「回呼」新增至委派的名稱，而非當做事件處理常式使用。<br /><br /> ❌請勿將後置詞「委派」新增至委派。|
|`System.EventArgs`|✔️新增尾碼 "EventArgs"。|
|`System.Enum`|❌請勿從這個類別衍生;請改用您的語言支援的關鍵字;例如，在 c # 中，使用 `enum` 關鍵字。<br /><br /> ❌請勿新增尾碼 "Enum" 或 "旗標"。|
|`System.Exception`|✔️新增尾碼 "Exception"。|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️新增尾碼「字典」。 請注意， `IDictionary` 是特定類型的集合，但這項指導方針優先于後面的較一般集合指導方針。|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️新增尾碼「集合」。|
|`System.IO.Stream`|✔️新增尾碼「串流」。|
|`CodeAccessPermission IPermission`|✔️新增尾碼「許可權」。|

## <a name="naming-enumerations"></a>命名列舉
 列舉類型的名稱（也稱為列舉）通常應該遵循標準類型命名規則（PascalCasing 等等）。 不過，還有其他適用于列舉的指導方針。

 ✔️請將單數類型名稱用於列舉，除非其值為位欄位。

 ✔️確實將複數型別名稱用於具有位欄位做為值（也稱為 flags 列舉）的列舉。

 ❌請不要在列舉型別名稱中使用 "Enum" 尾碼。

 ❌請不要在列舉型別名稱中使用「旗標」或「旗標」尾碼。

 ❌請不要在列舉值名稱上使用前置詞（例如，"ad" 代表 ADO enum，"rtf" 用於豐富文字列舉等等）。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)
- [命名方針](naming-guidelines.md)
