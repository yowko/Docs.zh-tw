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
ms.openlocfilehash: c7f8eb1fa4e1fa3d87474d048d5a60994b0b7fc5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071270"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="a2793-102">程序參數和引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2793-102">Procedure Parameters and Arguments (Visual Basic)</span></span>

<span data-ttu-id="a2793-103">在大部分的情況下，程式都需要有關其呼叫情況的一些資訊。</span><span class="sxs-lookup"><span data-stu-id="a2793-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="a2793-104">執行重複或共用工作的程式會針對每個呼叫使用不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="a2793-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="a2793-105">這項資訊是由您在呼叫過程中傳遞給程式的變數、常數和運算式所組成。</span><span class="sxs-lookup"><span data-stu-id="a2793-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="a2793-106">*參數*代表程式要求您在呼叫時提供的值。</span><span class="sxs-lookup"><span data-stu-id="a2793-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="a2793-107">程式的宣告會定義其參數。</span><span class="sxs-lookup"><span data-stu-id="a2793-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="a2793-108">您可以定義沒有參數、一個參數或一個以上的程式。</span><span class="sxs-lookup"><span data-stu-id="a2793-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="a2793-109">程序定義中指定參數的部分稱為 *參數清單*。</span><span class="sxs-lookup"><span data-stu-id="a2793-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="a2793-110">*引數*代表您在呼叫程式時提供給程式參數的值。</span><span class="sxs-lookup"><span data-stu-id="a2793-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="a2793-111">呼叫程式碼會在呼叫程式時提供引數。</span><span class="sxs-lookup"><span data-stu-id="a2793-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="a2793-112">程序呼叫中指定引數的部分稱為 *引數清單*。</span><span class="sxs-lookup"><span data-stu-id="a2793-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="a2793-113">下圖顯示 `safeSquareRoot` 從兩個不同的位置呼叫程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a2793-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="a2793-114">第一個呼叫會將變數 (4.0) 的值傳遞給 `x` 參數 `number` ， (2.0) 中的傳回值 `root` 會指派給變數 `y` 。</span><span class="sxs-lookup"><span data-stu-id="a2793-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="a2793-115">第二個呼叫會將常值9.0 傳遞至 `number` ，並將傳回值 (3.0) 指派給變數 `z` 。</span><span class="sxs-lookup"><span data-stu-id="a2793-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![顯示將引數傳遞給參數的圖表](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="a2793-117">如需詳細資訊，請參閱 [參數和引數之間的差異](./differences-between-parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="a2793-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="a2793-118">參數資料類型</span><span class="sxs-lookup"><span data-stu-id="a2793-118">Parameter Data Type</span></span>  

 <span data-ttu-id="a2793-119">您可以在宣告中使用子句，以定義參數的資料類型 `As` 。</span><span class="sxs-lookup"><span data-stu-id="a2793-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="a2793-120">例如，下列函數會接受字串和整數。</span><span class="sxs-lookup"><span data-stu-id="a2793-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="a2793-121">如果類型檢查參數 ([Option Strict 語句](../../../language-reference/statements/option-strict-statement.md)) 是 `Off,` 選擇性的 `As` 子句，但如果有任何一個參數使用它，則所有參數都必須使用它。</span><span class="sxs-lookup"><span data-stu-id="a2793-121">If the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="a2793-122">如果類型檢查是 `On` ，則 `As` 所有程式參數都需要子句。</span><span class="sxs-lookup"><span data-stu-id="a2793-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="a2793-123">如果呼叫程式碼預期提供的引數資料類型與其對應參數的資料類型不同，例如 `Byte` `String` 參數，則必須執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a2793-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="a2793-124">僅提供資料類型擴展至參數資料類型的引數;</span><span class="sxs-lookup"><span data-stu-id="a2793-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="a2793-125">設定 `Option Strict Off` 為允許隱含縮小轉換; 或</span><span class="sxs-lookup"><span data-stu-id="a2793-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="a2793-126">使用轉換關鍵字來明確轉換資料類型。</span><span class="sxs-lookup"><span data-stu-id="a2793-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="a2793-127">類型參數</span><span class="sxs-lookup"><span data-stu-id="a2793-127">Type Parameters</span></span>  

 <span data-ttu-id="a2793-128">*泛型*程式也會定義一個或多個*型別參數*，以及它的一般參數。</span><span class="sxs-lookup"><span data-stu-id="a2793-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="a2793-129">泛型程式可讓呼叫程式碼在每次呼叫程式時傳遞不同的資料類型，因此它可以將資料類型自訂為每個個別呼叫的需求。</span><span class="sxs-lookup"><span data-stu-id="a2793-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="a2793-130">請參閱 [Generic Procedures in Visual Basic](../data-types/generic-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="a2793-130">See [Generic Procedures in Visual Basic](../data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2793-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2793-131">See also</span></span>

- [<span data-ttu-id="a2793-132">程序</span><span class="sxs-lookup"><span data-stu-id="a2793-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="a2793-133">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="a2793-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="a2793-134">Function 程序</span><span class="sxs-lookup"><span data-stu-id="a2793-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="a2793-135">屬性程序</span><span class="sxs-lookup"><span data-stu-id="a2793-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="a2793-136">運算子程序</span><span class="sxs-lookup"><span data-stu-id="a2793-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a2793-137">如何：定義程序的參數</span><span class="sxs-lookup"><span data-stu-id="a2793-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="a2793-138">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="a2793-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="a2793-139">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="a2793-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="a2793-140">程序多載化</span><span class="sxs-lookup"><span data-stu-id="a2793-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="a2793-141">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="a2793-141">Type Conversions in Visual Basic</span></span>](../data-types/type-conversions.md)
