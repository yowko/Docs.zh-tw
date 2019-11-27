---
title: 如何：傳回程序的值
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 1371e4ed0ff28f9caf56eabf2a1bb9290edbe75c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346032"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="bc0ec-102">如何：傳回程序的值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc0ec-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="bc0ec-103">`Function` 程式會藉由執行 `Return` 語句或遇到 `Exit Function` 或 `End Function` 語句，將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="bc0ec-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="bc0ec-104">使用 Return 語句傳回值</span><span class="sxs-lookup"><span data-stu-id="bc0ec-104">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="bc0ec-105">將 `Return` 語句放在程式的工作完成的位置。</span><span class="sxs-lookup"><span data-stu-id="bc0ec-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="bc0ec-106">請在 `Return` 關鍵字後面加上運算式，其會產生您想要傳回給呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="bc0ec-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="bc0ec-107">同一個程序中可以有多個 `Return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bc0ec-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="bc0ec-108">下列 `Function` 程式會計算直角三角形的最長端（或斜邊），並將它傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="bc0ec-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="bc0ec-109">下列範例示範 `hypotenuse`的一般呼叫，它會儲存傳回的值。</span><span class="sxs-lookup"><span data-stu-id="bc0ec-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="bc0ec-110">使用 Exit 函數或 End 函式傳回值</span><span class="sxs-lookup"><span data-stu-id="bc0ec-110">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="bc0ec-111">在 `Function` 程式的至少一個位置中，將值指派給程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="bc0ec-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="bc0ec-112">當您執行 `Exit Function` 或 `End Function` 語句時，Visual Basic 會傳回最近指派給程式名稱的值。</span><span class="sxs-lookup"><span data-stu-id="bc0ec-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="bc0ec-113">同一個程序中可以有多個 `Exit Function` 陳述式，也可以混合 `Return` 和 `Exit Function` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bc0ec-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="bc0ec-114">`Function` 程式中只能有一個 `End Function` 語句。</span><span class="sxs-lookup"><span data-stu-id="bc0ec-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="bc0ec-115">如需詳細資訊和範例，請參閱[Function 語句](../../../../visual-basic/language-reference/statements/function-statement.md)中的「傳回值」。</span><span class="sxs-lookup"><span data-stu-id="bc0ec-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc0ec-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="bc0ec-116">See also</span></span>

- [<span data-ttu-id="bc0ec-117">程序</span><span class="sxs-lookup"><span data-stu-id="bc0ec-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="bc0ec-118">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="bc0ec-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="bc0ec-119">屬性程序</span><span class="sxs-lookup"><span data-stu-id="bc0ec-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="bc0ec-120">運算子程序</span><span class="sxs-lookup"><span data-stu-id="bc0ec-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="bc0ec-121">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="bc0ec-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="bc0ec-122">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="bc0ec-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="bc0ec-123">Return 陳述式</span><span class="sxs-lookup"><span data-stu-id="bc0ec-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="bc0ec-124">如何：建立傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="bc0ec-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="bc0ec-125">如何：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="bc0ec-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
