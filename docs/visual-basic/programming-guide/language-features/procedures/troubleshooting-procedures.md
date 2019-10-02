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
ms.openlocfilehash: d8309b9bd63a2a3d1b0b56f97be121a06b78d6b6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700124"
---
# <a name="troubleshooting-procedures-visual-basic"></a><span data-ttu-id="41db3-102">疑難排解程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41db3-102">Troubleshooting Procedures (Visual Basic)</span></span>

<span data-ttu-id="41db3-103">此頁面會列出使用程式時可能發生的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="41db3-103">This page lists some common problems that can occur when working with procedures.</span></span>

## <a name="returning-an-array-type-from-a-function-procedure"></a><span data-ttu-id="41db3-104">從函數程式傳回陣列型別</span><span class="sxs-lookup"><span data-stu-id="41db3-104">Returning an Array Type from a Function Procedure</span></span>

 <span data-ttu-id="41db3-105">如果 `Function` 程式傳回陣列資料類型，您就不能使用 `Function` 名稱來儲存陣列元素中的值。</span><span class="sxs-lookup"><span data-stu-id="41db3-105">If a `Function` procedure returns an array data type, you cannot use the `Function` name to store values in the elements of the array.</span></span> <span data-ttu-id="41db3-106">如果您嘗試這麼做，編譯器會將它解釋為 `Function` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="41db3-106">If you attempt to do this, the compiler interprets it as a call to the `Function`.</span></span> <span data-ttu-id="41db3-107">下列範例會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="41db3-107">The following example generates compiler errors.</span></span>

 ```vb
 Function AllOnes(n As Integer) As Integer()
     For i = 1 To n - 1
         ' The following statement generates a COMPILER ERROR.
         AllOnes(i) = 1
     Next
     ' The following statement generates a COMPILER ERROR.
     Return AllOnes()
 End Function
 ```
  
 <span data-ttu-id="41db3-108">語句 `AllOnes(i) = 1` 會產生編譯器錯誤，因為它似乎是以錯誤資料類型的引數呼叫 `AllOnes` （純量 `Integer`，而不是 `Integer` 陣列）。</span><span class="sxs-lookup"><span data-stu-id="41db3-108">The statement `AllOnes(i) = 1` generates a compiler error because it appears to call `AllOnes` with an argument of the wrong data type (a scalar `Integer` instead of an `Integer` array).</span></span> <span data-ttu-id="41db3-109">@No__t-0 的語句會產生編譯器錯誤，因為它似乎沒有引數呼叫 `AllOnes`。</span><span class="sxs-lookup"><span data-stu-id="41db3-109">The statement `Return AllOnes()` generates a compiler error because it appears to call `AllOnes` with no argument.</span></span>

 <span data-ttu-id="41db3-110">**正確的方法：** 若要能夠修改要傳回之陣列的元素，請將內部陣列定義為本機變數。</span><span class="sxs-lookup"><span data-stu-id="41db3-110">**Correct Approach:** To be able to modify the elements of an array that is to be returned, define an internal array as a local variable.</span></span> <span data-ttu-id="41db3-111">下列範例會編譯而不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="41db3-111">The following example compiles without error.</span></span>

 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]

## <a name="argument-not-being-modified-by-procedure-call"></a><span data-ttu-id="41db3-112">程序呼叫未修改引數</span><span class="sxs-lookup"><span data-stu-id="41db3-112">Argument Not Being Modified by Procedure Call</span></span>

 <span data-ttu-id="41db3-113">如果您想要允許程式變更呼叫程式碼中引數基礎的程式設計項目，您必須以傳址方式傳遞它。</span><span class="sxs-lookup"><span data-stu-id="41db3-113">If you intend to allow a procedure to change a programming element underlying an argument in the calling code, you must pass it by reference.</span></span> <span data-ttu-id="41db3-114">但是，即使您以傳值方式傳遞參考型別引數的專案，程式也可以存取這些元素。</span><span class="sxs-lookup"><span data-stu-id="41db3-114">But a procedure can access the elements of a reference type argument even if you pass it by value.</span></span>

