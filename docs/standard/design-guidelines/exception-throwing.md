---
title: 擲回例外狀況
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fbbe84811e3fa096b9e13c459143311bb75a198
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44132633"
---
# <a name="exception-throwing"></a>擲回例外狀況
擲回例外狀況這一節所述的指導方針需要良好定義的執行失敗的意義。 每當成員不是什麼，就會發生執行失敗設計 （成員名稱有隱含意義）。 例如，如果`OpenFile`方法無法傳回給呼叫端的開啟的檔案控制代碼，它會被視為新的執行失敗。  
  
 大部分的開發人員已熟悉使用使用狀況的錯誤，例如部門的例外狀況，藉由零或 null 參考。 在架構中，例外狀況會用於所有的錯誤狀況，包括執行錯誤。  
  
 **X DO NOT** 傳回的錯誤碼。  
  
 例外狀況是在架構中的錯誤報告的主要方法。  
  
 **✓ DO** 報表執行失敗數目，所擲回例外狀況。  
  
 **✓ CONSIDER** 藉由呼叫終止處理序 `System.Environment.FailFast` （.NET Framework 2.0 功能） 而不是擲回例外狀況，如果您的程式碼遇到的情況下，它是不安全的進一步執行。  
  
 **X DO NOT** 盡可能使用控制項的正常流程例外狀況。  
  
 除了系統失敗和作業可能發生競爭情形，架構設計人員應該設計 Api，因此使用者可以撰寫程式碼不會擲回例外狀況。 例如，您可以提供檢查先決條件之前呼叫的成員，因此使用者可以撰寫程式碼不會擲回例外狀況的方式。  
  
 用來檢查另一個成員的前置條件的成員通常稱為測試人員，並實際運作的成員呼叫 doer。  
  
 Tester-doer 模式可能無法接受的效能額外負荷時，有一些情況。 在此情況下，您應該考慮所謂的嘗試剖析模式 (請參閱[例外狀況和效能](../../../docs/standard/design-guidelines/exceptions-and-performance.md)如需詳細資訊)。  
  
 **✓ CONSIDER** 擲回例外狀況的效能含意。 每秒 100 以上的擲回率很可能會明顯影響大部分的應用程式的效能。  
  
 **✓ DO** 文件，因為成員的違規的緣故，公開呼叫成員所擲回的所有例外狀況合約 （而不是系統失敗），並視為程式合約的一部分。  
  
 合約的一部分的例外狀況不應該從某個版本變更至下一個 （亦即，不應該變更例外狀況類型，和不應新增新的例外狀況）。  
  
 **X DO NOT** 或不可以是擲回的公用成員取決於一些選項。  
  
 **X DO NOT** 擁有傳回例外狀況當做傳回值的公用成員或`out`參數。  
  
 傳回從公用 Api，而不是擲回的例外狀況，就失去了許多例外狀況架構錯誤報告的優點。  
  
 **✓ CONSIDER** 使用例外狀況產生器方法。  
  
 通常會從不同的地方擲回相同的例外狀況。 若要避免程式碼膨脹，使用協助程式方法，建立例外狀況，並初始化其屬性。  
  
 此外，擲回例外狀況的成員未內嵌。 移動的產生器將 throw 陳述式可能會允許要內嵌的成員。  
  
 **X DO NOT** 擲回例外狀況的例外狀況篩選條件區塊。  
  
 當例外狀況篩選條件會引發例外狀況時，clr，攔截例外狀況，並篩選條件傳回 false。 此行為是區別篩選執行，並明確傳回 false，因此很難偵錯。  
  
 **X AVOID** 明確擲回例外狀況的 finally 區塊。 隱含擲回的例外狀況所產生的呼叫會擲回的方法可接受的。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [例外狀況的設計方針](../../../docs/standard/design-guidelines/exceptions.md)
