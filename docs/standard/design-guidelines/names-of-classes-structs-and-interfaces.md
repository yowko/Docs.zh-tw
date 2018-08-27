---
title: 類別、結構和介面的名稱
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f60a2283c01d0dc2665dafaa99ea52000aa3bc47
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931203"
---
# <a name="names-of-classes-structs-and-interfaces"></a>類別、結構和介面的名稱
請依照下列命名方針適用於一般類型命名。  
  
 **✓ DO** 命名類別與結構名詞或名詞片語，使用 PascalCasing。  
  
 這可以區別型別名稱與命名的動詞片語的方法。  
  
 **✓ DO** 命名介面與形容詞片語，或有時候名詞或名詞片語。  
  
 名詞和名詞片語應該很少使用，而且它們可能表示的類型應該是抽象類別，並不是介面。  
  
 **X DO NOT** 提供以類別名稱的前置詞 (例如，"C")。  
  
 **✓ CONSIDER** 名稱的結尾衍生的基底類別名稱的類別。  
  
 這是非常清楚易讀，並且清楚地說明的關聯性。 這個程式碼中的一些範例包括： `ArgumentOutOfRangeException`，這是一種類型的`Exception`，並`SerializableAttribute`，這是一種的`Attribute`。 不過，務必使用合理的判斷，在套用這個指導方針;例如，`Button`類別是一種類型的`Control`事件，雖然`Control`不會出現在其名稱。  
  
 **✓ DO** 前置詞介面名稱以字母 I，表示型別是介面。  
  
 例如， `IComponent` （描述性名詞）， `ICustomAttributeProvider` （名詞片語） 和`IPersistable`（形容詞） 是適當的介面名稱。 如同其他類型名稱，避免縮寫。  
  
 **✓ DO** 確保僅由"I"前置詞上的介面名稱定義在類別是標準的介面實作的一組類別 – 介面時，名稱會不同。  
  
## <a name="names-of-generic-type-parameters"></a>泛型類型參數的名稱  
 新增泛型功能是以.NET Framework 2.0。 此功能導入新類型的識別項稱為*型別參數*。  
  
 **✓ DO** 泛型型別參數名稱使用描述性名稱，除非單一字母名稱是完全一目了然，而且專案的描述性名稱不會加入值。  
  
 **✓ CONSIDER** 使用 `T` 做為型別參數名稱與一個單一字母的型別參數的類型。  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ DO** 描述性型別參數名稱前面加上 `T`。  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDER** 指出條件約束放在以參數名稱的型別參數上。  
  
 例如，參數限制為`ISession`可能呼叫`TSession`。  
  
## <a name="names-of-common-types"></a>常見類型的名稱  
 **✓ DO** 遵循命名型別衍生自或實作特定的.NET Framework 型別時下, 表中所述的指導方針。  
  
|基底類型|衍生/實作型別指導方針|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ DO** 加入後置詞"Attribute"的自訂屬性的類別名稱。|  
|`System.Delegate`|**✓ DO** 將後置詞"事件處理常式 」 新增到事件中所使用的委派的名稱。<br /><br /> **✓ DO** 加入後置詞"Callback"名稱的委派以外做為事件處理常式。<br /><br /> **X DO NOT** 委派中加入後置詞 「 委派 」。|  
|`System.EventArgs`|**✓ DO** 加入後置詞"EventArgs。 」|  
|`System.Enum`|**X DO NOT** 衍生自這個類別使用改為您的語言支援的關鍵字; 例如，在 C# 中，使用 `enum` 關鍵字。<br /><br /> **X DO NOT** 加入後置詞 「 列舉 」 或 「 旗標。 」|  
|`System.Exception`|**✓ DO** 加入後置詞 「 例外狀況 」。|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ DO** 加入後置詞"字典。 請注意，`IDictionary`特定類型的集合，但這項指導方針的優先順序高於遵循的一般集合指導方針。|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ DO** 加入後置詞 「 集合 」。|  
|`System.IO.Stream`|**✓ DO** 加入後置詞"資料流。 」|  
|`CodeAccessPermission IPermission`|**✓ DO** 加入後置詞 「 權限。 」|  
  
## <a name="naming-enumerations"></a>命名的列舉型別  
 一般情況下 （也稱為列舉） 的列舉類型的名稱應該遵循標準型別命名規則 （PascalCasing 等等）。 不過，有一些額外的指導方針僅適用於列舉。  
  
 **✓ DO** 使用單數的型別名稱的列舉型別，除非其值是位元欄位。  
  
 **✓ DO** 與位元欄位使用列舉的複數的型別名稱，做為值，也稱為旗標列舉。  
  
 **X DO NOT** 列舉型別名稱中使用的 「 列舉 」 後置詞。  
  
 **X DO NOT** 使用 」 的旗標 」 或"Flags"尾碼在列舉型別名稱。  
  
 **X DO NOT** 使用前置詞上的列舉值名稱 (例如，"ad"ADO 列舉。)、"rtf"rtf 文字列舉等等。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
