---
title: 其他控制結構 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c42070ce2ea866e59e1b2e190f7c05e1ee7cc922
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907838"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="58fdd-102">其他控制結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58fdd-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="58fdd-103">Visual Basic 提供可協助您控制結構處置資源，或減少您必須重複的物件參考的次數。</span><span class="sxs-lookup"><span data-stu-id="58fdd-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="58fdd-104">使用...使用建構的結束</span><span class="sxs-lookup"><span data-stu-id="58fdd-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="58fdd-105">`Using...End Using`建構建立陳述式區塊，請在其中使用的資源，例如 SQL 連接。</span><span class="sxs-lookup"><span data-stu-id="58fdd-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="58fdd-106">您可以選擇性地取得的資源`Using`陳述式。</span><span class="sxs-lookup"><span data-stu-id="58fdd-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="58fdd-107">當您結束`Using`區塊時，Visual Basic 自動處置該資源使其可供其他程式碼，以使用。</span><span class="sxs-lookup"><span data-stu-id="58fdd-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="58fdd-108">資源必須是本機和可處置。</span><span class="sxs-lookup"><span data-stu-id="58fdd-108">The resource must be local and disposable.</span></span> <span data-ttu-id="58fdd-109">如需詳細資訊，請參閱 [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="58fdd-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="58fdd-110">與...建構的結尾</span><span class="sxs-lookup"><span data-stu-id="58fdd-110">With...End With Construction</span></span>  
 <span data-ttu-id="58fdd-111">`With...End With`建構可讓您一次指定的物件參考，然後再執行一系列存取其成員的陳述式。</span><span class="sxs-lookup"><span data-stu-id="58fdd-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="58fdd-112">這可以簡化程式碼，並改善效能，因為 Visual Basic 不需要重新建立每個陳述式來存取它的參考。</span><span class="sxs-lookup"><span data-stu-id="58fdd-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="58fdd-113">如需詳細資訊，請參閱[與...With...end With 陳述式](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="58fdd-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58fdd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58fdd-114">See also</span></span>

- [<span data-ttu-id="58fdd-115">控制流程</span><span class="sxs-lookup"><span data-stu-id="58fdd-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="58fdd-116">決策結構</span><span class="sxs-lookup"><span data-stu-id="58fdd-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="58fdd-117">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="58fdd-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="58fdd-118">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="58fdd-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="58fdd-119">Using 陳述式</span><span class="sxs-lookup"><span data-stu-id="58fdd-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
- [<span data-ttu-id="58fdd-120">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="58fdd-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
