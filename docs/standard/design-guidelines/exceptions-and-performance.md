---
title: 例外狀況和效能
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
author: KrzysztofCwalina
ms.openlocfilehash: f9fe3045d8bd8b4d625c5cd49bc18574ebb740de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707722"
---
# <a name="exceptions-and-performance"></a>例外狀況和效能
其中一個例外狀況的相關的一般考量，如果例外狀況會用於經常失敗的程式碼，實作的效能就是無法接受。 這是有效的考量。 當成員擲回例外狀況時，其效能可以呈數量級速度較慢。 不過，就可以達到良好的效能，同時完全符合不允許使用錯誤碼的例外狀況指導方針。 這一節所述的兩種模式提供建議這樣做。  
  
 **X DO NOT** 使用錯誤碼，例外狀況可能會造成負面影響效能的考量。  
  
 若要改善效能，就可以使用 Tester-doer 模式或嘗試剖析模式中，接下來兩節中所述。  
  
## <a name="tester-doer-pattern"></a>Tester-doer 模式  
 有時可以被提升效能例外狀況擲回成員的成員分成兩個。 讓我們看看<xref:System.Collections.Generic.ICollection%601.Add%2A>方法的<xref:System.Collections.Generic.ICollection%601>介面。  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 此方法`Add`如果集合是唯讀模式則會擲回。 這可以是在方法呼叫應該在其中經常失敗的情況下的效能問題。 其中一種方式，來緩和這個問題是測試集合是否為可寫入之前嘗試加入的值。  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 用來測試條件，這在我們的範例是屬性的成員`IsReadOnly`，稱為 「 測試人員。 用來執行可能擲回的作業，該成員`Add`在我們的範例，方法指 doer。  
  
 **✓ CONSIDER** Tester-doer 模式，可能會擲回例外狀況的成員在一般案例，以避免發生效能問題相關的例外狀況。  
  
## <a name="try-parse-pattern"></a>嘗試剖析模式  
 對於極為重視效能的 Api，應該使用與上一節中所述的 Tester-doer 模式甚至更快的模式。 此模式需要調整要定義完善的測試案例的一部分成員語意的成員名稱。 例如，<xref:System.DateTime>定義<xref:System.DateTime.Parse%2A>字串的剖析失敗時，擲回例外狀況的方法。 它也會定義相對應<xref:System.DateTime.TryParse%2A>嘗試剖析，但如果方法會傳回 false 剖析失敗，並傳回成功剖析使用結果`out`參數。  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 使用此模式時，務必在嚴格的詞彙定義試功能。 如果成員因為任何原因以外定義完善的嘗試失敗，成員必須仍會擲回對應的例外狀況。  
  
 **✓ CONSIDER** 再試一次剖析模式，可能會擲回例外狀況的成員在一般案例，以避免發生效能問題相關的例外狀況。  
  
 **✓ DO** 方法實作這個模式使用的前置詞"Try"和布林值傳回型別。  
  
 **✓ DO** 擲回例外狀況的成員提供使用 Try 剖析模式，每個成員。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [例外狀況的設計方針](../../../docs/standard/design-guidelines/exceptions.md)
