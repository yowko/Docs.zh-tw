---
title: 多載程序的考量
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
ms.openlocfilehash: 6197fa4041a22944542b2657e35bc293a6e5c244
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075053"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="c1fc8-102">多載化程序的考慮因素 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1fc8-102">Considerations in Overloading Procedures (Visual Basic)</span></span>

<span data-ttu-id="c1fc8-103">當您多載程式時，您必須針對每個多載版本使用 *不同的簽* 章。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="c1fc8-104">這通常表示每個版本都必須指定不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="c1fc8-105">如需詳細資訊，請參閱程式多載 [中的](./procedure-overloading.md)「不同簽章」。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="c1fc8-106">您可以使用程式來多載程式 `Function` `Sub` ，反之亦然，前提是它們具有不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="c1fc8-107">兩個多載不能不同，因為它有傳回值，另一個則沒有。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="c1fc8-108">您可以使用多載程式的相同方式來多載屬性，並具有相同的限制。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="c1fc8-109">不過，您不能使用屬性來多載程式，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="c1fc8-110">多載版本的替代專案</span><span class="sxs-lookup"><span data-stu-id="c1fc8-110">Alternatives to Overloaded Versions</span></span>  

 <span data-ttu-id="c1fc8-111">您有時會有多載版本的替代專案，特別是當引數的存在是選擇性的，或其數位為變數時。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="c1fc8-112">請記住，並非所有語言都支援選擇性引數，而且參數陣列僅限於 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="c1fc8-113">如果您要撰寫的程式可能會從以數種不同語言撰寫的程式碼中呼叫，多載版本提供最大的彈性。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="c1fc8-114">多載和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="c1fc8-114">Overloads and Optional Arguments</span></span>  

 <span data-ttu-id="c1fc8-115">當呼叫程式碼可以選擇性地提供或省略一或多個引數時，您可以定義多個多載版本或使用選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="c1fc8-116">使用多載版本的時機</span><span class="sxs-lookup"><span data-stu-id="c1fc8-116">When to Use Overloaded Versions</span></span>  

 <span data-ttu-id="c1fc8-117">在下列情況下，您可以考慮定義一連串的多載版本：</span><span class="sxs-lookup"><span data-stu-id="c1fc8-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="c1fc8-118">程式碼中的邏輯會根據呼叫程式碼是否提供選擇性引數而大幅不同。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
- <span data-ttu-id="c1fc8-119">程式碼無法可靠地測試呼叫程式碼是否已提供選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="c1fc8-120">例如，如果沒有任何可能的候選預設值，表示呼叫程式碼無法提供，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="c1fc8-121">使用選擇性參數的時機</span><span class="sxs-lookup"><span data-stu-id="c1fc8-121">When to Use Optional Parameters</span></span>  

 <span data-ttu-id="c1fc8-122">在下列情況下，您可能會想要使用一或多個選擇性參數：</span><span class="sxs-lookup"><span data-stu-id="c1fc8-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
