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
ms.openlocfilehash: a1841fbfcb76d5b56681b63ec4b39e9a7418707f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576138"
---
# <a name="names-of-classes-structs-and-interfaces"></a>類別、結構和介面的名稱
遵循的命名指導方針適用於一般類型命名。  
  
 **✓ 不要**命名類別與結構名詞或名詞片語，使用 PascalCasing。  
  
 這個區別型別名稱與命名的動詞片語的方法。  
  
 **✓ 不要**命名介面與形容詞片語，或有時候名詞或名詞片語。  
  
 名詞和名詞片語應該很少使用，它們可能表示的類型應該是抽象類別，並不是介面。  
  
 **X 不**提供以類別名稱的前置詞 (例如，"C")。  
  
 **✓ 考慮**名稱的結尾衍生的基底類別名稱的類別。  
  
 這是不易閱讀，而且清楚地說明的關聯性。 這個程式碼中的某些範例包括： `ArgumentOutOfRangeException`，這是一種的`Exception`，和`SerializableAttribute`，這是一種的`Attribute`。 不過，請務必使用合理判斷在套用這個指導方針。例如，`Button`類別是一種的`Control`事件，雖然`Control`不會出現在其名稱。  
  
 **✓ 不要**前置詞介面名稱以字母 I，表示型別是介面。  
  
 例如， `IComponent` （描述性名詞） `ICustomAttributeProvider` （名詞片語） 和`IPersistable`（形容詞） 是適當的介面名稱。 如同其他類型名稱，避免縮寫。  
  
 **✓ 不要**確保僅由"I"前置詞上的介面名稱定義在類別是標準的介面實作的一組類別 – 介面時，名稱會不同。  
  
## <a name="names-of-generic-type-parameters"></a>泛型型別參數的名稱  
 泛型已新增至.NET Framework 2.0。 此功能導入了一種新的識別項稱為*型別參數*。  
  
 **✓ 不要**泛型型別參數名稱使用描述性名稱，除非單一字母名稱是完全一目了然，而且專案的描述性名稱不會加入值。  
  
 **✓ 考慮**使用`T`做為型別參數名稱與一個單一字母的型別參數的類型。  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ 不要**描述性型別參數名稱前面加上`T`。  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 **✓ 考慮**指出條件約束放在以參數名稱的型別參數上。  
  
 例如，將參數限制為`ISession`可能呼叫`TSession`。  
  
## <a name="names-of-common-types"></a>一般型別的名稱  
 **✓ 不要**遵循命名型別衍生自或實作特定的.NET Framework 型別時下, 表中所述的指導方針。  
  
|基底類型|衍生/實作型別指導方針|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ 不要**加入後置詞"Attribute"的自訂屬性的類別名稱。|  
|`System.Delegate`|**✓ 不要**將後置詞"事件處理常式 」 新增到事件中所使用的委派的名稱。<br /><br /> **✓ 不要**加入後置詞"Callback"名稱的委派以外做為事件處理常式。<br /><br /> **X 不**委派中加入後置詞 「 委派 」。|  
|`System.EventArgs`|**✓ 不要**加入後置詞"EventArgs。 」|  
|`System.Enum`|**X 不**衍生自這個類別使用改為您的語言支援的關鍵字; 例如，在 C# 中，使用`enum`關鍵字。<br /><br /> **X 不**加入後置詞 「 列舉 」 或 「 旗標。 」|  
|`System.Exception`|**✓ 不要**加入後置詞 「 例外狀況 」。|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ 不要**加入後置詞"字典。 請注意，`IDictionary`特定類型的集合，但這項指導方針的優先順序高於遵循的一般集合導線。|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ 不要**加入後置詞 「 集合 」。|  
|`System.IO.Stream`|**✓ 不要**加入後置詞"資料流。 」|  
|`CodeAccessPermission IPermission`|**✓ 不要**加入後置詞 「 權限。 」|  
  
## <a name="naming-enumerations"></a>命名列舉型別  
 一般情況下 （也稱為列舉） 的列舉類型的名稱應該遵循的一般型別命名規則 （PascalCasing 等等）。 不過，有一些額外的指導方針適用於列舉。  
  
 **✓ 不要**使用單數的型別名稱的列舉型別，除非其值是位元欄位。  
  
 **✓ 不要**與位元欄位使用列舉的複數的型別名稱，做為值，也稱為旗標列舉。  
  
 **X 不**列舉型別名稱中使用的 「 列舉 」 後置詞。  
  
 **X 不**使用 」 的旗標 」 或"Flags"尾碼在列舉型別名稱。  
  
 **X 不**使用前置詞上的列舉值名稱 (例如，"ad"ADO 列舉。)、"rtf"rtf 文字列舉等等。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
