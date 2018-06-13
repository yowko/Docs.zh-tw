---
title: 參數陣列 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: a91da0d9e16ff11fdd4980588fee64b3e4a603c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652373"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="426d6-102">參數陣列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="426d6-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="426d6-103">通常，您無法呼叫具有多個引數數目比程序宣告指定的程序。</span><span class="sxs-lookup"><span data-stu-id="426d6-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="426d6-104">當您需要了不定數量的引數時，您可以宣告*參數陣列*，可讓程序以接受的參數值陣列。</span><span class="sxs-lookup"><span data-stu-id="426d6-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="426d6-105">您不必知道參數陣列中的項目數，當您定義的程序。</span><span class="sxs-lookup"><span data-stu-id="426d6-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="426d6-106">陣列大小取決於個別的程序的每個呼叫。</span><span class="sxs-lookup"><span data-stu-id="426d6-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="426d6-107">宣告參數陣列</span><span class="sxs-lookup"><span data-stu-id="426d6-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="426d6-108">您使用[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)關鍵字來代表在參數清單中的參數陣列。</span><span class="sxs-lookup"><span data-stu-id="426d6-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="426d6-109">可套用下列規則：</span><span class="sxs-lookup"><span data-stu-id="426d6-109">The following rules apply:</span></span>  
  
-   <span data-ttu-id="426d6-110">程序可以定義只有一個參數的陣列，而且它必須是程序定義中的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="426d6-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
-   <span data-ttu-id="426d6-111">參數陣列必須以傳值。</span><span class="sxs-lookup"><span data-stu-id="426d6-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="426d6-112">良好的程式設計作法明確包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)程序定義中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="426d6-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
-   <span data-ttu-id="426d6-113">參數陣列會自動為選用。</span><span class="sxs-lookup"><span data-stu-id="426d6-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="426d6-114">其預設值是空的一維陣列，參數陣列的項目類型。</span><span class="sxs-lookup"><span data-stu-id="426d6-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
-   <span data-ttu-id="426d6-115">參數陣列之前的所有參數必須都是必要的。</span><span class="sxs-lookup"><span data-stu-id="426d6-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="426d6-116">參數陣列必須是唯一的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="426d6-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="426d6-117">呼叫的參數陣列</span><span class="sxs-lookup"><span data-stu-id="426d6-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="426d6-118">當您呼叫定義的參數陣列的程序時，您可以在任何一種以下列方式提供引數：</span><span class="sxs-lookup"><span data-stu-id="426d6-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
-   <span data-ttu-id="426d6-119">執行任何動作，也就是您可以省略[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)引數。</span><span class="sxs-lookup"><span data-stu-id="426d6-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="426d6-120">在此情況下，空的陣列會傳遞至程序。</span><span class="sxs-lookup"><span data-stu-id="426d6-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="426d6-121">您也可以傳遞[Nothing](../../../../visual-basic/language-reference/nothing.md)關鍵字，使用相同的效果。</span><span class="sxs-lookup"><span data-stu-id="426d6-121">You can also pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, with the same effect.</span></span>  
  
-   <span data-ttu-id="426d6-122">任意數目的引數，並以逗號分隔的清單。</span><span class="sxs-lookup"><span data-stu-id="426d6-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="426d6-123">每個引數的資料類型必須是隱含地轉換成`ParamArray`項目類型。</span><span class="sxs-lookup"><span data-stu-id="426d6-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
-   <span data-ttu-id="426d6-124">具有相同的項目型別參數陣列的項目類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="426d6-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="426d6-125">在所有情況下，此程序中的程式碼會將參數的陣列視為具有相同的資料類型之項目的一維陣列`ParamArray`資料型別。</span><span class="sxs-lookup"><span data-stu-id="426d6-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="426d6-126">只要處理陣列，其中可能會無限期地大，會有風險的造成滿溢內部應用程式的容量。</span><span class="sxs-lookup"><span data-stu-id="426d6-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="426d6-127">如果您接受參數陣列時，您應該測試呼叫的程式碼傳遞給它之陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="426d6-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="426d6-128">如果您的應用程式而言太大，請採取適當的步驟。</span><span class="sxs-lookup"><span data-stu-id="426d6-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="426d6-129">如需詳細資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="426d6-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="426d6-130">範例</span><span class="sxs-lookup"><span data-stu-id="426d6-130">Example</span></span>  
 <span data-ttu-id="426d6-131">下列範例會定義和呼叫的函式`calcSum`。</span><span class="sxs-lookup"><span data-stu-id="426d6-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="426d6-132">`ParamArray`參數修飾詞`args`啟用接受可變數目的引數的函式。</span><span class="sxs-lookup"><span data-stu-id="426d6-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 <span data-ttu-id="426d6-133">下列範例定義的參數陣列的程序，並將輸出傳遞至參數陣列的所有陣列項目的值。</span><span class="sxs-lookup"><span data-stu-id="426d6-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="426d6-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="426d6-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [<span data-ttu-id="426d6-135">程序</span><span class="sxs-lookup"><span data-stu-id="426d6-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="426d6-136">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="426d6-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="426d6-137">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="426d6-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="426d6-138">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="426d6-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="426d6-139">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="426d6-139">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="426d6-140">程序多載化</span><span class="sxs-lookup"><span data-stu-id="426d6-140">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="426d6-141">陣列</span><span class="sxs-lookup"><span data-stu-id="426d6-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="426d6-142">Optional</span><span class="sxs-lookup"><span data-stu-id="426d6-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
