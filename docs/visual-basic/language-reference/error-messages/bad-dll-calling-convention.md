---
title: 不正確的 DLL 呼叫慣例
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: a60e44ce92b1805b0a5a6f1d4ce397c295eef202
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409877"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="e0826-102">不正確的 DLL 呼叫慣例</span><span class="sxs-lookup"><span data-stu-id="e0826-102">Bad DLL calling convention</span></span>
<span data-ttu-id="e0826-103">傳遞至動態連結程式庫（DLL）的引數必須完全符合常式所預期的參數。</span><span class="sxs-lookup"><span data-stu-id="e0826-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="e0826-104">呼叫慣例會處理引數的數目、類型和順序。</span><span class="sxs-lookup"><span data-stu-id="e0826-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="e0826-105">您的程式可能會在傳遞錯誤類型或引數數目的 DLL 中呼叫常式。</span><span class="sxs-lookup"><span data-stu-id="e0826-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e0826-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e0826-106">To correct this error</span></span>  
  
1. <span data-ttu-id="e0826-107">請確定所有引數類型都與您所呼叫之常式的宣告中指定的是一致的。</span><span class="sxs-lookup"><span data-stu-id="e0826-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="e0826-108">請確定您傳遞的引數數目與您呼叫的常式宣告中所指出的數量相同。</span><span class="sxs-lookup"><span data-stu-id="e0826-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="e0826-109">如果 DLL 常式預期會以傳值方式引數，請確定 `ByVal` 已針對常式宣告中的這些引數指定。</span><span class="sxs-lookup"><span data-stu-id="e0826-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0826-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0826-110">See also</span></span>

- [<span data-ttu-id="e0826-111">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="e0826-111">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="e0826-112">Call 陳述式</span><span class="sxs-lookup"><span data-stu-id="e0826-112">Call Statement</span></span>](../statements/call-statement.md)
- [<span data-ttu-id="e0826-113">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="e0826-113">Declare Statement</span></span>](../statements/declare-statement.md)
