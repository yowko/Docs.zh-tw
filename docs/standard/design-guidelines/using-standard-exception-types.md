---
title: 使用標準例外狀況類型
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81e4047c171e3a58f335821d64390432524b25df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574591"
---
# <a name="using-standard-exception-types"></a>使用標準例外狀況類型
本章節描述架構和其使用方式的詳細資料所提供的標準例外狀況。 清單是不是完整詳盡。 請參閱.NET Framework 參考文件的使用方式的其他架構例外狀況類型。  
  
## <a name="exception-and-systemexception"></a>例外狀況和 SystemException  
 **X 不**擲回<xref:System.Exception?displayProperty=nameWithType>或<xref:System.SystemException?displayProperty=nameWithType>。  
  
 **X 不**攔截`System.Exception`或`System.SystemException`framework 程式碼中，除非您想要重新擲回。  
  
 **請避免 x**攔截`System.Exception`或`System.SystemException`，除非在最上層例外狀況處理常式。  
  
## <a name="applicationexception"></a>ApplicationException  
 **X 不**擲回或衍生自<xref:System.ApplicationException>。  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ 不要**擲回<xref:System.InvalidOperationException>的物件是否不適當的狀態。  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException、 ArgumentNullException 和 ArgumentOutOfRangeException  
 **✓ 不要**擲回<xref:System.ArgumentException>或如果不正確的引數會傳遞給成員及其子型別之一。 如果適用，偏好最常衍生的例外狀況類型。  
  
 **✓ 不要**設定`ParamName`屬性時擲回的子類別的其中一個`ArgumentException`。  
  
 這個屬性表示造成擲回的例外狀況的參數名稱。 請注意，這個屬性可以使用其中一個建構函式多載設定。  
  
 **✓ 不要**使用`value`屬性 setter 的隱含值參數的名稱。  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException、 IndexOutOfRangeException 和了 AccessViolationException  
 **X 不**允許公開呼叫 Api，明確或隱含地擲回<xref:System.NullReferenceException>， <xref:System.AccessViolationException>，或<xref:System.IndexOutOfRangeException>。 這些例外狀況會保留並擲回的執行引擎在大部分情況下表示 bug。  
  
 執行檢查，以避免擲回這些例外狀況的引數。 擲回這些例外狀況會公開實作詳細資料，您可能會隨著時間變更的方法。  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X 不**明確擲回<xref:System.StackOverflowException>。 應該在只能由 CLR 明確擲回例外狀況。  
  
 **X 不**攔截`StackOverflowException`。  
  
 它是幾乎不可能撰寫仍然維持一致且任意堆疊溢位的 managed 程式碼。 使用探查移動堆疊溢位到妥善定義的位置而非從任意的堆疊溢位退出，unmanaged 的 CLR 組件保持一致。  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X 不**明確擲回<xref:System.OutOfMemoryException>。 是僅供 CLR 基礎結構會擲回這個例外狀況。  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException、 SEHException 和 ExecutionEngineException  
 **X 不**明確擲回<xref:System.Runtime.InteropServices.COMException>， <xref:System.ExecutionEngineException>，和<xref:System.Runtime.InteropServices.SEHException>。 這些例外狀況會擲回僅供 CLR 基礎結構。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [例外狀況的設計方針](../../../docs/standard/design-guidelines/exceptions.md)
