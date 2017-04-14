---
title: "例外狀況和效能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "tester-doer 模式"
  - "TryParse 模式"
  - "例外狀況，擲回"
  - "例外狀況、 效能"
  - "擲回例外狀況，效能"
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 例外狀況和效能
其中一個相關的例外狀況的一般考量是經常失敗的程式碼使用例外狀況，如果實作的效能將無法接受。 這才是有效的問題。 當成員擲回例外狀況時，其效能可能會的速度變慢。 不過，就可以達到良好效能，同時嚴格遵守不允許使用錯誤碼的例外狀況方針。 本節中所述的兩種模式建議執行這項操作的方法。  
  
 **X 不** 例外狀況可能會造成負面影響效能的考量而使用錯誤碼。  
  
 若要改善效能，就可以使用 Tester\-doer 模式或嘗試剖析模式，在接下來兩節中所述。  
  
## Tester\-doer 模式  
 有時可以改善效能的擲回例外狀況的成員分成兩個成員。 讓我們看看 <xref:System.Collections.Generic.ICollection%601.Add%2A> 方法 <xref:System.Collections.Generic.ICollection%601> 介面。  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 此方法 `Add` 會擲回，如果集合是唯讀的。 這可以是在方法呼叫希望容易失敗的情況下的效能問題。 其中一種方式，來緩和這個問題是測試集合是否為可寫入之前，先新增一個值。  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 用來測試條件，這在我們的範例是屬性的成員 `IsReadOnly`, ，就是軟體測試人員。 用來執行作業可能會擲回，成員 `Add` doer 指在我們的範例方法。  
  
 **✓ 考慮** Tester\-doer 模式，可能會擲回例外狀況的成員在一般案例，以避免發生效能問題相關的例外狀況。  
  
## 嘗試剖析模式  
 對於極為重視效能的 Api，應該使用比上一節中所述的 Tester\-doer 模式更快的模式。 模式需要調整的成員名稱來進行完善的測試案例的一部分成員語意 （semantics）。 例如， <xref:System.DateTime> 定義 <xref:System.DateTime.Parse%2A> 字串的剖析失敗時，擲回例外狀況的方法。 它也會定義對應 <xref:System.DateTime.TryParse%2A> ，嘗試剖析，但如果方法傳回 false 剖析失敗並傳回結果的成功剖析使用 `out` 參數。  
  
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
  
 使用此模式時，務必在嚴格的詞彙定義試功能。 如果成員無法妥善定義 try 以外的任何原因，該成員仍必須對應的例外狀況擲回。  
  
 **✓ 考慮** 的成員可能會擲回例外狀況，請嘗試剖析模式在一般案例，以避免發生效能問題相關的例外狀況。  
  
 **✓ 執行** 實作此模式的方法使用的前置詞 「 Try 」 和布林值傳回的型別。  
  
 **✓ 執行** 提供使用 Try 剖析模式的每個成員擲回例外狀況的成員。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [例外狀況的設計指導方針](../../../docs/standard/design-guidelines/exceptions.md)