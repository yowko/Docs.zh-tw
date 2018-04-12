---
title: 超出字串空間 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID14
ms.assetid: 16681c75-a400-422d-9351-c691d3c7614e
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d820bdfd7c66ecbe81f8cb75ada2374045257598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="out-of-string-space-visual-basic"></a><span data-ttu-id="d4391-102">超出字串空間 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4391-102">Out of string space (Visual Basic)</span></span>
<span data-ttu-id="d4391-103">Visual Basic 中，您可以使用非常大的字串。</span><span class="sxs-lookup"><span data-stu-id="d4391-103">With Visual Basic, you can use very large strings.</span></span> <span data-ttu-id="d4391-104">不過，需求的其他程式，您可以使用字串的方式，仍有可能導致這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="d4391-104">However, the requirements of other programs and the way you work with your strings can still cause this error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d4391-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d4391-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="d4391-106">請確定需要評估期間建立暫存字串的運算式，不會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="d4391-106">Make sure that an expression requiring temporary string creation during evaluation is not causing the error.</span></span>  
  
2.  <span data-ttu-id="d4391-107">移除任何不必要的應用程式記憶體來建立更多空間。</span><span class="sxs-lookup"><span data-stu-id="d4391-107">Remove any unnecessary applications from memory to create more space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4391-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4391-108">See Also</span></span>  
 [<span data-ttu-id="d4391-109">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="d4391-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="d4391-110">字串操作摘要</span><span class="sxs-lookup"><span data-stu-id="d4391-110">String Manipulation Summary</span></span>](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
