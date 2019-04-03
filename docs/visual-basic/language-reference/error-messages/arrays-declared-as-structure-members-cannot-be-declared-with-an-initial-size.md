---
title: 宣告為結構成員的陣列無法以初始大小宣告
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 58889809b3d8d0823784279c421a141dc8056984
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841962"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="af2b3-102">宣告為結構成員的陣列無法以初始大小宣告</span><span class="sxs-lookup"><span data-stu-id="af2b3-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="af2b3-103">陣列在結構中的宣告的初始大小。</span><span class="sxs-lookup"><span data-stu-id="af2b3-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="af2b3-104">您無法初始化任何結構項目，並宣告陣列大小是一種形式的初始化。</span><span class="sxs-lookup"><span data-stu-id="af2b3-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="af2b3-105">**錯誤 ID:** BC31043</span><span class="sxs-lookup"><span data-stu-id="af2b3-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="af2b3-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="af2b3-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="af2b3-107">定義在結構中的陣列，為動態 （沒有初始大小）。</span><span class="sxs-lookup"><span data-stu-id="af2b3-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2.  <span data-ttu-id="af2b3-108">如果您需要特定大小的陣列，您可以重訂維度的動態陣列[ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md)執行您的程式碼時。</span><span class="sxs-lookup"><span data-stu-id="af2b3-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="af2b3-109">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="af2b3-109">The following example illustrates this.</span></span>  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="af2b3-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af2b3-110">See also</span></span>

- [<span data-ttu-id="af2b3-111">陣列</span><span class="sxs-lookup"><span data-stu-id="af2b3-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="af2b3-112">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="af2b3-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
