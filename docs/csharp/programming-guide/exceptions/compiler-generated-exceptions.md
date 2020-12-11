---
title: 編譯器所產生的例外狀況 - C# 程式設計手冊
description: 瞭解編譯器產生的例外狀況。 檢查自動擲回的例外狀況及其錯誤狀況的清單。
ms.date: 12/09/2020
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 43bacbb1025bc0af3a5f21979315b3d1b0d61066
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110347"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>編譯器所產生的例外狀況 (C# 程式設計手冊)

當基本作業失敗時，.NET 執行時間會自動擲回一些例外狀況。 下表列出這些例外狀況和其錯誤條件。

|例外狀況|描述|
|---------------|-----------------|
|<xref:System.ArithmeticException>|在算術運算期間所發生的例外狀況 (例如 <xref:System.DivideByZeroException> 和 <xref:System.OverflowException>) 的基底類別。|
|<xref:System.ArrayTypeMismatchException>|當陣列無法儲存指定的專案時擲回，因為元素的實際類型與陣列的實際類型不相容。|
|<xref:System.DivideByZeroException>|嘗試將整數值除以零時擲回。|
|<xref:System.IndexOutOfRangeException>|索引小於零或超出陣列界限時嘗試編製陣列的索引時擲回。|
|<xref:System.InvalidCastException>|從基底類型到介面或衍生類型的明確轉換在執行階段失敗時擲回。|
|<xref:System.NullReferenceException>|嘗試參考其值為 [null](../../language-reference/keywords/null.md)的物件時擲回。|
|<xref:System.OutOfMemoryException>|嘗試使用 [new](../../language-reference/operators/new-operator.md) 運算子配置記憶體失敗時擲回。 這個例外狀況表示通用語言執行時間可用的記憶體已用盡。|
|<xref:System.OverflowException>|`checked` 內容中的算術運算溢位時擲回。|
|<xref:System.StackOverflowException>|在因太多暫止方法呼叫而耗盡執行堆疊時擲回；通常表示非常深或無限遞迴。|
|<xref:System.TypeInitializationException>|在靜態建構函式擲回例外狀況而且沒有相容的 `catch` 子句可攔截它時擲回。|

## <a name="see-also"></a>另請參閱

- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
