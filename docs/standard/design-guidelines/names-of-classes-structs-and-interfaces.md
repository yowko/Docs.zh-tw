---
title: 類別、結構和介面的名稱
description: 使用這些指導方針來命名類別、結構和介面，作為設計延伸和互動 .NET 程式庫之程式庫的指導方針。
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
ms.openlocfilehash: 49bafda0d5c362fa02313c5304436069d054cfd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706511"
---
# <a name="names-of-classes-structs-and-interfaces"></a>類別、結構和介面的名稱

接下來的命名指導方針適用于一般類型命名。

 ✔️使用 PascalCasing，利用名詞或名詞片語來命名類別和結構。

 這會從以動詞片語命名的方法中區分型別名稱。

 ✔️使用形容詞片語命名介面，或偶爾使用名詞或名詞片語。

 名詞和名詞片語應該很少使用，而且可能表示型別應該是抽象類別，而不是介面。

 ❌ 請勿將類別名稱指定為首碼 (例如 "C" ) 。

 ✔️考慮以基類的名稱結束衍生類別的名稱。

 這非常容易閱讀，並清楚說明關聯性。 程式碼中的一些範例包括：，也就是一種類型的 `ArgumentOutOfRangeException` `Exception` `SerializableAttribute` `Attribute` 。 不過，請務必在套用此指導方針時使用合理的判斷提示;例如， `Button` 類別是一種 `Control` 事件，但 `Control` 不會出現在其名稱中。

 ✔️使用字母 I 來加上前置詞介面名稱，以表示類型為介面。

 例如， `IComponent` (描述性名詞) 、 `ICustomAttributeProvider` (名詞片語) ，以及 `IPersistable` (形容詞) 是適當的介面名稱。 如同其他型別名稱，請避免使用縮寫。

 ✔️確定只有當您定義類別–介面組（其中類別是介面的標準實作為）時，介面名稱上的 "I" 前置詞才會有不同的名稱。

## <a name="names-of-generic-type-parameters"></a>泛型型別參數的名稱

 泛型已新增至 .NET Framework 2.0。 此功能引進了一種稱為 *類型參數* 的新識別碼。

 ✔️使用描述性的名稱來命名泛型型別參數，除非單一字母名稱完全一目了然，而且描述性名稱不會加上價值。

 ✔️請考慮使用做為類型 `T` 參數名稱的類型參數名稱，且類型為單一字母類型參數。

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️使用將描述性類型參數名稱加上前置詞 `T` 。

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️請考慮在參數名稱中指出在類型參數上放置的條件約束。

 例如，可能會呼叫受限制的參數 `ISession` `TSession` 。

## <a name="names-of-common-types"></a>一般類型的名稱

 ✔️確實遵循下表所述的指導方針來命名衍生自的型別，或執行某些 .NET Framework 類型。

|基底類型|衍生/實作為型別指導方針|
|---------------|------------------------------------------|
|`System.Attribute`|✔️將尾碼 "Attribute" 新增至自訂屬性類別的名稱。|
|`System.Delegate`|✔️請將後置詞 "EventHandler" 新增至事件中所使用之委派的名稱。<br /><br /> ✔️請將尾碼 "Callback" 新增至委派的名稱，而非做為事件處理常式使用的委派名稱。<br /><br /> ❌ 請勿將尾碼 "Delegate" 新增至委派。|
|`System.EventArgs`|✔️新增尾碼 "EventArgs"。|
|`System.Enum`|❌ 請勿從此類別衍生。請改用您的語言所支援的關鍵字;例如，在 c # 中使用 `enum` 關鍵字。<br /><br /> ❌ 請勿新增尾碼 "Enum" 或 "Flag"。|
|`System.Exception`|✔️新增尾碼「例外」。|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️新增尾碼「字典」。 請注意， `IDictionary` 這是特定類型的集合，但此指導方針優先于下面的一般集合指導方針。|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️新增尾碼「集合」。|
|`System.IO.Stream`|✔️新增尾碼 "Stream"。|
|`CodeAccessPermission IPermission`|✔️新增尾碼] 許可權。|

## <a name="naming-enumerations"></a>命名列舉

 列舉類型的名稱 (也稱為列舉) 一般應該遵循標準型別命名規則 (PascalCasing 等 ) 。 不過，還有其他適用于列舉的指導方針。

 除非其值為位欄位，否則✔️請使用列舉型別的單數型別名稱。

 ✔️請將複數類型名稱用於具有位欄位的列舉值，也稱為旗標列舉。

 ❌ 請勿在列舉型別名稱中使用 "Enum" 尾碼。

 ❌ 請勿在列舉型別名稱中使用 "Flag" 或 "Flags" 尾碼。

 ❌ 請勿在列舉值名稱上使用前置詞 (例如，"ad" 代表 ADO 列舉、"rtf" 代表 rich text 列舉等 ) 。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [架構設計指導方針](index.md)
- [命名指導方針](naming-guidelines.md)
