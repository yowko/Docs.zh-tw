---
title: 擲回例外狀況
ms.date: 10/22/2008
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: d41467b971e43ca9b22c59e3b64bdd45d16c740b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734396"
---
# <a name="exception-throwing"></a>擲回例外狀況

本節所述的例外狀況擲回指導方針，需要執行失敗意義的良好定義。 每當成員無法執行其設計來執行的作業時，就會發生執行失敗 (成員名稱表示) 。 例如，如果 `OpenFile` 方法無法將開啟的檔案控制代碼傳回給呼叫者，則會被視為執行失敗。

 大部分的開發人員都已熟悉使用例外狀況來處理使用錯誤，例如零除或 null 參考。 在架構中，會針對所有錯誤狀況（包括執行錯誤）使用例外狀況。

 ❌ 請勿傳回錯誤碼。

 例外狀況是在架構中報告錯誤的主要方法。

 ✔️藉由擲回例外狀況來執行報告執行失敗。

 ✔️請考慮藉由呼叫 `System.Environment.FailFast` ( .NET Framework 2.0) 功能來終止進程，而不是在程式碼遇到不安全的情況下擲回例外狀況，以供進一步執行。

 ❌ 如果可能的話，請勿使用一般控制流程的例外狀況。

 除了可能競爭情形的系統失敗和作業之外，架構設計人員應該設計 Api，讓使用者可以撰寫不會擲回例外狀況的程式碼。 例如，您可以在呼叫成員之前提供檢查前置條件的方法，讓使用者可以撰寫不會擲回例外狀況的程式碼。

 用來檢查另一個成員之前置條件的成員通常稱為測試人員，而實際執行工作的成員稱為惡人之手。

 在某些情況下，Tester-Doer 模式可能會造成無法接受的效能額外負荷。 在這種情況下，應該考慮所謂的 Try-Parse 模式 (看到詳細資訊) 的 [例外狀況和效能](exceptions-and-performance.md) 。

 ✔️考慮擲回例外狀況的效能含意。 每秒100以上的擲回率，可能會明顯影響大部分應用程式的效能。

 ✔️會記錄公開可呼叫成員所擲回的所有例外狀況，因為違反成員合約 (而不是系統失敗) 並將它們視為合約的一部分。

 屬於合約一部分的例外狀況不應從某個版本變更為下一個版本 (亦即，例外狀況類型不應變更，也不應將新的例外狀況加入) 。

 ❌ 沒有可擲回或不是根據某個選項的公用成員。

 ❌ 沒有會傳回例外狀況的公用成員做為傳回值或 `out` 參數。

 從公用 Api 傳回例外狀況，而不是擲回例外狀況，則會導致許多例外狀況型錯誤報表的優點。

 ✔️考慮使用例外狀況產生器方法。

 通常會從不同的位置擲回相同的例外狀況。 若要避免程式碼膨脹，請使用協助程式方法來建立例外狀況，並將其屬性初始化。

 此外，擲回例外狀況的成員將不會內嵌。 在產生器內移動 throw 語句可能會允許內嵌該成員。

 ❌ 請勿從例外狀況篩選區塊擲回例外狀況。

 例外狀況篩選準則引發例外狀況時，CLR 會攔截到例外狀況，而篩選會傳回 false。 這種行為與執行和明確傳回 false 的篩選器不區分，因此很難進行調試。

 ❌ 避免明確擲回來自 finally 區塊的例外狀況。 從呼叫擲回的方法所產生的隱含擲回例外狀況是可接受的。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [架構設計指導方針](index.md)
- [例外狀況的設計方針](exceptions.md)
