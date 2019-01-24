---
title: 堆疊空間不足 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 2f91763888069b6dca90da03995dc1b6812fd426
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655487"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="2d4cb-102">堆疊空間不足 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d4cb-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="2d4cb-103">堆疊是執行程式的需求使用動態記憶體成長和縮減工作區域。</span><span class="sxs-lookup"><span data-stu-id="2d4cb-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="2d4cb-104">已超過其限制。</span><span class="sxs-lookup"><span data-stu-id="2d4cb-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2d4cb-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2d4cb-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="2d4cb-106">請檢查該程序無巢狀太深。</span><span class="sxs-lookup"><span data-stu-id="2d4cb-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="2d4cb-107">請確定遞迴程序會正確地終止。</span><span class="sxs-lookup"><span data-stu-id="2d4cb-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="2d4cb-108">如果本機變數需要更多區域的變數空間大於可用，請嘗試宣告一些變數，在模組層級。</span><span class="sxs-lookup"><span data-stu-id="2d4cb-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="2d4cb-109">您也可以宣告程序中的所有變數靜態前面`Property`， `Sub`，或`Function`關鍵字搭配`Static`。</span><span class="sxs-lookup"><span data-stu-id="2d4cb-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="2d4cb-110">或者您可以使用`Static`陳述式來宣告程序內的個別靜態變數。</span><span class="sxs-lookup"><span data-stu-id="2d4cb-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="2d4cb-111">重新定義部分的可變長度的字串，為您固定長度字串的固定長度字串使用堆疊空間較可變長度的字串。</span><span class="sxs-lookup"><span data-stu-id="2d4cb-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="2d4cb-112">您也可以定義在模組層級，它不需要堆疊空間的字串。</span><span class="sxs-lookup"><span data-stu-id="2d4cb-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="2d4cb-113">檢查數目巢狀`DoEvents`函式呼叫，使用`Calls`對話方塊來檢視哪些程序會在堆疊上作用。</span><span class="sxs-lookup"><span data-stu-id="2d4cb-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="2d4cb-114">請確定您不會觸發已將事件程序呼叫堆疊的事件 」 事件 cascade"。</span><span class="sxs-lookup"><span data-stu-id="2d4cb-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="2d4cb-115">事件串聯類似於未結束的遞迴程序呼叫，但它是較不明顯，因為 Visual Basic，而不是明確呼叫程式碼中的進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="2d4cb-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="2d4cb-116">使用`Calls`對話方塊來檢視哪些程序會在堆疊上作用。</span><span class="sxs-lookup"><span data-stu-id="2d4cb-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d4cb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d4cb-117">See also</span></span>
- [<span data-ttu-id="2d4cb-118">記憶體視窗</span><span class="sxs-lookup"><span data-stu-id="2d4cb-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)
