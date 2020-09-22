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
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="a1267-102">Alias 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1267-102">Alias Clause (Visual Basic)</span></span>

<span data-ttu-id="a1267-103">指出外部程式在其 DLL 中有另一個名稱。</span><span class="sxs-lookup"><span data-stu-id="a1267-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1267-104">備註</span><span class="sxs-lookup"><span data-stu-id="a1267-104">Remarks</span></span>  

 <span data-ttu-id="a1267-105">`Alias`關鍵字可用於此內容中：</span><span class="sxs-lookup"><span data-stu-id="a1267-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="a1267-106">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="a1267-106">Declare Statement</span></span>](declare-statement.md)  
  
 <span data-ttu-id="a1267-107">在下列範例中， `Alias` 關鍵字是用來提供 advapi32.dll 中的函式名稱，在 `GetUserNameA` `getUserName` 此範例中會用來取代。</span><span class="sxs-lookup"><span data-stu-id="a1267-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="a1267-108">函數 `getUserName` 會在 sub 中呼叫 `getUser` ，以顯示目前使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="a1267-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="a1267-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1267-109">See also</span></span>

- [<span data-ttu-id="a1267-110">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a1267-110">Keywords</span></span>](../keywords/index.md)
