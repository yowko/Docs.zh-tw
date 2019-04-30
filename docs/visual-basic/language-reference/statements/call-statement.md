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
ms.openlocfilehash: 755443a99a1ad8b0430a76d2dba1ff27472d4c9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945063"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="61670-102">Call 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61670-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="61670-103">控制權轉移到`Function`， `Sub`，或動態連結程式庫 (DLL) 程序。</span><span class="sxs-lookup"><span data-stu-id="61670-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61670-104">語法</span><span class="sxs-lookup"><span data-stu-id="61670-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="61670-105">組件</span><span class="sxs-lookup"><span data-stu-id="61670-105">Parts</span></span>  
|||
|---|---|
|`procedureName`|<span data-ttu-id="61670-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="61670-106">Required.</span></span> <span data-ttu-id="61670-107">要呼叫的程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="61670-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="61670-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="61670-108">Optional.</span></span> <span data-ttu-id="61670-109">變數或運算式表示呼叫時，會傳遞至程序的引數的清單。</span><span class="sxs-lookup"><span data-stu-id="61670-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="61670-110">以逗號分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="61670-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="61670-111">如果您包含`argumentList`，您必須將它括在括號中。</span><span class="sxs-lookup"><span data-stu-id="61670-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="61670-112">備註</span><span class="sxs-lookup"><span data-stu-id="61670-112">Remarks</span></span>  
 <span data-ttu-id="61670-113">您可以使用`Call`關鍵字時呼叫的程序。</span><span class="sxs-lookup"><span data-stu-id="61670-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="61670-114">對於大部分的程序呼叫中，您不需要使用此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="61670-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="61670-115">您通常會使用`Call`關鍵字時呼叫的運算式開頭的識別項。</span><span class="sxs-lookup"><span data-stu-id="61670-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="61670-116">使用`Call`不建議用於其他用途的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="61670-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="61670-117">如果此程序的傳回值，`Call`陳述式便會捨棄它。</span><span class="sxs-lookup"><span data-stu-id="61670-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61670-118">範例</span><span class="sxs-lookup"><span data-stu-id="61670-118">Example</span></span>  
 <span data-ttu-id="61670-119">下列程式碼顯示兩個範例其中`Call`關鍵字，才能呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="61670-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="61670-120">在這兩個範例中，被呼叫的運算式不啟動之識別項。</span><span class="sxs-lookup"><span data-stu-id="61670-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a><span data-ttu-id="61670-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61670-121">See also</span></span>

- [<span data-ttu-id="61670-122">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="61670-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="61670-123">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="61670-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="61670-124">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="61670-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="61670-125">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="61670-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
