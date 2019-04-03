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
ms.openlocfilehash: 80065cabcacdcf44b04fef7bacb978ca9c8077ae
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825452"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="27dea-102">程序參數和引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27dea-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="27dea-103">在大部分情況下，程序會需要一些資訊在其中呼叫的情況。</span><span class="sxs-lookup"><span data-stu-id="27dea-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="27dea-104">執行重複或共用工作的程序會針對每個呼叫中使用不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="27dea-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="27dea-105">這項資訊是由變數、 常數和您傳遞至程序時呼叫它的運算式所組成。</span><span class="sxs-lookup"><span data-stu-id="27dea-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="27dea-106">A*參數*表示程序需要您提供當您呼叫它的值。</span><span class="sxs-lookup"><span data-stu-id="27dea-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="27dea-107">程序的宣告會定義其參數。</span><span class="sxs-lookup"><span data-stu-id="27dea-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="27dea-108">您可以定義具有任何參數，一個參數，或一個以上的程序。</span><span class="sxs-lookup"><span data-stu-id="27dea-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="27dea-109">在呼叫程序定義指定之參數的一部分*參數清單*。</span><span class="sxs-lookup"><span data-stu-id="27dea-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="27dea-110">*引數*程序參數代表您提供的值，當您呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="27dea-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="27dea-111">呼叫程序時，呼叫程式碼會提供引數。</span><span class="sxs-lookup"><span data-stu-id="27dea-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="27dea-112">指定的引數的程序呼叫的部分稱為*引數清單*。</span><span class="sxs-lookup"><span data-stu-id="27dea-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="27dea-113">下圖顯示程式碼呼叫程序`safeSquareRoot`從兩個不同的地方。</span><span class="sxs-lookup"><span data-stu-id="27dea-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="27dea-114">第一次呼叫會將變數的值傳遞`x`(4.0) 參數`number`，並在傳回的值`root`(2.0) 指派給變數`y`。</span><span class="sxs-lookup"><span data-stu-id="27dea-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="27dea-115">第二次呼叫會將傳遞常值數值 9.0 `number`，並將傳回的值 (3.0) 指派給變數`z`。</span><span class="sxs-lookup"><span data-stu-id="27dea-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![此圖顯示傳遞至參數的引數](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="27dea-117">如需詳細資訊，請參閱 <<c0> [ 參數之間的差異和引數](./differences-between-parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="27dea-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="27dea-118">參數資料類型</span><span class="sxs-lookup"><span data-stu-id="27dea-118">Parameter Data Type</span></span>  
 <span data-ttu-id="27dea-119">您定義資料類型的參數使用`As`在其宣告中的子句。</span><span class="sxs-lookup"><span data-stu-id="27dea-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="27dea-120">例如，下列函式會接受字串和整數。</span><span class="sxs-lookup"><span data-stu-id="27dea-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="27dea-121">如果類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`Off,``As`子句是選擇性的不同之處在於任何一個參數會使用它，如果所有參數必須都使用它。</span><span class="sxs-lookup"><span data-stu-id="27dea-121">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="27dea-122">如果型別檢查`On`，則`As`子句是必要的所有程序參數。</span><span class="sxs-lookup"><span data-stu-id="27dea-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="27dea-123">如果呼叫程式碼必須要有這類資料類型不同，其對應的參數提供引數`Byte`至`String`參數，它必須執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="27dea-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
-   <span data-ttu-id="27dea-124">提供引數會擴展為參數的資料型別; 的資料類型</span><span class="sxs-lookup"><span data-stu-id="27dea-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
-   <span data-ttu-id="27dea-125">設定`Option Strict Off`允許隱含的縮小轉換; 或</span><span class="sxs-lookup"><span data-stu-id="27dea-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
-   <span data-ttu-id="27dea-126">您可以使用轉換關鍵字，明確轉換成資料類型。</span><span class="sxs-lookup"><span data-stu-id="27dea-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="27dea-127">類型參數</span><span class="sxs-lookup"><span data-stu-id="27dea-127">Type Parameters</span></span>  
 <span data-ttu-id="27dea-128">A*泛型程序*也會定義一或多個*型別參數*除了其一般的參數。</span><span class="sxs-lookup"><span data-stu-id="27dea-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="27dea-129">泛型程序可讓呼叫端的程式碼，來傳遞不同的資料類型每次呼叫此程序，讓它可以調整資料類型需求的每個個別的呼叫。</span><span class="sxs-lookup"><span data-stu-id="27dea-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="27dea-130">請參閱 [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="27dea-130">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27dea-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27dea-131">See also</span></span>

- [<span data-ttu-id="27dea-132">程序</span><span class="sxs-lookup"><span data-stu-id="27dea-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="27dea-133">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="27dea-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="27dea-134">函式程序</span><span class="sxs-lookup"><span data-stu-id="27dea-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="27dea-135">屬性程序</span><span class="sxs-lookup"><span data-stu-id="27dea-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="27dea-136">運算子程序</span><span class="sxs-lookup"><span data-stu-id="27dea-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="27dea-137">如何：如需程序來定義參數</span><span class="sxs-lookup"><span data-stu-id="27dea-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="27dea-138">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="27dea-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="27dea-139">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="27dea-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="27dea-140">程序多載化</span><span class="sxs-lookup"><span data-stu-id="27dea-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="27dea-141">在 Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="27dea-141">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
