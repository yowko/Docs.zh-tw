---
title: 如何：呼叫傳回值的程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 7f5d46babf31ea3c6babb29c0f1c08a23e51d598
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340734"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="95187-102">如何：呼叫傳回值的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95187-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="95187-103">`Function` 程式會將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="95187-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="95187-104">您可以將其名稱和引數包含在指派語句的右邊或運算式中，藉以呼叫它。</span><span class="sxs-lookup"><span data-stu-id="95187-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="95187-105">若要在運算式內呼叫函式程式</span><span class="sxs-lookup"><span data-stu-id="95187-105">To call a Function procedure within an expression</span></span>  
  
1. <span data-ttu-id="95187-106">使用 `Function` 程式名稱，方法與使用變數的方式相同。</span><span class="sxs-lookup"><span data-stu-id="95187-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="95187-107">您可以在任何可在運算式中使用變數或常數的位置，使用 `Function` 程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="95187-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2. <span data-ttu-id="95187-108">請在程式名稱後面加上括弧，以括住引數清單。</span><span class="sxs-lookup"><span data-stu-id="95187-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="95187-109">如果沒有引數，您可以選擇性地省略括弧。</span><span class="sxs-lookup"><span data-stu-id="95187-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="95187-110">不過，使用括弧可讓您的程式碼更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="95187-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="95187-111">將引數放在括弧內的引數清單中，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="95187-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="95187-112">請務必以 `Function` 程式定義對應參數的相同順序來提供引數。</span><span class="sxs-lookup"><span data-stu-id="95187-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="95187-113">或者，您可以依名稱傳遞一或多個引數。</span><span class="sxs-lookup"><span data-stu-id="95187-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="95187-114">如需詳細資訊，請參閱[依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)。</span><span class="sxs-lookup"><span data-stu-id="95187-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4. <span data-ttu-id="95187-115">從程式傳回的值會參與運算式，就如同變數或常數的值一樣。</span><span class="sxs-lookup"><span data-stu-id="95187-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="95187-116">若要在指派語句中呼叫函數程式</span><span class="sxs-lookup"><span data-stu-id="95187-116">To call a Function procedure in an assignment statement</span></span>  
  
1. <span data-ttu-id="95187-117">在指派語句中的等號（`=`）後面，使用 `Function` 程式名稱。</span><span class="sxs-lookup"><span data-stu-id="95187-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2. <span data-ttu-id="95187-118">請在程式名稱後面加上括弧，以括住引數清單。</span><span class="sxs-lookup"><span data-stu-id="95187-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="95187-119">如果沒有引數，您可以選擇性地省略括弧。</span><span class="sxs-lookup"><span data-stu-id="95187-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="95187-120">不過，使用括弧可讓您的程式碼更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="95187-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="95187-121">將引數放在括弧內的引數清單中，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="95187-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="95187-122">請務必以 `Function` 程式定義對應參數的相同順序來提供引數，除非您依名稱傳遞它們。</span><span class="sxs-lookup"><span data-stu-id="95187-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4. <span data-ttu-id="95187-123">從程式傳回的值會儲存在指派語句左側的變數或屬性中。</span><span class="sxs-lookup"><span data-stu-id="95187-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95187-124">範例</span><span class="sxs-lookup"><span data-stu-id="95187-124">Example</span></span>  
 <span data-ttu-id="95187-125">下列範例會呼叫 Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> 來取出作業系統環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="95187-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="95187-126">第一行會呼叫運算式中的 `Environ`，而第二行則會在指派語句中呼叫它。</span><span class="sxs-lookup"><span data-stu-id="95187-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="95187-127">`Environ` 會將變數名稱當做其唯一引數。</span><span class="sxs-lookup"><span data-stu-id="95187-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="95187-128">它會將變數的值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="95187-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="95187-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="95187-129">See also</span></span>

- [<span data-ttu-id="95187-130">函式程序</span><span class="sxs-lookup"><span data-stu-id="95187-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="95187-131">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="95187-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="95187-132">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="95187-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="95187-133">如何：建立傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="95187-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="95187-134">如何：傳回程序的值</span><span class="sxs-lookup"><span data-stu-id="95187-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="95187-135">如何：呼叫不傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="95187-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