- <span data-ttu-id="41db3-115">**基礎變數**。</span><span class="sxs-lookup"><span data-stu-id="41db3-115">**Underlying Variable**.</span></span> <span data-ttu-id="41db3-116">若要允許程式取代基礎變數元素本身的值，程式必須宣告參數[ByRef](../../../language-reference/modifiers/byref.md)。</span><span class="sxs-lookup"><span data-stu-id="41db3-116">To allow the procedure to replace the value of the underlying variable element itself, the procedure must declare the parameter [ByRef](../../../language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="41db3-117">此外，呼叫程式碼不能將引數括在括弧中，因為這會覆寫 `ByRef` 傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="41db3-117">Also, the calling code must not enclose the argument in parentheses, because that would override the `ByRef` passing mechanism.</span></span>

- <span data-ttu-id="41db3-118">**參考型別元素**。</span><span class="sxs-lookup"><span data-stu-id="41db3-118">**Reference Type Elements**.</span></span> <span data-ttu-id="41db3-119">如果您宣告了參數[ByVal](../../../language-reference/modifiers/byval.md)，程式就無法修改基礎變數元素本身。</span><span class="sxs-lookup"><span data-stu-id="41db3-119">If you declare a parameter [ByVal](../../../language-reference/modifiers/byval.md), the procedure cannot modify the underlying variable element itself.</span></span> <span data-ttu-id="41db3-120">不過，如果引數是參考型別，則程式可以修改它所指向之物件的成員，即使它無法取代變數的值也一樣。</span><span class="sxs-lookup"><span data-stu-id="41db3-120">However, if the argument is a reference type, the procedure can modify the members of the object to which it points, even though it cannot replace the variable's value.</span></span> <span data-ttu-id="41db3-121">例如，如果引數是陣列變數，則程式無法指派新的陣列給它，但它可以變更一個或多個其元素。</span><span class="sxs-lookup"><span data-stu-id="41db3-121">For example, if the argument is an array variable, the procedure cannot assign a new array to it, but it can change one or more of its elements.</span></span> <span data-ttu-id="41db3-122">已變更的元素會反映在呼叫程式碼的基礎陣列變數中。</span><span class="sxs-lookup"><span data-stu-id="41db3-122">The changed elements are reflected in the underlying array variable in the calling code.</span></span>

 <span data-ttu-id="41db3-123">下列範例會定義兩個程式，以傳值方式使用陣列變數，並在其元素上操作。</span><span class="sxs-lookup"><span data-stu-id="41db3-123">The following example defines two procedures that take an array variable by value and operate on its elements.</span></span> <span data-ttu-id="41db3-124">程式 `increase` 只會將其中一個專案新增至每個元素。</span><span class="sxs-lookup"><span data-stu-id="41db3-124">Procedure `increase` simply adds one to each element.</span></span> <span data-ttu-id="41db3-125">程式 `replace` 會將新陣列指派給參數 `a()`，然後將其中一個新增至每個元素。</span><span class="sxs-lookup"><span data-stu-id="41db3-125">Procedure `replace` assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="41db3-126">不過，重新指派並不會影響呼叫程式碼中的基礎陣列變數，因為 `a()` 會宣告 `ByVal`。</span><span class="sxs-lookup"><span data-stu-id="41db3-126">However, the reassignment does not affect the underlying array variable in the calling code because `a()` is declared `ByVal`.</span></span>

 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]

 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]

 <span data-ttu-id="41db3-127">下列範例會呼叫 `increase`，並 `replace`。</span><span class="sxs-lookup"><span data-stu-id="41db3-127">The following example makes calls to `increase` and `replace`.</span></span>

 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]

 <span data-ttu-id="41db3-128">第一個 `MsgBox` 呼叫會在增加（n）之後顯示 "：11，21，31，41 "。</span><span class="sxs-lookup"><span data-stu-id="41db3-128">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="41db3-129">因為 `n` 是參考型別，所以 `increase` 可以變更其成員，即使是傳遞 `ByVal` 也一樣。</span><span class="sxs-lookup"><span data-stu-id="41db3-129">Because `n` is a reference type, `increase` can change its members, even though it is passed `ByVal`.</span></span>

 <span data-ttu-id="41db3-130">第二個 `MsgBox` 呼叫會顯示 "replace （n）：11，21，31，41 "。</span><span class="sxs-lookup"><span data-stu-id="41db3-130">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="41db3-131">因為 `n` 傳遞 `ByVal`，`replace` 無法藉由指派新的陣列來修改變數 `n`。</span><span class="sxs-lookup"><span data-stu-id="41db3-131">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` by assigning a new array to it.</span></span> <span data-ttu-id="41db3-132">當 `replace` 會建立新的陣列實例 `k`，並將它指派給本機變數 `a`，它會失去呼叫程式碼傳入之 `n` 的參考。</span><span class="sxs-lookup"><span data-stu-id="41db3-132">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="41db3-133">當它遞增 `a` 的成員時，只有 `k` 的本機陣列會受到影響。</span><span class="sxs-lookup"><span data-stu-id="41db3-133">When it increments the members of `a`, only the local array `k` is affected.</span></span>

 <span data-ttu-id="41db3-134">**正確的方法：** 若要能夠修改基礎變數元素本身，請以傳址方式傳遞它。</span><span class="sxs-lookup"><span data-stu-id="41db3-134">**Correct Approach:** To be able to modify an underlying variable element itself, pass it by reference.</span></span> <span data-ttu-id="41db3-135">下列範例顯示 `replace` 之宣告中的變更，讓它能夠在呼叫程式碼中以另一個陣列取代其中一個陣列。</span><span class="sxs-lookup"><span data-stu-id="41db3-135">The following example shows the change in the declaration of `replace` that allows it to replace one array with another in the calling code.</span></span>

 [!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]

## <a name="unable-to-define-an-overload"></a><span data-ttu-id="41db3-136">無法定義多載</span><span class="sxs-lookup"><span data-stu-id="41db3-136">Unable to Define an Overload</span></span>

 <span data-ttu-id="41db3-137">如果您想要定義程式的多載版本，您必須使用相同的名稱，但不能有不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="41db3-137">If you want to define an overloaded version of a procedure, you must use the same name but a different signature.</span></span> <span data-ttu-id="41db3-138">如果編譯器無法區分您的宣告與具有相同簽章的多載，則會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="41db3-138">If the compiler cannot differentiate your declaration from an overload with the same signature, it generates an error.</span></span>

 <span data-ttu-id="41db3-139">程式*的簽章取決於過程*名稱和參數清單。</span><span class="sxs-lookup"><span data-stu-id="41db3-139">The *signature* of a procedure is determined by the procedure name and the parameter list.</span></span> <span data-ttu-id="41db3-140">每個多載都必須與所有其他多載具有相同的名稱，但在簽章的其他其中一個元件中，必須與它們的全部相同。</span><span class="sxs-lookup"><span data-stu-id="41db3-140">Each overload must have the same name as all the other overloads but must differ from all of them in at least one of the other components of the signature.</span></span> <span data-ttu-id="41db3-141">如需詳細資訊，請參閱 [Procedure Overloading](procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="41db3-141">For more information, see [Procedure Overloading](procedure-overloading.md).</span></span>

 <span data-ttu-id="41db3-142">下列專案雖然與參數清單有關，但並不是程式簽章的元件：</span><span class="sxs-lookup"><span data-stu-id="41db3-142">The following items, even though they pertain to the parameter list, are not components of a procedure's signature:</span></span>

- <span data-ttu-id="41db3-143">程式修飾詞關鍵字，例如 `Public`、`Shared` 和 `Static`</span><span class="sxs-lookup"><span data-stu-id="41db3-143">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>

- <span data-ttu-id="41db3-144">參數名稱</span><span class="sxs-lookup"><span data-stu-id="41db3-144">Parameter names</span></span>

- <span data-ttu-id="41db3-145">參數修飾詞關鍵字，例如 `ByRef` 和 `Optional`</span><span class="sxs-lookup"><span data-stu-id="41db3-145">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>

- <span data-ttu-id="41db3-146">傳回值的資料類型（轉換運算子除外）</span><span class="sxs-lookup"><span data-stu-id="41db3-146">The data type of the return value (except for a conversion operator)</span></span>

 <span data-ttu-id="41db3-147">您無法藉由只改變一或多個先前的專案來多載程式。</span><span class="sxs-lookup"><span data-stu-id="41db3-147">You cannot overload a procedure by varying only one or more of the preceding items.</span></span>

 <span data-ttu-id="41db3-148">**正確的方法：** 若要能夠定義程式多載，您必須變更簽章。</span><span class="sxs-lookup"><span data-stu-id="41db3-148">**Correct Approach:** To be able to define a procedure overload, you must vary the signature.</span></span> <span data-ttu-id="41db3-149">因為您必須使用相同的名稱，所以您必須變更參數的數目、順序或資料類型。</span><span class="sxs-lookup"><span data-stu-id="41db3-149">Because you must use the same name, you must vary the number, order, or data types of the parameters.</span></span> <span data-ttu-id="41db3-150">在泛型程式中，您可以改變型別參數的數目。</span><span class="sxs-lookup"><span data-stu-id="41db3-150">In a generic procedure, you can vary the number of type parameters.</span></span> <span data-ttu-id="41db3-151">在轉換運算子（[CType 函數](../../../language-reference/functions/ctype-function.md)）中，您可以改變傳回型別。</span><span class="sxs-lookup"><span data-stu-id="41db3-151">In a conversion operator ([CType Function](../../../language-reference/functions/ctype-function.md)), you can vary the return type.</span></span>

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a><span data-ttu-id="41db3-152">具有選擇性和 ParamArray 引數的多載解析</span><span class="sxs-lookup"><span data-stu-id="41db3-152">Overload Resolution with Optional and ParamArray Arguments</span></span>

 <span data-ttu-id="41db3-153">如果您要多載具有一或多個[選擇性](../../../language-reference/modifiers/optional.md)參數或[ParamArray](../../../language-reference/modifiers/paramarray.md)參數的程式，您必須避免複製任何*隱含*的多載。</span><span class="sxs-lookup"><span data-stu-id="41db3-153">If you are overloading a procedure with one or more [Optional](../../../language-reference/modifiers/optional.md) parameters or a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter, you must avoid duplicating any of the *implicit overloads*.</span></span> <span data-ttu-id="41db3-154">如需詳細資訊，請參閱多載[程式的考慮](considerations-in-overloading-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="41db3-154">For information, see [Considerations in Overloading Procedures](considerations-in-overloading-procedures.md).</span></span>

## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a><span data-ttu-id="41db3-155">呼叫錯誤的多載程式版本</span><span class="sxs-lookup"><span data-stu-id="41db3-155">Calling a Wrong Version of an Overloaded Procedure</span></span>

 <span data-ttu-id="41db3-156">如果程式有數個多載版本，您應該熟悉其所有的參數清單，並瞭解 Visual Basic 如何解析多載之間的呼叫。</span><span class="sxs-lookup"><span data-stu-id="41db3-156">If a procedure has several overloaded versions, you should be familiar with all their parameter lists and understand how Visual Basic resolves calls among the overloads.</span></span> <span data-ttu-id="41db3-157">否則，您可以呼叫非預期的多載。</span><span class="sxs-lookup"><span data-stu-id="41db3-157">Otherwise you could call an overload other than the intended one.</span></span>

 <span data-ttu-id="41db3-158">當您決定要呼叫的多載時，請小心觀察下列規則：</span><span class="sxs-lookup"><span data-stu-id="41db3-158">When you have determined which overload you want to call, be careful to observe the following rules:</span></span>

- <span data-ttu-id="41db3-159">請以正確的順序提供正確的引數數目。</span><span class="sxs-lookup"><span data-stu-id="41db3-159">Supply the correct number of arguments, and in the correct order.</span></span>

- <span data-ttu-id="41db3-160">在理想的情況下，您的引數應該具有與對應參數完全相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="41db3-160">Ideally, your arguments should have the exact same data types as the corresponding parameters.</span></span> <span data-ttu-id="41db3-161">在任何情況下，每個引數的資料型別都必須擴展為其對應參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="41db3-161">In any case, the data type of each argument must widen to that of its corresponding parameter.</span></span> <span data-ttu-id="41db3-162">即使[Option Strict 語句](../../../language-reference/statements/option-strict-statement.md)設定為 `Off` 也是如此。</span><span class="sxs-lookup"><span data-stu-id="41db3-162">This is true even with the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) set to `Off`.</span></span> <span data-ttu-id="41db3-163">如果多載需要引數清單的任何縮小轉換，該多載就不符合呼叫的資格。</span><span class="sxs-lookup"><span data-stu-id="41db3-163">If an overload requires any narrowing conversion from your argument list, that overload is not eligible to be called.</span></span>

- <span data-ttu-id="41db3-164">如果您提供需要擴展的引數，請將其資料類型盡可能靠近對應的參數資料類型。</span><span class="sxs-lookup"><span data-stu-id="41db3-164">If you supply arguments that require widening, make their data types as close as possible to the corresponding parameter data types.</span></span> <span data-ttu-id="41db3-165">如果有兩個以上的多載接受您的引數資料類型，則編譯器會解析呼叫最少量擴展的多載呼叫。</span><span class="sxs-lookup"><span data-stu-id="41db3-165">If two or more overloads accept your argument data types, the compiler resolves your call to the overload that calls for the least amount of widening.</span></span>

 <span data-ttu-id="41db3-166">準備引數時，您可以使用[CType 函數](../../../language-reference/functions/ctype-function.md)轉換關鍵字，來減少資料類型不符的機會。</span><span class="sxs-lookup"><span data-stu-id="41db3-166">You can reduce the chance of data type mismatches by using the [CType Function](../../../language-reference/functions/ctype-function.md) conversion keyword when preparing your arguments.</span></span>

### <a name="overload-resolution-failure"></a><span data-ttu-id="41db3-167">多載解析失敗</span><span class="sxs-lookup"><span data-stu-id="41db3-167">Overload Resolution Failure</span></span>

 <span data-ttu-id="41db3-168">當您呼叫多載的程式時，編譯器會嘗試排除其中一個多載。</span><span class="sxs-lookup"><span data-stu-id="41db3-168">When you call an overloaded procedure, the compiler attempts to eliminate all but one of the overloads.</span></span> <span data-ttu-id="41db3-169">如果成功，它會解析對該多載的呼叫。</span><span class="sxs-lookup"><span data-stu-id="41db3-169">If it succeeds, it resolves the call to that overload.</span></span> <span data-ttu-id="41db3-170">如果它排除所有多載，或如果無法將合格的多載縮減為單一候選，則會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="41db3-170">If it eliminates all the overloads, or if it cannot reduce the eligible overloads to a single candidate, it generates an error.</span></span>

 <span data-ttu-id="41db3-171">下列範例說明多載解析進程。</span><span class="sxs-lookup"><span data-stu-id="41db3-171">The following example illustrates the overload resolution process.</span></span>

 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]

 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]

 <span data-ttu-id="41db3-172">在第一次呼叫中，編譯器會排除第一個多載，因為第一個引數（`Short`）的類型會縮小為對應參數的類型（`Byte`）。</span><span class="sxs-lookup"><span data-stu-id="41db3-172">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="41db3-173">然後，它會排除第三個多載，因為第二個多載中的每個引數類型（`Short` 和 `Single`）會擴展到第三個多載中的對應類型（`Integer` 和 `Single`）。</span><span class="sxs-lookup"><span data-stu-id="41db3-173">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="41db3-174">第二個多載需要較少的擴展，因此編譯器會使用它來進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="41db3-174">The second overload requires less widening, so the compiler uses it for the call.</span></span>

 <span data-ttu-id="41db3-175">在第二次呼叫中，編譯器無法以縮小的基礎來排除任何多載。</span><span class="sxs-lookup"><span data-stu-id="41db3-175">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="41db3-176">它會在第一次呼叫時排除第三個多載，因為它可以呼叫具有較少引數類型的第二個多載。</span><span class="sxs-lookup"><span data-stu-id="41db3-176">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="41db3-177">不過，編譯器無法解析第一個和第二個多載。</span><span class="sxs-lookup"><span data-stu-id="41db3-177">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="41db3-178">每個都有一個已定義的參數類型，可擴大至另一個中的對應類型（`Byte` 到 `Short`，但 `Single` 到 `Double`）。</span><span class="sxs-lookup"><span data-stu-id="41db3-178">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="41db3-179">因此，編譯器會產生多載解析錯誤。</span><span class="sxs-lookup"><span data-stu-id="41db3-179">The compiler therefore generates an overload resolution error.</span></span>

 <span data-ttu-id="41db3-180">**正確的方法：** 若要能夠呼叫多載程式而不明確，請使用[CType 函數](../../../language-reference/functions/ctype-function.md)來比對引數資料類型與參數類型。</span><span class="sxs-lookup"><span data-stu-id="41db3-180">**Correct Approach:** To be able to call an overloaded procedure without ambiguity, use [CType Function](../../../language-reference/functions/ctype-function.md) to match the argument data types to the parameter types.</span></span> <span data-ttu-id="41db3-181">下列範例示範對 `z` 的呼叫，它會強制解決第二個多載。</span><span class="sxs-lookup"><span data-stu-id="41db3-181">The following example shows a call to `z` that forces resolution to the second overload.</span></span>

 [!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]

### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a><span data-ttu-id="41db3-182">具有選擇性和 ParamArray 引數的多載解析</span><span class="sxs-lookup"><span data-stu-id="41db3-182">Overload Resolution with Optional and ParamArray Arguments</span></span>

 <span data-ttu-id="41db3-183">如果程式的兩個多載具有相同的簽章，但最後一個參數在其中一個和[ParamArray](../../../language-reference/modifiers/paramarray.md)中宣告為[選擇性](../../../language-reference/modifiers/optional.md)，則編譯器會根據最接近的相符項來解析該程式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="41db3-183">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../language-reference/modifiers/optional.md) in one and [ParamArray](../../../language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure according to the closest match.</span></span> <span data-ttu-id="41db3-184">如需詳細資訊，請參閱 [Overload Resolution](overload-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="41db3-184">For more information, see [Overload Resolution](overload-resolution.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="41db3-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41db3-185">See also</span></span>

- [<span data-ttu-id="41db3-186">程序</span><span class="sxs-lookup"><span data-stu-id="41db3-186">Procedures</span></span>](index.md)
- [<span data-ttu-id="41db3-187">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="41db3-187">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="41db3-188">函式程序</span><span class="sxs-lookup"><span data-stu-id="41db3-188">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="41db3-189">屬性程序</span><span class="sxs-lookup"><span data-stu-id="41db3-189">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="41db3-190">運算子程序</span><span class="sxs-lookup"><span data-stu-id="41db3-190">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="41db3-191">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="41db3-191">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="41db3-192">程序多載化</span><span class="sxs-lookup"><span data-stu-id="41db3-192">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="41db3-193">多載化程序的考慮因素</span><span class="sxs-lookup"><span data-stu-id="41db3-193">Considerations in Overloading Procedures</span></span>](considerations-in-overloading-procedures.md)
- [<span data-ttu-id="41db3-194">多載解析</span><span class="sxs-lookup"><span data-stu-id="41db3-194">Overload Resolution</span></span>](overload-resolution.md)
