---
title: "如何︰ 呼叫傳回的值 (Visual Basic) 的程序 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
- procedures, returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cc1e274a705618213c830d7cf4f61a5e64afd980
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="2148e-102">如何：呼叫傳回值的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2148e-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="2148e-103">A`Function`值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="2148e-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="2148e-104">它可以呼叫其名稱和引數包括在指派陳述式或運算式的右側。</span><span class="sxs-lookup"><span data-stu-id="2148e-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="2148e-105">若要呼叫的函式程序，在運算式中</span><span class="sxs-lookup"><span data-stu-id="2148e-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="2148e-106">使用`Function`程序的名稱相同的方式，您會使用變數。</span><span class="sxs-lookup"><span data-stu-id="2148e-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="2148e-107">您可以使用`Function`程序呼叫，您可以在運算式中使用變數或常數的任何地方。</span><span class="sxs-lookup"><span data-stu-id="2148e-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="2148e-108">請依照下列程序名稱以括號括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="2148e-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="2148e-109">如果不有任何引數，您可以省略括號。</span><span class="sxs-lookup"><span data-stu-id="2148e-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="2148e-110">不過，使用括號會讓您的程式碼容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="2148e-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="2148e-111">將引數放在括號，以逗號分隔的引數清單。</span><span class="sxs-lookup"><span data-stu-id="2148e-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="2148e-112">確定您提供的相同順序的引數，`Function`程序定義對應的參數。</span><span class="sxs-lookup"><span data-stu-id="2148e-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="2148e-113">或者，您可以依名稱傳遞一個或多個引數。</span><span class="sxs-lookup"><span data-stu-id="2148e-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="2148e-114">如需詳細資訊，請參閱[傳遞引數依位置和名稱](./passing-arguments-by-position-and-by-name.md)。</span><span class="sxs-lookup"><span data-stu-id="2148e-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="2148e-115">從程序傳回的值加入運算式中只做為值的變數或常數。</span><span class="sxs-lookup"><span data-stu-id="2148e-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="2148e-116">在指派陳述式中呼叫函式程序</span><span class="sxs-lookup"><span data-stu-id="2148e-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="2148e-117">使用`Function`之後等程序名稱 (`=`) 登入指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="2148e-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="2148e-118">請依照下列程序名稱以括號括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="2148e-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="2148e-119">如果不有任何引數，您可以省略括號。</span><span class="sxs-lookup"><span data-stu-id="2148e-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="2148e-120">不過，使用括號會讓您的程式碼容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="2148e-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="2148e-121">將引數放在括號，以逗號分隔的引數清單。</span><span class="sxs-lookup"><span data-stu-id="2148e-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="2148e-122">確定您提供的相同順序的引數，`Function`程序定義對應的參數，除非您依名稱傳遞它們。</span><span class="sxs-lookup"><span data-stu-id="2148e-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="2148e-123">從程序傳回的值儲存在變數或屬性指派陳述式的左邊。</span><span class="sxs-lookup"><span data-stu-id="2148e-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2148e-124">範例</span><span class="sxs-lookup"><span data-stu-id="2148e-124">Example</span></span>  
 <span data-ttu-id="2148e-125">下列範例會呼叫[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<xref:Microsoft.VisualBasic.Interaction.Environ%2A>擷取作業系統環境變數的值。</xref:Microsoft.VisualBasic.Interaction.Environ%2A></span><span class="sxs-lookup"><span data-stu-id="2148e-125">The following example calls the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="2148e-126">第一列呼叫`Environ`內第二個運算式，列在中呼叫它在指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="2148e-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="2148e-127">`Environ`使用變數名稱做為其唯一引數。</span><span class="sxs-lookup"><span data-stu-id="2148e-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="2148e-128">會傳回呼叫程式碼變數的值。</span><span class="sxs-lookup"><span data-stu-id="2148e-128">It returns the variable's value to the calling code.</span></span>  
  
 <span data-ttu-id="2148e-129">[!code-vb[VbVbcnProcedures #&7;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2148e-129">[!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2148e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2148e-130">See Also</span></span>  
 <span data-ttu-id="2148e-131">[Function 程序](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="2148e-131">[Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="2148e-132"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="2148e-132"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="2148e-133"> [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="2148e-133"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="2148e-134"> [如何︰ 建立程序傳回值](./how-to-create-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="2148e-134"> [How to: Create a Procedure that Returns a Value](./how-to-create-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="2148e-135"> [如何︰ 從程序傳回值](./how-to-return-a-value-from-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="2148e-135"> [How to: Return a Value from a Procedure](./how-to-return-a-value-from-a-procedure.md) </span></span>  
<span data-ttu-id="2148e-136"> [如何：呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="2148e-136"> [How to: Call a Procedure that Does Not Return a Value](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span></span>
