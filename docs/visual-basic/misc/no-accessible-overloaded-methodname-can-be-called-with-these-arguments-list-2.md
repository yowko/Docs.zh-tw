---
title: 無法使用這些引數呼叫可存取的多載 ' <methodname> '，而不需要縮小轉換： <list>
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall2
ms.assetid: 13b20ffa-9f02-4971-a3cb-e08b402fd971
ms.openlocfilehash: f824b1250c7cb98aeaf301ef57ee01ec2779215f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376699"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion-list"></a><span data-ttu-id="c9be6-102">無法使用這些引數呼叫可存取的多載 ' \<methodname> '，而不需要縮小轉換：\<list></span><span class="sxs-lookup"><span data-stu-id="c9be6-102">No accessible overloaded '\<methodname>' can be called with these arguments without a narrowing conversion: \<list></span></span>
<span data-ttu-id="c9be6-103">已呼叫多載方法，但沒有方法可在未縮小轉換的情況下，符合所提供的引數清單。</span><span class="sxs-lookup"><span data-stu-id="c9be6-103">An overloaded method was called, but the method cannot be matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c9be6-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c9be6-104">To correct this error</span></span>  
  
1. <span data-ttu-id="c9be6-105">指定 `Option Strict Off`。</span><span class="sxs-lookup"><span data-stu-id="c9be6-105">Specify `Option Strict Off`.</span></span>
  
2. <span data-ttu-id="c9be6-106">變更引數，以符合多載方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="c9be6-106">Change the arguments to match a signature of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9be6-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9be6-107">See also</span></span>

- [<span data-ttu-id="c9be6-108">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="c9be6-108">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="c9be6-109">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="c9be6-109">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
