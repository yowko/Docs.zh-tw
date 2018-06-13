---
title: 溢位 (Visual Basic 執行階段錯誤)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 9db79071c4895d49680352bde2d0824a3756d941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594171"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="2ea51-102">溢位 (Visual Basic 執行階段錯誤)</span><span class="sxs-lookup"><span data-stu-id="2ea51-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="2ea51-103">嘗試設定超出限制的指派的目標時，就會造成溢位。</span><span class="sxs-lookup"><span data-stu-id="2ea51-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ea51-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2ea51-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="2ea51-105">請確定指派、 計算和資料類型轉換不會太大，而無法表示變數的值，該類型所允許的範圍內，並將值指派給類型的變數的結果可以保存較大範圍的值如有必要。</span><span class="sxs-lookup"><span data-stu-id="2ea51-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="2ea51-106">請確定屬性的指派，符合所建立的屬性的範圍。</span><span class="sxs-lookup"><span data-stu-id="2ea51-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="2ea51-107">請確定強制轉換為整數的計算中使用的數字，並沒有比整數較大的結果。</span><span class="sxs-lookup"><span data-stu-id="2ea51-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea51-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ea51-108">See Also</span></span>  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [<span data-ttu-id="2ea51-109">資料類型</span><span class="sxs-lookup"><span data-stu-id="2ea51-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="2ea51-110">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="2ea51-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
