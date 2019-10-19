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
ms.openlocfilehash: edaaf09f5a984344f7e89c9da988c529774934e9
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583263"
---
# <a name="return-statement-visual-basic"></a>Return 陳述式 (Visual Basic)
將控制權傳回給呼叫 `Function`、`Sub`、`Get`、`Set` 或 `Operator` 程式的程式碼。  
  
## <a name="syntax"></a>語法  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a>組件  
 `expression`  
 在 `Function`、`Get` 或 `Operator` 程式中為必要項。 運算式，表示要傳回給呼叫程式碼的值。  
  
## <a name="remarks"></a>備註  
 在 `Sub` 或 `Set` 程式中，`Return` 語句相當於 `Exit Sub` 或 `Exit Property` 語句，而且不得提供 `expression`。  
  
 在 `Function`、`Get` 或 `Operator` 程式中，`Return` 語句必須包含 `expression`，而且 `expression` 必須評估為可轉換成程式之傳回型別的資料型別。 在 `Function` 或 `Get` 程式中，您也可以選擇將運算式指派給程式名稱，以做為傳回值，然後執行 `Exit Function` 或 `Exit Property` 語句。 在 `Operator` 程式中，您必須使用 `Return expression`。  
  
 您可以在相同的程式中包含任意數目的 `Return` 語句。  
  
> [!NOTE]
> @No__t_0 區塊中的程式碼會在遇到 `Try` 或 `Catch` 區塊中的 `Return` 語句之後，但在該 `Return` 語句執行之前執行。 @No__t_0 語句不能包含在 `Finally` 區塊中。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Return` 語句數次，以便在程式不需要執行任何動作時，返回呼叫程式碼。  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>請參閱

- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)
- [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
