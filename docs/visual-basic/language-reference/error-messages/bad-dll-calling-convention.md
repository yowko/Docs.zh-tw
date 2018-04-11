---
title: 不正確的 DLL 呼叫慣例
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="a8817-102">不正確的 DLL 呼叫慣例</span><span class="sxs-lookup"><span data-stu-id="a8817-102">Bad DLL calling convention</span></span>
<span data-ttu-id="a8817-103">引數傳遞至動態連結程式庫 (DLL) 必須完全符合所預期的常式。</span><span class="sxs-lookup"><span data-stu-id="a8817-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="a8817-104">呼叫慣例處理數目、 類型和引數的順序。</span><span class="sxs-lookup"><span data-stu-id="a8817-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="a8817-105">您的程式可能會呼叫常式傳入的引數數目的錯誤類型的 DLL 中。</span><span class="sxs-lookup"><span data-stu-id="a8817-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a8817-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a8817-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="a8817-107">請確定所有引數型別與所呼叫常式的宣告中指定數一致。</span><span class="sxs-lookup"><span data-stu-id="a8817-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2.  <span data-ttu-id="a8817-108">請確定您要將您要呼叫常式宣告所示的引數數目相同。</span><span class="sxs-lookup"><span data-stu-id="a8817-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3.  <span data-ttu-id="a8817-109">如果 DLL 常式的引數必須為值，請確定`ByVal`指定常式的宣告中的這些引數。</span><span class="sxs-lookup"><span data-stu-id="a8817-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8817-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8817-110">See Also</span></span>  
 [<span data-ttu-id="a8817-111">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="a8817-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="a8817-112">Call 陳述式</span><span class="sxs-lookup"><span data-stu-id="a8817-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)  
 [<span data-ttu-id="a8817-113">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="a8817-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
