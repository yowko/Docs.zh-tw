---
title: 溢位 (Visual Basic 執行階段錯誤)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1908ad576a499e79102aff23e3e2f11d7d99d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="efdd0-102">溢位 (Visual Basic 執行階段錯誤)</span><span class="sxs-lookup"><span data-stu-id="efdd0-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="efdd0-103">嘗試設定超出限制的指派的目標時，就會造成溢位。</span><span class="sxs-lookup"><span data-stu-id="efdd0-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="efdd0-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="efdd0-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="efdd0-105">請確定指派、 計算和資料類型轉換不會太大，而無法表示變數的值，該類型所允許的範圍內，並將值指派給類型的變數的結果可以保存較大範圍的值如有必要。</span><span class="sxs-lookup"><span data-stu-id="efdd0-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="efdd0-106">請確定屬性的指派，符合所建立的屬性的範圍。</span><span class="sxs-lookup"><span data-stu-id="efdd0-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="efdd0-107">請確定強制轉換為整數的計算中使用的數字，並沒有比整數較大的結果。</span><span class="sxs-lookup"><span data-stu-id="efdd0-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efdd0-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efdd0-108">See Also</span></span>  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [<span data-ttu-id="efdd0-109">資料類型</span><span class="sxs-lookup"><span data-stu-id="efdd0-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="efdd0-110">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="efdd0-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
