---
title: 堆疊空間不足 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3959c24aa4e95204e156a9863ef0ce237af1fcda
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="36413-102">堆疊空間不足 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36413-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="36413-103">堆疊是記憶體的工作區域的成長和壓縮，以動態方式與執行程式的需求。</span><span class="sxs-lookup"><span data-stu-id="36413-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="36413-104">已超過其限制。</span><span class="sxs-lookup"><span data-stu-id="36413-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="36413-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="36413-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="36413-106">請檢查該程序無巢狀太深。</span><span class="sxs-lookup"><span data-stu-id="36413-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="36413-107">請確定遞迴程序會正確地終止。</span><span class="sxs-lookup"><span data-stu-id="36413-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="36413-108">如果本機變數需要多個本機變數空間大於可用空間，請嘗試宣告部分模組層級的變數。</span><span class="sxs-lookup"><span data-stu-id="36413-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="36413-109">您也可以宣告程序中的所有變數靜態前`Property`， `Sub`，或`Function`關鍵字搭配`Static`。</span><span class="sxs-lookup"><span data-stu-id="36413-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="36413-110">您可以使用或`Static`宣告程序內的個別靜態變數的陳述式。</span><span class="sxs-lookup"><span data-stu-id="36413-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="36413-111">重新定義為可變長度字串，固定長度字串的部分為固定長度字串使用堆疊空間較可變長度的字串。</span><span class="sxs-lookup"><span data-stu-id="36413-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="36413-112">您也可以定義在模組層級，不需要堆疊空間的字串。</span><span class="sxs-lookup"><span data-stu-id="36413-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="36413-113">檢查數目巢狀`DoEvents`函式呼叫，使用`Calls`對話方塊來檢視哪些程序會在堆疊作用中。</span><span class="sxs-lookup"><span data-stu-id="36413-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="36413-114">請確定您未透過觸發已將事件程序呼叫堆疊的事件不會造成 」 事件串聯 」。</span><span class="sxs-lookup"><span data-stu-id="36413-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="36413-115">事件串聯結束的遞迴程序呼叫，類似，但它是較不明顯，因為呼叫由進行[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]而不是在程式碼中明確呼叫。</span><span class="sxs-lookup"><span data-stu-id="36413-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rather than an explicit call in the code.</span></span> <span data-ttu-id="36413-116">使用`Calls`對話方塊來檢視哪些程序會在堆疊作用中。</span><span class="sxs-lookup"><span data-stu-id="36413-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36413-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36413-117">See Also</span></span>  
 [<span data-ttu-id="36413-118">記憶體視窗</span><span class="sxs-lookup"><span data-stu-id="36413-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)
