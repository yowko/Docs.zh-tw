---
title: 宣告為結構成員的陣列無法以初始大小宣告
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: de9d77aa9ea853b6f044e91878044115588ca77c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701243"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="3db2d-102">宣告為結構成員的陣列無法以初始大小宣告</span><span class="sxs-lookup"><span data-stu-id="3db2d-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="3db2d-103">結構中的陣列是以初始大小來宣告。</span><span class="sxs-lookup"><span data-stu-id="3db2d-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="3db2d-104">您無法初始化任何結構專案，而且宣告陣列大小是一種初始化形式。</span><span class="sxs-lookup"><span data-stu-id="3db2d-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="3db2d-105">**錯誤識別碼：** BC31043</span><span class="sxs-lookup"><span data-stu-id="3db2d-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3db2d-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="3db2d-106">To correct this error</span></span>  
  
1. <span data-ttu-id="3db2d-107">在您的結構中將陣列定義為動態（沒有初始大小）。</span><span class="sxs-lookup"><span data-stu-id="3db2d-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2. <span data-ttu-id="3db2d-108">如果您需要特定大小的陣列，當您的程式碼執行時，可以使用[ReDim 語句](../../../visual-basic/language-reference/statements/redim-statement.md)來為動態陣列進行維數。</span><span class="sxs-lookup"><span data-stu-id="3db2d-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="3db2d-109">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="3db2d-109">The following example illustrates this.</span></span>  
  
    ```vb  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3db2d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3db2d-110">See also</span></span>

- [<span data-ttu-id="3db2d-111">陣列</span><span class="sxs-lookup"><span data-stu-id="3db2d-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="3db2d-112">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="3db2d-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
