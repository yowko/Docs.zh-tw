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
ms.openlocfilehash: 7a493e6591d90ce05a652e48807f63fa90764a91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573717"
---
# <a name="exception-throwing"></a>擲回例外狀況
擲回例外狀況這一節所述的指導方針需要良好定義的執行失敗的意義。 每當成員無法執行的動作前，就會發生執行失敗執行 （其成員名稱一樣）。 例如，如果`OpenFile`方法不能將開啟的檔案控制代碼傳回給呼叫者，它會被視為新的執行失敗。  
  
 大部分的開發人員已成為想要使用使用量錯誤，例如除法的例外狀況，由零或 null 參考。 在架構中，例外狀況會用於所有的錯誤狀況，包括執行錯誤。  
  
 **X DO NOT**傳回的錯誤碼。  
  
 例外狀況是報告錯誤架構中的主要方法。  
  
 **✓ DO**報表執行失敗數目，所擲回例外狀況。  
  
 **✓ CONSIDER**藉由呼叫終止處理序`System.Environment.FailFast`（.NET Framework 2.0 功能） 而不是擲回例外狀況，如果您的程式碼遇到的情況下，它是不安全的進一步執行。  
  
 **X DO NOT**盡可能使用控制項的正常流程例外狀況。  
  
 除了系統失敗和作業可能的競爭情形，架構設計人員應該設計應用程式開發介面，讓使用者都可以寫入不擲回例外狀況的程式碼。 例如，您可以提供檢查先決條件之前呼叫成員，因此使用者可以撰寫程式碼不會擲回例外狀況的方法。  
  
 用來檢查先決條件的另一個成員的成員通常稱為測試人員，並呼叫 doer 實際運作成員。  
  
 有些情況是當 Tester-doer 模式可能是無法接受的效能負擔。 在這種情況下，應該考量所謂再試一次剖析模式 (請參閱[例外狀況和效能](../../../docs/standard/design-guidelines/exceptions-and-performance.md)如需詳細資訊)。  
  
 **✓ CONSIDER**擲回例外狀況的效能含意。 每秒 100 以上的擲回率是有可能會大幅影響大部分的應用程式的效能。  
  
 **✓ DO**文件，因為成員的違規的緣故，公開呼叫成員所擲回的所有例外狀況合約 （而不是系統失敗），並視為程式合約的一部分。  
  
 例外狀況合約的一部分，不應該從一個版本變更至下一個 （亦即，不應該變更例外狀況類型，和不應該加入新的例外狀況）。  
  
 **X DO NOT**或不可以是擲回的公用成員取決於一些選項。  
  
 **X DO NOT**擁有傳回例外狀況當做傳回值的公用成員或`out`參數。  
  
 傳回從公用 Api，而不是擲回的例外狀況，就失去了許多例外狀況架構錯誤報告的優點。  
  
 **✓ CONSIDER**使用例外狀況產生器方法。  
  
 通常會從不同的地方擲回相同的例外狀況。 若要避免程式碼，請使用 helper 方法，建立例外狀況，並初始化其屬性。  
  
 此外，擲回例外狀況的成員不會進行內嵌。 移動產生器將 throw 陳述式可能會允許內嵌的成員。  
  
 **X DO NOT**擲回例外狀況的例外狀況篩選條件區塊。  
  
 當例外狀況篩選條件會引發例外狀況時，由 CLR 攔截例外狀況和篩選條件傳回 false。 此行為是區別執行篩選條件並明確傳回 false，因此很難偵錯。  
  
 **X AVOID**明確擲回例外狀況的 finally 區塊。 可接受的隱含擲回造成呼叫方法會擲回的例外狀況。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [例外狀況的設計方針](../../../docs/standard/design-guidelines/exceptions.md)
