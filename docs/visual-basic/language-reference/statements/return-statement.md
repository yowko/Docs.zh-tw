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
ms.openlocfilehash: af49ea95d7f9d01072190ac3ccf6ba2f1041347e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957666"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="72e4f-102">Return 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72e4f-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="72e4f-103">將控制權傳回給呼叫`Function` `Get`、 `Sub` `Set`、、或`Operator`程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="72e4f-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72e4f-104">語法</span><span class="sxs-lookup"><span data-stu-id="72e4f-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="72e4f-105">組件</span><span class="sxs-lookup"><span data-stu-id="72e4f-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="72e4f-106">在、 `Function` `Get`或程式中是必要的。`Operator`</span><span class="sxs-lookup"><span data-stu-id="72e4f-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="72e4f-107">運算式, 表示要傳回給呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="72e4f-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72e4f-108">備註</span><span class="sxs-lookup"><span data-stu-id="72e4f-108">Remarks</span></span>  
 <span data-ttu-id="72e4f-109">`Return` `Exit Property` `expression`在或程式`Set` 中,語句相當於或語句,而且不得提供`Exit Sub`。 `Sub`</span><span class="sxs-lookup"><span data-stu-id="72e4f-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="72e4f-110">`expression` `expression`在、或程式`Operator`中,`Return`語句必須包含, 而且必須評估為可轉換成程式之傳回類型的資料類型。 `Get` `Function`</span><span class="sxs-lookup"><span data-stu-id="72e4f-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="72e4f-111">`Exit Function` `Exit Property`在或程式`Get`中, 您也可以選擇將運算式指派給程式名稱, 以做為傳回值, 然後執行或語句。 `Function`</span><span class="sxs-lookup"><span data-stu-id="72e4f-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="72e4f-112">在程式`Operator`中, 您必須使用`Return expression`。</span><span class="sxs-lookup"><span data-stu-id="72e4f-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="72e4f-113">在相同的程式中`Return` , 您可以包含多個適當的語句。</span><span class="sxs-lookup"><span data-stu-id="72e4f-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72e4f-114">`Finally`區塊中的程式碼會在遇到`Return` `Try`或`Catch`區塊中的語句之後, 但在該`Return`語句執行之前執行。</span><span class="sxs-lookup"><span data-stu-id="72e4f-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="72e4f-115">語句不能包含`Finally`在區塊中。 `Return`</span><span class="sxs-lookup"><span data-stu-id="72e4f-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72e4f-116">範例</span><span class="sxs-lookup"><span data-stu-id="72e4f-116">Example</span></span>  
 <span data-ttu-id="72e4f-117">下列範例會使用`Return`語句數次, 以在程式不需要執行任何動作時返回呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="72e4f-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="72e4f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72e4f-118">See also</span></span>

- [<span data-ttu-id="72e4f-119">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="72e4f-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="72e4f-120">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="72e4f-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="72e4f-121">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="72e4f-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="72e4f-122">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="72e4f-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="72e4f-123">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="72e4f-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="72e4f-124">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="72e4f-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="72e4f-125">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="72e4f-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="72e4f-126">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="72e4f-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
