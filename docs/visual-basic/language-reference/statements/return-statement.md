---
title: Return 陳述式 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b66d16a249164b8989f05f10c785b97055bfde9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="9ec9d-102">Return 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ec9d-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="9ec9d-103">控制權傳回給呼叫的程式碼`Function`， `Sub`， `Get`， `Set`，或`Operator`程序。</span><span class="sxs-lookup"><span data-stu-id="9ec9d-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec9d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9ec9d-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="9ec9d-105">組件</span><span class="sxs-lookup"><span data-stu-id="9ec9d-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="9ec9d-106">中需要`Function`， `Get`，或`Operator`程序。</span><span class="sxs-lookup"><span data-stu-id="9ec9d-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="9ec9d-107">表示要傳回給呼叫程式碼的值運算式。</span><span class="sxs-lookup"><span data-stu-id="9ec9d-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ec9d-108">備註</span><span class="sxs-lookup"><span data-stu-id="9ec9d-108">Remarks</span></span>  
 <span data-ttu-id="9ec9d-109">在`Sub`或`Set`程序，`Return`陳述式相當於`Exit Sub`或`Exit Property`陳述式，和`expression`不可提供。</span><span class="sxs-lookup"><span data-stu-id="9ec9d-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="9ec9d-110">在`Function`， `Get`，或`Operator`程序，`Return`陳述式必須包含`expression`，和`expression`必須評估為可轉換成程序的傳回類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="9ec9d-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="9ec9d-111">在`Function`或`Get`程序中，您也可以選擇將運算式指派給要做為傳回值，程序名稱，然後執行`Exit Function`或`Exit Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9ec9d-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="9ec9d-112">在`Operator`程序中，您必須使用`Return``expression`。</span><span class="sxs-lookup"><span data-stu-id="9ec9d-112">In an `Operator` procedure, you must use `Return``expression`.</span></span>  
  
 <span data-ttu-id="9ec9d-113">您可以包含最大數量`Return`視需要在相同的程序的陳述式。</span><span class="sxs-lookup"><span data-stu-id="9ec9d-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ec9d-114">中的程式碼`Finally`區塊會執行`Return`陳述式中的`Try`或`Catch`區塊是發生，但之前會先`Return`陳述式會執行。</span><span class="sxs-lookup"><span data-stu-id="9ec9d-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="9ec9d-115">A`Return`陳述式不能包含在`Finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="9ec9d-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ec9d-116">範例</span><span class="sxs-lookup"><span data-stu-id="9ec9d-116">Example</span></span>  
 <span data-ttu-id="9ec9d-117">下列範例會使用`Return`陳述式時不需要進行其他任何處理程序傳回至呼叫的程式碼數次。</span><span class="sxs-lookup"><span data-stu-id="9ec9d-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9ec9d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ec9d-118">See Also</span></span>  
 [<span data-ttu-id="9ec9d-119">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ec9d-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="9ec9d-120">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ec9d-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="9ec9d-121">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ec9d-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="9ec9d-122">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ec9d-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="9ec9d-123">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ec9d-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="9ec9d-124">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ec9d-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="9ec9d-125">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ec9d-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="9ec9d-126">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ec9d-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
