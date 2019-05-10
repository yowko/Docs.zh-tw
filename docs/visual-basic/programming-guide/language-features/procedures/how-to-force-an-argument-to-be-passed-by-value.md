---
title: HOW TO：強制以傳值 (Visual Basic) 的引數
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
ms.openlocfilehash: 540271c414ac295c419533a4622657d60d123796
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665387"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="47af9-102">HOW TO：強制以傳值 (Visual Basic) 的引數</span><span class="sxs-lookup"><span data-stu-id="47af9-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="47af9-103">程序宣告判斷傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="47af9-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="47af9-104">如果參數宣告[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 需要以傳址方式傳遞相對應的引數。</span><span class="sxs-lookup"><span data-stu-id="47af9-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="47af9-105">這可讓程序來變更基礎呼叫程式碼中的引數的程式設計項目值。</span><span class="sxs-lookup"><span data-stu-id="47af9-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="47af9-106">如果您想要保護對這類變更的基礎項目，您可以覆寫`ByRef`程序中的傳遞機制來呼叫以括弧括住的引數名稱。</span><span class="sxs-lookup"><span data-stu-id="47af9-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="47af9-107">這些括號是以呼叫括住的引數清單的括號。</span><span class="sxs-lookup"><span data-stu-id="47af9-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="47af9-108">呼叫端程式碼無法覆寫[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)機制。</span><span class="sxs-lookup"><span data-stu-id="47af9-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="47af9-109">若要強制以傳值方式傳遞的引數</span><span class="sxs-lookup"><span data-stu-id="47af9-109">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="47af9-110">如果對應的參數宣告`ByVal`在程序中，您不需要採取任何額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="47af9-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="47af9-111">Visual Basic 已經需要以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="47af9-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="47af9-112">如果對應的參數宣告`ByRef`在程序中，括住的程序呼叫中的括號括住的引數。</span><span class="sxs-lookup"><span data-stu-id="47af9-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47af9-113">範例</span><span class="sxs-lookup"><span data-stu-id="47af9-113">Example</span></span>  
 <span data-ttu-id="47af9-114">下列範例會覆寫`ByRef`參數宣告。</span><span class="sxs-lookup"><span data-stu-id="47af9-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="47af9-115">會強制呼叫中`ByVal`，請注意括號內的兩個層級。</span><span class="sxs-lookup"><span data-stu-id="47af9-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="47af9-116">當`str`額外引數清單中中的括號括住`setNewString`程序不能變更呼叫程式碼，其值和`MsgBox`顯示如果傳遞 ByVal 無法取代 「 」。</span><span class="sxs-lookup"><span data-stu-id="47af9-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="47af9-117">當`str`未隨附在額外的括號中的程序可以將它變更，和`MsgBox`顯示"This is inString 引數的新值"。</span><span class="sxs-lookup"><span data-stu-id="47af9-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="47af9-118">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="47af9-118">Compiling the Code</span></span>  
 <span data-ttu-id="47af9-119">當您參考所傳遞的變數時，您必須使用`ByRef`關鍵字來指定這項機制。</span><span class="sxs-lookup"><span data-stu-id="47af9-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="47af9-120">在 Visual Basic 中的預設值是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="47af9-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="47af9-121">不過，它是良好的程式設計方式來包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或是[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。</span><span class="sxs-lookup"><span data-stu-id="47af9-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="47af9-122">這可讓您的程式碼更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="47af9-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="47af9-123">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="47af9-123">Robust Programming</span></span>  
 <span data-ttu-id="47af9-124">如果程序宣告的參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，正確執行的程式碼可能會因無法變更呼叫程式碼對應的項目而定。</span><span class="sxs-lookup"><span data-stu-id="47af9-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="47af9-125">呼叫程式碼覆寫此呼叫的機制，藉由將引數括在括號內，則它會傳遞為不可修改引數，此程序就無法變更基礎的項目。</span><span class="sxs-lookup"><span data-stu-id="47af9-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="47af9-126">這可能會產生非預期的結果，在呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="47af9-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="47af9-127">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="47af9-127">.NET Framework Security</span></span>  
 <span data-ttu-id="47af9-128">允許的程序來變更基礎呼叫程式碼中的引數的值中一律會有潛在的風險。</span><span class="sxs-lookup"><span data-stu-id="47af9-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="47af9-129">請確定您預期此值變更，並準備好使用之前，先將這些資料檢查有效性。</span><span class="sxs-lookup"><span data-stu-id="47af9-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47af9-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47af9-130">See also</span></span>

- [<span data-ttu-id="47af9-131">程序</span><span class="sxs-lookup"><span data-stu-id="47af9-131">Procedures</span></span>](./index.md)
- [<span data-ttu-id="47af9-132">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="47af9-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="47af9-133">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="47af9-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="47af9-134">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="47af9-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="47af9-135">可修改引數和不可修改引數之間的差異</span><span class="sxs-lookup"><span data-stu-id="47af9-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="47af9-136">以傳值或傳址方式傳遞引數的差別</span><span class="sxs-lookup"><span data-stu-id="47af9-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="47af9-137">如何：程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="47af9-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="47af9-138">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="47af9-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="47af9-139">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="47af9-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="47af9-140">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="47af9-140">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
