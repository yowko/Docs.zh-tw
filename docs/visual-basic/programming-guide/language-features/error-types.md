---
title: 錯誤類型
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
ms.openlocfilehash: caeaab9a358e3e3a995c1df7274d16daaff7a667
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083991"
---
# <a name="error-types-visual-basic"></a>錯誤類型 (Visual Basic)

在 Visual Basic 中，錯誤分為三種類別：語法錯誤、執行階段錯誤和邏輯錯誤。

## <a name="syntax-errors"></a>語法錯誤

 *語法錯誤* 是在您撰寫程式碼時所顯示的錯誤。 如果您使用 Visual Studio，Visual Basic 在 [程式 **代碼編輯器** ] 視窗中輸入程式碼時，會檢查您的程式碼，並在發生錯誤時發出警示，例如拼錯單字或不當使用語言元素。 如果您從命令列進行編譯，Visual Basic 會顯示編譯器錯誤，其中包含語法錯誤的相關資訊。 語法錯誤是最常見的錯誤類型。 您可以在撰寫程式碼的環境中，輕鬆地修正這些問題。

> [!NOTE]
> `Option Explicit`語句是避免語法錯誤的一種方法。 它會強制您事先宣告要在應用程式中使用的所有變數。 因此，在程式碼中使用這些變數時，會立即攔截任何印刷樣式錯誤並加以修正。

## <a name="run-time-errors"></a>執行階段錯誤

 *執行階段錯誤* 是只有在您編譯並執行程式碼之後才會出現的錯誤。 這些都包含可能正確的程式碼，因為它沒有語法錯誤，但不會執行。 例如，您可能會正確地撰寫一行程式碼來開啟檔案。 但是，如果檔案不存在，應用程式就無法開啟檔案，而且會擲回例外狀況。 您可以藉由重寫錯誤的程式碼或使用 [例外狀況處理](../../language-reference/statements/try-catch-finally-statement.md)來修正大部分的執行階段錯誤，然後重新編譯並重新執行。
  
## <a name="logic-errors"></a>邏輯錯誤

 *邏輯錯誤* 是應用程式正在使用時出現的錯誤。 它們通常是開發人員所做的錯誤假設，或是因應使用者動作而不想要或非預期的結果。 例如，輸入錯誤的索引鍵可能會提供不正確的資訊給方法，或者您可能會假設在不是這種情況下，一律會提供有效的值給方法。 雖然您可以使用 [例外狀況處理](../../language-reference/statements/try-catch-finally-statement.md) 來處理邏輯錯誤 (例如，藉由測試引數是否為和擲回 `Nothing` <xref:System.ArgumentNullException>) ，最常見的方法是修正邏輯中的錯誤，然後重新編譯應用程式。

## <a name="see-also"></a>另請參閱

- [Try...Catch...Finally 陳述式](../../language-reference/statements/try-catch-finally-statement.md)
- [偵錯工具基礎](/visualstudio/debugger/debugger-feature-tour)
