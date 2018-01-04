---
title: "例外狀況和效能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9a876a818086e0d54251f53a1e8f83cc74a574ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="exceptions-and-performance"></a>例外狀況和效能
一個常見的問題相關的例外狀況是針對經常失敗的程式碼使用例外狀況，如果實作的效能將會無法接受。 這是有效的問題。 當成員擲回例外狀況時，其效能可能會大幅度速度較慢。 不過，它是達成目標時不允許使用錯誤碼的例外狀況指導方針嚴格遵守良好的效能。 本節中所述的兩種模式提供的建議執行這項操作。  
  
 **X 不**使用錯誤碼，例外狀況可能會造成負面影響效能的考量。  
  
 若要改善效能，便可使用 Tester-doer 模式或再試一次剖析模式，在下兩節中所述。  
  
## <a name="tester-doer-pattern"></a>Tester-doer 模式  
 有時例外狀況擲回成員的可改善效能的分成兩個成員。 讓我們看看<xref:System.Collections.Generic.ICollection%601.Add%2A>方法<xref:System.Collections.Generic.ICollection%601>介面。  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 此方法`Add`會擲回，如果集合是唯讀狀態。 這可以是在方法呼叫失敗通常預期有效能問題。 其中一種方式來緩和這個問題是測試集合是否為可寫入之前嘗試加入的值。  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 用來測試條件，這在我們的範例是屬性之成員`IsReadOnly`，指軟體測試人員。 用於執行可能會擲回的作業，該成員`Add`在本例中，方法指 doer。  
  
 **✓ 考慮**Tester-doer 模式，可能會擲回例外狀況的成員在一般案例，以避免發生效能問題相關的例外狀況。  
  
## <a name="try-parse-pattern"></a>嘗試剖析模式  
 適用於極重視效能的 Api，應該使用更快的模式比上一節中所述的 Tester-doer 模式。 此模式需要調整的成員名稱來讓妥善定義的測試大小寫的成員語意的一部分。 例如，<xref:System.DateTime>定義<xref:System.DateTime.Parse%2A>剖析字串的失敗時，擲回例外狀況的方法。 它也會定義對應<xref:System.DateTime.TryParse%2A>嘗試剖析，但如果方法傳回 false 剖析器失敗，並傳回成功剖析使用的結果`out`參數。  
  
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
  
 當使用此模式時，務必在嚴格的詞彙定義再試一次功能。 如果成員失敗，因為任何原因以外完善再試一次，成員必須仍會擲回對應的例外狀況。  
  
 **✓ 考慮**再試一次剖析模式，可能會擲回例外狀況的成員在一般案例，以避免發生效能問題相關的例外狀況。  
  
 **✓ 不要**方法實作這個模式使用的前置詞"Try"和布林值傳回型別。  
  
 **✓ 不要**擲回例外狀況的成員提供使用 Try 剖析模式，每個成員。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [例外狀況的設計方針](../../../docs/standard/design-guidelines/exceptions.md)
