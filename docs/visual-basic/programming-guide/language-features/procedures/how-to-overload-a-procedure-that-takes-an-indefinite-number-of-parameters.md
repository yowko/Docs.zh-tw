---
title: HOW TO：多載不定數目參數 (Visual Basic) 的程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 54a8a65db6e1f532cd21e36eeb5b98670efd4289
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506386"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="395e9-102">HOW TO：多載不定數目參數 (Visual Basic) 的程序</span><span class="sxs-lookup"><span data-stu-id="395e9-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="395e9-103">如果程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，您不能定義採用的參數陣列的一維陣列的多載的版本。</span><span class="sxs-lookup"><span data-stu-id="395e9-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="395e9-104">如需詳細資訊，請參閱 「 隱含多載的參數陣列參數 」 中[多載化程序中的考量](./considerations-in-overloading-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="395e9-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="395e9-105">若要多載接受各種數目參數的程序</span><span class="sxs-lookup"><span data-stu-id="395e9-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1.  <span data-ttu-id="395e9-106">確認此程序與呼叫程式碼邏輯方面，從多載版本，從多個`ParamArray`參數。</span><span class="sxs-lookup"><span data-stu-id="395e9-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="395e9-107">請參閱中的 < 多載和參數陣列 >[多載化程序的考量](./considerations-in-overloading-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="395e9-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2.  <span data-ttu-id="395e9-108">判斷程序應該接受的提供值的數字中變數參數清單的一部分。</span><span class="sxs-lookup"><span data-stu-id="395e9-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="395e9-109">這可能包括的任何值，大小寫，且它可能包含單一的一維陣列的大小寫。</span><span class="sxs-lookup"><span data-stu-id="395e9-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3.  <span data-ttu-id="395e9-110">針對每個可接受提供的值數目，撰寫`Sub`或`Function`定義對應的參數清單的宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="395e9-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="395e9-111">請勿使用`Optional`或`ParamArray`在這個多載的版本中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="395e9-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4.  <span data-ttu-id="395e9-112">在每個宣告中，在前面`Sub`或是`Function`關鍵字搭配[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="395e9-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5.  <span data-ttu-id="395e9-113">下列每個宣告中，撰寫呼叫程式碼提供與該宣告的參數清單的對應值時執行的程序程式碼。</span><span class="sxs-lookup"><span data-stu-id="395e9-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6.  <span data-ttu-id="395e9-114">終止與每個程序`End Sub`或`End Function`適當的陳述式。</span><span class="sxs-lookup"><span data-stu-id="395e9-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="395e9-115">範例</span><span class="sxs-lookup"><span data-stu-id="395e9-115">Example</span></span>  
 <span data-ttu-id="395e9-116">下列範例示範使用定義的程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，然後按一下 對等一組多載程序。</span><span class="sxs-lookup"><span data-stu-id="395e9-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 <span data-ttu-id="395e9-117">您無法多載會採用參數陣列的一維陣列的參數清單的這類的程序。</span><span class="sxs-lookup"><span data-stu-id="395e9-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="395e9-118">不過，您可以使用其他隱含的多載的簽章。</span><span class="sxs-lookup"><span data-stu-id="395e9-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="395e9-119">下列宣告將說明這點。</span><span class="sxs-lookup"><span data-stu-id="395e9-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 <span data-ttu-id="395e9-120">若要測試是否呼叫程式碼提供一個或多個值並沒有多載的版本中的程式碼`ParamArray`參數，或如果是的話，多少。</span><span class="sxs-lookup"><span data-stu-id="395e9-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="395e9-121">Visual Basic 會將控制項傳遞至比對呼叫的引數清單的版本。</span><span class="sxs-lookup"><span data-stu-id="395e9-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="395e9-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="395e9-122">Compiling the Code</span></span>  
 <span data-ttu-id="395e9-123">因為程序時使用`ParamArray`參數相當於一組多載版本，您無法多載，這樣的程序對應到任何這些隱含的多載的參數清單。</span><span class="sxs-lookup"><span data-stu-id="395e9-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="395e9-124">如需詳細資訊，請參閱 <<c0> [ 多載化程序中的考量](./considerations-in-overloading-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="395e9-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="395e9-125">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="395e9-125">.NET Framework Security</span></span>  
 <span data-ttu-id="395e9-126">每當您處理陣列，其中可能會無限期地大，會有風險的造成滿溢內部應用程式的容量。</span><span class="sxs-lookup"><span data-stu-id="395e9-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="395e9-127">如果您接受參數陣列時，您應該測試呼叫程式碼傳遞給它，陣列的長度，並採取適當的步驟，如果它是對您的應用程式而言太大。</span><span class="sxs-lookup"><span data-stu-id="395e9-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395e9-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="395e9-128">See also</span></span>
- [<span data-ttu-id="395e9-129">程序</span><span class="sxs-lookup"><span data-stu-id="395e9-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="395e9-130">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="395e9-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="395e9-131">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="395e9-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="395e9-132">參數陣列</span><span class="sxs-lookup"><span data-stu-id="395e9-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="395e9-133">程序多載化</span><span class="sxs-lookup"><span data-stu-id="395e9-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="395e9-134">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="395e9-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="395e9-135">如何：定義多個版本的程序</span><span class="sxs-lookup"><span data-stu-id="395e9-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="395e9-136">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="395e9-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="395e9-137">如何：多載會採用選擇性參數的程序</span><span class="sxs-lookup"><span data-stu-id="395e9-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="395e9-138">多載解析</span><span class="sxs-lookup"><span data-stu-id="395e9-138">Overload Resolution</span></span>](./overload-resolution.md)
