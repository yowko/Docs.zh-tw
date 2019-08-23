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
ms.openlocfilehash: 5a2813b81490e7c2fcf1abcf5fd36ca89d9d7929
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933851"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="0fd0d-102">參數陣列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fd0d-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="0fd0d-103">通常, 您不能使用比程式宣告指定的多個引數來呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="0fd0d-104">當您需要不限數目的引數時, 您可以宣告*參數陣列*, 讓程式接受參數值陣列。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="0fd0d-105">當您定義程式時, 不需要知道參數陣列中的元素數目。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="0fd0d-106">陣列大小是由程式的每個呼叫個別決定。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="0fd0d-107">宣告 ParamArray</span><span class="sxs-lookup"><span data-stu-id="0fd0d-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="0fd0d-108">您可以使用[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)關鍵字來表示參數清單中的參數陣列。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="0fd0d-109">可套用下列規則：</span><span class="sxs-lookup"><span data-stu-id="0fd0d-109">The following rules apply:</span></span>  
  
- <span data-ttu-id="0fd0d-110">程式只能定義一個參數陣列, 而且它必須是程序定義中的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
- <span data-ttu-id="0fd0d-111">參數陣列必須以傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="0fd0d-112">在程序定義中明確包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)關鍵字是良好的程式設計作法。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
- <span data-ttu-id="0fd0d-113">參數陣列是自動選擇的。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="0fd0d-114">其預設值為參數陣列的元素類型的一維空陣列。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
- <span data-ttu-id="0fd0d-115">參數陣列前面的所有參數都必須是必要的。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="0fd0d-116">參數陣列必須是唯一的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="0fd0d-117">呼叫 ParamArray</span><span class="sxs-lookup"><span data-stu-id="0fd0d-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="0fd0d-118">當您呼叫定義參數陣列的程式時, 您可以使用下列任何一種方式提供引數:</span><span class="sxs-lookup"><span data-stu-id="0fd0d-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
- <span data-ttu-id="0fd0d-119">沒有, 也就是說, 您可以省略[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)引數。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="0fd0d-120">在此情況下, 會將空的陣列傳遞給程式。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="0fd0d-121">您也可以傳遞「[無](../../../../visual-basic/language-reference/nothing.md)關鍵字」的相同效果。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-121">You can also pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, with the same effect.</span></span>  
  
- <span data-ttu-id="0fd0d-122">任意數目的引數清單 (以逗號分隔)。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="0fd0d-123">每個引數的資料類型必須可以隱含地轉換`ParamArray`成元素類型。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
- <span data-ttu-id="0fd0d-124">陣列, 其元素類型與參數陣列的元素類型相同。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="0fd0d-125">在所有情況下, 程式內的程式碼會將參數陣列視為一維陣列, 其中包含與`ParamArray`資料類型相同之資料類型的元素。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0fd0d-126">當您處理可能會無限大的陣列時, 會有 overrunning 應用程式的一些內部容量的風險。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="0fd0d-127">如果您接受參數陣列, 您應該測試呼叫程式碼傳遞給它的陣列大小。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="0fd0d-128">如果您的應用程式太大, 請採取適當的步驟。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="0fd0d-129">如需詳細資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fd0d-130">範例</span><span class="sxs-lookup"><span data-stu-id="0fd0d-130">Example</span></span>  
 <span data-ttu-id="0fd0d-131">下列範例會定義和呼叫`calcSum`函式。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="0fd0d-132">`ParamArray` 參數`args`的修飾詞可讓函式接受可變數目的引數。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 <span data-ttu-id="0fd0d-133">下列範例會定義具有參數陣列的程式, 並輸出傳遞至參數陣列之所有陣列元素的值。</span><span class="sxs-lookup"><span data-stu-id="0fd0d-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a><span data-ttu-id="0fd0d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fd0d-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="0fd0d-135">程序</span><span class="sxs-lookup"><span data-stu-id="0fd0d-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="0fd0d-136">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="0fd0d-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0fd0d-137">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="0fd0d-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="0fd0d-138">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="0fd0d-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="0fd0d-139">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="0fd0d-139">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="0fd0d-140">程序多載化</span><span class="sxs-lookup"><span data-stu-id="0fd0d-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="0fd0d-141">陣列</span><span class="sxs-lookup"><span data-stu-id="0fd0d-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="0fd0d-142">Optional</span><span class="sxs-lookup"><span data-stu-id="0fd0d-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
