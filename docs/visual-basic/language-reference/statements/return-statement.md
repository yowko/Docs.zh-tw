---
title: Return 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: cdb58e32c30c8e6c1662fb698ac5576c3f71258c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404196"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="5af60-102">Return 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5af60-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="5af60-103">將控制權傳回給呼叫、、、或程式的程式碼 `Function` `Sub` `Get` `Set` `Operator` 。</span><span class="sxs-lookup"><span data-stu-id="5af60-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5af60-104">語法</span><span class="sxs-lookup"><span data-stu-id="5af60-104">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="5af60-105">部分</span><span class="sxs-lookup"><span data-stu-id="5af60-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="5af60-106">在、或程式中是必要的 `Function` `Get` `Operator` 。</span><span class="sxs-lookup"><span data-stu-id="5af60-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="5af60-107">運算式，表示要傳回給呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="5af60-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5af60-108">備註</span><span class="sxs-lookup"><span data-stu-id="5af60-108">Remarks</span></span>  
 <span data-ttu-id="5af60-109">在 `Sub` 或 `Set` 程式中， `Return` 語句相當於 `Exit Sub` 或 `Exit Property` 語句，而且 `expression` 不得提供。</span><span class="sxs-lookup"><span data-stu-id="5af60-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="5af60-110">在 `Function` 、 `Get` 或程式中 `Operator` ， `Return` 語句必須包含 `expression` ，而且 `expression` 必須評估為可轉換成程式之傳回類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5af60-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="5af60-111">在或程式中 `Function` `Get` ，您也可以選擇將運算式指派給程式名稱，以做為傳回值，然後執行 `Exit Function` 或 `Exit Property` 語句。</span><span class="sxs-lookup"><span data-stu-id="5af60-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="5af60-112">在程式中 `Operator` ，您必須使用 `Return expression` 。</span><span class="sxs-lookup"><span data-stu-id="5af60-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="5af60-113">在相同的程式中，您可以包含多個 `Return` 適當的語句。</span><span class="sxs-lookup"><span data-stu-id="5af60-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5af60-114">區塊中的 `Finally` `Return` 程式碼會在遇到或區塊中的語句之後 `Try` `Catch` ，但在該 `Return` 語句執行之前執行。</span><span class="sxs-lookup"><span data-stu-id="5af60-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="5af60-115">`Return`語句不能包含在區塊中 `Finally` 。</span><span class="sxs-lookup"><span data-stu-id="5af60-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5af60-116">範例</span><span class="sxs-lookup"><span data-stu-id="5af60-116">Example</span></span>  
 <span data-ttu-id="5af60-117">下列範例 `Return` 會使用語句數次，以在程式不需要執行任何動作時返回呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="5af60-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="5af60-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5af60-118">See also</span></span>

- [<span data-ttu-id="5af60-119">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="5af60-119">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="5af60-120">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="5af60-120">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="5af60-121">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="5af60-121">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="5af60-122">Set 語句</span><span class="sxs-lookup"><span data-stu-id="5af60-122">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="5af60-123">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="5af60-123">Operator Statement</span></span>](operator-statement.md)
- [<span data-ttu-id="5af60-124">Property Statement</span><span class="sxs-lookup"><span data-stu-id="5af60-124">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="5af60-125">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="5af60-125">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="5af60-126">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="5af60-126">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
