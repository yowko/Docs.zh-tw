---
title: REM 陳述式 (Visual Basic)
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
ms.openlocfilehash: 16149ce42e3476cf07a62298f83734fee9ec7253
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957765"
---
# <a name="rem-statement-visual-basic"></a>REM 陳述式 (Visual Basic)
用來在程式的原始程式碼中包含說明備註。  
  
## <a name="syntax"></a>語法  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>組件  
 `comment`  
 選擇性。 您想要包含之任何批註的文字。 `REM`關鍵字與`comment`之間必須有空格。  
  
## <a name="remarks"></a>備註  
 您可以將`REM`語句單獨放在一行上, 也可以將它放在另一個語句後面的一行。 `REM`語句必須是該行的最後一個語句。 如果它遵循另一個語句, `REM`必須以空格與該語句隔開。  
  
 您可以使用單引號 (`'`), `REM`而不是。 無論您的批註是在同一行的另一個語句後面, 還是單獨放在一行上, 都是如此。  
  
> [!NOTE]
> 您不能使用`REM`行接續順序 (`_`) 來繼續執行語句。 當批註開始時, 編譯器不會檢查字元是否有特殊意義。 對於多行批註, 請在每一行`REM`上使用另一個語句或`'`批註符號 ()。  
  
## <a name="example"></a>範例  
 下列範例說明`REM`語句, 其用來在程式中包含說明備註。 它也會顯示使用單引號字元 (`'`) `REM`而不是的替代方法。  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [程式碼中的註解](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [如何：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
