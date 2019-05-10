---
title: 疑難排解程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: 1a8cd568f1a9a05721f311cc72a22bfc2b6bcfc9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625462"
---
# <a name="troubleshooting-procedures-visual-basic"></a><span data-ttu-id="f1efc-102">疑難排解程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1efc-102">Troubleshooting Procedures (Visual Basic)</span></span>
<span data-ttu-id="f1efc-103">此頁面會列出處理程序時所發生的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="f1efc-103">This page lists some common problems that can occur when working with procedures.</span></span>  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a><span data-ttu-id="f1efc-104">從函式程序傳回陣列類型</span><span class="sxs-lookup"><span data-stu-id="f1efc-104">Returning an Array Type from a Function Procedure</span></span>  
 <span data-ttu-id="f1efc-105">如果`Function`程序會傳回陣列資料型別，您不能使用`Function`將值儲存在陣列的元素名稱。</span><span class="sxs-lookup"><span data-stu-id="f1efc-105">If a `Function` procedure returns an array data type, you cannot use the `Function` name to store values in the elements of the array.</span></span> <span data-ttu-id="f1efc-106">如果您嘗試執行這項操作時，編譯器就會將它解譯為要呼叫`Function`。</span><span class="sxs-lookup"><span data-stu-id="f1efc-106">If you attempt to do this, the compiler interprets it as a call to the `Function`.</span></span> <span data-ttu-id="f1efc-107">下列範例會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1efc-107">The following example generates compiler errors.</span></span>  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 <span data-ttu-id="f1efc-108">`' The following statement generates a`   `COMPILER ERROR`  `.`</span><span class="sxs-lookup"><span data-stu-id="f1efc-108">`' The following statement generates a`   `COMPILER ERROR`  `.`</span></span>  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 <span data-ttu-id="f1efc-109">`' The following statement generates a`   `COMPILER ERROR`  `.`</span><span class="sxs-lookup"><span data-stu-id="f1efc-109">`' The following statement generates a`   `COMPILER ERROR`  `.`</span></span>  
  
 `Return allOnes()`  
  
 `End Function`  
  
 <span data-ttu-id="f1efc-110">陳述式`allOnes(i) = 1`會產生編譯器錯誤，因為它看起來像是呼叫`allOnes`具有錯誤的資料類型的引數 (單一`Integer`而不是`Integer`陣列)。</span><span class="sxs-lookup"><span data-stu-id="f1efc-110">The statement `allOnes(i) = 1` generates a compiler error because it appears to call `allOnes` with an argument of the wrong data type (a singleton `Integer` instead of an `Integer` array).</span></span> <span data-ttu-id="f1efc-111">陳述式`Return allOnes()`會產生編譯器錯誤，因為它看起來像是呼叫`allOnes`但沒有引數。</span><span class="sxs-lookup"><span data-stu-id="f1efc-111">The statement `Return allOnes()` generates a compiler error because it appears to call `allOnes` with no argument.</span></span>  
  
 <span data-ttu-id="f1efc-112">**正確的方法：** 若要能夠修改要傳回之陣列的項目，定義內部陣列做為本機變數。</span><span class="sxs-lookup"><span data-stu-id="f1efc-112">**Correct Approach:** To be able to modify the elements of an array that is to be returned, define an internal array as a local variable.</span></span> <span data-ttu-id="f1efc-113">下列範例會編譯無誤。</span><span class="sxs-lookup"><span data-stu-id="f1efc-113">The following example compiles without error.</span></span>  
  
 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a><span data-ttu-id="f1efc-114">引數不修改程序呼叫</span><span class="sxs-lookup"><span data-stu-id="f1efc-114">Argument Not Being Modified by Procedure Call</span></span>  
 <span data-ttu-id="f1efc-115">如果您想要允許的程序來變更基礎呼叫程式碼中的引數的程式設計項目，您必須將它傳遞的參考。</span><span class="sxs-lookup"><span data-stu-id="f1efc-115">If you intend to allow a procedure to change a programming element underlying an argument in the calling code, you must pass it by reference.</span></span> <span data-ttu-id="f1efc-116">但一個程序可以存取的參考型別引數的項目，即使您傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="f1efc-116">But a procedure can access the elements of a reference type argument even if you pass it by value.</span></span>  
  
