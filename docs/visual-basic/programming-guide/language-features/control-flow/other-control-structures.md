---
title: 其他控制結構
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c6d80b237c7c3512c2904547842fdeb3c69bef68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402014"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="61c34-102">其他控制結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61c34-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="61c34-103">Visual Basic 提供控制結構，協助您處置資源，或減少必須重複物件參考的次數。</span><span class="sxs-lookup"><span data-stu-id="61c34-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="61c34-104">使用 .。。使用結構結束</span><span class="sxs-lookup"><span data-stu-id="61c34-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="61c34-105">此 `Using...End Using` 結構會建立一個語句區塊，您可以在其中使用 SQL 連接之類的資源。</span><span class="sxs-lookup"><span data-stu-id="61c34-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="61c34-106">您可以選擇性地使用語句取得資源 `Using` 。</span><span class="sxs-lookup"><span data-stu-id="61c34-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="61c34-107">當您結束 `Using` 區塊時，Visual Basic 會自動處置資源，使其可供其他程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="61c34-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="61c34-108">資源必須是本機且可處置的。</span><span class="sxs-lookup"><span data-stu-id="61c34-108">The resource must be local and disposable.</span></span> <span data-ttu-id="61c34-109">如需詳細資訊，請參閱[Using 語句](../../../language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="61c34-109">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="61c34-110">使用 .。。以結構結束</span><span class="sxs-lookup"><span data-stu-id="61c34-110">With...End With Construction</span></span>  
 <span data-ttu-id="61c34-111">此 `With...End With` 結構可讓您指定一次物件參考，然後執行一系列存取其成員的語句。</span><span class="sxs-lookup"><span data-stu-id="61c34-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="61c34-112">這可簡化您的程式碼並改善效能，因為 Visual Basic 不需要為存取它的每個語句重新建立參考。</span><span class="sxs-lookup"><span data-stu-id="61c34-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="61c34-113">如需詳細資訊，請參閱[With .。。結尾為語句](../../../language-reference/statements/with-end-with-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="61c34-113">For more information, see [With...End With Statement](../../../language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61c34-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61c34-114">See also</span></span>

- [<span data-ttu-id="61c34-115">控制流程</span><span class="sxs-lookup"><span data-stu-id="61c34-115">Control Flow</span></span>](index.md)
- [<span data-ttu-id="61c34-116">決策結構</span><span class="sxs-lookup"><span data-stu-id="61c34-116">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="61c34-117">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="61c34-117">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="61c34-118">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="61c34-118">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="61c34-119">Using 語句</span><span class="sxs-lookup"><span data-stu-id="61c34-119">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
- [<span data-ttu-id="61c34-120">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="61c34-120">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
