---
title: 堆疊空間用盡
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 9ae604a9727413f2705d42a4b68f5a50b7dd3feb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349188"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="42c19-102">堆疊空間不足 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42c19-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="42c19-103">堆疊是記憶體的工作區域，會隨著執行程式的需求動態成長和縮減。</span><span class="sxs-lookup"><span data-stu-id="42c19-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="42c19-104">已超過其限制。</span><span class="sxs-lookup"><span data-stu-id="42c19-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="42c19-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="42c19-105">To correct this error</span></span>  
  
1. <span data-ttu-id="42c19-106">檢查程式是否的嵌套太深。</span><span class="sxs-lookup"><span data-stu-id="42c19-106">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="42c19-107">請確定遞迴程式已正確終止。</span><span class="sxs-lookup"><span data-stu-id="42c19-107">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="42c19-108">如果本機變數需要的本機變數空間比可用的數目還要多，請嘗試在模組層級宣告一些變數。</span><span class="sxs-lookup"><span data-stu-id="42c19-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="42c19-109">您也可以在 `Property`、`Sub`或 `Function` 關鍵字前面加上 `Static`，以宣告程式中的所有變數。</span><span class="sxs-lookup"><span data-stu-id="42c19-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="42c19-110">或者，您可以使用 `Static` 語句，在程式內宣告個別的靜態變數。</span><span class="sxs-lookup"><span data-stu-id="42c19-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="42c19-111">將部分固定長度的字串重新定義為可變長度字串，因為固定長度的字串會使用比可變長度字串更多的堆疊空間。</span><span class="sxs-lookup"><span data-stu-id="42c19-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="42c19-112">您也可以在模組層級定義不需要堆疊空間的字串。</span><span class="sxs-lookup"><span data-stu-id="42c19-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="42c19-113">使用 [`Calls`] 對話方塊，查看堆疊上作用中的程式，以檢查嵌套 `DoEvents` 函式呼叫的數目。</span><span class="sxs-lookup"><span data-stu-id="42c19-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="42c19-114">觸發呼叫已在堆疊上之事件程式的事件，以確定您未造成「事件 cascade」。</span><span class="sxs-lookup"><span data-stu-id="42c19-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="42c19-115">事件 cascade 類似于未結束的遞迴程序呼叫，但較不明顯，因為呼叫是由 Visual Basic，而不是程式碼中的明確呼叫所發出。</span><span class="sxs-lookup"><span data-stu-id="42c19-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="42c19-116">使用 [`Calls`] 對話方塊，即可查看堆疊上作用中的程式。</span><span class="sxs-lookup"><span data-stu-id="42c19-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c19-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="42c19-117">See also</span></span>

- [<span data-ttu-id="42c19-118">記憶體視窗</span><span class="sxs-lookup"><span data-stu-id="42c19-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)
