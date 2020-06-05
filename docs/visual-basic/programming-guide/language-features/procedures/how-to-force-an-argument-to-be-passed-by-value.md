---
title: 如何：強制以傳值方式傳遞引數
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 48f7d7afebd76916cba11459532d89d71871c79b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387960"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="7fa44-102">如何：強制以傳值方式傳遞引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fa44-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="7fa44-103">程式宣告會決定傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="7fa44-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="7fa44-104">如果參數宣告為[ByRef](../../../language-reference/modifiers/byref.md)，Visual Basic 預期會以傳址方式傳遞對應的引數。</span><span class="sxs-lookup"><span data-stu-id="7fa44-104">If a parameter is declared [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="7fa44-105">這可讓程式變更呼叫程式碼中引數的基礎程式設計項目的值。</span><span class="sxs-lookup"><span data-stu-id="7fa44-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="7fa44-106">如果您想要保護基礎元素不受這類變更的限制，您可以將 `ByRef` 引數名稱括在括弧中，以覆寫程序呼叫中的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="7fa44-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="7fa44-107">這些括弧除了括住呼叫中引數清單的括弧之外。</span><span class="sxs-lookup"><span data-stu-id="7fa44-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="7fa44-108">呼叫程式碼無法覆寫[ByVal](../../../language-reference/modifiers/byval.md)機制。</span><span class="sxs-lookup"><span data-stu-id="7fa44-108">The calling code cannot override a [ByVal](../../../language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="7fa44-109">強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="7fa44-109">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="7fa44-110">如果在程式中宣告對應的參數 `ByVal` ，您就不需要採取任何額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="7fa44-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="7fa44-111">Visual Basic 已經預期會以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="7fa44-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="7fa44-112">如果在程式中宣告對應的參數 `ByRef` ，請在程序呼叫的括弧中括住引數。</span><span class="sxs-lookup"><span data-stu-id="7fa44-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fa44-113">範例</span><span class="sxs-lookup"><span data-stu-id="7fa44-113">Example</span></span>  
 <span data-ttu-id="7fa44-114">下列範例會覆寫 `ByRef` 參數宣告。</span><span class="sxs-lookup"><span data-stu-id="7fa44-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="7fa44-115">在強制的呼叫中 `ByVal` ，請注意兩個層級的括弧。</span><span class="sxs-lookup"><span data-stu-id="7fa44-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="7fa44-116">當 `str` 以引數清單內的額外括弧括住時，程式 `setNewString` 無法在呼叫程式碼中變更其值，而且會 `MsgBox` 顯示「如果傳遞 ByVal 則無法取代」。</span><span class="sxs-lookup"><span data-stu-id="7fa44-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="7fa44-117">當不 `str` 是以多餘的括弧括住時，程式可以變更它，並 `MsgBox` 顯示「這是 inString 引數的新值」。</span><span class="sxs-lookup"><span data-stu-id="7fa44-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="7fa44-118">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="7fa44-118">Compile the code</span></span>  
 <span data-ttu-id="7fa44-119">當您以傳址方式傳遞變數時，您必須使用 `ByRef` 關鍵字來指定這項機制。</span><span class="sxs-lookup"><span data-stu-id="7fa44-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="7fa44-120">Visual Basic 中的預設值是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="7fa44-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="7fa44-121">不過，在每個宣告的參數中包含[ByVal](../../../language-reference/modifiers/byval.md)或[ByRef](../../../language-reference/modifiers/byref.md)關鍵字是很好的程式設計作法。</span><span class="sxs-lookup"><span data-stu-id="7fa44-121">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="7fa44-122">這可讓您的程式碼更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="7fa44-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7fa44-123">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="7fa44-123">Robust Programming</span></span>  
 <span data-ttu-id="7fa44-124">如果程式宣告參數[ByRef](../../../language-reference/modifiers/byref.md)，程式碼的正確執行可能取決於能夠變更呼叫程式碼中的基礎元素。</span><span class="sxs-lookup"><span data-stu-id="7fa44-124">If a procedure declares a parameter [ByRef](../../../language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="7fa44-125">如果呼叫程式碼會藉由在括弧中括住引數來覆寫此呼叫機制，或如果它傳遞不可修改的引數，此程式就無法變更基礎元素。</span><span class="sxs-lookup"><span data-stu-id="7fa44-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="7fa44-126">這可能會在呼叫程式碼中產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="7fa44-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7fa44-127">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="7fa44-127">.NET Framework Security</span></span>  
 <span data-ttu-id="7fa44-128">允許程式變更呼叫程式碼中引數的基礎值，一律會有潛在的風險。</span><span class="sxs-lookup"><span data-stu-id="7fa44-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="7fa44-129">請確定您預期會變更此值，並在使用它之前準備好檢查其有效性。</span><span class="sxs-lookup"><span data-stu-id="7fa44-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa44-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fa44-130">See also</span></span>

- [<span data-ttu-id="7fa44-131">程序</span><span class="sxs-lookup"><span data-stu-id="7fa44-131">Procedures</span></span>](./index.md)
- [<span data-ttu-id="7fa44-132">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="7fa44-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="7fa44-133">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="7fa44-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="7fa44-134">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="7fa44-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="7fa44-135">可修改引數和不可修改引數之間的差異</span><span class="sxs-lookup"><span data-stu-id="7fa44-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="7fa44-136">以傳值或傳址方式傳遞引數的差別</span><span class="sxs-lookup"><span data-stu-id="7fa44-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="7fa44-137">如何：變更程序引數的值</span><span class="sxs-lookup"><span data-stu-id="7fa44-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="7fa44-138">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="7fa44-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="7fa44-139">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="7fa44-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="7fa44-140">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="7fa44-140">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
