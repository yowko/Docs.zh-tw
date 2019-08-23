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
ms.openlocfilehash: af49ea95d7f9d01072190ac3ccf6ba2f1041347e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957666"
---
# <a name="return-statement-visual-basic"></a>Return 陳述式 (Visual Basic)
將控制權傳回給呼叫`Function` `Get`、 `Sub` `Set`、、或`Operator`程式的程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>組件  
 `expression`  
 在、 `Function` `Get`或程式中是必要的。`Operator` 運算式, 表示要傳回給呼叫程式碼的值。  
  
## <a name="remarks"></a>備註  
 `Return` `Exit Property` `expression`在或程式`Set` 中,語句相當於或語句,而且不得提供`Exit Sub`。 `Sub`  
  
 `expression` `expression`在、或程式`Operator`中,`Return`語句必須包含, 而且必須評估為可轉換成程式之傳回類型的資料類型。 `Get` `Function` `Exit Function` `Exit Property`在或程式`Get`中, 您也可以選擇將運算式指派給程式名稱, 以做為傳回值, 然後執行或語句。 `Function` 在程式`Operator`中, 您必須使用`Return expression`。  
  
 在相同的程式中`Return` , 您可以包含多個適當的語句。  
  
> [!NOTE]
> `Finally`區塊中的程式碼會在遇到`Return` `Try`或`Catch`區塊中的語句之後, 但在該`Return`語句執行之前執行。 語句不能包含`Finally`在區塊中。 `Return`  
  
## <a name="example"></a>範例  
 下列範例會使用`Return`語句數次, 以在程式不需要執行任何動作時返回呼叫程式碼。  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>另請參閱

- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)
- [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
