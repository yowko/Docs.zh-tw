---
title: Alias 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 84c8f39e632eebbe5382492669820910b38bc360
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839739"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="bb049-102">Alias 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb049-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="bb049-103">表示外部程序在其 DLL 中有另一個名稱。</span><span class="sxs-lookup"><span data-stu-id="bb049-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb049-104">備註</span><span class="sxs-lookup"><span data-stu-id="bb049-104">Remarks</span></span>  
 <span data-ttu-id="bb049-105">`Alias`關鍵字可以用在此內容中：</span><span class="sxs-lookup"><span data-stu-id="bb049-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="bb049-106">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="bb049-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="bb049-107">在下列範例中，`Alias`關鍵字用以提供位在 advapi32.dll，函式名稱`GetUserNameA`，、 該`getUserName`此範例中使用的位置。</span><span class="sxs-lookup"><span data-stu-id="bb049-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="bb049-108">函式`getUserName`稱為子`getUser`，其中顯示目前使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="bb049-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="bb049-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb049-109">See also</span></span>

- [<span data-ttu-id="bb049-110">關鍵字</span><span class="sxs-lookup"><span data-stu-id="bb049-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
