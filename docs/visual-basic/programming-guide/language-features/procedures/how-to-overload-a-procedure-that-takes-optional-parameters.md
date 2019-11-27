---
title: 如何：使用選擇性參數的多載程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 4d31980e4b968cff274091ba4f307dffddab1100
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350869"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="47d15-102">如何：多載使用選擇性參數的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47d15-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="47d15-103">如果程式有一或多個[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數，您就無法定義多載版本來符合它的任何隱含多載。</span><span class="sxs-lookup"><span data-stu-id="47d15-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="47d15-104">如需詳細資訊，請參閱多載[程式的考慮](./considerations-in-overloading-procedures.md)中的「選擇性參數的隱含多載」。</span><span class="sxs-lookup"><span data-stu-id="47d15-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="47d15-105">一個選擇性參數</span><span class="sxs-lookup"><span data-stu-id="47d15-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="47d15-106">若要多載採用一個選擇性參數的程式</span><span class="sxs-lookup"><span data-stu-id="47d15-106">To overload a procedure that takes one optional parameter</span></span>  
  
1. <span data-ttu-id="47d15-107">撰寫 `Sub` 或 `Function` 宣告語句，其中包含參數清單中的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="47d15-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="47d15-108">請勿在此多載的版本中使用 `Optional` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="47d15-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2. <span data-ttu-id="47d15-109">在 `Sub` 或 `Function` 關鍵字之前加上[Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="47d15-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3. <span data-ttu-id="47d15-110">撰寫當呼叫程式碼提供選擇性引數時應執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="47d15-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4. <span data-ttu-id="47d15-111">視需要使用 `End Sub` 或 `End Function` 語句來終止程式。</span><span class="sxs-lookup"><span data-stu-id="47d15-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5. <span data-ttu-id="47d15-112">撰寫與第一個宣告相同的第二個宣告語句，不同之處在于它不會在參數清單中包含選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="47d15-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6. <span data-ttu-id="47d15-113">撰寫當呼叫程式碼未提供選擇性引數時，應執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="47d15-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="47d15-114">視需要使用 `End Sub` 或 `End Function` 語句來終止程式。</span><span class="sxs-lookup"><span data-stu-id="47d15-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="47d15-115">下列範例顯示的程式是以選擇性參數、一組對等的兩個多載程式來定義，最後是無效和有效的多載版本的範例。</span><span class="sxs-lookup"><span data-stu-id="47d15-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="47d15-116">多個選擇性參數</span><span class="sxs-lookup"><span data-stu-id="47d15-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="47d15-117">針對具有多個選擇性參數的程式，您通常需要兩個以上的多載版本。</span><span class="sxs-lookup"><span data-stu-id="47d15-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="47d15-118">例如，如果有兩個選擇性參數，而且呼叫程式碼可以單獨提供或省略彼此，則您需要四個多載版本，每個可能的提供引數組合一個。</span><span class="sxs-lookup"><span data-stu-id="47d15-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="47d15-119">當選擇性參數數目增加時，多載的複雜度會增加。</span><span class="sxs-lookup"><span data-stu-id="47d15-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="47d15-120">除非提供的引數組合無法接受，否則針對 N 個選擇性參數，您需要 2 ^ N 個多載版本。</span><span class="sxs-lookup"><span data-stu-id="47d15-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="47d15-121">視程式的本質而定，您可能會發現邏輯的清楚，是要定義所有多載版本的額外工作。</span><span class="sxs-lookup"><span data-stu-id="47d15-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="47d15-122">若要多載接受一個以上選用參數的程式</span><span class="sxs-lookup"><span data-stu-id="47d15-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1. <span data-ttu-id="47d15-123">判斷程式邏輯可以接受哪些提供的選擇性引數組合。</span><span class="sxs-lookup"><span data-stu-id="47d15-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="47d15-124">如果一個選擇性參數相依于另一個，則可能會發生無法接受的組合。</span><span class="sxs-lookup"><span data-stu-id="47d15-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="47d15-125">例如，如果一個參數接受個人名稱，另一個則接受該人員的年齡，則提供年齡但省略名稱的引數組合就無法接受。</span><span class="sxs-lookup"><span data-stu-id="47d15-125">For example, if one parameter accepts a person's name and another accepts the person's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2. <span data-ttu-id="47d15-126">針對所提供之選擇性引數的每個可接受組合，撰寫定義對應參數清單的 `Sub` 或 `Function` 宣告語句。</span><span class="sxs-lookup"><span data-stu-id="47d15-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="47d15-127">請勿使用 `Optional` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="47d15-127">Do not use the `Optional` keyword.</span></span>  
  
3. <span data-ttu-id="47d15-128">在每個宣告中，在 `Sub` 或 `Function` 關鍵字之前加上[Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="47d15-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4. <span data-ttu-id="47d15-129">遵循每個宣告，撰寫呼叫程式碼提供對應至該宣告之參數清單的引數清單時，應執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="47d15-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5. <span data-ttu-id="47d15-130">視需要使用 `End Sub` 或 `End Function` 語句來終止每個程式。</span><span class="sxs-lookup"><span data-stu-id="47d15-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d15-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="47d15-131">See also</span></span>

- [<span data-ttu-id="47d15-132">程序</span><span class="sxs-lookup"><span data-stu-id="47d15-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="47d15-133">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="47d15-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="47d15-134">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="47d15-134">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="47d15-135">參數陣列</span><span class="sxs-lookup"><span data-stu-id="47d15-135">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="47d15-136">程序多載化</span><span class="sxs-lookup"><span data-stu-id="47d15-136">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="47d15-137">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="47d15-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="47d15-138">如何：定義程序的多個版本</span><span class="sxs-lookup"><span data-stu-id="47d15-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="47d15-139">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="47d15-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="47d15-140">如何：多載使用不確定參數數目的程序</span><span class="sxs-lookup"><span data-stu-id="47d15-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="47d15-141">多載解析</span><span class="sxs-lookup"><span data-stu-id="47d15-141">Overload Resolution</span></span>](./overload-resolution.md)
