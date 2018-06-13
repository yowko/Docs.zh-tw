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
ms.openlocfilehash: cfa53b3585846da25711739fb7af4bde21746b29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602849"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="3c76a-102">Throw 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c76a-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="3c76a-103">擲回例外狀況程序內。</span><span class="sxs-lookup"><span data-stu-id="3c76a-103">Throws an exception within a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c76a-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c76a-104">Syntax</span></span>  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a><span data-ttu-id="3c76a-105">組件</span><span class="sxs-lookup"><span data-stu-id="3c76a-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="3c76a-106">提供要擲回的例外狀況的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3c76a-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="3c76a-107">當位於`Catch`陳述式，否則為必要項。</span><span class="sxs-lookup"><span data-stu-id="3c76a-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c76a-108">備註</span><span class="sxs-lookup"><span data-stu-id="3c76a-108">Remarks</span></span>  
 <span data-ttu-id="3c76a-109">`Throw`陳述式會擲回的例外狀況，您可以處理與結構化例外狀況處理程式碼 (`Try`...`Catch`...`Finally`) 或非結構化例外狀況處理程式碼 (`On Error GoTo`)。</span><span class="sxs-lookup"><span data-stu-id="3c76a-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="3c76a-110">您可以使用`Throw`陳述式來攔截錯誤程式碼內，因為 Visual Basic 將呼叫堆疊向上移動，直到找到適當的例外狀況處理程式碼。</span><span class="sxs-lookup"><span data-stu-id="3c76a-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>  
  
 <span data-ttu-id="3c76a-111">A`Throw`沒有運算式的陳述式只可用在`Catch`陳述式，在其中案例陳述式會重新擲回目前所處理的例外狀況`Catch`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3c76a-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>  
  
 <span data-ttu-id="3c76a-112">`Throw`陳述式重設的呼叫堆疊`expression`例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3c76a-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="3c76a-113">如果`expression`未提供，呼叫堆疊會保持不變。</span><span class="sxs-lookup"><span data-stu-id="3c76a-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="3c76a-114">您可以存取透過例外狀況的呼叫堆疊<xref:System.Exception.StackTrace%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="3c76a-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c76a-115">範例</span><span class="sxs-lookup"><span data-stu-id="3c76a-115">Example</span></span>  
 <span data-ttu-id="3c76a-116">下列程式碼會使用`Throw`陳述式擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="3c76a-116">The following code uses the `Throw` statement to throw an exception:</span></span>  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="3c76a-117">需求</span><span class="sxs-lookup"><span data-stu-id="3c76a-117">Requirements</span></span>  
 <span data-ttu-id="3c76a-118">**命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="3c76a-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="3c76a-119">**模組：** `Interaction`</span><span class="sxs-lookup"><span data-stu-id="3c76a-119">**Module:** `Interaction`</span></span>  
  
 <span data-ttu-id="3c76a-120">**組件：** Visual Basic Runtime Library （位於 Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="3c76a-120">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c76a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c76a-121">See Also</span></span>  
 [<span data-ttu-id="3c76a-122">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="3c76a-122">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="3c76a-123">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="3c76a-123">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
