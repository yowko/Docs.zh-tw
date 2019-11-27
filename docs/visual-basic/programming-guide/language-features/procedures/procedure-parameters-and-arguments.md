---
title: 程序參數和引數
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
ms.openlocfilehash: 7dfbbcb39cf7bb05c8a62a7a252e425f287c9a09
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352574"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="9603b-102">程序參數和引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9603b-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="9603b-103">在大部分的情況下，程式需要一些有關已呼叫它的情況的資訊。</span><span class="sxs-lookup"><span data-stu-id="9603b-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="9603b-104">執行重複或共用工作的程式會針對每個呼叫使用不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="9603b-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="9603b-105">這項資訊是由您在呼叫它時傳遞給程式的變數、常數和運算式所組成。</span><span class="sxs-lookup"><span data-stu-id="9603b-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="9603b-106">*參數*代表當您呼叫它時，程式預期會提供的值。</span><span class="sxs-lookup"><span data-stu-id="9603b-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="9603b-107">程式的宣告會定義其參數。</span><span class="sxs-lookup"><span data-stu-id="9603b-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="9603b-108">您可以定義不含任何參數、一個參數或一個以上的程式。</span><span class="sxs-lookup"><span data-stu-id="9603b-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="9603b-109">指定參數之程序定義的部分稱為「參數清單」（ *parameter list*）。</span><span class="sxs-lookup"><span data-stu-id="9603b-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="9603b-110">*引數*代表當您呼叫程式時，您提供給程式參數的值。</span><span class="sxs-lookup"><span data-stu-id="9603b-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="9603b-111">呼叫程式碼會在呼叫程式時提供引數。</span><span class="sxs-lookup"><span data-stu-id="9603b-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="9603b-112">程序呼叫中指定引數的部分稱為*引數清單*。</span><span class="sxs-lookup"><span data-stu-id="9603b-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="9603b-113">下圖顯示從兩個不同的位置呼叫程式 `safeSquareRoot` 程式碼。</span><span class="sxs-lookup"><span data-stu-id="9603b-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="9603b-114">第一個呼叫會將變數的值 `x` （4.0）傳遞給參數 `number`，並將 `root` （2.0）中的傳回值指派給變數 `y`。</span><span class="sxs-lookup"><span data-stu-id="9603b-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="9603b-115">第二個呼叫會將常值9.0 傳遞給 `number`，並將傳回值（3.0）指派給變數 `z`。</span><span class="sxs-lookup"><span data-stu-id="9603b-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![顯示將引數傳遞至參數的圖表](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="9603b-117">如需詳細資訊，請參閱[參數和引數之間的差異](./differences-between-parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="9603b-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="9603b-118">參數資料類型</span><span class="sxs-lookup"><span data-stu-id="9603b-118">Parameter Data Type</span></span>  
 <span data-ttu-id="9603b-119">您可以在其宣告中使用 `As` 子句，以定義參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="9603b-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="9603b-120">例如，下列函數會接受字串和整數。</span><span class="sxs-lookup"><span data-stu-id="9603b-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="9603b-121">如果類型檢查參數（[Option Strict 語句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)）為 `Off,` 則 `As` 子句是選擇性的，但如果有任何一個參數使用它，則所有參數都必須使用它。</span><span class="sxs-lookup"><span data-stu-id="9603b-121">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="9603b-122">如果 `On`類型檢查，所有程式參數都需要 `As` 子句。</span><span class="sxs-lookup"><span data-stu-id="9603b-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="9603b-123">如果呼叫程式碼預期提供的引數與其對應參數的資料類型不同，例如 `Byte` 至 `String` 參數，則必須執行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="9603b-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="9603b-124">僅提供資料類型為的引數，可擴大為參數資料類型;</span><span class="sxs-lookup"><span data-stu-id="9603b-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="9603b-125">將 `Option Strict Off` 設定為允許隱含的縮小轉換;或</span><span class="sxs-lookup"><span data-stu-id="9603b-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="9603b-126">使用轉換關鍵字來明確轉換資料類型。</span><span class="sxs-lookup"><span data-stu-id="9603b-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="9603b-127">類型參數</span><span class="sxs-lookup"><span data-stu-id="9603b-127">Type Parameters</span></span>  
 <span data-ttu-id="9603b-128">*泛型*程式也會定義一或多個*型別參數*，以及其一般參數。</span><span class="sxs-lookup"><span data-stu-id="9603b-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="9603b-129">泛型程式可讓呼叫程式碼在每次呼叫程式時傳遞不同的資料類型，因此它可以根據每個個別呼叫的需求來量身訂做資料類型。</span><span class="sxs-lookup"><span data-stu-id="9603b-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="9603b-130">請參閱 [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="9603b-130">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9603b-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="9603b-131">See also</span></span>

- [<span data-ttu-id="9603b-132">程序</span><span class="sxs-lookup"><span data-stu-id="9603b-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="9603b-133">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="9603b-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="9603b-134">函式程序</span><span class="sxs-lookup"><span data-stu-id="9603b-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="9603b-135">屬性程序</span><span class="sxs-lookup"><span data-stu-id="9603b-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="9603b-136">運算子程序</span><span class="sxs-lookup"><span data-stu-id="9603b-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="9603b-137">如何：定義程序的參數</span><span class="sxs-lookup"><span data-stu-id="9603b-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="9603b-138">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="9603b-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="9603b-139">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="9603b-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="9603b-140">程序多載化</span><span class="sxs-lookup"><span data-stu-id="9603b-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="9603b-141">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="9603b-141">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
