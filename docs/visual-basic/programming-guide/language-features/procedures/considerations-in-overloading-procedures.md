---
title: 多載化程序的考慮因素 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: b5a26a8b68a2f786213aa49f30247d692b3de2f7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649651"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="af39a-102">多載化程序的考慮因素 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af39a-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="af39a-103">當您多載程序時，您必須使用不同*簽章*針對每個多載版本。</span><span class="sxs-lookup"><span data-stu-id="af39a-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="af39a-104">這通常表示每個版本必須指定不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="af39a-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="af39a-105">如需詳細資訊，請參閱 「 不同的簽章 」 中[程序多載](./procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="af39a-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="af39a-106">您可以多載`Function`程序`Sub`程序中，而且反之亦然，提供它們有不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="af39a-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="af39a-107">兩個多載無法差異只在於有傳回值及其他則否。</span><span class="sxs-lookup"><span data-stu-id="af39a-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="af39a-108">您可以多載程序中，相同的方式多載屬性和具有相同的限制。</span><span class="sxs-lookup"><span data-stu-id="af39a-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="af39a-109">不過，您無法多載程序與屬性，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="af39a-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="af39a-110">多載版本的替代方案</span><span class="sxs-lookup"><span data-stu-id="af39a-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="af39a-111">是選擇性的引數存在，或其數目為變數時，特別是，有時候會有多載版本的替代方案。</span><span class="sxs-lookup"><span data-stu-id="af39a-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="af39a-112">請記住，選擇性引數不一定支援所有的語言，以及參數陣列僅限於使用 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="af39a-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="af39a-113">如果您正在撰寫可能從任何有幾種不同語言撰寫的程式碼呼叫的程序，多載版本的供應項目最大的彈性。</span><span class="sxs-lookup"><span data-stu-id="af39a-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="af39a-114">多載和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="af39a-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="af39a-115">當呼叫程式碼可以選擇性地提供或省略一或多個引數時，您可以定義多個多載的版本，或使用選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="af39a-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="af39a-116">使用多載的版本的時機</span><span class="sxs-lookup"><span data-stu-id="af39a-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="af39a-117">在下列情況下，可以考慮一系列的多載版本：</span><span class="sxs-lookup"><span data-stu-id="af39a-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="af39a-118">程序程式碼中的邏輯是根據呼叫的程式碼是否提供選擇性引數截然不同。</span><span class="sxs-lookup"><span data-stu-id="af39a-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
- <span data-ttu-id="af39a-119">是否呼叫程式碼已提供的選擇性引數，無法可靠地測試程序程式碼。</span><span class="sxs-lookup"><span data-stu-id="af39a-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="af39a-120">此情況下，比方說，如果有任何可能的候選項目的預設值，呼叫程式碼可能不需要提供。</span><span class="sxs-lookup"><span data-stu-id="af39a-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="af39a-121">當使用選擇性參數</span><span class="sxs-lookup"><span data-stu-id="af39a-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="af39a-122">您可能會偏好在下列情況中的一或多個選擇性參數：</span><span class="sxs-lookup"><span data-stu-id="af39a-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
- <span data-ttu-id="af39a-123">若要將參數設定為預設值是唯一必要的動作時呼叫的程式碼中未提供選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="af39a-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="af39a-124">在此情況下中的程序程式碼可以變得簡單許多，如果您定義具有一或多個單一版本`Optional`參數。</span><span class="sxs-lookup"><span data-stu-id="af39a-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="af39a-125">如需詳細資訊，請參閱 <<c0> [ 選擇性參數](./optional-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="af39a-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="af39a-126">多載和參數陣列</span><span class="sxs-lookup"><span data-stu-id="af39a-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="af39a-127">當呼叫的程式碼可以傳遞可變數目的引數時，您可以定義多個多載的版本，或使用參數陣列。</span><span class="sxs-lookup"><span data-stu-id="af39a-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="af39a-128">使用多載的版本的時機</span><span class="sxs-lookup"><span data-stu-id="af39a-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="af39a-129">在下列情況下，可以考慮一系列的多載版本：</span><span class="sxs-lookup"><span data-stu-id="af39a-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="af39a-130">您知道，呼叫程式碼永遠不會傳遞多個一小部分的值給參數陣列。</span><span class="sxs-lookup"><span data-stu-id="af39a-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
- <span data-ttu-id="af39a-131">程序程式碼中的邏輯是根據呼叫的程式碼傳遞的值數目大幅不同。</span><span class="sxs-lookup"><span data-stu-id="af39a-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
- <span data-ttu-id="af39a-132">呼叫端程式碼可以傳遞不同的資料類型的值。</span><span class="sxs-lookup"><span data-stu-id="af39a-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="af39a-133">使用參數陣列的時機</span><span class="sxs-lookup"><span data-stu-id="af39a-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="af39a-134">您會取得更佳服務`ParamArray`參數，在下列情況：</span><span class="sxs-lookup"><span data-stu-id="af39a-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
- <span data-ttu-id="af39a-135">您不能預測多少值呼叫的程式碼可以傳遞給參數陣列，並可能是大的數字。</span><span class="sxs-lookup"><span data-stu-id="af39a-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
- <span data-ttu-id="af39a-136">程序邏輯可用於逐一查看通過呼叫程式碼，執行本質相同之作業的每個值上的所有值。</span><span class="sxs-lookup"><span data-stu-id="af39a-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="af39a-137">如需詳細資訊，請參閱 <<c0> [ 參數陣列](./parameter-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="af39a-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="af39a-138">選擇性參數的隱含多載</span><span class="sxs-lookup"><span data-stu-id="af39a-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="af39a-139">使用的程序[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數相當於兩個多載的程序，一個選擇性參數，而不需要它的另一個。</span><span class="sxs-lookup"><span data-stu-id="af39a-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="af39a-140">您無法多載這樣的程序，使用對應至其中的參數清單。</span><span class="sxs-lookup"><span data-stu-id="af39a-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="af39a-141">下列宣告將說明這點。</span><span class="sxs-lookup"><span data-stu-id="af39a-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="af39a-142">一個以上的選擇性參數的程序，沒有一組隱含的多載，抵達類似於在上述範例中的邏輯。</span><span class="sxs-lookup"><span data-stu-id="af39a-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="af39a-143">ParamArray 參數的隱含多載</span><span class="sxs-lookup"><span data-stu-id="af39a-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="af39a-144">編譯器會考慮使用的程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數具有無限個多載，彼此不同項目呼叫的程式碼將傳遞給參數陣列，如下所示：</span><span class="sxs-lookup"><span data-stu-id="af39a-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
- <span data-ttu-id="af39a-145">其中一個多載的呼叫端程式碼時未提供的引數 `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="af39a-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
- <span data-ttu-id="af39a-146">針對呼叫的程式碼時提供的一維陣列的其中一個多載`ParamArray`項目類型</span><span class="sxs-lookup"><span data-stu-id="af39a-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
- <span data-ttu-id="af39a-147">對每一個正整數，其中一個多載時呼叫的程式碼提供該數目的引數，每個`ParamArray`項目類型</span><span class="sxs-lookup"><span data-stu-id="af39a-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="af39a-148">下列宣告會說明這些隱含的多載。</span><span class="sxs-lookup"><span data-stu-id="af39a-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="af39a-149">您無法多載會採用參數陣列的一維陣列的參數清單的這類的程序。</span><span class="sxs-lookup"><span data-stu-id="af39a-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="af39a-150">不過，您可以使用其他隱含的多載的簽章。</span><span class="sxs-lookup"><span data-stu-id="af39a-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="af39a-151">下列宣告將說明這點。</span><span class="sxs-lookup"><span data-stu-id="af39a-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="af39a-152">除了多載的無類型程式設計</span><span class="sxs-lookup"><span data-stu-id="af39a-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="af39a-153">如果您想要允許呼叫端的程式碼，來傳遞參數至不同的資料類型，另一個方法是無型別程式設計。</span><span class="sxs-lookup"><span data-stu-id="af39a-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="af39a-154">您可以設定類型檢查參數來`Off`與其中一個[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)或[/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="af39a-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="af39a-155">然後您沒有宣告參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="af39a-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="af39a-156">不過，這個方法會有下列缺點相較於多載：</span><span class="sxs-lookup"><span data-stu-id="af39a-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
- <span data-ttu-id="af39a-157">無類型程式設計產生效率較低的執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="af39a-157">Typeless programming produces less efficient execution code.</span></span>  
  
- <span data-ttu-id="af39a-158">此程序必須測試它預期傳遞的每一個資料型別。</span><span class="sxs-lookup"><span data-stu-id="af39a-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
- <span data-ttu-id="af39a-159">編譯器無法通知發生錯誤，如果呼叫程式碼會將此程序不支援的資料類型。</span><span class="sxs-lookup"><span data-stu-id="af39a-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af39a-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af39a-160">See also</span></span>

- [<span data-ttu-id="af39a-161">程序</span><span class="sxs-lookup"><span data-stu-id="af39a-161">Procedures</span></span>](./index.md)
- [<span data-ttu-id="af39a-162">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="af39a-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="af39a-163">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="af39a-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="af39a-164">如何：定義多個版本的程序</span><span class="sxs-lookup"><span data-stu-id="af39a-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="af39a-165">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="af39a-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="af39a-166">如何：多載會採用選擇性參數的程序</span><span class="sxs-lookup"><span data-stu-id="af39a-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="af39a-167">如何：多載不定數目參數的程序</span><span class="sxs-lookup"><span data-stu-id="af39a-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="af39a-168">多載解析</span><span class="sxs-lookup"><span data-stu-id="af39a-168">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="af39a-169">多載</span><span class="sxs-lookup"><span data-stu-id="af39a-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
