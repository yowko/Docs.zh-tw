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
ms.openlocfilehash: 729d0710d65c0cda750061e72309ced527bbcfe7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582052"
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
 選擇項。 您想要包含之任何批註的文字。 @No__t_0 關鍵字與 `comment` 之間必須有空格。  
  
## <a name="remarks"></a>備註  
 您可以將 `REM` 語句單獨放在一行上，也可以將它放在另一個語句後面的一行。 @No__t_0 語句必須是該行的最後一個語句。 如果它遵循另一個語句，`REM` 必須以空格與該語句隔開。  
  
 您可以使用單引號（`'`），而不是 `REM`。 無論您的批註是在同一行的另一個語句後面，還是單獨放在一行上，都是如此。  
  
> [!NOTE]
> 您不能使用行接續順序（`_`）繼續 `REM` 語句。 當批註開始時，編譯器不會檢查字元是否有特殊意義。 對於多行批註，請在每一行上使用另一個 `REM` 語句或批註符號（`'`）。  
  
## <a name="example"></a>範例  
 下列範例說明用來在程式中包含說明備註的 `REM` 語句。 它也會顯示使用單引號字元（`'`），而不是 `REM` 的替代方法。  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>請參閱

- [程式碼中的註解](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [操作說明：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
