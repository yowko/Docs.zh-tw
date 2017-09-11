---
title: "疑難排解程序 (Visual Basic) |Microsoft 文件"
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
- troubleshooting Visual Basic, procedures
- procedures, troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures, about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
caps.latest.revision: 17
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
ms.openlocfilehash: a16a03aa8c12e6696f80eeddb96f4f90c3bb7c68
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="troubleshooting-procedures-visual-basic"></a><span data-ttu-id="4136b-102">疑難排解程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4136b-102">Troubleshooting Procedures (Visual Basic)</span></span>
<span data-ttu-id="4136b-103">此頁面會列出處理程序時所發生的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="4136b-103">This page lists some common problems that can occur when working with procedures.</span></span>  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a><span data-ttu-id="4136b-104">從函式程序傳回的陣列型別</span><span class="sxs-lookup"><span data-stu-id="4136b-104">Returning an Array Type from a Function Procedure</span></span>  
 <span data-ttu-id="4136b-105">如果`Function`程序會傳回陣列的資料型別，您無法使用`Function`將值儲存在陣列元素的名稱。</span><span class="sxs-lookup"><span data-stu-id="4136b-105">If a `Function` procedure returns an array data type, you cannot use the `Function` name to store values in the elements of the array.</span></span> <span data-ttu-id="4136b-106">如果您嘗試這樣做，編譯器會解譯為呼叫`Function`。</span><span class="sxs-lookup"><span data-stu-id="4136b-106">If you attempt to do this, the compiler interprets it as a call to the `Function`.</span></span> <span data-ttu-id="4136b-107">下列範例會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="4136b-107">The following example generates compiler errors.</span></span>  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 <span data-ttu-id="4136b-108">`' The following statement generates a`   `COMPILER ERROR`  `.`</span><span class="sxs-lookup"><span data-stu-id="4136b-108">`' The following statement generates a`   `COMPILER ERROR`  `.`</span></span>  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 <span data-ttu-id="4136b-109">`' The following statement generates a`   `COMPILER ERROR`  `.`</span><span class="sxs-lookup"><span data-stu-id="4136b-109">`' The following statement generates a`   `COMPILER ERROR`  `.`</span></span>  
  
 `Return allOnes()`  
  
 `End Function`  
  
 <span data-ttu-id="4136b-110">陳述式`allOnes(i) = 1`呼叫，所以會產生編譯器錯誤`allOnes`與錯誤的資料類型的引數 (單一`Integer`而不是`Integer`陣列)。</span><span class="sxs-lookup"><span data-stu-id="4136b-110">The statement `allOnes(i) = 1` generates a compiler error because it appears to call `allOnes` with an argument of the wrong data type (a singleton `Integer` instead of an `Integer` array).</span></span> <span data-ttu-id="4136b-111">陳述式`Return allOnes()`呼叫，所以會產生編譯器錯誤`allOnes`但沒有引數。</span><span class="sxs-lookup"><span data-stu-id="4136b-111">The statement `Return allOnes()` generates a compiler error because it appears to call `allOnes` with no argument.</span></span>  
  
 <span data-ttu-id="4136b-112">**正確的方法︰**能夠修改要傳回之陣列的項目，定義內部陣列做為本機變數。</span><span class="sxs-lookup"><span data-stu-id="4136b-112">**Correct Approach:** To be able to modify the elements of an array that is to be returned, define an internal array as a local variable.</span></span> <span data-ttu-id="4136b-113">下列範例會編譯無誤。</span><span class="sxs-lookup"><span data-stu-id="4136b-113">The following example compiles without error.</span></span>  
  
 <span data-ttu-id="4136b-114">[!code-vb[VbVbcnProcedures #&66;](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4136b-114">[!code-vb[VbVbcnProcedures#66](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]</span></span>  
  
## <a name="argument-not-being-modified-by-procedure-call"></a><span data-ttu-id="4136b-115">未修改的引數的程序呼叫</span><span class="sxs-lookup"><span data-stu-id="4136b-115">Argument Not Being Modified by Procedure Call</span></span>  
 <span data-ttu-id="4136b-116">如果您想要允許的程序來變更對應的引數呼叫程式碼的程式設計項目，您必須參考來傳遞。</span><span class="sxs-lookup"><span data-stu-id="4136b-116">If you intend to allow a procedure to change a programming element underlying an argument in the calling code, you must pass it by reference.</span></span> <span data-ttu-id="4136b-117">但即使您傳值方式傳遞程序可以存取參考型別引數的項目。</span><span class="sxs-lookup"><span data-stu-id="4136b-117">But a procedure can access the elements of a reference type argument even if you pass it by value.</span></span>  
  
-   <span data-ttu-id="4136b-118">**基礎變數**。</span><span class="sxs-lookup"><span data-stu-id="4136b-118">**Underlying Variable**.</span></span> <span data-ttu-id="4136b-119">若要允許的程序來取代對應變數項目本身的值，此程序必須宣告參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。</span><span class="sxs-lookup"><span data-stu-id="4136b-119">To allow the procedure to replace the value of the underlying variable element itself, the procedure must declare the parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="4136b-120">此外，呼叫程式碼必須沒有引數括號括住，因為，就會覆寫`ByRef`傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="4136b-120">Also, the calling code must not enclose the argument in parentheses, because that would override the `ByRef` passing mechanism.</span></span>  
  
-   <span data-ttu-id="4136b-121">**參考型別項目**。</span><span class="sxs-lookup"><span data-stu-id="4136b-121">**Reference Type Elements**.</span></span> <span data-ttu-id="4136b-122">如果您將參數宣告[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)，程序無法修改對應變數項目本身。</span><span class="sxs-lookup"><span data-stu-id="4136b-122">If you declare a parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), the procedure cannot modify the underlying variable element itself.</span></span> <span data-ttu-id="4136b-123">不過，如果引數是參考型別，此程序可以修改它所指向的物件的成員即使它無法取代變數的值。</span><span class="sxs-lookup"><span data-stu-id="4136b-123">However, if the argument is a reference type, the procedure can modify the members of the object to which it points, even though it cannot replace the variable's value.</span></span> <span data-ttu-id="4136b-124">比方說，如果引數陣列變數，程序無法將新的陣列指派給它，但可以變更一或多個項目。</span><span class="sxs-lookup"><span data-stu-id="4136b-124">For example, if the argument is an array variable, the procedure cannot assign a new array to it, but it can change one or more of its elements.</span></span> <span data-ttu-id="4136b-125">已變更的項目會反映在呼叫程式碼中的陣列變數。</span><span class="sxs-lookup"><span data-stu-id="4136b-125">The changed elements are reflected in the underlying array variable in the calling code.</span></span>  
  
 <span data-ttu-id="4136b-126">下列範例會定義兩個程序，以傳值方式取得陣列變數和操作其項目上。</span><span class="sxs-lookup"><span data-stu-id="4136b-126">The following example defines two procedures that take an array variable by value and operate on its elements.</span></span> <span data-ttu-id="4136b-127">程序`increase`直接加入至每個項目。</span><span class="sxs-lookup"><span data-stu-id="4136b-127">Procedure `increase` simply adds one to each element.</span></span> <span data-ttu-id="4136b-128">程序`replace`將新的陣列指派給參數`a()`並將每個項目。</span><span class="sxs-lookup"><span data-stu-id="4136b-128">Procedure `replace` assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="4136b-129">不過，重新指派不會影響呼叫程式碼中的陣列變數因為`a()`宣告`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="4136b-129">However, the reassignment does not affect the underlying array variable in the calling code because `a()` is declared `ByVal`.</span></span>  
  
 <span data-ttu-id="4136b-130">[!code-vb[VbVbcnProcedures #&35;](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="4136b-130">[!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]</span></span>  
  
 <span data-ttu-id="4136b-131">[!code-vb[VbVbcnProcedures #&38;](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="4136b-131">[!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]</span></span>  
  
 <span data-ttu-id="4136b-132">下列範例會呼叫`increase`和`replace`。</span><span class="sxs-lookup"><span data-stu-id="4136b-132">The following example makes calls to `increase` and `replace`.</span></span>  
  
 <span data-ttu-id="4136b-133">[!code-vb[VbVbcnProcedures #&37;](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="4136b-133">[!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]</span></span>  
  
 <span data-ttu-id="4136b-134">第一個`MsgBox`呼叫會顯示 「 後 increase(n): 11、 21、 31、 41 」。</span><span class="sxs-lookup"><span data-stu-id="4136b-134">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="4136b-135">因為`n`是參考型別，`increase`可以變更其成員，即使它傳遞`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="4136b-135">Because `n` is a reference type, `increase` can change its members, even though it is passed `ByVal`.</span></span>  
  
 <span data-ttu-id="4136b-136">第二個`MsgBox`呼叫會顯示 「 後 replace(n): 11、 21、 31、 41 」。</span><span class="sxs-lookup"><span data-stu-id="4136b-136">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="4136b-137">因為`n`傳遞`ByVal`，`replace`無法修改變數`n`指派給它的新陣列。</span><span class="sxs-lookup"><span data-stu-id="4136b-137">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` by assigning a new array to it.</span></span> <span data-ttu-id="4136b-138">當`replace`建立新的陣列執行個體`k`並將它指派給本機變數`a`，它就不會參考`n`傳入呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="4136b-138">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="4136b-139">它會遞增的成員`a`，只有本機陣列`k`會受到影響。</span><span class="sxs-lookup"><span data-stu-id="4136b-139">When it increments the members of `a`, only the local array `k` is affected.</span></span>  
  
 <span data-ttu-id="4136b-140">**正確的方法︰**能夠修改對應的變數項目本身，它傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="4136b-140">**Correct Approach:** To be able to modify an underlying variable element itself, pass it by reference.</span></span> <span data-ttu-id="4136b-141">下列範例顯示的宣告中的變更`replace`，可讓它與另一個呼叫程式碼來取代一個陣列。</span><span class="sxs-lookup"><span data-stu-id="4136b-141">The following example shows the change in the declaration of `replace` that allows it to replace one array with another in the calling code.</span></span>  
  
 <span data-ttu-id="4136b-142">[!code-vb[VbVbcnProcedures #&64;](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="4136b-142">[!code-vb[VbVbcnProcedures#64](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]</span></span>  
  
## <a name="unable-to-define-an-overload"></a><span data-ttu-id="4136b-143">無法定義多載</span><span class="sxs-lookup"><span data-stu-id="4136b-143">Unable to Define an Overload</span></span>  
 <span data-ttu-id="4136b-144">如果您想要定義的程序多載的版本，您必須使用相同名稱但不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="4136b-144">If you want to define an overloaded version of a procedure, you must use the same name but a different signature.</span></span> <span data-ttu-id="4136b-145">如果編譯器無法辨識您的宣告與相同的簽章的多載，它會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4136b-145">If the compiler cannot differentiate your declaration from an overload with the same signature, it generates an error.</span></span>  
  
 <span data-ttu-id="4136b-146">*簽章*程序由程序名稱和參數清單。</span><span class="sxs-lookup"><span data-stu-id="4136b-146">The *signature* of a procedure is determined by the procedure name and the parameter list.</span></span> <span data-ttu-id="4136b-147">每個多載必須有同名的所有其他多載，但是必須不同於全部都在至少一個簽章的其他元件。</span><span class="sxs-lookup"><span data-stu-id="4136b-147">Each overload must have the same name as all the other overloads but must differ from all of them in at least one of the other components of the signature.</span></span> <span data-ttu-id="4136b-148">如需詳細資訊，請參閱[程序多載](./procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="4136b-148">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="4136b-149">下列項目，即使它們屬於參數清單中，不是元件的程序的簽章︰</span><span class="sxs-lookup"><span data-stu-id="4136b-149">The following items, even though they pertain to the parameter list, are not components of a procedure's signature:</span></span>  
  
-   <span data-ttu-id="4136b-150">程序的修飾詞關鍵字，例如`Public`， `Shared`，並`Static`</span><span class="sxs-lookup"><span data-stu-id="4136b-150">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
-   <span data-ttu-id="4136b-151">參數名稱</span><span class="sxs-lookup"><span data-stu-id="4136b-151">Parameter names</span></span>  
  
-   <span data-ttu-id="4136b-152">參數修飾詞關鍵字，例如`ByRef`和`Optional`</span><span class="sxs-lookup"><span data-stu-id="4136b-152">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
-   <span data-ttu-id="4136b-153">傳回值 （除了轉換運算子） 的資料類型</span><span class="sxs-lookup"><span data-stu-id="4136b-153">The data type of the return value (except for a conversion operator)</span></span>  
  
 <span data-ttu-id="4136b-154">您無法只改變一個或多個上述項目的多載程序。</span><span class="sxs-lookup"><span data-stu-id="4136b-154">You cannot overload a procedure by varying only one or more of the preceding items.</span></span>  
  
 <span data-ttu-id="4136b-155">**正確的方法︰**可以定義程序多載，所以必須改變簽章。</span><span class="sxs-lookup"><span data-stu-id="4136b-155">**Correct Approach:** To be able to define a procedure overload, you must vary the signature.</span></span> <span data-ttu-id="4136b-156">因為您必須使用相同的名稱，您必須變更數目、 順序或參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4136b-156">Because you must use the same name, you must vary the number, order, or data types of the parameters.</span></span> <span data-ttu-id="4136b-157">在一般的程序，您可以更改類型參數的數目。</span><span class="sxs-lookup"><span data-stu-id="4136b-157">In a generic procedure, you can vary the number of type parameters.</span></span> <span data-ttu-id="4136b-158">在轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md))，您可以變更傳回型別。</span><span class="sxs-lookup"><span data-stu-id="4136b-158">In a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)), you can vary the return type.</span></span>  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a><span data-ttu-id="4136b-159">多載使用選擇性的解析度和 ParamArray 引數</span><span class="sxs-lookup"><span data-stu-id="4136b-159">Overload Resolution with Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="4136b-160">如果您多載化程序時使用一或多個[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數或[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，您必須避免重複的任何*隱含多載*。</span><span class="sxs-lookup"><span data-stu-id="4136b-160">If you are overloading a procedure with one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters or a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you must avoid duplicating any of the *implicit overloads*.</span></span> <span data-ttu-id="4136b-161">如需資訊，請參閱[中多載化程序的考量](./considerations-in-overloading-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="4136b-161">For information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a><span data-ttu-id="4136b-162">呼叫的多載的程序的版本錯誤</span><span class="sxs-lookup"><span data-stu-id="4136b-162">Calling a Wrong Version of an Overloaded Procedure</span></span>  
 <span data-ttu-id="4136b-163">如果程序有數個多載的版本，您應該先熟悉所有的參數清單，並了解如何[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]解析多載之間的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4136b-163">If a procedure has several overloaded versions, you should be familiar with all their parameter lists and understand how [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] resolves calls among the overloads.</span></span> <span data-ttu-id="4136b-164">否則，您可以呼叫非預期的多載。</span><span class="sxs-lookup"><span data-stu-id="4136b-164">Otherwise you could call an overload other than the intended one.</span></span>  
  
 <span data-ttu-id="4136b-165">當您決定您想要呼叫的多載時，小心觀察下列規則︰</span><span class="sxs-lookup"><span data-stu-id="4136b-165">When you have determined which overload you want to call, be careful to observe the following rules:</span></span>  
  
-   <span data-ttu-id="4136b-166">請提供正確數目的引數，並以正確的順序。</span><span class="sxs-lookup"><span data-stu-id="4136b-166">Supply the correct number of arguments, and in the correct order.</span></span>  
  
-   <span data-ttu-id="4136b-167">在理想情況下，您的引數應該有完全相同的資料類型與對應的參數。</span><span class="sxs-lookup"><span data-stu-id="4136b-167">Ideally, your arguments should have the exact same data types as the corresponding parameters.</span></span> <span data-ttu-id="4136b-168">在任何情況下，每個引數的資料型別必須擴展成其對應的參數。</span><span class="sxs-lookup"><span data-stu-id="4136b-168">In any case, the data type of each argument must widen to that of its corresponding parameter.</span></span> <span data-ttu-id="4136b-169">這是即使有，則為 true [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設為`Off`。</span><span class="sxs-lookup"><span data-stu-id="4136b-169">This is true even with the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) set to `Off`.</span></span> <span data-ttu-id="4136b-170">如果多載需要任何引數清單，該多載，縮小轉換不能夠呼叫。</span><span class="sxs-lookup"><span data-stu-id="4136b-170">If an overload requires any narrowing conversion from your argument list, that overload is not eligible to be called.</span></span>  
  
-   <span data-ttu-id="4136b-171">如果您提供需要擴展的引數，請盡可能靠近彼此相對應的參數資料型別及其資料型別。</span><span class="sxs-lookup"><span data-stu-id="4136b-171">If you supply arguments that require widening, make their data types as close as possible to the corresponding parameter data types.</span></span> <span data-ttu-id="4136b-172">如果兩個或多個多載會接受引數的資料型別，編譯器會解析您對呼叫的擴展程度最少的多載的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4136b-172">If two or more overloads accept your argument data types, the compiler resolves your call to the overload that calls for the least amount of widening.</span></span>  
  
 <span data-ttu-id="4136b-173">您可以使用，以降低資料型別不相符的機率[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)準備您的引數時，轉換關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4136b-173">You can reduce the chance of data type mismatches by using the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) conversion keyword when preparing your arguments.</span></span>  
  
### <a name="overload-resolution-failure"></a><span data-ttu-id="4136b-174">多載解析失敗</span><span class="sxs-lookup"><span data-stu-id="4136b-174">Overload Resolution Failure</span></span>  
 <span data-ttu-id="4136b-175">當您呼叫多載的程序時，編譯器就會嘗試排除其中一個多載。</span><span class="sxs-lookup"><span data-stu-id="4136b-175">When you call an overloaded procedure, the compiler attempts to eliminate all but one of the overloads.</span></span> <span data-ttu-id="4136b-176">如果成功，它會解析該多載的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4136b-176">If it succeeds, it resolves the call to that overload.</span></span> <span data-ttu-id="4136b-177">如果它也消除了所有多載，或如果它不能減少為單一的候選者合格的多載，它會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4136b-177">If it eliminates all the overloads, or if it cannot reduce the eligible overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="4136b-178">下列範例說明多載解析程序。</span><span class="sxs-lookup"><span data-stu-id="4136b-178">The following example illustrates the overload resolution process.</span></span>  
  
 <span data-ttu-id="4136b-179">[!code-vb[VbVbcnProcedures #&62;](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="4136b-179">[!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]</span></span>  
  
 <span data-ttu-id="4136b-180">[!code-vb[VbVbcnProcedures #&63;](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="4136b-180">[!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]</span></span>  
  
 <span data-ttu-id="4136b-181">在第一次呼叫時，編譯器會排除第一個多載因為第一個引數型別 (`Short`) 的範圍縮小，對應參數的型別 (`Byte`)。</span><span class="sxs-lookup"><span data-stu-id="4136b-181">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="4136b-182">它接著排除第三個多載，因為每個引數型別中的第二個多載 (`Short`和`Single`) 擴展至對應的型別中的第三個多載 (`Integer`和`Single`)。</span><span class="sxs-lookup"><span data-stu-id="4136b-182">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="4136b-183">第二個多載需要較少的擴展，因此編譯器會將它的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4136b-183">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="4136b-184">在第二個呼叫中，編譯器無法排除任何以縮小為基礎的多載。</span><span class="sxs-lookup"><span data-stu-id="4136b-184">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="4136b-185">它也消除了第三個多載基於相同理由，第一個呼叫，因為它可以呼叫第二個多載，較不需要擴展引數型別。</span><span class="sxs-lookup"><span data-stu-id="4136b-185">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="4136b-186">不過，編譯器無法解析的第一個和第二個多載之間。</span><span class="sxs-lookup"><span data-stu-id="4136b-186">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="4136b-187">每個都有擴展至對應的型別，在另一個定義的參數型別 (`Byte`至`Short`，但`Single`到`Double`)。</span><span class="sxs-lookup"><span data-stu-id="4136b-187">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="4136b-188">因此，編譯器會產生多載解析錯誤。</span><span class="sxs-lookup"><span data-stu-id="4136b-188">The compiler therefore generates an overload resolution error.</span></span>  
  
 <span data-ttu-id="4136b-189">**正確的方法︰**能夠呼叫沒有模稜兩可的多載程序，請使用[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)以符合參數型別引數資料型別。</span><span class="sxs-lookup"><span data-stu-id="4136b-189">**Correct Approach:** To be able to call an overloaded procedure without ambiguity, use [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to match the argument data types to the parameter types.</span></span> <span data-ttu-id="4136b-190">下列範例會示範呼叫`z`，強制第二個多載解析。</span><span class="sxs-lookup"><span data-stu-id="4136b-190">The following example shows a call to `z` that forces resolution to the second overload.</span></span>  
  
 <span data-ttu-id="4136b-191">[!code-vb[VbVbcnProcedures #&65;](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="4136b-191">[!code-vb[VbVbcnProcedures#65](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]</span></span>  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a><span data-ttu-id="4136b-192">多載使用選擇性的解析度和 ParamArray 引數</span><span class="sxs-lookup"><span data-stu-id="4136b-192">Overload Resolution with Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="4136b-193">如果程序的兩個多載具有相同的簽章，不同之處在於最後一個參數宣告[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)一個和[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)中，編譯器會根據最符合該程序的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4136b-193">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure according to the closest match.</span></span> <span data-ttu-id="4136b-194">如需詳細資訊，請參閱[多載解析](./overload-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="4136b-194">For more information, see [Overload Resolution](./overload-resolution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4136b-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4136b-195">See Also</span></span>  
 <span data-ttu-id="4136b-196">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="4136b-196">[Procedures](./index.md) </span></span>  
<span data-ttu-id="4136b-197"> [Sub 程序](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4136b-197"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="4136b-198"> [Function 程序](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4136b-198"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="4136b-199"> [Property 程序](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4136b-199"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="4136b-200"> [運算子程序](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4136b-200"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="4136b-201"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="4136b-201"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="4136b-202"> [多載化程序](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="4136b-202"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="4136b-203"> [多載化程序的考量](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4136b-203"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="4136b-204"> [多載解析](./overload-resolution.md)</span><span class="sxs-lookup"><span data-stu-id="4136b-204"> [Overload Resolution](./overload-resolution.md)</span></span>
