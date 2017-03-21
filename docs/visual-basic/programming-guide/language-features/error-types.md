---
title: "錯誤類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors, Visual Basic
- run-time errors, types of errors
- syntax errors, Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d48756b74baf757f043e68124d8b65c2f613e595
ms.lasthandoff: 03/13/2017

---
# <a name="error-types-visual-basic"></a>錯誤類型 (Visual Basic)
在[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，錯誤 (也稱為*例外狀況*) 分為三種類別︰ 語法錯誤、 執行階段錯誤和邏輯錯誤。  
  
## <a name="syntax-errors"></a>語法錯誤  
 *語法錯誤*是指您撰寫程式碼時出現。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會檢查您的程式碼，在您輸入時所**程式碼編輯器**視窗，並發生錯誤，例如拼字錯誤或不當使用的語言項目發出警示。 語法錯誤是最常見的錯誤類型。 您可以修正它們輕鬆地在程式碼撰寫環境中發生時。  
  
> [!NOTE]
>  `Option Explicit`陳述式是一種避免語法錯誤。 它會強制您事先宣告應用程式中使用的所有變數。 因此，程式碼中使用這些變數時，任何字面上的錯誤可立即發現及修復。  
  
## <a name="run-time-errors"></a>執行階段錯誤  
 *執行階段錯誤*是指只有在您編譯並執行您的程式碼時，才會出現。 這些技巧包括似乎是正確的因為它有沒有語法錯誤，但卻無法執行的程式碼。 例如，您可以正確撰寫一行程式碼，來開啟檔案。 如果檔案已損毀，無法執行應用程式，但`Open`函式，而且它會停止執行。 您可以重新撰寫程式碼，然後重新編譯與執行，以修正大部分的執行階段錯誤。  
  
## <a name="logic-errors"></a>邏輯錯誤  
 *邏輯錯誤*是指應用程式在使用時出現。 也就是大部分通常不必要或非預期的結果以回應使用者動作。 例如，輸入錯誤的索引鍵或其他外部的影響可能會導致您的應用程式停止運作在預期的參數，或完全。 邏輯錯誤通常是最困難的型別，若要修正，因為它不一定清楚發生原因。  
  
## <a name="see-also"></a>另請參閱  
 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [偵錯工具基礎](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)
