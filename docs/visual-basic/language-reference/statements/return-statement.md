---
title: Return 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: fe200add4e29fe4bbe0fdf335dcd94107b8ff1eb
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323320"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="fe016-102">Return 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe016-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="fe016-103">呼叫的程式碼將控制權還給`Function`， `Sub`， `Get`， `Set`，或`Operator`程序。</span><span class="sxs-lookup"><span data-stu-id="fe016-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe016-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe016-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="fe016-105">組件</span><span class="sxs-lookup"><span data-stu-id="fe016-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="fe016-106">在所需`Function`， `Get`，或`Operator`程序。</span><span class="sxs-lookup"><span data-stu-id="fe016-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="fe016-107">運算式，表示要傳回給呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="fe016-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe016-108">備註</span><span class="sxs-lookup"><span data-stu-id="fe016-108">Remarks</span></span>  
 <span data-ttu-id="fe016-109">在 `Sub`或`Set`程序中，`Return`陳述式相當於`Exit Sub`或`Exit Property`陳述式，和`expression`不可提供。</span><span class="sxs-lookup"><span data-stu-id="fe016-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="fe016-110">在  `Function`， `Get`，或`Operator`程序中，`Return`陳述式必須包含`expression`，和`expression`必須評估為可轉換為程序的傳回類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="fe016-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="fe016-111">在 `Function`或是`Get`程序中，您也可以另一種程序名稱，以做為傳回值，指派運算式，然後執行`Exit Function`或`Exit Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="fe016-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="fe016-112">在 `Operator`程序中，您必須使用`Return expression`。</span><span class="sxs-lookup"><span data-stu-id="fe016-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="fe016-113">您可以包含更多`Return`視需要在相同的程序的陳述式。</span><span class="sxs-lookup"><span data-stu-id="fe016-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe016-114">中的程式碼`Finally`區塊會執行`Return`中的陳述式`Try`或`Catch`區塊是發生，但在那之前`Return`陳述式會執行。</span><span class="sxs-lookup"><span data-stu-id="fe016-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="fe016-115">A`Return`陳述式不能包含在`Finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="fe016-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe016-116">範例</span><span class="sxs-lookup"><span data-stu-id="fe016-116">Example</span></span>  
 <span data-ttu-id="fe016-117">下列範例會使用`Return`陳述式時不需要採取任何動作的程序傳回給呼叫程式碼數次。</span><span class="sxs-lookup"><span data-stu-id="fe016-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fe016-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe016-118">See Also</span></span>  
 [<span data-ttu-id="fe016-119">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="fe016-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="fe016-120">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="fe016-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="fe016-121">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="fe016-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="fe016-122">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="fe016-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="fe016-123">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="fe016-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="fe016-124">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="fe016-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="fe016-125">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="fe016-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="fe016-126">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="fe016-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
