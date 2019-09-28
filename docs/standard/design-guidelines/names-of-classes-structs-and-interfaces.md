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
author: KrzysztofCwalina
ms.openlocfilehash: 2ecd708ccb8eb91270e8ef9c174b8d7e599a2629
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353718"
---
# <a name="names-of-classes-structs-and-interfaces"></a>類別、結構和介面的名稱
後面的命名指導方針適用于一般類型命名。  
  
 **✓ DO** 命名類別與結構名詞或名詞片語，使用 PascalCasing。  
  
 這會區分方法中的型別名稱，其以動詞片語命名。  
  
 **✓ DO** 命名介面與形容詞片語，或有時候名詞或名詞片語。  
  
 名詞和名詞片語應該很少使用，而且可能表示該類型應該是抽象類別，而不是介面。  
  
 **X DO NOT** 提供以類別名稱的前置詞 (例如，"C")。  
  
 **✓ CONSIDER** 名稱的結尾衍生的基底類別名稱的類別。  
  
 這是非常容易閱讀的，並且清楚地說明關聯性。 程式碼中的一些範例如下： `ArgumentOutOfRangeException`，這是一種 `Exception`，而 `SerializableAttribute`，這是一種 `Attribute`。 不過，請務必在套用此指導方針時使用合理的判斷。例如，`Button` 類別是一種 `Control` 事件，但 `Control` 不會出現在其名稱中。  
  
 **✓ DO** 前置詞介面名稱以字母 I，表示型別是介面。  
  
 例如，`IComponent` （描述性名詞）、`ICustomAttributeProvider` （名詞片語）和 `IPersistable` （形容詞）都是適當的介面名稱。 如同其他類型名稱，請避免使用縮寫。  
  
 **✓ DO** 確保僅由"I"前置詞上的介面名稱定義在類別是標準的介面實作的一組類別 – 介面時，名稱會不同。  
  
## <a name="names-of-generic-type-parameters"></a>泛型型別參數的名稱  
 泛型已加入至 .NET Framework 2.0。 此功能引進了一種稱為「*型別參數*」的新識別碼。  
  
 **✓ DO** 泛型型別參數名稱使用描述性名稱，除非單一字母名稱是完全一目了然，而且專案的描述性名稱不會加入值。  
  
 **✓ CONSIDER** 使用 `T` 做為型別參數名稱與一個單一字母的型別參數的類型。  
  
```csharp  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ DO** 描述性型別參數名稱前面加上 `T`。  
  
```csharp  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDER** 指出條件約束放在以參數名稱的型別參數上。  
  
 例如，限制為 `ISession` 的參數可能會被呼叫 `TSession`。  
  
## <a name="names-of-common-types"></a>一般類型的名稱  
 **✓ DO** 遵循命名型別衍生自或實作特定的.NET Framework 型別時下, 表中所述的指導方針。  
  
|基底類型|衍生/執行類型指導方針|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ DO** 加入後置詞"Attribute"的自訂屬性的類別名稱。|  
|`System.Delegate`|**✓ DO** 將後置詞"事件處理常式 」 新增到事件中所使用的委派的名稱。<br /><br /> **✓ DO** 加入後置詞"Callback"名稱的委派以外做為事件處理常式。<br /><br /> **X DO NOT** 委派中加入後置詞 「 委派 」。|  
|`System.EventArgs`|**✓ DO** 加入後置詞"EventArgs。 」|  
|`System.Enum`|**X DO NOT** 衍生自這個類別使用改為您的語言支援的關鍵字; 例如，在 C# 中，使用 `enum` 關鍵字。<br /><br /> **X DO NOT** 加入後置詞 「 列舉 」 或 「 旗標。 」|  
|`System.Exception`|**✓ DO** 加入後置詞 「 例外狀況 」。|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ DO** 加入後置詞"字典。 請注意，`IDictionary` 是特定類型的集合，但這項指導方針優先于後面的較一般集合指導方針。|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ DO** 加入後置詞 「 集合 」。|  
|`System.IO.Stream`|**✓ DO** 加入後置詞"資料流。 」|  
|`CodeAccessPermission IPermission`|**✓ DO** 加入後置詞 「 權限。 」|  
  
## <a name="naming-enumerations"></a>命名列舉  
 列舉類型的名稱（也稱為列舉）通常應該遵循標準類型命名規則（PascalCasing 等等）。 不過，還有其他適用于列舉的指導方針。  
  
 **✓ DO** 使用單數的型別名稱的列舉型別，除非其值是位元欄位。  
  
 **✓ DO** 與位元欄位使用列舉的複數的型別名稱，做為值，也稱為旗標列舉。  
  
 **X DO NOT** 列舉型別名稱中使用的 「 列舉 」 後置詞。  
  
 **X DO NOT** 使用 」 的旗標 」 或"Flags"尾碼在列舉型別名稱。  
  
 **X DO NOT** 使用前置詞上的列舉值名稱 (例如，"ad"ADO 列舉。)、"rtf"rtf 文字列舉等等。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 從 @no__t 1Framework 設計指導方針中，@no__t 0Reprinted by 皮耳森教育，Inc. 的許可權：可重複使用的 .NET 程式庫、第2版 @ no__t-0 by Krzysztof Cwalina 和 Brad Abrams 的慣例、慣用語和模式，已于2008年10月22日發行，其為 Microsoft Windows 開發系列的一部分 Addison-Wesley Professional。 *  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
