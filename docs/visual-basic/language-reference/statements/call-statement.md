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
ms.openlocfilehash: 2074f44aedf59f1570e73c898a9bf64e57034923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603388"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="d2648-102">Call 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2648-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="d2648-103">控制權轉移到`Function`， `Sub`，或動態連結程式庫 (DLL) 程序。</span><span class="sxs-lookup"><span data-stu-id="d2648-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2648-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2648-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d2648-105">組件</span><span class="sxs-lookup"><span data-stu-id="d2648-105">Parts</span></span>  
 `procedureName`  
 <span data-ttu-id="d2648-106">必要。</span><span class="sxs-lookup"><span data-stu-id="d2648-106">Required.</span></span> <span data-ttu-id="d2648-107">若要呼叫的程序名稱。</span><span class="sxs-lookup"><span data-stu-id="d2648-107">Name of the procedure to call.</span></span>  
  
 `argumentList`  
 <span data-ttu-id="d2648-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d2648-108">Optional.</span></span> <span data-ttu-id="d2648-109">變數或運算式表示呼叫時，會傳遞至程序的引數的清單。</span><span class="sxs-lookup"><span data-stu-id="d2648-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="d2648-110">以逗號分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="d2648-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="d2648-111">如果您包含`argumentList`，您必須將它括在括號中。</span><span class="sxs-lookup"><span data-stu-id="d2648-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2648-112">備註</span><span class="sxs-lookup"><span data-stu-id="d2648-112">Remarks</span></span>  
 <span data-ttu-id="d2648-113">您可以使用`Call`關鍵字時呼叫的程序。</span><span class="sxs-lookup"><span data-stu-id="d2648-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="d2648-114">大部分的程序呼叫中，您不需要使用這個關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d2648-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="d2648-115">您通常會使用`Call`被呼叫的運算式無法啟動的識別項時的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d2648-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="d2648-116">使用`Call`給其他用途的關鍵字時，不建議。</span><span class="sxs-lookup"><span data-stu-id="d2648-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="d2648-117">此程序傳回值，如果`Call`陳述式便會捨棄它。</span><span class="sxs-lookup"><span data-stu-id="d2648-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2648-118">範例</span><span class="sxs-lookup"><span data-stu-id="d2648-118">Example</span></span>  
 <span data-ttu-id="d2648-119">下列程式碼顯示兩個範例其中`Call`關鍵字，才能呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="d2648-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="d2648-120">在這兩個範例中，被呼叫的運算式不會啟動識別碼。</span><span class="sxs-lookup"><span data-stu-id="d2648-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d2648-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2648-121">See Also</span></span>  
 [<span data-ttu-id="d2648-122">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="d2648-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="d2648-123">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="d2648-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="d2648-124">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="d2648-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="d2648-125">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="d2648-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
