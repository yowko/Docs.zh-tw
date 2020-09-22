---
title: 堆疊空間用盡
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: afb6a42372bdbd2e49ac15fbbf2b9e254f8db431
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871318"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="01737-102">堆疊空間不足 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01737-102">Out of stack space (Visual Basic)</span></span>

<span data-ttu-id="01737-103">堆疊是記憶體的工作區域，會隨著執行程式的需求動態增加和縮減。</span><span class="sxs-lookup"><span data-stu-id="01737-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="01737-104">已超過其限制。</span><span class="sxs-lookup"><span data-stu-id="01737-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="01737-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="01737-105">To correct this error</span></span>  
  
1. <span data-ttu-id="01737-106">檢查程式是否太深。</span><span class="sxs-lookup"><span data-stu-id="01737-106">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="01737-107">請確定遞迴程式會正常終止。</span><span class="sxs-lookup"><span data-stu-id="01737-107">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="01737-108">如果區域變數需要的本機變數空間超過可用的數目，請嘗試在模組層級宣告一些變數。</span><span class="sxs-lookup"><span data-stu-id="01737-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="01737-109">您也可以在 `Property` 、或關鍵字前面加上，將程式中的所有變數宣告 `Sub` `Function` 為靜態 `Static` 。</span><span class="sxs-lookup"><span data-stu-id="01737-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="01737-110">或者，您可以使用 `Static` 語句來宣告程式中的個別靜態變數。</span><span class="sxs-lookup"><span data-stu-id="01737-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="01737-111">將部分固定長度的字串重新定義為可變長度的字串，因為固定長度的字串使用的堆疊空間比可變長度的字串多。</span><span class="sxs-lookup"><span data-stu-id="01737-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="01737-112">您也可以在模組層級定義不需要任何堆疊空間的字串。</span><span class="sxs-lookup"><span data-stu-id="01737-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="01737-113">檢查嵌套 `DoEvents` 函式呼叫的數目，方法是使用 `Calls` 對話方塊來查看堆疊上的作用中程式。</span><span class="sxs-lookup"><span data-stu-id="01737-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="01737-114">藉由觸發呼叫已在堆疊上之事件程式的事件，確定您未產生「事件串聯」。</span><span class="sxs-lookup"><span data-stu-id="01737-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="01737-115">事件串聯類似于未結束的遞迴程序呼叫，但比較不明顯，因為呼叫是由 Visual Basic 而不是程式碼中的明確呼叫所進行。</span><span class="sxs-lookup"><span data-stu-id="01737-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="01737-116">使用 `Calls` 對話方塊可查看堆疊上的作用中程式。</span><span class="sxs-lookup"><span data-stu-id="01737-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01737-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01737-117">See also</span></span>

- [<span data-ttu-id="01737-118">記憶體視窗</span><span class="sxs-lookup"><span data-stu-id="01737-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)
