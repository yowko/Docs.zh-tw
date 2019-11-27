---
title: 如何：防止程序引數的值變更
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: 36092eb597b5b20e1da42cd9d15ab8633636cfb1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344851"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="ea4cd-102">如何：防止程序引數的值變更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea4cd-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>
<span data-ttu-id="ea4cd-103">如果程式將參數宣告為[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 會提供程式碼直接參考呼叫程式碼中引數的基礎程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-103">If a procedure declares a parameter as [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="ea4cd-104">這允許程式變更呼叫程式碼中引數的基礎值。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="ea4cd-105">在某些情況下，呼叫程式碼可能會想要防止這類變更。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="ea4cd-106">您隨時可以在程式中宣告對應的參數[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ，藉此保護引數的變更。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="ea4cd-107">如果您想要在某些情況下變更指定的引數，而不是其他情況，則可以將它宣告 `ByRef` 並讓呼叫程式碼判斷每次呼叫中的傳遞機制。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="ea4cd-108">其執行方式是將對應的引數括在括弧中，以傳值方式傳遞它，或不將其括在括弧中以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="ea4cd-109">如需詳細資訊，請參閱[如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea4cd-110">範例</span><span class="sxs-lookup"><span data-stu-id="ea4cd-110">Example</span></span>  
 <span data-ttu-id="ea4cd-111">下列範例顯示兩個採用陣列變數並在其專案上操作的程式。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="ea4cd-112">`increase` 程式只會將一個專案新增至每個元素。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="ea4cd-113">`replace` 程式會將新的陣列指派給參數 `a()`，然後將其中一個加入至每個元素。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="ea4cd-114">不過，重新指派並不會影響呼叫程式碼中的基礎陣列變數。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="ea4cd-115">第一個 `MsgBox` 呼叫會顯示「增加後（n）：11，21，31，41」。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-115">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="ea4cd-116">因為陣列 `n` 是參考型別，所以 `increase` 可以變更其成員，即使傳遞機制 `ByVal`也一樣。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-116">Because the array `n` is a reference type, `increase` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="ea4cd-117">第二個 `MsgBox` 呼叫會顯示「取代後（n）：11，21，31，41」。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-117">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="ea4cd-118">因為 `ByVal`傳遞 `n`，所以 `replace` 無法藉由指派新的陣列來修改呼叫程式碼中 `n` 的變數。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-118">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="ea4cd-119">當 `replace` 建立新的陣列實例 `k`，並將它指派給本機變數 `a`時，就會失去呼叫程式碼所傳入之 `n` 的參考。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-119">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="ea4cd-120">當它變更 `a`的成員時，只有本機陣列 `k` 會受到影響。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-120">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="ea4cd-121">因此，`replace` 不會在呼叫程式碼中增加陣列 `n` 的值。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-121">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ea4cd-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ea4cd-122">Compiling the Code</span></span>  
 <span data-ttu-id="ea4cd-123">Visual Basic 中的預設值是以傳值方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-123">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="ea4cd-124">不過，在每個宣告的參數中包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字是很好的程式設計作法。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-124">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="ea4cd-125">這可讓您的程式碼更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="ea4cd-125">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea4cd-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea4cd-126">See also</span></span>

- [<span data-ttu-id="ea4cd-127">程序</span><span class="sxs-lookup"><span data-stu-id="ea4cd-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ea4cd-128">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="ea4cd-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ea4cd-129">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="ea4cd-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="ea4cd-130">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="ea4cd-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="ea4cd-131">可修改引數和不可修改引數之間的差異</span><span class="sxs-lookup"><span data-stu-id="ea4cd-131">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="ea4cd-132">以傳值或傳址方式傳遞引數的差別</span><span class="sxs-lookup"><span data-stu-id="ea4cd-132">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="ea4cd-133">如何：變更程序引數的值</span><span class="sxs-lookup"><span data-stu-id="ea4cd-133">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="ea4cd-134">如何：強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="ea4cd-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="ea4cd-135">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="ea4cd-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="ea4cd-136">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="ea4cd-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
