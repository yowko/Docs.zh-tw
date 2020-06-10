---
title: 使用標準例外狀況類型
description: 瞭解 .NET 中的標準例外狀況類型。 深入瞭解 SystemException、ApplicationException、ArgumentException、ComException 等等。
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: f95529eabd87d9ec7c379b9f790e039e1192ac53
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663053"
---
# <a name="using-standard-exception-types"></a>使用標準例外狀況類型
本節說明架構所提供的標準例外狀況，以及其使用方式的詳細資料。 清單完全不是完整的。 如需其他架構例外狀況類型的使用方式，請參閱 .NET Framework 參考檔。

## <a name="exception-and-systemexception"></a>Exception 和 SystemException
 ❌請勿擲回 <xref:System.Exception?displayProperty=nameWithType> 或 <xref:System.SystemException?displayProperty=nameWithType> 。

 ❌除非您想要重新擲回，否則請勿攔截 `System.Exception` 或 `System.SystemException` 在架構程式碼中。

 ❌避免攔截 `System.Exception` 或 `System.SystemException` ，但最上層例外狀況處理常式除外。

## <a name="applicationexception"></a>ApplicationException
 ❌不擲回或衍生自 <xref:System.ApplicationException> 。

## <a name="invalidoperationexception"></a>InvalidOperationException
 <xref:System.InvalidOperationException>如果物件處於不適當的狀態，✔️會擲回。

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException、System.argumentnullexception 和 ArgumentOutOfRangeException
 <xref:System.ArgumentException>如果將不正確的引數傳遞給成員，✔️會擲回或其中一個子類型。 偏好最常衍生的例外狀況類型（如果適用的話）。

 當擲回的 `ParamName` 其中一個子類別時，✔️設定屬性 `ArgumentException` 。

 這個屬性代表導致擲回例外狀況的參數名稱。 請注意，您可以使用其中一個函式多載來設定屬性。

 ✔️請使用做 `value` 為屬性 setter 之隱含值參數的名稱。

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException、IndexOutOfRangeException 和 AccessViolationException
 ❌不允許可公開呼叫的 Api 明確或隱含地擲回 <xref:System.NullReferenceException> 、 <xref:System.AccessViolationException> 或 <xref:System.IndexOutOfRangeException> 。 這些例外狀況是由執行引擎保留和擲回，而在大部分情況下則表示 bug。

 執行引數檢查以避免擲回這些例外狀況。 擲回這些例外狀況會公開可能隨著時間變更之方法的執行詳細資料。

## <a name="stackoverflowexception"></a>StackOverflowException
 ❌請勿明確擲回 <xref:System.StackOverflowException> 。 例外狀況應該僅由 CLR 明確擲回。

 ❌不要攔截 `StackOverflowException` 。

 在出現任意堆疊溢位的情況中，幾乎不可能撰寫會保持一致的 managed 程式碼。 CLR 的非受控元件會使用探查將堆疊溢位移到妥善定義的位置，而不是從任意堆疊溢位進行備份，以保持一致。

## <a name="outofmemoryexception"></a>OutOfMemoryException
 ❌請勿明確擲回 <xref:System.OutOfMemoryException> 。 這個例外狀況只會由 CLR 基礎結構擲回。

## <a name="comexception-sehexception-and-executionengineexception"></a>ComException、SEHException 和 ExecutionEngineException
 ❌請勿明確擲回 <xref:System.Runtime.InteropServices.COMException> 、 <xref:System.ExecutionEngineException> 和 <xref:System.Runtime.InteropServices.SEHException> 。 這些例外狀況只會由 CLR 基礎結構擲回。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)
- [例外狀況的設計方針](exceptions.md)
