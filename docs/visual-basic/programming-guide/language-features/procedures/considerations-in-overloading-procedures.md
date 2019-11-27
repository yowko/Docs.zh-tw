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
ms.openlocfilehash: 4a0cfe176a59b3f90f5850ae8b4e34784c400c6b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351003"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="20a7f-102">多載化程序的考慮因素 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20a7f-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="20a7f-103">當您多載程式時，您必須針對每個多載版本使用*不同的簽*章。</span><span class="sxs-lookup"><span data-stu-id="20a7f-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="20a7f-104">這通常表示每個版本都必須指定不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="20a7f-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="20a7f-105">如需詳細資訊，請參閱程式多載[中的「不同的簽](./procedure-overloading.md)章」。</span><span class="sxs-lookup"><span data-stu-id="20a7f-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="20a7f-106">您可以使用 `Sub` 程式來多載 `Function` 程式，反之亦然，前提是它們有不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="20a7f-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="20a7f-107">兩個多載不能有不同的差異，只有其中一個具有傳回值，另一個則沒有。</span><span class="sxs-lookup"><span data-stu-id="20a7f-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="20a7f-108">您可以使用與多載程式相同的方式來多載屬性，而且具有相同的限制。</span><span class="sxs-lookup"><span data-stu-id="20a7f-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="20a7f-109">但是，您無法使用屬性來多載程式，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="20a7f-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="20a7f-110">多載版本的替代專案</span><span class="sxs-lookup"><span data-stu-id="20a7f-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="20a7f-111">有時候，您會有多載版本的替代專案，特別是當引數的存在是選擇性或其數位為變數時。</span><span class="sxs-lookup"><span data-stu-id="20a7f-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="20a7f-112">請記住，所有語言都不一定支援選擇性引數，而且參數陣列僅限於 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="20a7f-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="20a7f-113">如果您撰寫的程式可能會從以多種不同語言撰寫的程式碼中呼叫，則多載版本提供最大的彈性。</span><span class="sxs-lookup"><span data-stu-id="20a7f-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="20a7f-114">多載和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="20a7f-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="20a7f-115">當呼叫程式碼可以選擇性地提供或省略一或多個引數時，您可以定義多個多載版本或使用選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="20a7f-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="20a7f-116">使用多載版本的時機</span><span class="sxs-lookup"><span data-stu-id="20a7f-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="20a7f-117">在下列情況下，您可以考慮定義一連串的多載版本：</span><span class="sxs-lookup"><span data-stu-id="20a7f-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="20a7f-118">程式碼中的邏輯會根據呼叫程式碼是否提供選擇性引數而有很大的差異。</span><span class="sxs-lookup"><span data-stu-id="20a7f-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
- <span data-ttu-id="20a7f-119">程式碼無法可靠地測試呼叫程式碼是否已提供選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="20a7f-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="20a7f-120">例如，如果沒有可供呼叫程式碼無法提供的預設值，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="20a7f-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="20a7f-121">使用選擇性參數的時機</span><span class="sxs-lookup"><span data-stu-id="20a7f-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="20a7f-122">在下列情況中，您可能會偏好使用一或多個選擇性參數：</span><span class="sxs-lookup"><span data-stu-id="20a7f-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
- <span data-ttu-id="20a7f-123">當呼叫程式碼未提供選擇性引數時，唯一必要的動作是將參數設定為預設值。</span><span class="sxs-lookup"><span data-stu-id="20a7f-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="20a7f-124">在這種情況下，如果您定義具有一或多個 `Optional` 參數的單一版本，程式碼可能會比較不復雜。</span><span class="sxs-lookup"><span data-stu-id="20a7f-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="20a7f-125">如需詳細資訊，請參閱[選擇性參數](./optional-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="20a7f-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="20a7f-126">多載和 ParamArrays</span><span class="sxs-lookup"><span data-stu-id="20a7f-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="20a7f-127">當呼叫程式碼可以傳遞可變數目的引數時，您可以定義多個多載版本，或使用參數陣列。</span><span class="sxs-lookup"><span data-stu-id="20a7f-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="20a7f-128">使用多載版本的時機</span><span class="sxs-lookup"><span data-stu-id="20a7f-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="20a7f-129">在下列情況下，您可以考慮定義一連串的多載版本：</span><span class="sxs-lookup"><span data-stu-id="20a7f-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="20a7f-130">您知道呼叫程式碼絕對不會將一個以上的值傳遞給參數陣列。</span><span class="sxs-lookup"><span data-stu-id="20a7f-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
- <span data-ttu-id="20a7f-131">程式碼中的邏輯會明顯不同，這取決於呼叫程式碼傳遞多少個值。</span><span class="sxs-lookup"><span data-stu-id="20a7f-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
- <span data-ttu-id="20a7f-132">呼叫程式碼可以傳遞不同資料類型的值。</span><span class="sxs-lookup"><span data-stu-id="20a7f-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="20a7f-133">使用參數陣列的時機</span><span class="sxs-lookup"><span data-stu-id="20a7f-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="20a7f-134">在下列情況下，`ParamArray` 參數會提供較佳的服務：</span><span class="sxs-lookup"><span data-stu-id="20a7f-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
- <span data-ttu-id="20a7f-135">您無法預測呼叫程式碼可以傳遞給參數陣列的值數目，而且可能是很大的數位。</span><span class="sxs-lookup"><span data-stu-id="20a7f-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
- <span data-ttu-id="20a7f-136">程式邏輯可自行逐一查看呼叫程式碼所通過的所有值，對每個值基本上執行相同的作業。</span><span class="sxs-lookup"><span data-stu-id="20a7f-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="20a7f-137">如需詳細資訊，請參閱[參數陣列](./parameter-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="20a7f-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="20a7f-138">選擇性參數的隱含多載</span><span class="sxs-lookup"><span data-stu-id="20a7f-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="20a7f-139">具有[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數的程式相當於兩個多載的程式，一個包含選擇性參數，另一個則沒有。</span><span class="sxs-lookup"><span data-stu-id="20a7f-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="20a7f-140">您無法使用對應于其中任一項的參數清單來多載這類程式。</span><span class="sxs-lookup"><span data-stu-id="20a7f-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="20a7f-141">下列宣告說明這種情況。</span><span class="sxs-lookup"><span data-stu-id="20a7f-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="20a7f-142">針對具有多個選擇性參數的程式，會有一組隱含的多載，並以類似上述範例中的邏輯抵達。</span><span class="sxs-lookup"><span data-stu-id="20a7f-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="20a7f-143">ParamArray 參數的隱含多載</span><span class="sxs-lookup"><span data-stu-id="20a7f-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="20a7f-144">編譯器會將具有[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數的程式視為具有無限數量的多載，並在呼叫程式碼傳遞給參數陣列的內容中彼此不同，如下所示：</span><span class="sxs-lookup"><span data-stu-id="20a7f-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
- <span data-ttu-id="20a7f-145">呼叫程式碼未提供引數給 `ParamArray` 時的一個多載</span><span class="sxs-lookup"><span data-stu-id="20a7f-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
- <span data-ttu-id="20a7f-146">當呼叫程式碼提供 `ParamArray` 專案類型的一維陣列時，一個多載</span><span class="sxs-lookup"><span data-stu-id="20a7f-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
- <span data-ttu-id="20a7f-147">針對每個正整數，當呼叫程式碼提供該數目的引數時，一個多載，其中每個都是 `ParamArray` 的元素類型</span><span class="sxs-lookup"><span data-stu-id="20a7f-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="20a7f-148">下列宣告說明這些隱含多載。</span><span class="sxs-lookup"><span data-stu-id="20a7f-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="20a7f-149">您無法使用參數清單來多載這類程式，其中會採用一維陣列做為參數陣列。</span><span class="sxs-lookup"><span data-stu-id="20a7f-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="20a7f-150">不過，您可以使用其他隱含多載的簽章。</span><span class="sxs-lookup"><span data-stu-id="20a7f-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="20a7f-151">下列宣告說明這種情況。</span><span class="sxs-lookup"><span data-stu-id="20a7f-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="20a7f-152">無程式設計是多載的替代方法</span><span class="sxs-lookup"><span data-stu-id="20a7f-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="20a7f-153">如果您想要允許呼叫程式碼將不同的資料類型傳遞給參數，另一個替代方法是無類型的程式設計。</span><span class="sxs-lookup"><span data-stu-id="20a7f-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="20a7f-154">您可以使用[Option Strict 語句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)或[-optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項，將類型檢查參數設定為 `Off`。</span><span class="sxs-lookup"><span data-stu-id="20a7f-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [-optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="20a7f-155">然後您就不需要宣告參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="20a7f-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="20a7f-156">不過，相較于多載，此方法具有下列缺點：</span><span class="sxs-lookup"><span data-stu-id="20a7f-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
- <span data-ttu-id="20a7f-157">無語言程式設計會產生較不有效率的執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="20a7f-157">Typeless programming produces less efficient execution code.</span></span>  
  
- <span data-ttu-id="20a7f-158">此程式必須針對預期傳遞的每個資料類型進行測試。</span><span class="sxs-lookup"><span data-stu-id="20a7f-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
- <span data-ttu-id="20a7f-159">如果呼叫程式碼傳遞程式不支援的資料類型，編譯器就無法通知錯誤。</span><span class="sxs-lookup"><span data-stu-id="20a7f-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a7f-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20a7f-160">See also</span></span>

- [<span data-ttu-id="20a7f-161">程序</span><span class="sxs-lookup"><span data-stu-id="20a7f-161">Procedures</span></span>](./index.md)
- [<span data-ttu-id="20a7f-162">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="20a7f-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="20a7f-163">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="20a7f-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="20a7f-164">如何：定義程序的多個版本</span><span class="sxs-lookup"><span data-stu-id="20a7f-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="20a7f-165">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="20a7f-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="20a7f-166">如何：使用選擇性參數的多載程序</span><span class="sxs-lookup"><span data-stu-id="20a7f-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="20a7f-167">如何：多載使用不確定參數數目的程序</span><span class="sxs-lookup"><span data-stu-id="20a7f-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="20a7f-168">多載解析</span><span class="sxs-lookup"><span data-stu-id="20a7f-168">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="20a7f-169">多載</span><span class="sxs-lookup"><span data-stu-id="20a7f-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
