---
title: 如何：多載使用不確定參數數目的程序
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
ms.openlocfilehash: 94f12b4cc6cb35864fefbb3b5bb1378bec5e974c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347557"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="650d6-102">如何：多載使用不定數目參數的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="650d6-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="650d6-103">如果程式具有[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，您就無法為參數陣列定義接受一維陣列的多載版本。</span><span class="sxs-lookup"><span data-stu-id="650d6-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="650d6-104">如需詳細資訊，請參閱多載[程式的考慮](./considerations-in-overloading-procedures.md)中的「ParamArray 參數的隱含多載」。</span><span class="sxs-lookup"><span data-stu-id="650d6-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="650d6-105">若要多載採用可變數目參數的程式</span><span class="sxs-lookup"><span data-stu-id="650d6-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="650d6-106">確定程式和呼叫程式碼邏輯受益于多載版本，而不是從 `ParamArray` 參數。</span><span class="sxs-lookup"><span data-stu-id="650d6-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="650d6-107">請參閱多載[程式的考慮](./considerations-in-overloading-procedures.md)中的「多載和 ParamArrays」。</span><span class="sxs-lookup"><span data-stu-id="650d6-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="650d6-108">判斷程式應在參數清單的變數部分中接受的提供值數目。</span><span class="sxs-lookup"><span data-stu-id="650d6-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="650d6-109">這可能包括不含任何值的案例，而且可能包含單一一維陣列的大小寫。</span><span class="sxs-lookup"><span data-stu-id="650d6-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="650d6-110">針對每個可接受的提供值數目，撰寫定義對應參數清單的 `Sub` 或 `Function` 宣告語句。</span><span class="sxs-lookup"><span data-stu-id="650d6-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="650d6-111">請勿在此多載的版本中使用 `Optional` 或 `ParamArray` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="650d6-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="650d6-112">在每個宣告中，在 `Sub` 或 `Function` 關鍵字之前加上[Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="650d6-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="650d6-113">在每個宣告後面，撰寫呼叫程式碼提供對應至該宣告之參數清單的值時，應執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="650d6-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="650d6-114">視需要使用 `End Sub` 或 `End Function` 語句來終止每個程式。</span><span class="sxs-lookup"><span data-stu-id="650d6-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="650d6-115">範例</span><span class="sxs-lookup"><span data-stu-id="650d6-115">Example</span></span>  
 <span data-ttu-id="650d6-116">下列範例顯示使用[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數定義的程式，然後是一組對等的多載程式。</span><span class="sxs-lookup"><span data-stu-id="650d6-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="650d6-117">您無法使用參數清單來多載這類程式，其中會採用一維陣列做為參數陣列。</span><span class="sxs-lookup"><span data-stu-id="650d6-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="650d6-118">不過，您可以使用其他隱含多載的簽章。</span><span class="sxs-lookup"><span data-stu-id="650d6-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="650d6-119">下列宣告說明這種情況。</span><span class="sxs-lookup"><span data-stu-id="650d6-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="650d6-120">多載版本中的程式碼不需要測試呼叫程式碼是否為 `ParamArray` 參數提供了一或多個值，如果有的話，也不需這麼做。</span><span class="sxs-lookup"><span data-stu-id="650d6-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="650d6-121">Visual Basic 會將控制權傳遞至符合呼叫引數清單的版本。</span><span class="sxs-lookup"><span data-stu-id="650d6-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="650d6-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="650d6-122">Compile the code</span></span>  
 <span data-ttu-id="650d6-123">因為具有 `ParamArray` 參數的程式相當於一組多載版本，所以您無法使用對應至這些隱含多載的參數清單來多載這類程式。</span><span class="sxs-lookup"><span data-stu-id="650d6-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="650d6-124">如需詳細資訊，請參閱多載[程式的考慮](./considerations-in-overloading-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="650d6-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="650d6-125">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="650d6-125">.NET Framework Security</span></span>  
 <span data-ttu-id="650d6-126">當您處理可能會無限大的陣列時，會有 overrunning 應用程式的一些內部容量的風險。</span><span class="sxs-lookup"><span data-stu-id="650d6-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="650d6-127">如果您接受參數陣列，您應該測試呼叫的程式碼傳遞給它的陣列長度，如果對您的應用程式而言太大，則採取適當的步驟。</span><span class="sxs-lookup"><span data-stu-id="650d6-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="650d6-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="650d6-128">See also</span></span>

- [<span data-ttu-id="650d6-129">程序</span><span class="sxs-lookup"><span data-stu-id="650d6-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="650d6-130">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="650d6-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="650d6-131">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="650d6-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="650d6-132">參數陣列</span><span class="sxs-lookup"><span data-stu-id="650d6-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="650d6-133">程序多載化</span><span class="sxs-lookup"><span data-stu-id="650d6-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="650d6-134">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="650d6-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="650d6-135">如何：定義程序的多個版本</span><span class="sxs-lookup"><span data-stu-id="650d6-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="650d6-136">如何：呼叫多載程序</span><span class="sxs-lookup"><span data-stu-id="650d6-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="650d6-137">如何：使用選擇性參數的多載程序</span><span class="sxs-lookup"><span data-stu-id="650d6-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="650d6-138">多載解析</span><span class="sxs-lookup"><span data-stu-id="650d6-138">Overload Resolution</span></span>](./overload-resolution.md)
