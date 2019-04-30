---
title: Alias 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 84c8f39e632eebbe5382492669820910b38bc360
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053349"
---
# <a name="alias-clause-visual-basic"></a>Alias 子句 (Visual Basic)
表示外部程序在其 DLL 中有另一個名稱。  
  
## <a name="remarks"></a>備註  
 `Alias`關鍵字可以用在此內容中：  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 在下列範例中，`Alias`關鍵字用以提供位在 advapi32.dll，函式名稱`GetUserNameA`，、 該`getUserName`此範例中使用的位置。 函式`getUserName`稱為子`getUser`，其中顯示目前使用者的名稱。  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>另請參閱

- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
