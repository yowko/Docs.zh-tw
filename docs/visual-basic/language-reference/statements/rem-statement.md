---
title: REM 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 68c898145bd8845c657b6ebb8776a3a9027c359c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404261"
---
# <a name="rem-statement-visual-basic"></a>REM 陳述式 (Visual Basic)
用來在程式的原始程式碼中包含說明備註。  
  
## <a name="syntax"></a>語法  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a>組件  
 `comment`  
 選擇性。 您想要包含之任何批註的文字。 關鍵字與之間必須有空格 `REM` `comment` 。  
  
## <a name="remarks"></a>備註  
 您可以將 `REM` 語句單獨放在一行上，也可以將它放在另一個語句後面的一行。 `REM`語句必須是該行的最後一個語句。 如果它遵循另一個語句， `REM` 必須以空格與該語句隔開。  
  
 您可以使用單引號（ `'` ），而不是 `REM` 。 無論您的批註是在同一行的另一個語句後面，還是單獨放在一行上，都是如此。  
  
> [!NOTE]
> 您不能 `REM` 使用行接續順序（）來繼續執行語句 `_` 。 當批註開始時，編譯器不會檢查字元是否有特殊意義。 對於多行批註，請 `REM` 在每一行上使用另一個語句或批註符號（ `'` ）。  
  
## <a name="example"></a>範例  
 下列範例說明 `REM` 語句，其用來在程式中包含說明備註。 它也會顯示使用單引號字元（ `'` ）而不是的替代方法 `REM` 。  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [程式碼中的註解](../../programming-guide/program-structure/comments-in-code.md)
- [作法：程式碼中的 Break 及 Combine 陳述式](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
