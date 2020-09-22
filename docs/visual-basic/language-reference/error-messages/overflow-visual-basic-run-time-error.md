---
title: 溢位 (Visual Basic 執行階段錯誤)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: e287d6c24eca75d8bf20181a201056f467d6fc4e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871226"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="4cd90-102">溢位 (Visual Basic 執行階段錯誤)</span><span class="sxs-lookup"><span data-stu-id="4cd90-102">Overflow (Visual Basic Run-Time Error)</span></span>

<span data-ttu-id="4cd90-103">當您嘗試的指派超過指派的目標限制時，就會產生溢位。</span><span class="sxs-lookup"><span data-stu-id="4cd90-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4cd90-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4cd90-104">To correct this error</span></span>  
  
1. <span data-ttu-id="4cd90-105">請確定指派、計算和資料類型轉換的結果不太大而無法在該類型值所允許的變數範圍內表示，並視需要將值指派給可保存較大範圍之值的型別變數。</span><span class="sxs-lookup"><span data-stu-id="4cd90-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2. <span data-ttu-id="4cd90-106">請確定屬性的指派符合它們所做的屬性範圍。</span><span class="sxs-lookup"><span data-stu-id="4cd90-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3. <span data-ttu-id="4cd90-107">請確定已強制轉型為整數的計算中所使用的數位沒有大於整數的結果。</span><span class="sxs-lookup"><span data-stu-id="4cd90-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd90-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cd90-108">See also</span></span>

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [<span data-ttu-id="4cd90-109">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="4cd90-109">Data Types</span></span>](../data-types/index.md)
- [<span data-ttu-id="4cd90-110">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="4cd90-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
