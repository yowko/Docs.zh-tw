---
title: "編譯器所產生的例外狀況 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "例外狀況 [C#], 編譯器產生"
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# 編譯器所產生的例外狀況 (C# 程式設計手冊)
當基本運算失敗時，.NET Framework 的 Common Language Runtime \(CLR\) 會自動擲回某些例外狀況。  這些例外狀況及其錯誤條件會在下表中列出。  
  
|例外狀況|描述|  
|----------|--------|  
|<xref:System.ArithmeticException>|在算術作業期間發生的例外狀況的基底類別，例如 <xref:System.DivideByZeroException> 和 <xref:System.OverflowException>。|  
|<xref:System.ArrayTypeMismatchException>|陣列無法儲存指定元素時會擲回這個例外狀況，因為元素的實際型別與陣列的實際型別不相容。|  
|<xref:System.DivideByZeroException>|嘗試用零除整數值時會擲回此例外狀況。|  
|<xref:System.IndexOutOfRangeException>|嘗試以小於零或超出陣列界限的索引值建立陣列索引時，會擲回此例外狀況。|  
|<xref:System.InvalidCastException>|在執行階段將基底型別明確轉換成介面或衍生型別發生失敗時，會擲回此例外狀況。|  
|<xref:System.NullReferenceException>|在嘗試參考值為 [null](../../../csharp/language-reference/keywords/null.md) 的物件時，會擲回此例外狀況。|  
|<xref:System.OutOfMemoryException>|在嘗試使用 [new](../../../csharp/language-reference/keywords/new-operator.md) 運算子配置記憶體但卻失敗時，會擲回此例外狀況。  這個例外狀況指出已用盡 Common Language Runtime 可用的記憶體。|  
|<xref:System.OverflowException>|在 `checked` 內容中的算術運算溢位時，會擲回此例外狀況。|  
|<xref:System.StackOverflowException>|因有太多待處理的方法呼叫而導致執行堆疊耗盡時，會擲回這個例外狀況，這通常表示發生深層或無窮遞迴。|  
|<xref:System.TypeInitializationException>|靜態建構函式擲回例外狀況，但沒有相容的 `catch` 子句攔截它時，會擲回此例外狀況。|  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [例外狀況處理](../../../csharp/programming-guide/exceptions/exception-handling.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)