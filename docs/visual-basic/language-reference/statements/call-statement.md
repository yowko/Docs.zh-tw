---
title: "Call 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72450fd6f931f36f640d3e384a6fd38d57a7a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="126ea-102">Call 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="126ea-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="126ea-103">控制權轉移到`Function`， `Sub`，或動態連結程式庫 (DLL) 程序。</span><span class="sxs-lookup"><span data-stu-id="126ea-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="126ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="126ea-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="126ea-105">組件</span><span class="sxs-lookup"><span data-stu-id="126ea-105">Parts</span></span>  
 `procedureName`  
 <span data-ttu-id="126ea-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="126ea-106">Required.</span></span> <span data-ttu-id="126ea-107">若要呼叫的程序名稱。</span><span class="sxs-lookup"><span data-stu-id="126ea-107">Name of the procedure to call.</span></span>  
  
 `argumentList`  
 <span data-ttu-id="126ea-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="126ea-108">Optional.</span></span> <span data-ttu-id="126ea-109">變數或運算式表示呼叫時，會傳遞至程序的引數的清單。</span><span class="sxs-lookup"><span data-stu-id="126ea-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="126ea-110">以逗號分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="126ea-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="126ea-111">如果您包含`argumentList`，您必須將它括在括號中。</span><span class="sxs-lookup"><span data-stu-id="126ea-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="126ea-112">備註</span><span class="sxs-lookup"><span data-stu-id="126ea-112">Remarks</span></span>  
 <span data-ttu-id="126ea-113">您可以使用`Call`關鍵字時呼叫的程序。</span><span class="sxs-lookup"><span data-stu-id="126ea-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="126ea-114">大部分的程序呼叫中，您不需要使用這個關鍵字。</span><span class="sxs-lookup"><span data-stu-id="126ea-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="126ea-115">您通常會使用`Call`被呼叫的運算式無法啟動的識別項時的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="126ea-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="126ea-116">使用`Call`給其他用途的關鍵字時，不建議。</span><span class="sxs-lookup"><span data-stu-id="126ea-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="126ea-117">此程序傳回值，如果`Call`陳述式便會捨棄它。</span><span class="sxs-lookup"><span data-stu-id="126ea-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="126ea-118">範例</span><span class="sxs-lookup"><span data-stu-id="126ea-118">Example</span></span>  
 <span data-ttu-id="126ea-119">下列程式碼顯示兩個範例其中`Call`關鍵字，才能呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="126ea-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="126ea-120">在這兩個範例中，被呼叫的運算式不會啟動識別碼。</span><span class="sxs-lookup"><span data-stu-id="126ea-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="126ea-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="126ea-121">See Also</span></span>  
 [<span data-ttu-id="126ea-122">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="126ea-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="126ea-123">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="126ea-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="126ea-124">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="126ea-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="126ea-125">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="126ea-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
