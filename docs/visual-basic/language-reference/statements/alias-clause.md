---
title: Alias 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 3b1a66ecfd3c023a12ac62191ca3671a195b45a6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978224"
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
