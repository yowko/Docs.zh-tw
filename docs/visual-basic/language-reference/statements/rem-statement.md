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
ms.openlocfilehash: 3c63c5613b40cb2014c77a0a996e3acb2cc304d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817015"
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
 選擇性。 您想要包含的任何註解文字。 之間的空間，須`REM`關鍵字和`comment`。  
  
## <a name="remarks"></a>備註  
 您可以放入`REM`陳述式單獨一行，或您可以將它放在另一個陳述式之後。 `REM`陳述式必須是該行的最後一個陳述式。 它會依照另一個陳述式，如果`REM`必須從該陳述式，以空格分隔。  
  
 您可以使用單引號 (`'`) 而不是`REM`。 您的註解另一個陳述式之後的同一行上還是位於單獨一行，也是如此。  
  
> [!NOTE]
>  您無法繼續`REM`陳述式使用行接續序列 (`_`)。 註解開始時，編譯器不會檢查特殊意義的字元。 對於多行註解，請使用另一個`REM`陳述式或註解符號 (`'`) 在每一行。  
  
## <a name="example"></a>範例  
 下列範例說明`REM`陳述式，這用來在程式中包含說明備註。 它也會顯示另一種使用單一的引號字元 (`'`) 而不是`REM`。  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [程式碼中的註解](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [如何：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
