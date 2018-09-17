---
title: 編譯器所產生的例外狀況 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 476f5940b0b93d0c28bcd2bc9ca73147bc7bf3eb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45668453"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>編譯器所產生的例外狀況 (C# 程式設計手冊)
基本作業失敗時，.NET Framework 的 Common Language Runtime (CLR) 會自動擲回一些例外狀況。 下表列出這些例外狀況和其錯誤條件。  
  
|例外|描述|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|在算術運算期間所發生的例外狀況 (例如 <xref:System.DivideByZeroException> 和 <xref:System.OverflowException>) 的基底類別。|  
|<xref:System.ArrayTypeMismatchException>|陣列因項目的實際類型與陣列的實際類型不相容而無法儲存指定的項目時擲回。|  
|<xref:System.DivideByZeroException>|嘗試將整數值除以零時擲回。|  
|<xref:System.IndexOutOfRangeException>|索引小於零或超出陣列界限時嘗試編製陣列的索引時擲回。|  
|<xref:System.InvalidCastException>|從基底類型到介面或衍生類型的明確轉換在執行階段失敗時擲回。|  
|<xref:System.NullReferenceException>|嘗試參考值為 [null](../../../csharp/language-reference/keywords/null.md) 的物件時擲回。|  
|<xref:System.OutOfMemoryException>|嘗試使用 [new](../../../csharp/language-reference/keywords/new-operator.md) 運算子配置記憶體失敗時擲回。 這表示 Common Language Runtime 的可用記憶體己用完。|  
|<xref:System.OverflowException>|`checked` 內容中的算術運算溢位時擲回。|  
|<xref:System.StackOverflowException>|在因太多暫止方法呼叫而耗盡執行堆疊時擲回；通常表示非常深或無限遞迴。|  
|<xref:System.TypeInitializationException>|在靜態建構函式擲回例外狀況而且沒有相容的 `catch` 子句可攔截它時擲回。|  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/index.md)  
- [例外狀況處理](../../../csharp/programming-guide/exceptions/exception-handling.md)  
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
- [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
- [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
