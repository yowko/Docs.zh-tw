---
title: "'ReDim' 只能變更最右側的維度"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: f38bcb99b682ace497859b67fe3bb829bbc80c4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664411"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="a7b9d-102">'ReDim' 只能變更最右側的維度</span><span class="sxs-lookup"><span data-stu-id="a7b9d-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="a7b9d-103">`ReDim` 陳述式嘗試使用 `Preserve` 關鍵字來變更不是最後一個維度的陣列的維度。</span><span class="sxs-lookup"><span data-stu-id="a7b9d-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="a7b9d-104">使用 `Preserve`時，您只能調整陣列的最後一個維度。</span><span class="sxs-lookup"><span data-stu-id="a7b9d-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="a7b9d-105">對於所有其他維度，您必須指定與現有陣列相同的大小。</span><span class="sxs-lookup"><span data-stu-id="a7b9d-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a7b9d-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a7b9d-106">To correct this error</span></span>  
  
- <span data-ttu-id="a7b9d-107">請移除 `Preserve` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a7b9d-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b9d-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7b9d-108">See also</span></span>

- [<span data-ttu-id="a7b9d-109">Visual Basic 中的陣列</span><span class="sxs-lookup"><span data-stu-id="a7b9d-109">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="a7b9d-110">Visual Basic 中的陣列維度</span><span class="sxs-lookup"><span data-stu-id="a7b9d-110">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="a7b9d-111">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="a7b9d-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="a7b9d-112">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="a7b9d-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
