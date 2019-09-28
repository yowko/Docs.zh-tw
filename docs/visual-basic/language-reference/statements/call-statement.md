---
title: Call 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: af0b62d6cfacbcf94f527e049e07e51bf496a6cf
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392754"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="f1f97-102">Call 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1f97-102">Call Statement (Visual Basic)</span></span>

<span data-ttu-id="f1f97-103">將控制權轉移至 `Function`、@no__t 1 或動態連結程式庫（DLL）程式。</span><span class="sxs-lookup"><span data-stu-id="f1f97-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="f1f97-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1f97-104">Syntax</span></span>

```vb
[ Call ] procedureName [ (argumentList) ]
```

## <a name="parts"></a><span data-ttu-id="f1f97-105">組件</span><span class="sxs-lookup"><span data-stu-id="f1f97-105">Parts</span></span>

|||
|---|---|
|`procedureName`|<span data-ttu-id="f1f97-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="f1f97-106">Required.</span></span> <span data-ttu-id="f1f97-107">要呼叫的程式名稱。</span><span class="sxs-lookup"><span data-stu-id="f1f97-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="f1f97-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f1f97-108">Optional.</span></span> <span data-ttu-id="f1f97-109">變數或運算式的清單，代表呼叫時傳遞給程式的引數。</span><span class="sxs-lookup"><span data-stu-id="f1f97-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="f1f97-110">以逗號分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="f1f97-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="f1f97-111">如果您包含 `argumentList`，則必須將它括在括弧中。</span><span class="sxs-lookup"><span data-stu-id="f1f97-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="f1f97-112">備註</span><span class="sxs-lookup"><span data-stu-id="f1f97-112">Remarks</span></span>

 <span data-ttu-id="f1f97-113">當您呼叫程式時，可以使用 `Call` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f1f97-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="f1f97-114">對於大部分的程序呼叫，您不需要使用此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f1f97-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>

 <span data-ttu-id="f1f97-115">當被呼叫的運算式不是以識別碼開頭時，您通常會使用 `Call` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f1f97-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="f1f97-116">不建議針對其他用途使用 `Call` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f1f97-116">Use of the `Call` keyword for other uses isn't recommended.</span></span>

 <span data-ttu-id="f1f97-117">如果程式傳回值，則 @no__t 0 語句會將它捨棄。</span><span class="sxs-lookup"><span data-stu-id="f1f97-117">If the procedure returns a value, the `Call` statement discards it.</span></span>

## <a name="example"></a><span data-ttu-id="f1f97-118">範例</span><span class="sxs-lookup"><span data-stu-id="f1f97-118">Example</span></span>

 <span data-ttu-id="f1f97-119">下列程式碼顯示兩個範例，其中需要 `Call` 關鍵字來呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="f1f97-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="f1f97-120">在這兩個範例中，被呼叫的運算式不是以識別碼開頭。</span><span class="sxs-lookup"><span data-stu-id="f1f97-120">In both examples, the called expression doesn't start with an identifier.</span></span>

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a><span data-ttu-id="f1f97-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1f97-121">See also</span></span>

- [<span data-ttu-id="f1f97-122">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="f1f97-122">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="f1f97-123">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="f1f97-123">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="f1f97-124">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="f1f97-124">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="f1f97-125">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="f1f97-125">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
