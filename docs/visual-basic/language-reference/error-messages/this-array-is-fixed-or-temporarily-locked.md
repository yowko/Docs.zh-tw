---
title: 此陣列為固定長度或暫時鎖定 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: f0b80e2be007ff44569365f37a2331f1ecd7a216
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839401"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="43581-102">此陣列為固定長度或暫時鎖定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43581-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="43581-103">此錯誤有下列可能的原因：</span><span class="sxs-lookup"><span data-stu-id="43581-103">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="43581-104">使用`ReDim`若要變更的固定大小陣列的項目數。</span><span class="sxs-lookup"><span data-stu-id="43581-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
-   <span data-ttu-id="43581-105">Redimensioning 模組層級動態陣列，在其中一個項目已傳遞做為引數給程序。</span><span class="sxs-lookup"><span data-stu-id="43581-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="43581-106">如果傳遞的項目，則陣列會鎖定以防止解除配置記憶體的程序內參考參數。</span><span class="sxs-lookup"><span data-stu-id="43581-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
-   <span data-ttu-id="43581-107">嘗試指派值給`Variant`變數，其中包含陣列，但`Variant`目前已鎖定。</span><span class="sxs-lookup"><span data-stu-id="43581-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="43581-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="43581-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="43581-109">將原始陣列設為動態，而不是藉由宣告它與已修正`ReDim`（如果陣列宣告程序內），或藉由宣告但未指定的元素數目 （如果陣列在模組層級中宣告。</span><span class="sxs-lookup"><span data-stu-id="43581-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2.  <span data-ttu-id="43581-110">判斷您是否真的需要將項目，因為它是在模組中的所有程序內為可見。</span><span class="sxs-lookup"><span data-stu-id="43581-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3.  <span data-ttu-id="43581-111">判斷功能正鎖住`Variant`並加以修正它。</span><span class="sxs-lookup"><span data-stu-id="43581-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43581-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43581-112">See also</span></span>

- [<span data-ttu-id="43581-113">陣列</span><span class="sxs-lookup"><span data-stu-id="43581-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
