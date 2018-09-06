---
title: 溢位 (Visual Basic 執行階段錯誤)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 7546676b85465577b357b7ad0757b4db8d40dbe3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784071"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="29c93-102">溢位 (Visual Basic 執行階段錯誤)</span><span class="sxs-lookup"><span data-stu-id="29c93-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="29c93-103">當您嘗試超過限制的指派目標的指派時，就會造成溢位。</span><span class="sxs-lookup"><span data-stu-id="29c93-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="29c93-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="29c93-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="29c93-105">請確定指派、 計算和資料類型轉換不會太大而無法表示變數的值，該類型所允許的範圍內，並將值指派給類型的變數的結果可以保存較大範圍的值如有必要。</span><span class="sxs-lookup"><span data-stu-id="29c93-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="29c93-106">請確定指派屬性符合的屬性會將所做的範圍。</span><span class="sxs-lookup"><span data-stu-id="29c93-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="29c93-107">請確定會強制轉型成整數的計算中使用的數字，並沒有比整數較大的結果。</span><span class="sxs-lookup"><span data-stu-id="29c93-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c93-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29c93-108">See Also</span></span>  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [<span data-ttu-id="29c93-109">資料類型</span><span class="sxs-lookup"><span data-stu-id="29c93-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="29c93-110">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="29c93-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
