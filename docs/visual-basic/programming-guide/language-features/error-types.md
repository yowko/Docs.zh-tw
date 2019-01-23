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
ms.openlocfilehash: dc7cba394f623ae94a0d9ca8285fc12af8f0dacf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600332"
---
# <a name="error-types-visual-basic"></a>錯誤類型 (Visual Basic)
在 Visual Basic 中的錯誤 (也稱為*例外狀況*) 分為三類： 語法錯誤、 執行階段錯誤，以及邏輯錯誤。  
  
## <a name="syntax-errors"></a>語法錯誤  
 *語法錯誤*是指您撰寫程式碼時出現。 Visual Basic 會檢查您的程式碼，在您輸入時所**程式碼編輯器**視窗，提醒您，如果您犯了錯誤，例如拼錯字，或不當使用語言項目。 語法錯誤是最常見的錯誤類型。 修正方式輕鬆地在程式碼撰寫環境中，它們就會發生。  
  
> [!NOTE]
>  `Option Explicit`陳述式是一種避免發生語法錯誤。 它會強制您預先宣告的應用程式中使用的所有變數。 因此，當程式碼中使用這些變數，印刷樣式的任何錯誤立即發現，而且可以修正。  
  
## <a name="run-time-errors"></a>執行階段錯誤  
 *執行階段錯誤*是指您編譯並執行您的程式碼時，才會出現。 這些轉換可能會顯示為正確，因為它沒有任何語法錯誤，但卻無法執行的程式碼。 例如，您可以正確撰寫一行程式碼，以開啟檔案。 如果檔案已損毀，無法執行應用程式，但`Open`函式，而且它會停止執行。 您可以重寫程式碼，然後重新編譯並重新執行它，就可修正大部分的執行階段錯誤。  
  
## <a name="logic-errors"></a>邏輯錯誤  
 *邏輯錯誤*是指應用程式在使用時出現。 也就是回應使用者動作的大部分通常不必要或非預期結果。 例如，輸入錯誤的索引鍵或其他外部的影響可能會導致您的應用程式停止運作中預期的參數，或完全。 邏輯錯誤通常是最困難的型別，若要修正，因為它不一定清楚其來源。  
  
## <a name="see-also"></a>另請參閱
- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [偵錯工具基礎](/visualstudio/debugger/debugger-basics)
