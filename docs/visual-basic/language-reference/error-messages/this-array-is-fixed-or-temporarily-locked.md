---
title: 這是固定陣列，或陣列暫被鎖定
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 8d5e4add2d92a575126fb934ac3874a2e37685f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350780"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="c71b0-102">此陣列為固定長度或暫時鎖定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c71b0-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="c71b0-103">此錯誤的可能原因如下：</span><span class="sxs-lookup"><span data-stu-id="c71b0-103">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="c71b0-104">使用 `ReDim` 變更固定大小陣列的元素數目。</span><span class="sxs-lookup"><span data-stu-id="c71b0-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
- <span data-ttu-id="c71b0-105">Redimensioning 模組層級動態陣列，其中一個元素已當做引數傳遞至程式。</span><span class="sxs-lookup"><span data-stu-id="c71b0-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="c71b0-106">如果傳遞了元素，陣列就會鎖定，以避免在程式內解除配置參考參數的記憶體。</span><span class="sxs-lookup"><span data-stu-id="c71b0-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
- <span data-ttu-id="c71b0-107">嘗試將值指派給包含陣列的 `Variant` 變數，但 `Variant` 目前已鎖定。</span><span class="sxs-lookup"><span data-stu-id="c71b0-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c71b0-108">若要改正這項錯誤</span><span class="sxs-lookup"><span data-stu-id="c71b0-108">To correct this error</span></span>  
  
1. <span data-ttu-id="c71b0-109">將原始陣列設為動態，而不是修正，方法是使用 `ReDim` （如果陣列是在程式內宣告），或是宣告它而不指定專案數（如果陣列是在模組層級宣告）。</span><span class="sxs-lookup"><span data-stu-id="c71b0-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2. <span data-ttu-id="c71b0-110">判斷您是否真的需要傳遞專案，因為它在模組的所有程式中都是可見的。</span><span class="sxs-lookup"><span data-stu-id="c71b0-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3. <span data-ttu-id="c71b0-111">判斷哪些鎖定 `Variant` 並加以修正。</span><span class="sxs-lookup"><span data-stu-id="c71b0-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c71b0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c71b0-112">See also</span></span>

- [<span data-ttu-id="c71b0-113">陣列</span><span class="sxs-lookup"><span data-stu-id="c71b0-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
