---
title: Alias 子句
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: a7f67224c5d26816bdc1974dc4aa82d796c41284
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349152"
---
# <a name="alias-clause-visual-basic"></a>Alias 子句 (Visual Basic)
Indicates that an external procedure has another name in its DLL.  
  
## <a name="remarks"></a>備註  
 The `Alias` keyword can be used in this context:  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example. Function `getUserName` is called in sub `getUser`, which displays the name of the current user.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>請參閱

- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
