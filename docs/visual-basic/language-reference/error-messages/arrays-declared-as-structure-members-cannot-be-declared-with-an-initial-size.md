---
title: 宣告為結構成員的陣列無法以初始大小宣告
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 83342b780c0fa7c3a2e0a6797b80ef788117ae92
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250145"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="87b2f-102">宣告為結構成員的陣列無法以初始大小宣告</span><span class="sxs-lookup"><span data-stu-id="87b2f-102">Arrays declared as structure members cannot be declared with an initial size</span></span>

<span data-ttu-id="87b2f-103">結構中的陣列是以初始大小來宣告。</span><span class="sxs-lookup"><span data-stu-id="87b2f-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="87b2f-104">您無法初始化任何結構專案，而且宣告陣列大小是一種初始化形式。</span><span class="sxs-lookup"><span data-stu-id="87b2f-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>

<span data-ttu-id="87b2f-105">**錯誤識別碼：** BC31043</span><span class="sxs-lookup"><span data-stu-id="87b2f-105">**Error ID:** BC31043</span></span>

## <a name="example"></a><span data-ttu-id="87b2f-106">範例</span><span class="sxs-lookup"><span data-stu-id="87b2f-106">Example</span></span>

<span data-ttu-id="87b2f-107">下列範例會產生 BC31043：</span><span class="sxs-lookup"><span data-stu-id="87b2f-107">The following example generates BC31043:</span></span>

```vb
Structure DemoStruct
    Public demoArray(9) As Integer
End Structure
```

## <a name="to-correct-this-error"></a><span data-ttu-id="87b2f-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="87b2f-108">To correct this error</span></span>

1. <span data-ttu-id="87b2f-109">在您的結構中將陣列定義為動態（沒有初始大小）。</span><span class="sxs-lookup"><span data-stu-id="87b2f-109">Define the array in your structure as dynamic (no initial size).</span></span>

2. <span data-ttu-id="87b2f-110">如果您需要特定大小的陣列，當您的程式碼執行時，可以使用[ReDim 語句](../statements/redim-statement.md)來為動態陣列進行維數。</span><span class="sxs-lookup"><span data-stu-id="87b2f-110">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="87b2f-111">下面這個範例可說明這點：</span><span class="sxs-lookup"><span data-stu-id="87b2f-111">The following example illustrates this:</span></span>
  
    ```vb
    Structure DemoStruct
        Public demoArray() As Integer
    End Structure
    Sub UseStruct()
        Dim struct As DemoStruct  
        ReDim struct.demoArray(9)
        Struct.demoArray(2) = 777
    End Sub  
    ```
  
## <a name="see-also"></a><span data-ttu-id="87b2f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87b2f-112">See also</span></span>

- [<span data-ttu-id="87b2f-113">陣列</span><span class="sxs-lookup"><span data-stu-id="87b2f-113">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="87b2f-114">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="87b2f-114">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
