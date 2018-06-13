---
title: 如何：呼叫傳回值的程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 35f757609b6d0b36652db3b14e62ecd299a063ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649408"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="2b5a0-102">如何：呼叫傳回值的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b5a0-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="2b5a0-103">A`Function`程序傳回給呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="2b5a0-104">您可以呼叫它藉由其名稱和引數右側在指派陳述式或運算式中。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="2b5a0-105">若要呼叫的函式程序，在運算式內</span><span class="sxs-lookup"><span data-stu-id="2b5a0-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="2b5a0-106">使用`Function`程序的名稱相同的方式，您會使用變數。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="2b5a0-107">您可以使用`Function`程序呼叫的運算式中使用變數或常數的任何地方。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="2b5a0-108">請依照下列程序名稱與括號來括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="2b5a0-109">如果有任何引數，您可以選擇性地省略括號。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="2b5a0-110">不過，使用括號可讓您的程式碼更方便閱讀。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="2b5a0-111">將引數放在括號，並以逗號分隔的引數清單。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="2b5a0-112">確定您提供的相同順序的引數，`Function`程序所定義的對應參數。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="2b5a0-113">或者，您可以依名稱傳遞一個或多個引數。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="2b5a0-114">如需詳細資訊，請參閱[傳遞引數依位置和名稱](./passing-arguments-by-position-and-by-name.md)。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="2b5a0-115">程序所傳回的值加入運算式中只做為值的變數或常數。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="2b5a0-116">在指派陳述式中呼叫的函式程序</span><span class="sxs-lookup"><span data-stu-id="2b5a0-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="2b5a0-117">使用`Function`之後等程序名稱 (`=`) 登入指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="2b5a0-118">請依照下列程序名稱與括號來括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="2b5a0-119">如果有任何引數，您可以選擇性地省略括號。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="2b5a0-120">不過，使用括號可讓您的程式碼更方便閱讀。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="2b5a0-121">將引數放在括號，並以逗號分隔的引數清單。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="2b5a0-122">確定您提供的相同順序的引數，`Function`程序所定義的對應參數，除非您依名稱傳遞它們。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="2b5a0-123">程序所傳回的值會儲存在變數或指派陳述式左邊的屬性。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b5a0-124">範例</span><span class="sxs-lookup"><span data-stu-id="2b5a0-124">Example</span></span>  
 <span data-ttu-id="2b5a0-125">下列範例會呼叫 Visual Basic<xref:Microsoft.VisualBasic.Interaction.Environ%2A>擷取作業系統的環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="2b5a0-126">第一列呼叫`Environ`內使用運算式中，且第二個列中呼叫它的指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="2b5a0-127">`Environ` 使用變數名稱做為其唯一的引數。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="2b5a0-128">它會傳回呼叫程式碼的變數的值。</span><span class="sxs-lookup"><span data-stu-id="2b5a0-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2b5a0-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b5a0-129">See Also</span></span>  
 [<span data-ttu-id="2b5a0-130">函式程序</span><span class="sxs-lookup"><span data-stu-id="2b5a0-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="2b5a0-131">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="2b5a0-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="2b5a0-132">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="2b5a0-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="2b5a0-133">如何：建立傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="2b5a0-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="2b5a0-134">如何：傳回程序的值</span><span class="sxs-lookup"><span data-stu-id="2b5a0-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="2b5a0-135">如何：呼叫不傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="2b5a0-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