- <span data-ttu-id="c1fc8-123">當呼叫程式碼未提供選擇性引數時，唯一必要的動作是將參數設定為預設值。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="c1fc8-124">在這種情況下，如果您使用一或多個參數來定義單一版本，程式程式碼可能會比較複雜 `Optional` 。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="c1fc8-125">如需詳細資訊，請參閱 [選用參數](./optional-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="c1fc8-126">多載和 ParamArrays</span><span class="sxs-lookup"><span data-stu-id="c1fc8-126">Overloads and ParamArrays</span></span>  

 <span data-ttu-id="c1fc8-127">當呼叫程式碼可以傳遞變數數目的引數時，您可以定義多個多載版本或使用參數陣列。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="c1fc8-128">使用多載版本的時機</span><span class="sxs-lookup"><span data-stu-id="c1fc8-128">When to Use Overloaded Versions</span></span>  

 <span data-ttu-id="c1fc8-129">在下列情況下，您可以考慮定義一連串的多載版本：</span><span class="sxs-lookup"><span data-stu-id="c1fc8-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="c1fc8-130">您知道呼叫程式碼永遠不會將較小的值傳遞給參數陣列。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
- <span data-ttu-id="c1fc8-131">程式碼中的邏輯會根據呼叫程式碼所傳遞的值數目，而有很大的不同。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
- <span data-ttu-id="c1fc8-132">呼叫程式碼可以傳遞不同資料類型的值。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="c1fc8-133">使用參數陣列的時機</span><span class="sxs-lookup"><span data-stu-id="c1fc8-133">When to Use a Parameter Array</span></span>  

 <span data-ttu-id="c1fc8-134">在下列情況下，參數會提供更好的服務 `ParamArray` ：</span><span class="sxs-lookup"><span data-stu-id="c1fc8-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
- <span data-ttu-id="c1fc8-135">您無法預測呼叫程式碼可以傳遞給參數陣列的值數目，也可以是大型數位。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
- <span data-ttu-id="c1fc8-136">程式邏輯適合用來逐一查看呼叫程式碼所傳遞的所有值，基本上在每個值上執行相同的作業。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="c1fc8-137">如需詳細資訊，請參閱 [參數陣列](./parameter-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="c1fc8-138">選擇性參數的隱含多載</span><span class="sxs-lookup"><span data-stu-id="c1fc8-138">Implicit Overloads for Optional Parameters</span></span>  

 <span data-ttu-id="c1fc8-139">具有 [選擇性](../../../language-reference/modifiers/optional.md) 參數的程式相當於兩個多載程式，一個具有選擇性參數，另一個則沒有。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-139">A procedure with an [Optional](../../../language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="c1fc8-140">您無法使用對應至其中一種的參數清單來多載這類程式。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="c1fc8-141">下列宣告說明這一點。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="c1fc8-142">針對具有多個選擇性參數的程式，會有一組隱含的多載，與前述範例中的邏輯類似。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="c1fc8-143">ParamArray 參數的隱含多載</span><span class="sxs-lookup"><span data-stu-id="c1fc8-143">Implicit Overloads for a ParamArray Parameter</span></span>  

 <span data-ttu-id="c1fc8-144">編譯器會將具有 [ParamArray](../../../language-reference/modifiers/paramarray.md) 參數的程式視為具有無限數量的多載，這些多載在呼叫程式碼傳遞至參數陣列的情況下彼此不同，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c1fc8-144">The compiler considers a procedure with a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
- <span data-ttu-id="c1fc8-145">當呼叫程式碼未提供引數給時，會有一個多載 `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="c1fc8-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
- <span data-ttu-id="c1fc8-146">當呼叫程式碼提供專案類型的一維陣列時，會有一個多載 `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="c1fc8-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
- <span data-ttu-id="c1fc8-147">針對每個正整數，當呼叫程式碼提供該數目的引數時，會有一個多載，每個 `ParamArray` 元素類型</span><span class="sxs-lookup"><span data-stu-id="c1fc8-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="c1fc8-148">下列宣告說明這些隱含多載。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="c1fc8-149">您無法使用接受一維陣列作為參數陣列的參數清單來多載這類程式。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="c1fc8-150">不過，您可以使用其他隱含多載的簽章。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="c1fc8-151">下列宣告說明這一點。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="c1fc8-152">無程式設計為多載的替代方案</span><span class="sxs-lookup"><span data-stu-id="c1fc8-152">Typeless Programming as an Alternative to Overloading</span></span>  

 <span data-ttu-id="c1fc8-153">如果您想要允許呼叫程式碼將不同的資料類型傳遞給參數，替代方法是無型別的程式設計。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="c1fc8-154">您可以 `Off` 使用 [Option Strict 語句](../../../language-reference/statements/option-strict-statement.md) 或 [-optionstrict](../../../reference/command-line-compiler/optionstrict.md) 編譯器選項，將類型檢查參數設定為。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) or the [-optionstrict](../../../reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="c1fc8-155">然後您不需要宣告參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="c1fc8-156">不過，相較于多載，此方法的缺點如下：</span><span class="sxs-lookup"><span data-stu-id="c1fc8-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
- <span data-ttu-id="c1fc8-157">無程式設計會產生效率不佳的執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-157">Typeless programming produces less efficient execution code.</span></span>  
  
- <span data-ttu-id="c1fc8-158">程式必須測試預期傳遞的每個資料類型。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
- <span data-ttu-id="c1fc8-159">如果呼叫程式碼傳遞程式不支援的資料類型，則編譯器無法通知錯誤。</span><span class="sxs-lookup"><span data-stu-id="c1fc8-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1fc8-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1fc8-160">See also</span></span>

- [<span data-ttu-id="c1fc8-161">程序</span><span class="sxs-lookup"><span data-stu-id="c1fc8-161">Procedures</span></span>](./index.md)
- [<span data-ttu-id="c1fc8-162">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="c1fc8-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c1fc8-163">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="c1fc8-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="c1fc8-164">如何：定義程序的多個版本</span><span class="sxs-lookup"><span data-stu-id="c1fc8-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="c1fc8-165">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="c1fc8-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="c1fc8-166">如何：使用選擇性參數的多載程序</span><span class="sxs-lookup"><span data-stu-id="c1fc8-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="c1fc8-167">如何：多載使用不確定參數數目的程序</span><span class="sxs-lookup"><span data-stu-id="c1fc8-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="c1fc8-168">多載解析</span><span class="sxs-lookup"><span data-stu-id="c1fc8-168">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="c1fc8-169">多載</span><span class="sxs-lookup"><span data-stu-id="c1fc8-169">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
