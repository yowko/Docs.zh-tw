---
title: 擲回例外狀況
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 6bbc6e8fa11759afbd3a1fb2d785f476a6c178ad
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289807"
---
# <a name="exception-throwing"></a>擲回例外狀況
這一節中所述的例外狀況擲回指導方針，需要有良好的執行失敗意義定義。 當成員無法執行其設計所要執行的作業時（成員名稱會隱含），就會發生執行失敗。 例如，如果 `OpenFile` 方法無法將開啟的檔案控制代碼傳回給呼叫端，則會將它視為執行失敗。

 大部分的開發人員都已熟悉使用例外狀況來處理使用錯誤，例如零除或 null 參考。 在架構中，例外狀況會用於所有的錯誤情況，包括執行錯誤。

 ❌不要傳回錯誤碼。

 例外狀況是在架構中報告錯誤的主要方法。

 ✔️會擲回例外狀況來報告執行失敗。

 ✔️考慮藉由呼叫 `System.Environment.FailFast` （.NET Framework 2.0 功能）來終止進程，而不是在程式碼遇到不安全的情況下擲回例外狀況，以供進一步執行。

 ❌如果可能，請不要使用一般控制流程的例外狀況。

 除了系統失敗和具有潛在競爭情況的作業以外，架構設計人員應該設計 Api，讓使用者可以撰寫不會擲回例外狀況的程式碼。 例如，您可以提供方法來檢查前置條件，然後再呼叫成員，讓使用者可以撰寫不會擲回例外狀況的程式碼。

 用來檢查另一個成員之前置條件的成員通常稱為「測試者」，而實際執行工作的成員稱為「惡人之手」。

 在某些情況下，測試人員惡人之手模式可能會造成無法接受的效能負擔。 在這種情況下，應該考慮所謂的嘗試剖析模式（如需詳細資訊，請參閱[例外狀況和效能](exceptions-and-performance.md)）。

 ✔️考慮擲回例外狀況的效能影響。 每秒100以上的擲回率可能會明顯影響大部分應用程式的效能。

 ✔️確實記載由公開可呼叫成員擲回的所有例外狀況，因為違反了成員合約（而不是系統失敗），並將它們視為合約的一部分。

 屬於合約一部分的例外狀況不應該從某個版本變更為下一個版本（亦即，例外狀況類型不應變更，也不應該加入新的例外狀況）。

 ❌沒有可以擲回或不是根據某個選項的公用成員。

 ❌沒有會傳回例外狀況的公用成員做為傳回值或 `out` 參數。

 從公用 Api 傳回例外狀況，而不是擲回它們，會使例外狀況錯誤報表的許多優點。

 ✔️考慮使用例外狀況產生器方法。

 通常會從不同的位置擲回相同的例外狀況。 若要避免程式碼膨脹，請使用建立例外狀況的 helper 方法，並初始化其屬性。

 此外，擲回例外狀況的成員不會內嵌。 在產生器內移動 throw 語句可能會允許內嵌該成員。

 ❌不要從例外狀況篩選區塊擲回例外狀況。

 例外狀況篩選準則引發例外狀況時，CLR 會攔截例外狀況，而篩選準則會傳回 false。 這種行為與執行和明確傳回 false 的篩選器不區分，因此很難進行偵錯工具。

 ❌避免從 finally 區塊明確擲回例外狀況。 隱含擲回的例外狀況是由呼叫可接受的方法所產生。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)
- [例外狀況的設計方針](exceptions.md)
