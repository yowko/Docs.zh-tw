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
ms.openlocfilehash: 3bd526b08e1ba3be856e1e823cf8ef49ea9b6c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604272"
---
# <a name="rem-statement-visual-basic"></a>REM 陳述式 (Visual Basic)
用來在程式碼的原始程式碼中包含說明備註。  
  
## <a name="syntax"></a>語法  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>組件  
 `comment`  
 選擇性。 您要包含的任何註解的文字。 不需要之間的空間`REM`關鍵字和`comment`。  
  
## <a name="remarks"></a>備註  
 您可以放入`REM`陳述式單獨一行，或者您可以將它放在另一個陳述式的一行。 `REM`陳述式必須是該行的最後一個陳述式。 如果另一個陳述式之後，`REM`必須從該陳述式，以空格分隔。  
  
 您可以使用單引號 (`'`) 而不是`REM`。 您的註解是否另一個陳述式後面的同一行，或位於單獨的一行，也是如此。  
  
> [!NOTE]
>  您無法繼續`REM`陳述式使用行接續序列 (`_`)。 註解開始時，編譯器不會檢查特殊意義的字元。 對於多行註解，使用另一個`REM`陳述式或註解符號 (`'`) 在每一行。  
  
## <a name="example"></a>範例  
 下列範例說明`REM`陳述式，用來在程式中包含說明備註。 它也會顯示另一種使用單一的引號字元 (`'`) 而不是`REM`。  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程式碼中的註解](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [操作說明：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
