---
title: 其他控制結構
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 758df361f421684655147ae288af3f350e53c4d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348138"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="4b44b-102">其他控制結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b44b-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="4b44b-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span><span class="sxs-lookup"><span data-stu-id="4b44b-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="4b44b-104">Using...End Using Construction</span><span class="sxs-lookup"><span data-stu-id="4b44b-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="4b44b-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span><span class="sxs-lookup"><span data-stu-id="4b44b-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="4b44b-106">You can optionally acquire the resource with the `Using` statement.</span><span class="sxs-lookup"><span data-stu-id="4b44b-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="4b44b-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span><span class="sxs-lookup"><span data-stu-id="4b44b-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="4b44b-108">The resource must be local and disposable.</span><span class="sxs-lookup"><span data-stu-id="4b44b-108">The resource must be local and disposable.</span></span> <span data-ttu-id="4b44b-109">如需詳細資訊，請參閱 [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4b44b-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="4b44b-110">With...End With Construction</span><span class="sxs-lookup"><span data-stu-id="4b44b-110">With...End With Construction</span></span>  
 <span data-ttu-id="4b44b-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span><span class="sxs-lookup"><span data-stu-id="4b44b-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="4b44b-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span><span class="sxs-lookup"><span data-stu-id="4b44b-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="4b44b-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4b44b-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b44b-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="4b44b-114">See also</span></span>

- [<span data-ttu-id="4b44b-115">控制流程</span><span class="sxs-lookup"><span data-stu-id="4b44b-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="4b44b-116">決策結構</span><span class="sxs-lookup"><span data-stu-id="4b44b-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="4b44b-117">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="4b44b-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="4b44b-118">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="4b44b-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="4b44b-119">Using 陳述式</span><span class="sxs-lookup"><span data-stu-id="4b44b-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
- [<span data-ttu-id="4b44b-120">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="4b44b-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
