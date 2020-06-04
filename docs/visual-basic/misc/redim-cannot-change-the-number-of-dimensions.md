---
title: "'ReDim' 無法變更維度的數目"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: b2404927c2faf30d1d058d2163fd5d67e1a52e1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358163"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="1d10f-102">'ReDim' 無法變更維度的數目</span><span class="sxs-lookup"><span data-stu-id="1d10f-102">'ReDim' cannot change the number of dimensions</span></span>
<span data-ttu-id="1d10f-103">作業嘗試使用 `ReDim` 陳述式變更陣列的陣序 (維度數目)。</span><span class="sxs-lookup"><span data-stu-id="1d10f-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="1d10f-104">`ReDim` 可以變更已正式宣告之陣列的一或多個維度大小，但無法變更陣列的陣序。</span><span class="sxs-lookup"><span data-stu-id="1d10f-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1d10f-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1d10f-105">To correct this error</span></span>  
  
- <span data-ttu-id="1d10f-106">請確定您是要變更陣列的陣序，而不是其維度的大小，並且請盡可能地使用 `Dim` 來宣告具有所需陣序的新陣列。</span><span class="sxs-lookup"><span data-stu-id="1d10f-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d10f-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d10f-107">See also</span></span>

- [<span data-ttu-id="1d10f-108">Visual Basic 中的陣列</span><span class="sxs-lookup"><span data-stu-id="1d10f-108">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="1d10f-109">Visual Basic 中的陣列維度</span><span class="sxs-lookup"><span data-stu-id="1d10f-109">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="1d10f-110">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="1d10f-110">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="1d10f-111">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="1d10f-111">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
