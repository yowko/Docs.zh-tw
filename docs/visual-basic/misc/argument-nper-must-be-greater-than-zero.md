---
title: 引數 'NPer' 必須大於零
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: 86bbf892997ee512b6042ef400e2485edabe731d
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2018
ms.locfileid: "53773480"
---
# <a name="argument-nper-must-be-greater-than-zero"></a><span data-ttu-id="c7f65-102">引數 'NPer' 必須大於零</span><span class="sxs-lookup"><span data-stu-id="c7f65-102">Argument 'NPer' must be greater than zero</span></span>
<span data-ttu-id="c7f65-103">`NPer` 函式會傳回 `Double` 指定根據定期支付和固定利率的年金期數，它需要大於零的引數。</span><span class="sxs-lookup"><span data-stu-id="c7f65-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c7f65-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c7f65-104">To correct this error</span></span>  
  
-   <span data-ttu-id="c7f65-105">請檢查運算式中的引數拼法。</span><span class="sxs-lookup"><span data-stu-id="c7f65-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="c7f65-106">拼錯的變數名稱可能會隱含地建立初始化為零的數值變數。</span><span class="sxs-lookup"><span data-stu-id="c7f65-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
-   <span data-ttu-id="c7f65-107">請檢查運算式中先前的變數作業，特別是那些作為引數從其他程序傳遞至程序的變數。</span><span class="sxs-lookup"><span data-stu-id="c7f65-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f65-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7f65-108">See Also</span></span>  
 [<span data-ttu-id="c7f65-109">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="c7f65-109">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
