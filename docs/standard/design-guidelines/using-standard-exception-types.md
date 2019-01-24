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
author: KrzysztofCwalina
ms.openlocfilehash: b947c7cce057c060b1ab5054d1227f5703ccbf89
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543902"
---
# <a name="using-standard-exception-types"></a>使用標準例外狀況類型
本章節描述的架構和其使用方式詳細資料所提供的標準例外狀況。 清單並不詳盡。 請參閱.NET Framework 參考文件的使用方式的其他 Framework 例外狀況型別。  
  
## <a name="exception-and-systemexception"></a>例外狀況和 SystemException  
 **X DO NOT** 擲回 <xref:System.Exception?displayProperty=nameWithType> 或 <xref:System.SystemException?displayProperty=nameWithType>。  
  
 **X DO NOT** 攔截 `System.Exception` 或 `System.SystemException` framework 程式碼中，除非您想要重新擲回。  
  
 **X AVOID** 攔截 `System.Exception` 或 `System.SystemException`，除非在最上層例外狀況處理常式。  
  
## <a name="applicationexception"></a>ApplicationException  
 **X DO NOT** 擲回或衍生自 <xref:System.ApplicationException>。  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ DO** 擲回 <xref:System.InvalidOperationException> 的物件是否不適當的狀態。  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException、 ArgumentNullException 和 ArgumentOutOfRangeException  
 **✓ DO** 擲回 <xref:System.ArgumentException> 或如果不正確的引數會傳遞給成員及其子型別之一。 如果適用的話，偏好使用最具衍生性的例外狀況類型。  
  
 **✓ DO** 設定 `ParamName` 屬性時擲回的子類別的其中一個 `ArgumentException`。  
  
 這個屬性代表造成擲回的例外狀況的參數名稱。 請注意，屬性可以使用其中一個建構函式多載設定。  
  
 **✓ DO** 使用 `value` 屬性 setter 的隱含值參數的名稱。  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException、 IndexOutOfRangeException 和 AccessViolationException  
 **X DO NOT** 允許公開呼叫 Api，明確或隱含地擲回 <xref:System.NullReferenceException>， <xref:System.AccessViolationException>， 或 <xref:System.IndexOutOfRangeException>。 這些例外狀況會保留並擲回的執行引擎在大部分情況下是 bug。  
  
 執行檢查，以避免擲回這些例外狀況的引數。 擲回這些例外狀況會公開實作詳細資料，您可能會隨著時間變更的方法。  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X DO NOT** 明確擲回 <xref:System.StackOverflowException>。 應該在只能由 CLR 明確擲回例外狀況。  
  
 **X DO NOT** 攔截 `StackOverflowException`。  
  
 它幾乎是不可能撰寫受管理的程式碼，保持一致且任意的堆疊溢位。 藉由使用探查來移動堆疊溢位為妥善定義的位置，而不是藉由從任意的堆疊溢位備份，CLR 的 unmanaged 的部分都保持一致。  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X DO NOT** 明確擲回 <xref:System.OutOfMemoryException>。 這個例外狀況是只由 CLR 基礎結構擲回。  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException、 SEHException 和 ExecutionEngineException  
 **X DO NOT** 明確擲回 <xref:System.Runtime.InteropServices.COMException>， <xref:System.ExecutionEngineException>，和 <xref:System.Runtime.InteropServices.SEHException>。 這些例外狀況是只由 CLR 基礎結構擲回。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [例外狀況的設計方針](../../../docs/standard/design-guidelines/exceptions.md)
