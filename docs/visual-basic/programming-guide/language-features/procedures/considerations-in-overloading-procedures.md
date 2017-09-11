---
title: "考量多載化程序 (Visual Basic) |Microsoft 文件"
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
- signatures, ParamArray arguments
- ParamArray keyword, parameter arrays
- ParamArray keyword, arguments and signatures
- function overloading, implicit overloads for ParamArray
- ParamArray keyword, signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures, overloading
- parameters, lists
- function overloading, typeless programming
- typeless programming
- function overloading, restrictions
- arguments [Visual Basic], optional
- optional arguments, overloading
- signatures, procedure
- parameter lists
- parameter arrays, overloading arguments
- Visual Basic code, parameter lists
- procedure overloading, considerations
- Option Explicit statement
- restrictions, overloading procedures
- procedures, parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
caps.latest.revision: 26
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
ms.openlocfilehash: 486e6c08fe6284cc9b5856fb848f7307a5651120
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="21f3f-102">多載化程序的考慮因素 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21f3f-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="21f3f-103">當您多載程序時，您必須使用不同*簽章*每個多載版本。</span><span class="sxs-lookup"><span data-stu-id="21f3f-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="21f3f-104">這通常表示每個版本都必須指定不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="21f3f-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="21f3f-105">如需詳細資訊，請參閱 「 不同簽章 」 中[程序多載](./procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="21f3f-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="21f3f-106">您可以多載`Function`程序`Sub`程序，並且反之亦然，提供它們具有不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="21f3f-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="21f3f-107">兩個多載不能不同只在於一個具有傳回值，其他則否。</span><span class="sxs-lookup"><span data-stu-id="21f3f-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="21f3f-108">您可以如同您多載程序中，多載屬性和相同的限制。</span><span class="sxs-lookup"><span data-stu-id="21f3f-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="21f3f-109">不過，您無法多載程序與屬性，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="21f3f-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="21f3f-110">多載版本的替代方案</span><span class="sxs-lookup"><span data-stu-id="21f3f-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="21f3f-111">是選擇性的引數的存在或其數目為變數時，特別是，有時候必須多載版本的替代方案。</span><span class="sxs-lookup"><span data-stu-id="21f3f-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="21f3f-112">請記住，選擇性引數不一定支援所有的語言，並會限制使用參數陣列[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="21f3f-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="21f3f-113">如果您正在撰寫可能以任何有幾種不同語言所撰寫的程式碼呼叫的程序，多載版本就可以提供最大的彈性。</span><span class="sxs-lookup"><span data-stu-id="21f3f-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="21f3f-114">多載和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="21f3f-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="21f3f-115">當呼叫程式碼可以選擇性地提供，或略過一或多個引數時，您可以定義多個多載的版本，或使用選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="21f3f-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="21f3f-116">使用多載的版本的時機</span><span class="sxs-lookup"><span data-stu-id="21f3f-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="21f3f-117">您可以考慮在下列情況下定義一系列的多載版本︰</span><span class="sxs-lookup"><span data-stu-id="21f3f-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="21f3f-118">程序程式碼中的邏輯是根據呼叫的程式碼是否提供選擇性引數明顯不同。</span><span class="sxs-lookup"><span data-stu-id="21f3f-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
-   <span data-ttu-id="21f3f-119">程序程式碼無法可靠地測試是否呼叫程式碼已提供選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="21f3f-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="21f3f-120">這種情況，例如，如果沒有任何可做為預設值，呼叫程式碼可能不需要提供。</span><span class="sxs-lookup"><span data-stu-id="21f3f-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="21f3f-121">當使用選擇性參數</span><span class="sxs-lookup"><span data-stu-id="21f3f-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="21f3f-122">您可能偏好在下列情況下的一個或多個選擇性參數︰</span><span class="sxs-lookup"><span data-stu-id="21f3f-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
-   <span data-ttu-id="21f3f-123">若要將參數設定為預設值是唯一必要的動作時呼叫的程式碼並不提供選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="21f3f-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="21f3f-124">在這種情況下中的程序程式碼可能較不複雜，如果您定義的其中一個或多個單一版本`Optional`參數。</span><span class="sxs-lookup"><span data-stu-id="21f3f-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="21f3f-125">如需詳細資訊，請參閱[選擇性參數](./optional-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="21f3f-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="21f3f-126">多載和參數陣列</span><span class="sxs-lookup"><span data-stu-id="21f3f-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="21f3f-127">當呼叫程式碼可以傳遞可變引數數目時，您可以定義多個多載的版本，或使用參數陣列。</span><span class="sxs-lookup"><span data-stu-id="21f3f-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="21f3f-128">使用多載的版本的時機</span><span class="sxs-lookup"><span data-stu-id="21f3f-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="21f3f-129">您可以考慮在下列情況下定義一系列的多載版本︰</span><span class="sxs-lookup"><span data-stu-id="21f3f-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="21f3f-130">您知道，呼叫程式碼永遠不會傳遞多個少量的值給參數陣列。</span><span class="sxs-lookup"><span data-stu-id="21f3f-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
-   <span data-ttu-id="21f3f-131">程序程式碼中的邏輯是根據呼叫的程式碼傳遞的值數目明顯不同。</span><span class="sxs-lookup"><span data-stu-id="21f3f-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
-   <span data-ttu-id="21f3f-132">呼叫程式碼可以傳遞不同的資料類型的值。</span><span class="sxs-lookup"><span data-stu-id="21f3f-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="21f3f-133">何時使用參數陣列</span><span class="sxs-lookup"><span data-stu-id="21f3f-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="21f3f-134">您最好由`ParamArray`參數，在下列情況︰</span><span class="sxs-lookup"><span data-stu-id="21f3f-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
-   <span data-ttu-id="21f3f-135">您不能預測多少值呼叫的程式碼可以傳遞給參數陣列，並可能很多。</span><span class="sxs-lookup"><span data-stu-id="21f3f-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
-   <span data-ttu-id="21f3f-136">程序邏輯可用於逐一查看所有呼叫的程式碼傳遞，執行本質相同之作業上的每個值的值。</span><span class="sxs-lookup"><span data-stu-id="21f3f-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="21f3f-137">如需詳細資訊，請參閱[參數陣列](./parameter-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="21f3f-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="21f3f-138">選擇性參數的隱含多載</span><span class="sxs-lookup"><span data-stu-id="21f3f-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="21f3f-139">程序時使用[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數相當於兩個多載的程序，一個選擇性參數，另一個則不。</span><span class="sxs-lookup"><span data-stu-id="21f3f-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="21f3f-140">您無法多載程序，使用對應至其中的參數清單。</span><span class="sxs-lookup"><span data-stu-id="21f3f-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="21f3f-141">下列宣告可說明這點。</span><span class="sxs-lookup"><span data-stu-id="21f3f-141">The following declarations illustrate this.</span></span>  
  
 <span data-ttu-id="21f3f-142">[!code-vb[VbVbcnProcedures #&58;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="21f3f-142">[!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="21f3f-143">[!code-vb[VbVbcnProcedures #&60;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="21f3f-143">[!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]</span></span>  
  
 <span data-ttu-id="21f3f-144">[!code-vb[VbVbcnProcedures #&61;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="21f3f-144">[!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]</span></span>  
  
 <span data-ttu-id="21f3f-145">對於具有多個選擇性參數的程序，沒有一組邏輯類似於上述範例所到達的隱含多載。</span><span class="sxs-lookup"><span data-stu-id="21f3f-145">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="21f3f-146">參數陣列參數的隱含多載</span><span class="sxs-lookup"><span data-stu-id="21f3f-146">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="21f3f-147">編譯器會考慮使用的程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數具有無限個多載，不同於其他什麼呼叫程式碼會傳遞到參數陣列，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="21f3f-147">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
-   <span data-ttu-id="21f3f-148">當呼叫程式碼不會提供的引數的其中一個多載`ParamArray`</span><span class="sxs-lookup"><span data-stu-id="21f3f-148">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
-   <span data-ttu-id="21f3f-149">當呼叫程式碼提供的一維陣列的其中一個多載`ParamArray`項目型別</span><span class="sxs-lookup"><span data-stu-id="21f3f-149">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
-   <span data-ttu-id="21f3f-150">對每一個正整數，其中一個多載時呼叫的程式碼提供該數目的引數，每個`ParamArray`項目型別</span><span class="sxs-lookup"><span data-stu-id="21f3f-150">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="21f3f-151">下列宣告會說明這些隱含多載。</span><span class="sxs-lookup"><span data-stu-id="21f3f-151">The following declarations illustrate these implicit overloads.</span></span>  
  
 <span data-ttu-id="21f3f-152">[!code-vb[VbVbcnProcedures #&68;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="21f3f-152">[!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]</span></span>  
  
 <span data-ttu-id="21f3f-153">[!code-vb[VbVbcnProcedures #&70;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="21f3f-153">[!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]</span></span>  
  
 <span data-ttu-id="21f3f-154">您無法多載，這樣的程序的參數清單，會採用參數陣列的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="21f3f-154">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="21f3f-155">不過，您可以使用其他隱含多載的簽章。</span><span class="sxs-lookup"><span data-stu-id="21f3f-155">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="21f3f-156">下列宣告可說明這點。</span><span class="sxs-lookup"><span data-stu-id="21f3f-156">The following declarations illustrate this.</span></span>  
  
 <span data-ttu-id="21f3f-157">[!code-vb[VbVbcnProcedures #&71;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="21f3f-157">[!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]</span></span>  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="21f3f-158">另一種多載的無類型程式設計</span><span class="sxs-lookup"><span data-stu-id="21f3f-158">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="21f3f-159">如果您想要允許不同的資料型別傳遞至參數呼叫的程式碼，另一個方法是無型別程式設計。</span><span class="sxs-lookup"><span data-stu-id="21f3f-159">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="21f3f-160">您可以設定型別檢查切換到`Off`與[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)或[/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="21f3f-160">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="21f3f-161">然後您不需要宣告參數的資料型別。</span><span class="sxs-lookup"><span data-stu-id="21f3f-161">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="21f3f-162">不過，這個方法有下列缺點相較於多載︰</span><span class="sxs-lookup"><span data-stu-id="21f3f-162">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
-   <span data-ttu-id="21f3f-163">無類型程式設計產生效率較低的執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="21f3f-163">Typeless programming produces less efficient execution code.</span></span>  
  
-   <span data-ttu-id="21f3f-164">此程序必須測試它預期傳遞的每一個資料型別。</span><span class="sxs-lookup"><span data-stu-id="21f3f-164">The procedure must test for every data type it anticipates being passed.</span></span>  
  
-   <span data-ttu-id="21f3f-165">編譯器無法通知發生錯誤，如果呼叫程式碼會將此程序不支援的資料類型。</span><span class="sxs-lookup"><span data-stu-id="21f3f-165">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f3f-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21f3f-166">See Also</span></span>  
 <span data-ttu-id="21f3f-167">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="21f3f-167">[Procedures](./index.md) </span></span>  
<span data-ttu-id="21f3f-168"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="21f3f-168"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="21f3f-169"> [疑難排解程序](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="21f3f-169"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="21f3f-170"> [如何︰ 定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="21f3f-170"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="21f3f-171"> [如何︰ 呼叫多載程序](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="21f3f-171"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="21f3f-172"> [如何︰ 多載使用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="21f3f-172"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="21f3f-173"> [如何︰ 多載使用不定數目參數的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="21f3f-173"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="21f3f-174"> [多載解析](./overload-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="21f3f-174"> [Overload Resolution](./overload-resolution.md) </span></span>  
<span data-ttu-id="21f3f-175"> [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)</span><span class="sxs-lookup"><span data-stu-id="21f3f-175"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)</span></span>
