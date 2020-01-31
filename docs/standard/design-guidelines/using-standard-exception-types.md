---
title: 使用標準例外狀況類型
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: 3caa94d9a39966614161e4b19201dcf6065776a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743548"
---
# <a name="using-standard-exception-types"></a>使用標準例外狀況類型
本節說明架構所提供的標準例外狀況，以及其使用方式的詳細資料。 清單完全不是完整的。 如需其他架構例外狀況類型的使用方式，請參閱 .NET Framework 參考檔。

## <a name="exception-and-systemexception"></a>Exception 和 SystemException
 ❌ 不會擲回 <xref:System.Exception?displayProperty=nameWithType> 或 <xref:System.SystemException?displayProperty=nameWithType>。

 除非您想要重新擲回，否則 ❌ 不會在 framework 程式碼中攔截 `System.Exception` 或 `System.SystemException`。

 ❌ 避免攔截 `System.Exception` 或 `System.SystemException`，但最上層的例外狀況處理常式除外。

## <a name="applicationexception"></a>ApplicationException
 ❌ 不會擲回或衍生自 <xref:System.ApplicationException>。

## <a name="invalidoperationexception"></a>InvalidOperationException
 如果物件處於不適當的狀態，✔️會擲回 <xref:System.InvalidOperationException>。

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException、System.argumentnullexception 和 ArgumentOutOfRangeException
 如果將不正確的引數傳遞給成員，✔️會擲回 <xref:System.ArgumentException> 或其中一個子類型。 偏好最常衍生的例外狀況類型（如果適用的話）。

 ✔️在擲回 `ArgumentException`的其中一個子類別時，請設定 `ParamName` 屬性。

 這個屬性代表導致擲回例外狀況的參數名稱。 請注意，您可以使用其中一個函式多載來設定屬性。

 ✔️請將 `value` 用於屬性 setter 的隱含值參數的名稱。

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException、IndexOutOfRangeException 和 AccessViolationException
 ❌ 不允許可公開呼叫的 Api 明確或隱含地擲回 <xref:System.NullReferenceException>、<xref:System.AccessViolationException>或 <xref:System.IndexOutOfRangeException>。 這些例外狀況是由執行引擎保留和擲回，而在大部分情況下則表示 bug。

 執行引數檢查以避免擲回這些例外狀況。 擲回這些例外狀況會公開可能隨著時間變更之方法的執行詳細資料。

## <a name="stackoverflowexception"></a>StackOverflowException
 ❌ 不會明確擲回 <xref:System.StackOverflowException>。 例外狀況應該僅由 CLR 明確擲回。

 ❌ 不會攔截 `StackOverflowException`。

 在出現任意堆疊溢位的情況中，幾乎不可能撰寫會保持一致的 managed 程式碼。 CLR 的非受控元件會使用探查將堆疊溢位移到妥善定義的位置，而不是從任意堆疊溢位進行備份，以保持一致。

## <a name="outofmemoryexception"></a>OutOfMemoryException
 ❌ 不會明確擲回 <xref:System.OutOfMemoryException>。 這個例外狀況只會由 CLR 基礎結構擲回。

## <a name="comexception-sehexception-and-executionengineexception"></a>ComException、SEHException 和 ExecutionEngineException
 ❌ 不會明確擲回 <xref:System.Runtime.InteropServices.COMException>、<xref:System.ExecutionEngineException>和 <xref:System.Runtime.InteropServices.SEHException>。 這些例外狀況只會由 CLR 基礎結構擲回。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [例外狀況的設計方針](../../../docs/standard/design-guidelines/exceptions.md)
