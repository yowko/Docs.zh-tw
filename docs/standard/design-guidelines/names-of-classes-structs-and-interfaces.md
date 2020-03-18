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
# <a name="names-of-classes-structs-and-interfaces"></a>類別、結構和介面的名稱
以下命名準則適用于常規類型命名。

 ✔️使用 PascalCasing 命名類和帶有名詞或名詞短語的結構。

 這將類型名稱與用動詞短語命名的方法區分開來。

 ✔️使用形容詞短語，或偶爾使用名詞或名詞短語進行命名介面。

 名詞和名詞短語應很少使用，它們可能表示類型應為抽象類別，而不是介面。

 ❌不要給類名首碼（例如，"C"）。

 ✔️考慮用基類的名稱結束派生類的名稱。

 這是非常可讀的，並清楚地解釋了這種關係。 代碼中這方面的一些示例是： `ArgumentOutOfRangeException`，這是一種`Exception`，和`SerializableAttribute`，是 一`Attribute`種 。 但是，在適用本準則時，必須運用合理的判斷;例如，`Button`類是一種`Control`事件，儘管`Control`未出現在其名稱中。

 ✔️ DO 首碼介面名稱與字母 I，以指示類型是介面。

 例如，（`IComponent`描述性名詞）、（`ICustomAttributeProvider`名詞短語）和`IPersistable`（形容詞）是適當的介面名稱。 與其他類型名稱一樣，請避免縮寫。

 ✔️，在定義類介面對時，確保名稱僅與介面名稱上的"I"首碼不同，其中類是介面的標準實現。

## <a name="names-of-generic-type-parameters"></a>泛型型別參數的名稱
 泛型已添加到 .NET 框架 2.0 中。 該功能引入了一種稱為*類型參數*的識別碼。

 ✔️ DO 名稱泛型型別參數（帶有描述性名稱）除非單字母名稱完全不言自明，並且描述性名稱不會增加值。

 ✔️考慮使用`T`具有單字母類型參數的類型作為類型參數名稱。

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️ DO 首碼描述性`T`類型參數名稱。

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️考慮指示在參數名稱中對類型參數放置的約束。

 例如，約束到`ISession`的參數可能稱為`TSession`。

## <a name="names-of-common-types"></a>常見類型的名稱
 ✔️命名派生自某些 .NET 框架類型或實現某些 .NET 框架類型時，請遵循下表中描述的準則。

|基底類型|派生/實現類型指南|
|---------------|------------------------------------------|
|`System.Attribute`|✔️DO將尾碼"屬性"添加到自訂屬性類的名稱中。|
|`System.Delegate`|✔️DO將尾碼"事件處理常式"添加到事件中使用的委託名稱中。<br /><br /> ✔️將尾碼"回檔"添加到用作事件處理常式的委託名稱以外的委託名稱中。<br /><br /> ❌不要將尾碼"委託"添加到委託。|
|`System.EventArgs`|✔️添加尾碼"事件阿格"。|
|`System.Enum`|❌不要從此類派生;因此，請勿從此類派生。改用語言支援的關鍵字;例如，在 C# 中，`enum`使用 關鍵字。<br /><br /> ❌請勿添加尾碼"枚舉"或"標記"。|
|`System.Exception`|✔️添加尾碼"異常"。|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️添加尾碼"字典"。 請注意，`IDictionary`這是特定類型的集合，但此準則優先于以下更常規的集合準則。|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️添加尾碼"集合"。|
|`System.IO.Stream`|✔️添加尾碼"流"。|
|`CodeAccessPermission IPermission`|✔️添加尾碼"許可權"。|

## <a name="naming-enumerations"></a>命名枚舉
 枚舉類型（也稱為枚舉）的名稱通常應遵循標準類型命名規則（PascalCasing 等）。 但是，還有其他特別適用于枚舉的準則。

 ✔️DO使用單一類型名稱進行枚舉，除非其值為位欄位。

 ✔️DO使用複數類型名稱進行枚舉，其中位欄位為值，也稱為標誌枚舉。

 ❌請勿在枚舉類型名稱中使用"枚舉"尾碼。

 ❌請勿在枚舉類型名稱中使用"標記"或"標記"尾碼。

 ❌請勿在枚舉值名稱上使用首碼（例如，ADO 枚舉的"ad"，富文本枚舉的"rtf"等）。

 *部分© 2005， 2009 微軟公司.保留擁有權利。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
