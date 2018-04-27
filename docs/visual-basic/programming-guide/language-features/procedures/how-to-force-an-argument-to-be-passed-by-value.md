---
title: 如何：強制以傳值方式傳遞引數 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 30f5e5fe7b9c92f90673dc99a0e299136a38305b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="2bf79-102">如何：強制以傳值方式傳遞引數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2bf79-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="2bf79-103">程序宣告判斷傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="2bf79-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="2bf79-104">如果參數宣告[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 預期依參考傳遞相對應的引數。</span><span class="sxs-lookup"><span data-stu-id="2bf79-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="2bf79-105">這可讓程序來變更呼叫的程式碼中引數的基礎的程式設計項目值。</span><span class="sxs-lookup"><span data-stu-id="2bf79-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="2bf79-106">如果您想要保護對應的項目，針對這類變更，您可以覆寫`ByRef`括弧括住的引數名稱呼叫程序中的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="2bf79-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="2bf79-107">這些括號是封閉的呼叫中引數清單的括號。</span><span class="sxs-lookup"><span data-stu-id="2bf79-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="2bf79-108">呼叫程式碼不能覆寫[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)機制。</span><span class="sxs-lookup"><span data-stu-id="2bf79-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="2bf79-109">若要強制以傳值方式傳遞的引數</span><span class="sxs-lookup"><span data-stu-id="2bf79-109">To force an argument to be passed by value</span></span>  
  
-   <span data-ttu-id="2bf79-110">如果對應的參數宣告`ByVal`在程序，您不需要採取任何額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="2bf79-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="2bf79-111">Visual Basic 已預期傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="2bf79-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
-   <span data-ttu-id="2bf79-112">如果對應的參數宣告`ByRef`在程序，將括在括號中的程序呼叫中引數。</span><span class="sxs-lookup"><span data-stu-id="2bf79-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bf79-113">範例</span><span class="sxs-lookup"><span data-stu-id="2bf79-113">Example</span></span>  
 <span data-ttu-id="2bf79-114">下列範例會覆寫`ByRef`參數宣告。</span><span class="sxs-lookup"><span data-stu-id="2bf79-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="2bf79-115">強制執行的呼叫中`ByVal`，請注意括號內的兩個層級。</span><span class="sxs-lookup"><span data-stu-id="2bf79-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 <span data-ttu-id="2bf79-116">當`str`引數，則清單中的額外括號括住`setNewString`程序不能變更呼叫的程式碼，其值和`MsgBox`顯示如果傳遞 ByVal 無法取代 「 」。</span><span class="sxs-lookup"><span data-stu-id="2bf79-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="2bf79-117">當`str`未加多餘的括號中的程序可以將它變更，並`MsgBox`顯示"This is inString 引數的新值"。</span><span class="sxs-lookup"><span data-stu-id="2bf79-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2bf79-118">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="2bf79-118">Compiling the Code</span></span>  
 <span data-ttu-id="2bf79-119">當您依參考傳遞的變數時，您必須使用`ByRef`關鍵字來指定這項機制。</span><span class="sxs-lookup"><span data-stu-id="2bf79-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="2bf79-120">在 Visual Basic 中的預設值是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="2bf79-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="2bf79-121">不過，它是良好的程式設計作法中包含  [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。</span><span class="sxs-lookup"><span data-stu-id="2bf79-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="2bf79-122">這可讓您的程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="2bf79-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2bf79-123">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="2bf79-123">Robust Programming</span></span>  
 <span data-ttu-id="2bf79-124">如果程序會宣告參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，正確執行的程式碼可能會相依於不能變更呼叫的程式碼中對應的項目。</span><span class="sxs-lookup"><span data-stu-id="2bf79-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="2bf79-125">如果呼叫程式碼覆寫這個呼叫的機制將引數括在括號內，或如果通過不可修改引數，程序不能變更對應的項目。</span><span class="sxs-lookup"><span data-stu-id="2bf79-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="2bf79-126">這可能會產生非預期的結果，呼叫程式碼中。</span><span class="sxs-lookup"><span data-stu-id="2bf79-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2bf79-127">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="2bf79-127">.NET Framework Security</span></span>  
 <span data-ttu-id="2bf79-128">在允許的程序來變更對應的引數呼叫的程式碼中的值一律會有潛在的風險。</span><span class="sxs-lookup"><span data-stu-id="2bf79-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="2bf79-129">請確定您預期此變更，並準備好檢查它的有效性，然後再將它的值。</span><span class="sxs-lookup"><span data-stu-id="2bf79-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf79-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bf79-130">See Also</span></span>  
 [<span data-ttu-id="2bf79-131">程序</span><span class="sxs-lookup"><span data-stu-id="2bf79-131">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="2bf79-132">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="2bf79-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="2bf79-133">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="2bf79-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="2bf79-134">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="2bf79-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="2bf79-135">可修改引數和不可修改引數之間的差異</span><span class="sxs-lookup"><span data-stu-id="2bf79-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="2bf79-136">以傳值或傳址方式傳遞引數的差別</span><span class="sxs-lookup"><span data-stu-id="2bf79-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="2bf79-137">如何：變更程序引數的值</span><span class="sxs-lookup"><span data-stu-id="2bf79-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="2bf79-138">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="2bf79-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="2bf79-139">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="2bf79-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="2bf79-140">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="2bf79-140">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
