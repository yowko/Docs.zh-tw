---
title: "宣告為結構成員的陣列無法以初始大小宣告"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords: BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 983154a144a79991c86db5056ad0e0e563a3ba73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="0674d-102">宣告為結構成員的陣列無法以初始大小宣告</span><span class="sxs-lookup"><span data-stu-id="0674d-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="0674d-103">陣列結構中的宣告的初始大小。</span><span class="sxs-lookup"><span data-stu-id="0674d-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="0674d-104">您無法初始化任何結構項目，並宣告陣列大小是一種形式的初始化。</span><span class="sxs-lookup"><span data-stu-id="0674d-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="0674d-105">**錯誤 ID:** BC31043</span><span class="sxs-lookup"><span data-stu-id="0674d-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0674d-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="0674d-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="0674d-107">定義在結構中的陣列，為動態 （沒有初始大小）。</span><span class="sxs-lookup"><span data-stu-id="0674d-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2.  <span data-ttu-id="0674d-108">如果您需要特定大小的陣列，您可以重新維度化與動態陣列[ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md)執行您的程式碼時。</span><span class="sxs-lookup"><span data-stu-id="0674d-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="0674d-109">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="0674d-109">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0674d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0674d-110">See Also</span></span>  
 [<span data-ttu-id="0674d-111">陣列</span><span class="sxs-lookup"><span data-stu-id="0674d-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="0674d-112">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="0674d-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
