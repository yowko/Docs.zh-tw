---
title: 這是固定陣列，或陣列暫被鎖定
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 05fb8e2ef788920fd200d79a75eec3d7c252b123
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873592"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="abb5e-102">此陣列為固定長度或暫時鎖定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abb5e-102">This array is fixed or temporarily locked (Visual Basic)</span></span>

<span data-ttu-id="abb5e-103">此錯誤有下列可能的原因：</span><span class="sxs-lookup"><span data-stu-id="abb5e-103">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="abb5e-104">使用 `ReDim` 變更固定大小陣列的元素數目。</span><span class="sxs-lookup"><span data-stu-id="abb5e-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
- <span data-ttu-id="abb5e-105">Redimensioning 模組層級動態陣列，其中一個元素已做為引數傳遞至程式。</span><span class="sxs-lookup"><span data-stu-id="abb5e-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="abb5e-106">如果傳遞元素，則會鎖定陣列，以防止在程式內解除配置參考參數的記憶體。</span><span class="sxs-lookup"><span data-stu-id="abb5e-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
- <span data-ttu-id="abb5e-107">嘗試將值指派給 `Variant` 包含陣列的變數，但 `Variant` 目前已鎖定。</span><span class="sxs-lookup"><span data-stu-id="abb5e-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="abb5e-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="abb5e-108">To correct this error</span></span>  
  
1. <span data-ttu-id="abb5e-109">如果陣列是在程式) 內宣告，或在不指定專案數目的情況下宣告，則讓原始陣列變成動態，而不是 (固定的 `ReDim` （如果陣列是在模組層級宣告，則會將它宣告，而不需要指定專案數目 (）。</span><span class="sxs-lookup"><span data-stu-id="abb5e-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2. <span data-ttu-id="abb5e-110">判斷您是否真的需要傳遞元素，因為它會顯示在課程模組中的所有程式內。</span><span class="sxs-lookup"><span data-stu-id="abb5e-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3. <span data-ttu-id="abb5e-111">判斷鎖定的內容 `Variant` ，並加以補救。</span><span class="sxs-lookup"><span data-stu-id="abb5e-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb5e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abb5e-112">See also</span></span>

- [<span data-ttu-id="abb5e-113">陣列</span><span class="sxs-lookup"><span data-stu-id="abb5e-113">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
