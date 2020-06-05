---
title: Return 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: cdb58e32c30c8e6c1662fb698ac5576c3f71258c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404196"
---
# <a name="return-statement-visual-basic"></a>Return 陳述式 (Visual Basic)
將控制權傳回給呼叫、、、或程式的程式碼 `Function` `Sub` `Get` `Set` `Operator` 。  
  
## <a name="syntax"></a>語法  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a>部分  
 `expression`  
 在、或程式中是必要的 `Function` `Get` `Operator` 。 運算式，表示要傳回給呼叫程式碼的值。  
  
## <a name="remarks"></a>備註  
 在 `Sub` 或 `Set` 程式中， `Return` 語句相當於 `Exit Sub` 或 `Exit Property` 語句，而且 `expression` 不得提供。  
  
 在 `Function` 、 `Get` 或程式中 `Operator` ， `Return` 語句必須包含 `expression` ，而且 `expression` 必須評估為可轉換成程式之傳回類型的資料類型。 在或程式中 `Function` `Get` ，您也可以選擇將運算式指派給程式名稱，以做為傳回值，然後執行 `Exit Function` 或 `Exit Property` 語句。 在程式中 `Operator` ，您必須使用 `Return expression` 。  
  
 在相同的程式中，您可以包含多個 `Return` 適當的語句。  
  
> [!NOTE]
> 區塊中的 `Finally` `Return` 程式碼會在遇到或區塊中的語句之後 `Try` `Catch` ，但在該 `Return` 語句執行之前執行。 `Return`語句不能包含在區塊中 `Finally` 。  
  
## <a name="example"></a>範例  
 下列範例 `Return` 會使用語句數次，以在程式不需要執行任何動作時返回呼叫程式碼。  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>另請參閱

- [Function 陳述式](function-statement.md)
- [Sub 陳述式](sub-statement.md)
- [Get 陳述式](get-statement.md)
- [Set 語句](set-statement.md)
- [Operator Statement](operator-statement.md)
- [Property Statement](property-statement.md)
- [Exit 陳述式](exit-statement.md)
- [Try...Catch...Finally 陳述式](try-catch-finally-statement.md)
