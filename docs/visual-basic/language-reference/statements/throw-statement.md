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
ms.openlocfilehash: a6d10982cf199e9285334e0d72e6622275d51b4d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626204"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="ab1d2-102">Throw 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab1d2-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="ab1d2-103">在程式中擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ab1d2-103">Throws an exception within a procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="ab1d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab1d2-104">Syntax</span></span>

```vb
Throw [ expression ]
```

## <a name="part"></a><span data-ttu-id="ab1d2-105">組件</span><span class="sxs-lookup"><span data-stu-id="ab1d2-105">Part</span></span>
 <span data-ttu-id="ab1d2-106">`expression`提供要擲回之例外狀況的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ab1d2-106">`expression` Provides information about the exception to be thrown.</span></span> <span data-ttu-id="ab1d2-107">如果位於`Catch`語句中, 則為選擇性, 否則為必要項。</span><span class="sxs-lookup"><span data-stu-id="ab1d2-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="ab1d2-108">備註</span><span class="sxs-lookup"><span data-stu-id="ab1d2-108">Remarks</span></span>
 <span data-ttu-id="ab1d2-109">語句會擲回例外狀況, 您可以處理結構化例外狀況處理常式`Try`代碼 (... `Throw``Catch`...) 或非結構化例外狀況處理`On Error GoTo`程式碼 ()。 `Finally`</span><span class="sxs-lookup"><span data-stu-id="ab1d2-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="ab1d2-110">您可以使用`Throw`語句來攔截程式碼內的錯誤, 因為 Visual Basic 會向上移動呼叫堆疊, 直到找到適當的例外狀況處理常式代碼為止。</span><span class="sxs-lookup"><span data-stu-id="ab1d2-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>
 
 <span data-ttu-id="ab1d2-111">沒有運算式的`Catch` `Catch`語句只能在語句中使用, 在此情況下, 語句會重新擲回目前正由語句處理的例外狀況。 `Throw`</span><span class="sxs-lookup"><span data-stu-id="ab1d2-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>

 <span data-ttu-id="ab1d2-112">語句會重設`expression`例外狀況的呼叫堆疊。 `Throw`</span><span class="sxs-lookup"><span data-stu-id="ab1d2-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="ab1d2-113">如果`expression`未提供, 則會將呼叫堆疊保持不變。</span><span class="sxs-lookup"><span data-stu-id="ab1d2-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="ab1d2-114">您可以透過<xref:System.Exception.StackTrace%2A>屬性存取例外狀況的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="ab1d2-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="ab1d2-115">範例</span><span class="sxs-lookup"><span data-stu-id="ab1d2-115">Example</span></span>
 <span data-ttu-id="ab1d2-116">下列程式碼會使用`Throw`語句來擲回例外狀況:</span><span class="sxs-lookup"><span data-stu-id="ab1d2-116">The following code uses the `Throw` statement to throw an exception:</span></span>
 
 [!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

  
## <a name="see-also"></a><span data-ttu-id="ab1d2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab1d2-117">See also</span></span>

- [<span data-ttu-id="ab1d2-118">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="ab1d2-118">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="ab1d2-119">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="ab1d2-119">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
