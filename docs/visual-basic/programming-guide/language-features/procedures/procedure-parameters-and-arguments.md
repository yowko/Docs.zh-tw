---
title: 程序參數和引數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: b0ab186945b456d7fb4dde3f52724b08a99e2827
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652496"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="422d7-102">程序參數和引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="422d7-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="422d7-103">在大部分情況下，需要一些資訊在其中呼叫的情況的相關程序。</span><span class="sxs-lookup"><span data-stu-id="422d7-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="422d7-104">執行重複或共用的工作的程序會針對每個呼叫使用不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="422d7-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="422d7-105">這項資訊包含變數、 常數和呼叫它時傳遞至程序的運算式。</span><span class="sxs-lookup"><span data-stu-id="422d7-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="422d7-106">A*參數*表示程序需要您提供當您呼叫它的值。</span><span class="sxs-lookup"><span data-stu-id="422d7-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="422d7-107">程序的宣告會定義它的參數。</span><span class="sxs-lookup"><span data-stu-id="422d7-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="422d7-108">您可以定義具有任何參數，一個參數，或一個以上的程序。</span><span class="sxs-lookup"><span data-stu-id="422d7-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="422d7-109">呼叫程序定義指定之參數的一部分*參數清單*。</span><span class="sxs-lookup"><span data-stu-id="422d7-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="422d7-110">*引數*程序參數表示您提供的值時呼叫的程序。</span><span class="sxs-lookup"><span data-stu-id="422d7-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="422d7-111">呼叫程序時，如果呼叫程式碼所提供的引數。</span><span class="sxs-lookup"><span data-stu-id="422d7-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="422d7-112">指定的引數的程序呼叫的部份稱為*引數清單*。</span><span class="sxs-lookup"><span data-stu-id="422d7-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="422d7-113">下圖顯示程式碼呼叫此程序`safeSquareRoot`兩個不同位置。</span><span class="sxs-lookup"><span data-stu-id="422d7-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="422d7-114">第一次呼叫會將變數的值傳遞`x`(4.0) 的參數`number`，和傳回值中的`root`(2.0) 指派給變數`y`。</span><span class="sxs-lookup"><span data-stu-id="422d7-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="422d7-115">第二個呼叫會傳遞至常值 9.0 `number`，並將傳回的值 (3.0) 指派給變數`z`。</span><span class="sxs-lookup"><span data-stu-id="422d7-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 <span data-ttu-id="422d7-116">![傳遞引數至參數示意圖](./media/parametersargue.gif "ParametersArgue")</span><span class="sxs-lookup"><span data-stu-id="422d7-116">![Graphic diagram of passing argument to parameter](./media/parametersargue.gif "ParametersArgue")</span></span>  
<span data-ttu-id="422d7-117">傳遞至參數的引數</span><span class="sxs-lookup"><span data-stu-id="422d7-117">Passing an argument to a parameter</span></span>  
  
 <span data-ttu-id="422d7-118">如需詳細資訊，請參閱[參數之間的差異和引數](./differences-between-parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="422d7-118">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="422d7-119">參數資料類型</span><span class="sxs-lookup"><span data-stu-id="422d7-119">Parameter Data Type</span></span>  
 <span data-ttu-id="422d7-120">您定義資料類型的參數使用`As`在其宣告中的子句。</span><span class="sxs-lookup"><span data-stu-id="422d7-120">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="422d7-121">例如，下列函式會接受一個字串和整數。</span><span class="sxs-lookup"><span data-stu-id="422d7-121">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 <span data-ttu-id="422d7-122">如果類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`Off,``As`子句是選擇性的不同之處在於任何一個參數會使用它，如果所有參數必須都使用它。</span><span class="sxs-lookup"><span data-stu-id="422d7-122">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="422d7-123">如果型別檢查`On`、`As`子句是必要的所有程序參數。</span><span class="sxs-lookup"><span data-stu-id="422d7-123">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="422d7-124">如果呼叫的程式碼必須不同於其對應的參數資料類型提供的引數，例如`Byte`至`String`參數，則必須執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="422d7-124">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
-   <span data-ttu-id="422d7-125">提供唯一可擴展參數資料類型; 資料類型的引數</span><span class="sxs-lookup"><span data-stu-id="422d7-125">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
-   <span data-ttu-id="422d7-126">設定`Option Strict Off`允許隱含的縮小轉換; 或</span><span class="sxs-lookup"><span data-stu-id="422d7-126">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
-   <span data-ttu-id="422d7-127">使用轉換關鍵字，明確地轉換資料類型。</span><span class="sxs-lookup"><span data-stu-id="422d7-127">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="422d7-128">型別參數</span><span class="sxs-lookup"><span data-stu-id="422d7-128">Type Parameters</span></span>  
 <span data-ttu-id="422d7-129">A*泛型程序*也會定義一或多個*型別參數*除了一般參數。</span><span class="sxs-lookup"><span data-stu-id="422d7-129">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="422d7-130">泛型程序可讓呼叫的程式碼傳遞不同的資料類型每次呼叫程序，讓它可以調整資料類型，每個個別呼叫的需求。</span><span class="sxs-lookup"><span data-stu-id="422d7-130">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="422d7-131">請參閱 [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="422d7-131">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="422d7-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="422d7-132">See Also</span></span>  
 [<span data-ttu-id="422d7-133">程序</span><span class="sxs-lookup"><span data-stu-id="422d7-133">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="422d7-134">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="422d7-134">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="422d7-135">函式程序</span><span class="sxs-lookup"><span data-stu-id="422d7-135">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="422d7-136">屬性程序</span><span class="sxs-lookup"><span data-stu-id="422d7-136">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="422d7-137">運算子程序</span><span class="sxs-lookup"><span data-stu-id="422d7-137">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="422d7-138">如何：定義程序的參數</span><span class="sxs-lookup"><span data-stu-id="422d7-138">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="422d7-139">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="422d7-139">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="422d7-140">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="422d7-140">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="422d7-141">程序多載化</span><span class="sxs-lookup"><span data-stu-id="422d7-141">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="422d7-142">在 Visual Basic 中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="422d7-142">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
