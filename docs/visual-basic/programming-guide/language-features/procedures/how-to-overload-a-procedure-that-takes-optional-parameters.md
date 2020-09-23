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
ms.openlocfilehash: 78ca6b2b95dfd5a7f208e5251f08dfccc5514946
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071517"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="b2641-102">如何：多載使用選擇性參數的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2641-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>

<span data-ttu-id="b2641-103">如果程式有一或多個 [選擇性](../../../language-reference/modifiers/optional.md) 參數，您就無法定義符合其任何隱含多載的多載版本。</span><span class="sxs-lookup"><span data-stu-id="b2641-103">If a procedure has one or more [Optional](../../../language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="b2641-104">如需詳細資訊，請參閱多載 [程式的考慮](./considerations-in-overloading-procedures.md)中的「選擇性參數的隱含多載」。</span><span class="sxs-lookup"><span data-stu-id="b2641-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="b2641-105">一個選擇性參數</span><span class="sxs-lookup"><span data-stu-id="b2641-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="b2641-106">若要多載採用一個選擇性參數的程式</span><span class="sxs-lookup"><span data-stu-id="b2641-106">To overload a procedure that takes one optional parameter</span></span>  
  
1. <span data-ttu-id="b2641-107">`Sub` `Function` 在參數清單中撰寫包含選擇性參數的或宣告語句。</span><span class="sxs-lookup"><span data-stu-id="b2641-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="b2641-108">請勿 `Optional` 在這個多載版本中使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b2641-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2. <span data-ttu-id="b2641-109">在或關鍵字之前加上 `Sub` `Function` [Overloads](../../../language-reference/modifiers/overloads.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b2641-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3. <span data-ttu-id="b2641-110">撰寫呼叫程式碼提供選擇性引數時應執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b2641-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4. <span data-ttu-id="b2641-111">`End Sub` `End Function` 適當地使用或語句來終止程式。</span><span class="sxs-lookup"><span data-stu-id="b2641-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5. <span data-ttu-id="b2641-112">撰寫與第一個宣告相同的第二個宣告語句，不同之處在于它不包含參數清單中的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="b2641-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6. <span data-ttu-id="b2641-113">撰寫當呼叫程式碼未提供選擇性引數時，應執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b2641-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="b2641-114">`End Sub` `End Function` 適當地使用或語句來終止程式。</span><span class="sxs-lookup"><span data-stu-id="b2641-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="b2641-115">下列範例顯示以選擇性參數定義的程式、一組對等的兩個多載程式，以及最後一個無效和有效多載版本的範例。</span><span class="sxs-lookup"><span data-stu-id="b2641-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="b2641-116">多個選擇性參數</span><span class="sxs-lookup"><span data-stu-id="b2641-116">Multiple Optional Parameters</span></span>  

 <span data-ttu-id="b2641-117">針對具有多個選擇性參數的程式，您通常需要兩個以上的多載版本。</span><span class="sxs-lookup"><span data-stu-id="b2641-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="b2641-118">例如，如果有兩個選擇性的參數，而且呼叫程式碼可以獨立提供或省略彼此，您需要四個多載版本，每一個提供的引數組合各有一個。</span><span class="sxs-lookup"><span data-stu-id="b2641-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="b2641-119">當選擇性參數的數目增加時，多載的複雜度會增加。</span><span class="sxs-lookup"><span data-stu-id="b2641-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="b2641-120">除非無法接受提供的引數組合，否則您需要 2 ^ N 個多載版本的 N 個選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="b2641-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="b2641-121">視程式的本質而定，您可能會發現邏輯清楚地表示定義所有多載版本的額外工作。</span><span class="sxs-lookup"><span data-stu-id="b2641-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="b2641-122">若要多載採用多個選擇性參數的程式</span><span class="sxs-lookup"><span data-stu-id="b2641-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1. <span data-ttu-id="b2641-123">判斷程式的邏輯可接受哪些提供的選擇性引數組合。</span><span class="sxs-lookup"><span data-stu-id="b2641-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="b2641-124">如果有一個選擇性參數相依于另一個參數，則可能會發生無法接受的組合。</span><span class="sxs-lookup"><span data-stu-id="b2641-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="b2641-125">例如，如果某個參數接受人員的名稱，而另一個接受該人的年齡，則提供年齡但省略名稱的引數組合是無法接受的。</span><span class="sxs-lookup"><span data-stu-id="b2641-125">For example, if one parameter accepts a person's name and another accepts the person's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2. <span data-ttu-id="b2641-126">針對每個可接受的選擇性引數組合， `Sub` 撰寫 `Function` 定義對應參數清單的或宣告語句。</span><span class="sxs-lookup"><span data-stu-id="b2641-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="b2641-127">請勿使用 `Optional` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b2641-127">Do not use the `Optional` keyword.</span></span>  
  
3. <span data-ttu-id="b2641-128">在每個宣告中，在或關鍵字之前加上 `Sub` `Function` [Overloads](../../../language-reference/modifiers/overloads.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b2641-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4. <span data-ttu-id="b2641-129">在每個宣告之後，撰寫呼叫程式碼提供對應至該宣告之參數清單的引數清單時，應執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b2641-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5. <span data-ttu-id="b2641-130">`End Sub`適當地使用或語句來終止每個程式 `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="b2641-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2641-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2641-131">See also</span></span>

- [<span data-ttu-id="b2641-132">程序</span><span class="sxs-lookup"><span data-stu-id="b2641-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="b2641-133">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="b2641-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b2641-134">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="b2641-134">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="b2641-135">參數陣列</span><span class="sxs-lookup"><span data-stu-id="b2641-135">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="b2641-136">程序多載化</span><span class="sxs-lookup"><span data-stu-id="b2641-136">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="b2641-137">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="b2641-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="b2641-138">如何：定義程序的多個版本</span><span class="sxs-lookup"><span data-stu-id="b2641-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="b2641-139">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="b2641-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="b2641-140">如何：多載使用不確定參數數目的程序</span><span class="sxs-lookup"><span data-stu-id="b2641-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="b2641-141">多載解析</span><span class="sxs-lookup"><span data-stu-id="b2641-141">Overload Resolution</span></span>](./overload-resolution.md)
