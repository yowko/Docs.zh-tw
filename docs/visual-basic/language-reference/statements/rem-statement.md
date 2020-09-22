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
ms.openlocfilehash: 6161a9f7e589988882b5f76477bc069afd2b9b41
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871955"
---
# <a name="rem-statement-visual-basic"></a>REM 陳述式 (Visual Basic)

用來在程式的原始程式碼中包含解釋備註。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a>組件  

 `comment`  
 選擇性。 您想要包含的任何註解文字。 關鍵字和之間必須有一個空格 `REM` `comment` 。  
  
## <a name="remarks"></a>備註  

 您可以單獨將 `REM` 語句放在一行上，也可以將它放在另一個語句後面的一行。 `REM`語句必須是該行的最後一個語句。 如果它遵循另一個語句，則 `REM` 必須以空格分隔該語句。  
  
 您可以使用單引號 (`'`) 而不是 `REM` 。 無論您的批註是在同一行上的另一個語句之後，還是單獨在一行上，都是如此。  
  
> [!NOTE]
> 您無法 `REM` 使用行接續順序 () 來繼續執行語句 `_` 。 當批註開始時，編譯器不會檢查字元的特殊意義。 若為多行批註，請 `REM` 在每一行上使用另一個語句或批註符號 (`'`) 。  
  
## <a name="example"></a>範例  

 下列範例說明 `REM` 用來在程式中包含說明備註的語句。 它也會顯示使用單引號字元 (`'`) ，而不是的替代方法 `REM` 。  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [程式碼中的註解](../../programming-guide/program-structure/comments-in-code.md)
- [作法：程式碼中的 Break 及 Combine 陳述式](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
