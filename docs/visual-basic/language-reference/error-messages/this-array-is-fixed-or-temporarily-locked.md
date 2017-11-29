---
title: "此陣列為固定長度或暫時鎖定 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: adff10d4ae61e45402df64ebaa3baf146371ff9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="8d051-102">此陣列為固定長度或暫時鎖定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d051-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="8d051-103">此錯誤有下列可能原因：</span><span class="sxs-lookup"><span data-stu-id="8d051-103">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="8d051-104">使用`ReDim`可以變更的固定大小陣列的項目數目。</span><span class="sxs-lookup"><span data-stu-id="8d051-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
-   <span data-ttu-id="8d051-105">Redimensioning 模組層級動態陣列，在其中一個項目已傳遞做為引數至程序。</span><span class="sxs-lookup"><span data-stu-id="8d051-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="8d051-106">如果傳遞的項目，陣列會鎖定以防止解除配置記憶體的程序內參考參數。</span><span class="sxs-lookup"><span data-stu-id="8d051-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
-   <span data-ttu-id="8d051-107">嘗試指派值給`Variant`變數，其中包含屬於陣列、 但`Variant`目前已鎖定。</span><span class="sxs-lookup"><span data-stu-id="8d051-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8d051-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="8d051-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="8d051-109">請原始陣列，而不是藉由宣告它具有固定動態`ReDim`（如果陣列宣告程序內），或藉由宣告但未指定的項目數 （如果在模組層級中宣告陣列。</span><span class="sxs-lookup"><span data-stu-id="8d051-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2.  <span data-ttu-id="8d051-110">決定您是否真的需要將項目，因為它是在模組中的所有程序內為可見。</span><span class="sxs-lookup"><span data-stu-id="8d051-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3.  <span data-ttu-id="8d051-111">判斷哪些鎖定`Variant`及修復它。</span><span class="sxs-lookup"><span data-stu-id="8d051-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d051-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d051-112">See Also</span></span>  
 [<span data-ttu-id="8d051-113">陣列</span><span class="sxs-lookup"><span data-stu-id="8d051-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
