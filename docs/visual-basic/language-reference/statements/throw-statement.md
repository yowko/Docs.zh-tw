---
title: Throw 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 2494eac2f61f112f3ba6321ada7404f8cd618049
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821366"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="b6fbe-102">Throw 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6fbe-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="b6fbe-103">擲回例外狀況程序內。</span><span class="sxs-lookup"><span data-stu-id="b6fbe-103">Throws an exception within a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6fbe-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6fbe-104">Syntax</span></span>  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a><span data-ttu-id="b6fbe-105">組件</span><span class="sxs-lookup"><span data-stu-id="b6fbe-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="b6fbe-106">提供將會擲回的例外狀況的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b6fbe-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="b6fbe-107">選擇性時位於`Catch`陳述式，否則為必要項。</span><span class="sxs-lookup"><span data-stu-id="b6fbe-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6fbe-108">備註</span><span class="sxs-lookup"><span data-stu-id="b6fbe-108">Remarks</span></span>  
 <span data-ttu-id="b6fbe-109">`Throw`陳述式會擲回的例外狀況，您可以使用結構化例外狀況處理程式碼處理 (`Try`...`Catch`...`Finally`) 或非結構化例外狀況處理程式碼 (`On Error GoTo`)。</span><span class="sxs-lookup"><span data-stu-id="b6fbe-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="b6fbe-110">您可以使用`Throw`陳述式來截取您的程式碼中的錯誤，因為 Visual Basic 會在呼叫堆疊中向上移動，直到找到適當的例外狀況處理程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6fbe-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>  
  
 <span data-ttu-id="b6fbe-111">A`Throw`但沒有運算式的陳述式僅適用於在`Catch`陳述式，在其中 case 陳述式會重新擲回目前正在處理的例外狀況`Catch`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b6fbe-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>  
  
 <span data-ttu-id="b6fbe-112">`Throw`陳述式會重設的呼叫堆疊`expression`例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b6fbe-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="b6fbe-113">如果`expression`未提供，呼叫堆疊會保持不變。</span><span class="sxs-lookup"><span data-stu-id="b6fbe-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="b6fbe-114">您可以透過例外狀況的呼叫堆疊<xref:System.Exception.StackTrace%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b6fbe-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6fbe-115">範例</span><span class="sxs-lookup"><span data-stu-id="b6fbe-115">Example</span></span>  
 <span data-ttu-id="b6fbe-116">下列程式碼會使用`Throw`擲回例外狀況的陳述式：</span><span class="sxs-lookup"><span data-stu-id="b6fbe-116">The following code uses the `Throw` statement to throw an exception:</span></span>  
  
 [!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]  
  
## <a name="requirements"></a><span data-ttu-id="b6fbe-117">需求</span><span class="sxs-lookup"><span data-stu-id="b6fbe-117">Requirements</span></span>  
 <span data-ttu-id="b6fbe-118">**命名空間：**[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="b6fbe-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="b6fbe-119">**模組：** `Interaction`</span><span class="sxs-lookup"><span data-stu-id="b6fbe-119">**Module:** `Interaction`</span></span>  
  
 <span data-ttu-id="b6fbe-120">**組件：** Visual Basic Runtime Library (位於 Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="b6fbe-120">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6fbe-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6fbe-121">See also</span></span>

- [<span data-ttu-id="b6fbe-122">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="b6fbe-122">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="b6fbe-123">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="b6fbe-123">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
