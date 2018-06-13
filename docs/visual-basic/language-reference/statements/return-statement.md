---
title: Return 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 2f614045be1b91b9c747d961cdefd526ba1bab98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603518"
---
# <a name="return-statement-visual-basic"></a>Return 陳述式 (Visual Basic)
控制權傳回給呼叫的程式碼`Function`， `Sub`， `Get`， `Set`，或`Operator`程序。  
  
## <a name="syntax"></a>語法  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>組件  
 `expression`  
 中需要`Function`， `Get`，或`Operator`程序。 表示要傳回給呼叫程式碼的值運算式。  
  
## <a name="remarks"></a>備註  
 在`Sub`或`Set`程序，`Return`陳述式相當於`Exit Sub`或`Exit Property`陳述式，和`expression`不可提供。  
  
 在`Function`， `Get`，或`Operator`程序，`Return`陳述式必須包含`expression`，和`expression`必須評估為可轉換成程序的傳回類型的資料類型。 在`Function`或`Get`程序中，您也可以選擇將運算式指派給要做為傳回值，程序名稱，然後執行`Exit Function`或`Exit Property`陳述式。 在`Operator`程序中，您必須使用`Return``expression`。  
  
 您可以包含最大數量`Return`視需要在相同的程序的陳述式。  
  
> [!NOTE]
>  中的程式碼`Finally`區塊會執行`Return`陳述式中的`Try`或`Catch`區塊是發生，但之前會先`Return`陳述式會執行。 A`Return`陳述式不能包含在`Finally`區塊。  
  
## <a name="example"></a>範例  
 下列範例會使用`Return`陳述式時不需要進行其他任何處理程序傳回至呼叫的程式碼數次。  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
