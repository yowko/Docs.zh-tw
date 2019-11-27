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
表示外部程式在其 DLL 中有另一個名稱。  
  
## <a name="remarks"></a>備註  
 `Alias` 關鍵字可以在此內容中使用：  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 在下列範例中，`Alias` 關鍵字是用來在 advapi32.dll 中提供函式的名稱，`GetUserNameA`，在此範例中會使用 `getUserName` 來取代。 函式 `getUserName` 是在子 `getUser`中呼叫，它會顯示目前使用者的名稱。  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>另請參閱

- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
