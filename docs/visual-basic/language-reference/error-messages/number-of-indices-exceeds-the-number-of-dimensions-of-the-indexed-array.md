---
title: 索引數目超過索引陣列維度的數目
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 4d8ffd2c4ad0a386053ced0f98503969723c7168
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409370"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a><span data-ttu-id="92c8a-102">索引數目超過索引陣列維度的數目</span><span class="sxs-lookup"><span data-stu-id="92c8a-102">Number of indices exceeds the number of dimensions of the indexed array</span></span>
<span data-ttu-id="92c8a-103">用來存取陣列項目的索引數目必須與陣列的陣序 (也就是為其宣告的維度數目) 完全相同。</span><span class="sxs-lookup"><span data-stu-id="92c8a-103">The number of indices used to access an array element must be exactly the same as the rank of the array, that is, the number of dimensions declared for it.</span></span>  
  
 <span data-ttu-id="92c8a-104">**錯誤識別碼：** BC30106</span><span class="sxs-lookup"><span data-stu-id="92c8a-104">**Error ID:** BC30106</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="92c8a-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="92c8a-105">To correct this error</span></span>  
  
- <span data-ttu-id="92c8a-106">從陣列參考移除下標，直到注標總數等於陣列的順位。</span><span class="sxs-lookup"><span data-stu-id="92c8a-106">Remove subscripts from the array reference until the total number of subscripts equals the rank of the array.</span></span> <span data-ttu-id="92c8a-107">例如：</span><span class="sxs-lookup"><span data-stu-id="92c8a-107">For example:</span></span>  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="92c8a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92c8a-108">See also</span></span>

- [<span data-ttu-id="92c8a-109">陣列</span><span class="sxs-lookup"><span data-stu-id="92c8a-109">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