- <span data-ttu-id="f1efc-117">**基礎變數**。</span><span class="sxs-lookup"><span data-stu-id="f1efc-117">**Underlying Variable**.</span></span> <span data-ttu-id="f1efc-118">若要允許的程序來取代基礎變數項目本身的值，此程序必須宣告的參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。</span><span class="sxs-lookup"><span data-stu-id="f1efc-118">To allow the procedure to replace the value of the underlying variable element itself, the procedure must declare the parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="f1efc-119">此外，呼叫程式碼必須沒有引數括號括住，因為，將會覆寫`ByRef`傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="f1efc-119">Also, the calling code must not enclose the argument in parentheses, because that would override the `ByRef` passing mechanism.</span></span>  
  
- <span data-ttu-id="f1efc-120">**參考型別項目**。</span><span class="sxs-lookup"><span data-stu-id="f1efc-120">**Reference Type Elements**.</span></span> <span data-ttu-id="f1efc-121">如果您宣告的參數[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)，程序無法修改基礎變數項目本身。</span><span class="sxs-lookup"><span data-stu-id="f1efc-121">If you declare a parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), the procedure cannot modify the underlying variable element itself.</span></span> <span data-ttu-id="f1efc-122">不過，如果引數是參考類型，程序可以修改它所指向，物件的成員即使它不能取代變數的值。</span><span class="sxs-lookup"><span data-stu-id="f1efc-122">However, if the argument is a reference type, the procedure can modify the members of the object to which it points, even though it cannot replace the variable's value.</span></span> <span data-ttu-id="f1efc-123">比方說，如果引數陣列變數，程序無法將新的陣列指派給它，但它可以變更一或多個子項目。</span><span class="sxs-lookup"><span data-stu-id="f1efc-123">For example, if the argument is an array variable, the procedure cannot assign a new array to it, but it can change one or more of its elements.</span></span> <span data-ttu-id="f1efc-124">已變更的項目會反映在呼叫程式碼中的陣列變數。</span><span class="sxs-lookup"><span data-stu-id="f1efc-124">The changed elements are reflected in the underlying array variable in the calling code.</span></span>  
  
 <span data-ttu-id="f1efc-125">下列範例會定義兩個程序，以傳值方式取得陣列變數和操作其項目上。</span><span class="sxs-lookup"><span data-stu-id="f1efc-125">The following example defines two procedures that take an array variable by value and operate on its elements.</span></span> <span data-ttu-id="f1efc-126">程序`increase`直接新增至每個項目。</span><span class="sxs-lookup"><span data-stu-id="f1efc-126">Procedure `increase` simply adds one to each element.</span></span> <span data-ttu-id="f1efc-127">程序`replace`將新的陣列指派給參數`a()`，然後新增一個每個項目。</span><span class="sxs-lookup"><span data-stu-id="f1efc-127">Procedure `replace` assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="f1efc-128">不過，重新指派不會影響呼叫端程式碼中的陣列變數因為`a()`宣告`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="f1efc-128">However, the reassignment does not affect the underlying array variable in the calling code because `a()` is declared `ByVal`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 <span data-ttu-id="f1efc-129">下列範例會呼叫`increase`和`replace`。</span><span class="sxs-lookup"><span data-stu-id="f1efc-129">The following example makes calls to `increase` and `replace`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="f1efc-130">第一個`MsgBox`呼叫會顯示 「 increase(n) 之後：11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="f1efc-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="f1efc-131">因為`n`是參考型別`increase`可以變更其成員，即使它傳遞`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="f1efc-131">Because `n` is a reference type, `increase` can change its members, even though it is passed `ByVal`.</span></span>  
  
 <span data-ttu-id="f1efc-132">第二個`MsgBox`呼叫會顯示 「 replace(n) 之後：11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="f1efc-132">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="f1efc-133">因為`n`傳遞`ByVal`，`replace`不能修改變數`n`藉由將新的陣列指派給它。</span><span class="sxs-lookup"><span data-stu-id="f1efc-133">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` by assigning a new array to it.</span></span> <span data-ttu-id="f1efc-134">當`replace`建立新的陣列執行個體`k`並將它指派給區域變數`a`，就會失去參考`n`傳入呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f1efc-134">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="f1efc-135">它會遞增的成員`a`，只有本機陣列`k`會受到影響。</span><span class="sxs-lookup"><span data-stu-id="f1efc-135">When it increments the members of `a`, only the local array `k` is affected.</span></span>  
  
 <span data-ttu-id="f1efc-136">**正確的方法：** 若要能夠修改對應的變數項目本身，傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="f1efc-136">**Correct Approach:** To be able to modify an underlying variable element itself, pass it by reference.</span></span> <span data-ttu-id="f1efc-137">下列範例顯示的宣告中的變更`replace`可取代呼叫的程式碼中的另一個陣列。</span><span class="sxs-lookup"><span data-stu-id="f1efc-137">The following example shows the change in the declaration of `replace` that allows it to replace one array with another in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]  
  
## <a name="unable-to-define-an-overload"></a><span data-ttu-id="f1efc-138">無法定義多載</span><span class="sxs-lookup"><span data-stu-id="f1efc-138">Unable to Define an Overload</span></span>  
 <span data-ttu-id="f1efc-139">如果您想要定義的程序的多載的版本，您必須使用相同名稱但不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="f1efc-139">If you want to define an overloaded version of a procedure, you must use the same name but a different signature.</span></span> <span data-ttu-id="f1efc-140">如果編譯器無法區分您的宣告，從相同的簽章的多載，它會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1efc-140">If the compiler cannot differentiate your declaration from an overload with the same signature, it generates an error.</span></span>  
  
 <span data-ttu-id="f1efc-141">*簽章*程序取決於程序名稱和參數清單。</span><span class="sxs-lookup"><span data-stu-id="f1efc-141">The *signature* of a procedure is determined by the procedure name and the parameter list.</span></span> <span data-ttu-id="f1efc-142">每個多載必須有相同的名稱，為所有其他的多載，但必須不同於全部都放在至少一個簽章的其他元件。</span><span class="sxs-lookup"><span data-stu-id="f1efc-142">Each overload must have the same name as all the other overloads but must differ from all of them in at least one of the other components of the signature.</span></span> <span data-ttu-id="f1efc-143">如需詳細資訊，請參閱 [Procedure Overloading](./procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="f1efc-143">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="f1efc-144">下列項目，即使它們屬於 [參數] 清單中，不是元件的程序的簽章：</span><span class="sxs-lookup"><span data-stu-id="f1efc-144">The following items, even though they pertain to the parameter list, are not components of a procedure's signature:</span></span>  
  
- <span data-ttu-id="f1efc-145">程序修飾詞關鍵字，例如`Public`， `Shared`，及 `Static`</span><span class="sxs-lookup"><span data-stu-id="f1efc-145">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
- <span data-ttu-id="f1efc-146">參數名稱</span><span class="sxs-lookup"><span data-stu-id="f1efc-146">Parameter names</span></span>  
  
- <span data-ttu-id="f1efc-147">參數修飾詞關鍵字，例如`ByRef`和 `Optional`</span><span class="sxs-lookup"><span data-stu-id="f1efc-147">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
- <span data-ttu-id="f1efc-148">傳回值 （除了轉換運算子） 的資料類型</span><span class="sxs-lookup"><span data-stu-id="f1efc-148">The data type of the return value (except for a conversion operator)</span></span>  
  
 <span data-ttu-id="f1efc-149">若要多載程序，不能只改變一個或多個先前的項目。</span><span class="sxs-lookup"><span data-stu-id="f1efc-149">You cannot overload a procedure by varying only one or more of the preceding items.</span></span>  
  
 <span data-ttu-id="f1efc-150">**正確的方法：** 若要定義的程序多載，您必須變更簽章。</span><span class="sxs-lookup"><span data-stu-id="f1efc-150">**Correct Approach:** To be able to define a procedure overload, you must vary the signature.</span></span> <span data-ttu-id="f1efc-151">因為您必須使用相同的名稱，您必須變更數目、 順序或參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f1efc-151">Because you must use the same name, you must vary the number, order, or data types of the parameters.</span></span> <span data-ttu-id="f1efc-152">在一般的程序中，您可以變更類型參數的數目。</span><span class="sxs-lookup"><span data-stu-id="f1efc-152">In a generic procedure, you can vary the number of type parameters.</span></span> <span data-ttu-id="f1efc-153">在 轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md))，您可以變更傳回型別。</span><span class="sxs-lookup"><span data-stu-id="f1efc-153">In a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)), you can vary the return type.</span></span>  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a><span data-ttu-id="f1efc-154">多載使用選擇性的解析度和 ParamArray 引數</span><span class="sxs-lookup"><span data-stu-id="f1efc-154">Overload Resolution with Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="f1efc-155">如果您多載具有一或多個的程序[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數或[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，您必須避免重複任何*隱含的多載*。</span><span class="sxs-lookup"><span data-stu-id="f1efc-155">If you are overloading a procedure with one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters or a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you must avoid duplicating any of the *implicit overloads*.</span></span> <span data-ttu-id="f1efc-156">如需資訊，請參閱[多載化程序中的考量](./considerations-in-overloading-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="f1efc-156">For information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a><span data-ttu-id="f1efc-157">呼叫的多載的程序的版本錯誤</span><span class="sxs-lookup"><span data-stu-id="f1efc-157">Calling a Wrong Version of an Overloaded Procedure</span></span>  
 <span data-ttu-id="f1efc-158">如果程序有數個多載的版本，您應該先熟悉所有的參數清單，並了解 Visual Basic 如何解析多載之間的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f1efc-158">If a procedure has several overloaded versions, you should be familiar with all their parameter lists and understand how Visual Basic resolves calls among the overloads.</span></span> <span data-ttu-id="f1efc-159">否則，您可以呼叫非預期的多載。</span><span class="sxs-lookup"><span data-stu-id="f1efc-159">Otherwise you could call an overload other than the intended one.</span></span>  
  
 <span data-ttu-id="f1efc-160">當您已經決定您想要呼叫哪個多的載時，請務必遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="f1efc-160">When you have determined which overload you want to call, be careful to observe the following rules:</span></span>  
  
- <span data-ttu-id="f1efc-161">請提供正確數目的引數，並以正確的順序。</span><span class="sxs-lookup"><span data-stu-id="f1efc-161">Supply the correct number of arguments, and in the correct order.</span></span>  
  
- <span data-ttu-id="f1efc-162">在理想情況下，您的引數應該完全相同的資料類型與對應的參數。</span><span class="sxs-lookup"><span data-stu-id="f1efc-162">Ideally, your arguments should have the exact same data types as the corresponding parameters.</span></span> <span data-ttu-id="f1efc-163">在任何情況下，每個引數的資料類型必須擴展為，其對應參數。</span><span class="sxs-lookup"><span data-stu-id="f1efc-163">In any case, the data type of each argument must widen to that of its corresponding parameter.</span></span> <span data-ttu-id="f1efc-164">這是 true，即使[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定為`Off`。</span><span class="sxs-lookup"><span data-stu-id="f1efc-164">This is true even with the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) set to `Off`.</span></span> <span data-ttu-id="f1efc-165">如果多載都需要任何引數清單，請多載的縮小轉換不符合資格，來呼叫。</span><span class="sxs-lookup"><span data-stu-id="f1efc-165">If an overload requires any narrowing conversion from your argument list, that overload is not eligible to be called.</span></span>  
  
- <span data-ttu-id="f1efc-166">如果您提供需要擴展的引數，請為對應的參數資料類型，盡可能接近其資料類型。</span><span class="sxs-lookup"><span data-stu-id="f1efc-166">If you supply arguments that require widening, make their data types as close as possible to the corresponding parameter data types.</span></span> <span data-ttu-id="f1efc-167">如果兩個或多個多載會接受引數的資料型別，編譯器會解析您最少擴展的呼叫多載的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f1efc-167">If two or more overloads accept your argument data types, the compiler resolves your call to the overload that calls for the least amount of widening.</span></span>  
  
 <span data-ttu-id="f1efc-168">您可以使用，以降低可能發生的資料類型不符[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)轉換關鍵字，準備您的引數時。</span><span class="sxs-lookup"><span data-stu-id="f1efc-168">You can reduce the chance of data type mismatches by using the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) conversion keyword when preparing your arguments.</span></span>  
  
### <a name="overload-resolution-failure"></a><span data-ttu-id="f1efc-169">多載解析失敗</span><span class="sxs-lookup"><span data-stu-id="f1efc-169">Overload Resolution Failure</span></span>  
 <span data-ttu-id="f1efc-170">當您呼叫多載的程序時，編譯器會嘗試排除所有只留下其中一個多載。</span><span class="sxs-lookup"><span data-stu-id="f1efc-170">When you call an overloaded procedure, the compiler attempts to eliminate all but one of the overloads.</span></span> <span data-ttu-id="f1efc-171">如果成功，它會解析該多載的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f1efc-171">If it succeeds, it resolves the call to that overload.</span></span> <span data-ttu-id="f1efc-172">它會排除所有多載，則它無法縮小到單一的候選資格的多載，它會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1efc-172">If it eliminates all the overloads, or if it cannot reduce the eligible overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="f1efc-173">下列範例說明多載解析程序。</span><span class="sxs-lookup"><span data-stu-id="f1efc-173">The following example illustrates the overload resolution process.</span></span>  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 <span data-ttu-id="f1efc-174">在第一個呼叫中，編譯器會排除第一個多載因為第一個引數的類型 (`Short`) 的範圍縮小，對應參數的型別 (`Byte`)。</span><span class="sxs-lookup"><span data-stu-id="f1efc-174">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="f1efc-175">它然後排除第三個多載，因為每個引數類型中的第二個多載 (`Short`並`Single`) 可擴展為對應的型別中的第三個多載 (`Integer`和`Single`)。</span><span class="sxs-lookup"><span data-stu-id="f1efc-175">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="f1efc-176">第二個多載都需要較少的擴展，因此編譯器會將它用於呼叫。</span><span class="sxs-lookup"><span data-stu-id="f1efc-176">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="f1efc-177">在第二個呼叫中，編譯器無法排除任何根據縮小的多載。</span><span class="sxs-lookup"><span data-stu-id="f1efc-177">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="f1efc-178">基於相同理由，如同第一次呼叫中中,，因為它可以呼叫第二個多載，較不需要擴展的引數類型，它會排除第三個多載。</span><span class="sxs-lookup"><span data-stu-id="f1efc-178">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="f1efc-179">不過，編譯器無法解析的第一個和第二個多載之間。</span><span class="sxs-lookup"><span data-stu-id="f1efc-179">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="f1efc-180">各有一個定義的參數類型可擴展成其他對應的類型 (`Byte`來`Short`，但`Single`至`Double`)。</span><span class="sxs-lookup"><span data-stu-id="f1efc-180">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="f1efc-181">因此，編譯器會產生多載解析錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1efc-181">The compiler therefore generates an overload resolution error.</span></span>  
  
 <span data-ttu-id="f1efc-182">**正確的方法：** 若要能夠呼叫沒有模稜兩可的多載程序，使用[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)來比對引數資料類型與參數類型。</span><span class="sxs-lookup"><span data-stu-id="f1efc-182">**Correct Approach:** To be able to call an overloaded procedure without ambiguity, use [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to match the argument data types to the parameter types.</span></span> <span data-ttu-id="f1efc-183">下列範例示範呼叫`z`，強制第二個多載解析。</span><span class="sxs-lookup"><span data-stu-id="f1efc-183">The following example shows a call to `z` that forces resolution to the second overload.</span></span>  
  
 [!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a><span data-ttu-id="f1efc-184">多載使用選擇性的解析度和 ParamArray 引數</span><span class="sxs-lookup"><span data-stu-id="f1efc-184">Overload Resolution with Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="f1efc-185">如果程序的兩個多載具有相同簽章，不同之處在於最後一個參數宣告[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)其中一並[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)在另一個，編譯器會解析該程序的呼叫根據最接近的相符項目。</span><span class="sxs-lookup"><span data-stu-id="f1efc-185">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure according to the closest match.</span></span> <span data-ttu-id="f1efc-186">如需詳細資訊，請參閱 [Overload Resolution](./overload-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="f1efc-186">For more information, see [Overload Resolution](./overload-resolution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1efc-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1efc-187">See also</span></span>

- [<span data-ttu-id="f1efc-188">程序</span><span class="sxs-lookup"><span data-stu-id="f1efc-188">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f1efc-189">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="f1efc-189">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="f1efc-190">函式程序</span><span class="sxs-lookup"><span data-stu-id="f1efc-190">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="f1efc-191">屬性程序</span><span class="sxs-lookup"><span data-stu-id="f1efc-191">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="f1efc-192">運算子程序</span><span class="sxs-lookup"><span data-stu-id="f1efc-192">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="f1efc-193">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="f1efc-193">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f1efc-194">程序多載化</span><span class="sxs-lookup"><span data-stu-id="f1efc-194">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="f1efc-195">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="f1efc-195">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="f1efc-196">多載解析</span><span class="sxs-lookup"><span data-stu-id="f1efc-196">Overload Resolution</span></span>](./overload-resolution.md)
