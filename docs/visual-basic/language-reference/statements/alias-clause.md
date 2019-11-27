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
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="50799-102">Alias 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50799-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="50799-103">表示外部程式在其 DLL 中有另一個名稱。</span><span class="sxs-lookup"><span data-stu-id="50799-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50799-104">備註</span><span class="sxs-lookup"><span data-stu-id="50799-104">Remarks</span></span>  
 <span data-ttu-id="50799-105">`Alias` 關鍵字可以在此內容中使用：</span><span class="sxs-lookup"><span data-stu-id="50799-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="50799-106">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="50799-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="50799-107">在下列範例中，`Alias` 關鍵字是用來在 advapi32.dll 中提供函式的名稱，`GetUserNameA`，在此範例中會使用 `getUserName` 來取代。</span><span class="sxs-lookup"><span data-stu-id="50799-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="50799-108">函式 `getUserName` 是在子 `getUser`中呼叫，它會顯示目前使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="50799-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="50799-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50799-109">See also</span></span>

- [<span data-ttu-id="50799-110">關鍵字</span><span class="sxs-lookup"><span data-stu-id="50799-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
