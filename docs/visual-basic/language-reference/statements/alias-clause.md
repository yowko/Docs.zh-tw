---
title: Alias 子句
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 77d4685f242864842e5a84b3a3de3ba1793e9aa4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866683"
---
# <a name="alias-clause-visual-basic"></a>Alias 子句 (Visual Basic)

指出外部程式在其 DLL 中有另一個名稱。  
  
## <a name="remarks"></a>備註  

 `Alias`關鍵字可用於此內容中：  
  
 [Declare Statement](declare-statement.md)  
  
 在下列範例中， `Alias` 關鍵字是用來提供 advapi32.dll 中的函式名稱，在 `GetUserNameA` `getUserName` 此範例中會用來取代。 函數 `getUserName` 會在 sub 中呼叫 `getUser` ，以顯示目前使用者的名稱。  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>另請參閱

- [關鍵字](../keywords/index.md)
