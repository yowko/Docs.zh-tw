---
title: Alias 子句
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: c28e931a376b20b2058a7187551405cd9523d4fe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408467"
---
# <a name="alias-clause-visual-basic"></a>Alias 子句 (Visual Basic)
表示外部程式在其 DLL 中有另一個名稱。  
  
## <a name="remarks"></a>備註  
 `Alias`關鍵字可以在此內容中使用：  
  
 [Declare Statement](declare-statement.md)  
  
 在下列範例中， `Alias` 關鍵字是用來在 advapi32.dll 中提供函式的名稱，此函式 `GetUserNameA` 會在 `getUserName` 此範例中用來取代。 函數 `getUserName` 是在 sub 中呼叫 `getUser` ，它會顯示目前使用者的名稱。  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>另請參閱

- [關鍵字](../keywords/index.md)
