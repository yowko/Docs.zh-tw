---
title: "如何：使用指標複製位元組陣列 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 375cab76063e4c77515d6b05b42f2d97ff3efc44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="ffc51-102">如何：使用指標複製位元組陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="ffc51-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>
<span data-ttu-id="ffc51-103">下列範例會使用指標，以將位元組從某個陣列複製到另一個陣列。</span><span class="sxs-lookup"><span data-stu-id="ffc51-103">The following example uses pointers to copy bytes from one array to another.</span></span>  
  
 <span data-ttu-id="ffc51-104">這個範例會使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字，讓您可以使用 `Copy` 方法中的指標。</span><span class="sxs-lookup"><span data-stu-id="ffc51-104">This example uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="ffc51-105">[fixed](../../../csharp/language-reference/keywords/fixed-statement.md) 陳述式用來宣告來源和目的陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="ffc51-105">The [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="ffc51-106">這會將來源和目的陣列的位置「釘選」到記憶體中，讓記憶體回收不會移動它們。</span><span class="sxs-lookup"><span data-stu-id="ffc51-106">This *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="ffc51-107">`fixed` 區塊完成時，會取消釘選陣列的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="ffc51-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="ffc51-108">因為這個範例中的 `Copy` 方法使用 `unsafe` 關鍵字，所以必須使用 **/unsafe** 編譯器選項進行編譯。</span><span class="sxs-lookup"><span data-stu-id="ffc51-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the **/unsafe** compiler option.</span></span> <span data-ttu-id="ffc51-109">若要在 Visual Studio 中設定選項，請以滑鼠右鍵按一下專案名稱，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="ffc51-109">To set the option in Visual Studio, right-click the project name, and then click **Properties**.</span></span> <span data-ttu-id="ffc51-110">在 [建置] 索引標籤上，選取 [容許 Unsafe 程式碼]。</span><span class="sxs-lookup"><span data-stu-id="ffc51-110">On the **Build** tab, select **Allow unsafe code**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffc51-111">範例</span><span class="sxs-lookup"><span data-stu-id="ffc51-111">Example</span></span>  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ffc51-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffc51-112">See Also</span></span>  
 [<span data-ttu-id="ffc51-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ffc51-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ffc51-114">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="ffc51-114">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="ffc51-115">/unsafe (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="ffc51-115">/unsafe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)  
 [<span data-ttu-id="ffc51-116">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="ffc51-116">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
