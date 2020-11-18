---
title: 使用標準例外狀況類型
description: 瞭解 .NET 中的標準例外狀況類型。 瞭解 SystemException、ApplicationException、ArgumentException、ComException 等等。
ms.date: 10/22/2008
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: d8e75f7104b755476f255563c9c1f7ece14f67db
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828461"
---
# <a name="using-standard-exception-types"></a>使用標準例外狀況類型
本節說明架構所提供的標準例外狀況，以及其使用方式的詳細資料。 這份清單並不完整。 請參閱 .NET Framework 參考檔，以取得其他架構例外狀況類型的使用方式。

## <a name="exception-and-systemexception"></a>例外狀況和 SystemException
 ❌ 請勿擲回 <xref:System.Exception?displayProperty=nameWithType> 或 <xref:System.SystemException?displayProperty=nameWithType> 。

 ❌ 除非您想要重新擲回，否則請勿攔截 `System.Exception` 或 `System.SystemException` 在架構程式碼中。

 ❌ 避免攔截 `System.Exception` 或 `System.SystemException` （除了最上層例外狀況處理常式之外）。

## <a name="applicationexception"></a>ApplicationException
 ❌ 請勿擲回或衍生自 <xref:System.ApplicationException> 。

## <a name="invalidoperationexception"></a>InvalidOperationException
 <xref:System.InvalidOperationException>如果物件處於不適當的狀態，✔️就會擲回。

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException、System.argumentnullexception 和 ArgumentOutOfRangeException
 <xref:System.ArgumentException>如果將不正確的引數傳遞給成員，✔️會擲回或其中一個子類型。 偏好最常衍生的例外狀況類型（如果適用）。

 ✔️當擲回 `ParamName` 的其中一個子類別時，請設定屬性 `ArgumentException` 。

 此屬性代表導致擲回例外狀況的參數名稱。 請注意，您可以使用其中一個函數多載來設定屬性。

 ✔️請將 `value` 用於屬性 setter 的隱含值參數名稱。

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException、IndexOutOfRangeException 和了 [accessviolationexception
 ❌ 不允許可公開呼叫的 Api 明確或隱含地擲回 <xref:System.NullReferenceException> 、 <xref:System.AccessViolationException> 或 <xref:System.IndexOutOfRangeException> 。 這些例外狀況會由執行引擎保留並擲回，而在大部分情況下，則表示有錯誤。

 請檢查引數，以避免擲回這些例外狀況。 擲回這些例外狀況會公開可能隨著時間變更之方法的執行詳細資料。

## <a name="stackoverflowexception"></a>StackOverflowException
 ❌ 不要明確擲回 <xref:System.StackOverflowException> 。 例外狀況只能由 CLR 明確擲回。

 ❌ 請勿攔截 `StackOverflowException` 。

 撰寫 managed 程式碼時，幾乎不可能發生任意堆疊溢位的情況。 CLR 未受管理的部分保持一致，方法是使用探查將堆疊溢位移至妥善定義的位置，而不是從任意堆疊溢位進行備份。

## <a name="outofmemoryexception"></a>OutOfMemoryException
 ❌ 不要明確擲回 <xref:System.OutOfMemoryException> 。 只有 CLR 基礎結構才會擲回這個例外狀況。

## <a name="comexception-sehexception-and-executionengineexception"></a>ComException、SEHException 和 ExecutionEngineException
 ❌ 請勿明確擲回 <xref:System.Runtime.InteropServices.COMException> 、  <xref:System.ExecutionEngineException> 和 <xref:System.Runtime.InteropServices.SEHException> 。 這些例外狀況只能由 CLR 基礎結構擲回。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [架構設計指導方針](index.md)
- [例外狀況的設計方針](exceptions.md)
