---
title: "堆疊空間 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID28
dev_langs:
- VB
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 256ef0c7fcb3632e0c13d12737d438225343884f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="cd1f1-102">堆疊空間不足 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd1f1-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="cd1f1-103">堆疊是執行程式的要求使用動態記憶體成長和縮減工作區域。</span><span class="sxs-lookup"><span data-stu-id="cd1f1-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="cd1f1-104">已超過其限制。</span><span class="sxs-lookup"><span data-stu-id="cd1f1-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cd1f1-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cd1f1-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="cd1f1-106">請檢查程序不太深，巢狀。</span><span class="sxs-lookup"><span data-stu-id="cd1f1-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="cd1f1-107">請確定遞迴程序會正確地終止。</span><span class="sxs-lookup"><span data-stu-id="cd1f1-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="cd1f1-108">如果區域變數需要多個本機變數空間大於可用空間，請嘗試一些變數，在模組層級中宣告。</span><span class="sxs-lookup"><span data-stu-id="cd1f1-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="cd1f1-109">您也可以宣告此程序中的所有變數靜態前面的`Property`， `Sub`，或`Function`關鍵字與`Static`。</span><span class="sxs-lookup"><span data-stu-id="cd1f1-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="cd1f1-110">或者您可以使用`Static`陳述式來宣告程序內的個別靜態變數。</span><span class="sxs-lookup"><span data-stu-id="cd1f1-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="cd1f1-111">重新定義一些固定長度字串為可變長度字串的固定長度字串使用堆疊空間較可變長度的字串。</span><span class="sxs-lookup"><span data-stu-id="cd1f1-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="cd1f1-112">您也可以定義在模組層級，不需要堆疊空間的字串。</span><span class="sxs-lookup"><span data-stu-id="cd1f1-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="cd1f1-113">檢查數目巢狀`DoEvents`函式呼叫，使用`Calls`對話方塊來檢視哪些程序會在堆疊上作用。</span><span class="sxs-lookup"><span data-stu-id="cd1f1-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="cd1f1-114">請確定您不會 」 事件串聯"造成所觸發的事件，已經呼叫堆疊上的事件程序。</span><span class="sxs-lookup"><span data-stu-id="cd1f1-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="cd1f1-115">事件串聯結束的遞迴程序呼叫，類似，但它是較不明顯，因為呼叫由進行[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]而不是在程式碼中明確呼叫。</span><span class="sxs-lookup"><span data-stu-id="cd1f1-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] rather than an explicit call in the code.</span></span> <span data-ttu-id="cd1f1-116">使用`Calls`對話方塊來檢視哪些程序會在堆疊上作用。</span><span class="sxs-lookup"><span data-stu-id="cd1f1-116">Use the `Calls`dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd1f1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd1f1-117">See Also</span></span>  
 [<span data-ttu-id="cd1f1-118">記憶體視窗</span><span class="sxs-lookup"><span data-stu-id="cd1f1-118">Memory Windows</span></span>](https://docs.microsoft.com/visualstudio/debugger/memory-windows)
