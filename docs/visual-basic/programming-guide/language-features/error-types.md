---
title: 錯誤類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: ab554b60f7ba44ee0b92b76e1362ffdbb25f2afb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965374"
---
# <a name="error-types-visual-basic"></a>錯誤類型 (Visual Basic)
在 Visual Basic 中, 錯誤會屬於下列三個類別之一: 語法錯誤、執行階段錯誤和邏輯錯誤。

## <a name="syntax-errors"></a>語法錯誤
 *語法錯誤*是您撰寫程式碼時所顯示的錯誤。 如果您使用 Visual Studio, 當您在 [程式**代碼編輯器**] 視窗中輸入程式碼時, Visual Basic 會檢查它, 並在犯錯誤時向您發出警告, 例如拼錯單字或使用 language 元素不正確。 如果您從命令列進行編譯, Visual Basic 會顯示編譯器錯誤, 其中包含語法錯誤的相關資訊。 語法錯誤是最常見的錯誤類型。 您可以輕鬆地在程式碼撰寫環境中進行修正。

> [!NOTE]
> `Option Explicit`語句是避免語法錯誤的一種方法。 它會強制您事先宣告要在應用程式中使用的所有變數。 因此, 在程式碼中使用這些變數時, 任何印刷樣式錯誤都會立即捕捉, 而且可以修正。

## <a name="run-time-errors"></a>執行階段錯誤
 *執行階段錯誤*是指只有在您編譯和執行程式碼之後才會出現的錯誤。 這些程式碼包含可能正確的程式碼, 因為它沒有任何語法錯誤, 但不會執行。 例如, 您可以正確地撰寫一行程式碼來開啟檔案。 但是, 如果檔案不存在, 應用程式就無法開啟檔案, 而且會擲回例外狀況。 您可以藉由重寫錯誤的程式碼或使用[例外狀況處理](../../language-reference/statements/try-catch-finally-statement.md)來修正大部分的執行階段錯誤, 然後重新編譯並重新執行它。
  
## <a name="logic-errors"></a>邏輯錯誤
 *邏輯錯誤*是應用程式在使用中時出現的錯誤。 這通常是開發人員所做的錯誤假設, 或回應使用者動作的不必要或非預期的結果。 例如, 輸入錯誤的索引鍵可能會提供不正確的資訊給方法, 或者您可能會假設有效的值一律會提供給方法 (如果不是這種情況)。 雖然邏輯錯誤可以使用[例外狀況處理](../../language-reference/statements/try-catch-finally-statement.md)來處理 (例如, 藉由測試引數是否為`Nothing`和<xref:System.ArgumentNullException>擲回), 但最常見的解決方法是在邏輯中更正錯誤並重新編譯應用程式.

## <a name="see-also"></a>另請參閱

- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [偵錯工具基礎](/visualstudio/debugger/debugger-basics)
