---
title: "類別、 結構和介面的名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "型別名稱的指導方針"
  - "類別 [.NET Framework] 名稱"
  - "列舉 [.NET Framework] 名稱"
  - "名稱 [.NET Framework] 介面"
  - "一般型別名稱"
  - "名稱 [.NET Framework] 的型別名稱"
  - "名稱 [.NET Framework] 類別"
  - "介面 [.NET Framework] 名稱"
  - "泛型型別參數"
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# 類別、 結構和介面的名稱
請依照下列命名指導方針適用於一般類型命名。  
  
 **✓ 執行** 命名類別與結構名詞或名詞片語，使用 PascalCasing。  
  
 這可以區別型別名稱與命名的動詞片語的方法。  
  
 **✓ 執行** 命名形容詞片語，或有時候名詞或名詞片語的介面。  
  
 名詞和名詞片語應該使用很少，而且它們可能表示的類型應該是抽象類別，並不是介面。  
  
 **X 不** 為指定類別名稱的前置詞 \(例如，"C"\)。  
  
 **✓ 考慮** 名稱的結尾衍生的基底類別的類別名稱。  
  
 這是非常容易閱讀，而且清楚地說明的關聯性。 這個程式碼中的部分範例如下︰ `ArgumentOutOfRangeException`, ，這是一種的 `Exception`, ，和 `SerializableAttribute`, ，這是一種的 `Attribute`。 不過，請務必使用合理判斷在套用此指導方針。例如， `Button` 類別是一種類型的 `Control` 事件，雖然 `Control` 不會出現在其名稱。  
  
 **✓ 執行** 前置詞介面名稱以字母 I，以表示型別是介面。  
  
 例如， `IComponent` （描述性名詞） `ICustomAttributeProvider` （名詞片語） 和 `IPersistable` （形容詞） 是適當的介面名稱。 如同其他的型別名稱，避免縮寫。  
  
 **✓ 執行** 確保僅由"I"前置詞上的介面名稱定義其中類別是標準的介面實作的一組類別 – 介面時，名稱會不同。  
  
## 泛型型別參數的名稱  
 .NET Framework 2.0 已加入泛型。 此功能導入新類型的識別項稱為 *型別參數*。  
  
 **✓ 執行** 泛型型別參數名稱使用描述性名稱，除非單一字母名稱是完全一目了然，而且具描述性的名稱不會增加其值。  
  
 **✓ 考慮** 使用 `T` 做為型別參數名稱用於具有一個單一字母型別參數的類型。  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ 執行** 描述性型別參數名稱前面加上 `T`。  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 **✓ 考慮** 指出條件約束放在以參數名稱的型別參數。  
  
 例如，參數限制為 `ISession` 可能呼叫 `TSession`。  
  
## 一般型別的名稱  
 **✓ 執行** 遵循命名型別衍生自或實作特定的.NET Framework 型別時下, 表中所述的指導方針。  
  
|基底型別|衍生\/實作型別指導方針|  
|----------|------------------|  
|`System.Attribute`|**✓ 執行** 將後置詞 「 屬性 」 新增到自訂屬性類別的名稱。 將自訂屬性類別的名稱尾碼 \[屬性\]。|  
|`System.Delegate`|**✓ 執行** 將後置詞"事件處理常式 」 新增到事件中所使用的委派的名稱。<br /><br /> **✓ 執行** 加入做為事件處理常式之外的後置詞 「 回呼 」 名稱的委派。<br /><br /> **X 不** 加入委派的後置詞 「 委派 」。|  
|`System.EventArgs`|**✓ 執行** 新增尾碼"EventArgs 」。|  
|`System.Enum`|**X 不** 衍生自這個類別使用改為您的語言所支援的關鍵字; 例如，在 C\# 中，使用 enum 關鍵字。<br /><br /> **X 不** 加入後置詞 「 列舉 」 或 「 旗標 」。|  
|`System.Exception`|**✓ 執行** 加入後置詞 「 例外狀況 」。|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ 執行** 新增尾碼 \[字典\]。 請注意， `IDictionary` 是特定類型的集合，但這項指導方針的優先順序高於遵循的一般集合方針。|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ 執行** 加入後置詞 「 集合 」。|  
|`System.IO.Stream`|**✓ 執行** 加入後置詞 「 資料流 」。|  
|`CodeAccessPermission IPermission`|**✓ 執行** 加入後置詞 「 使用權限 」。|  
  
## 命名的列舉型別  
 一般的列舉型別 （也稱為列舉） 的名稱應遵循的一般型別命名規則 （PascalCasing 等）。 不過，有一些額外的指導方針適用於列舉。  
  
 **✓ 執行** 使用單數型別名稱的列舉型別，除非其值是位元欄位。  
  
 **✓ 執行** 具有位元欄位使用列舉的複數的型別名稱，做為值，也稱為旗標列舉。  
  
 **X 不** 列舉型別名稱中使用之 「 列舉 」 後置字元。  
  
 **X 不** 使用"標示"或"Flags"後的置字元在列舉型別名稱。  
  
 **X 不** 列舉值名稱 \(例如，"ad"適用於 ADO 的列舉。\)、 「 rtf 」 上使用前置詞 rich text 格式的列舉，依此類推。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)