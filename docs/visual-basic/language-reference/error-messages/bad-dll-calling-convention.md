---
title: 不正確的 DLL 呼叫慣例
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: f7b0c3a6edbe0b950195306fa66287ff9b209bfe
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306619"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="acacd-102">不正確的 DLL 呼叫慣例</span><span class="sxs-lookup"><span data-stu-id="acacd-102">Bad DLL calling convention</span></span>
<span data-ttu-id="acacd-103">引數傳遞至動態連結程式庫 (DLL) 必須完全符合所預期的常式。</span><span class="sxs-lookup"><span data-stu-id="acacd-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="acacd-104">呼叫慣例處理數字、 類型和引數的順序。</span><span class="sxs-lookup"><span data-stu-id="acacd-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="acacd-105">您的程式可能會呼叫常式錯誤的類型或數目的引數傳遞的 DLL 中。</span><span class="sxs-lookup"><span data-stu-id="acacd-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="acacd-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="acacd-106">To correct this error</span></span>  
  
1. <span data-ttu-id="acacd-107">請確定您要呼叫的常式的宣告中所指定同意所有引數類型。</span><span class="sxs-lookup"><span data-stu-id="acacd-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="acacd-108">請確定您傳遞您要呼叫的常式的宣告中指定的引數數目相同。</span><span class="sxs-lookup"><span data-stu-id="acacd-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="acacd-109">如果 DLL 常式的引數必須為值，請確定`ByVal`指定這些引數的常式的宣告中。</span><span class="sxs-lookup"><span data-stu-id="acacd-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acacd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acacd-110">See also</span></span>

- [<span data-ttu-id="acacd-111">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="acacd-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="acacd-112">Call 陳述式</span><span class="sxs-lookup"><span data-stu-id="acacd-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)
- [<span data-ttu-id="acacd-113">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="acacd-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
