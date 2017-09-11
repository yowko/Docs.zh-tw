---
title: "如何：使用指標複製位元組陣列 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 808a74f75e4dcbcec47735d98063138e2c7456e5
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="96512-102">如何：使用指標複製位元組陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="96512-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>
<span data-ttu-id="96512-103">下列範例會使用指標，以將位元組從某個陣列複製到另一個陣列。</span><span class="sxs-lookup"><span data-stu-id="96512-103">The following example uses pointers to copy bytes from one array to another.</span></span>  
  
 <span data-ttu-id="96512-104">這個範例會使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字，讓您可以使用 `Copy` 方法中的指標。</span><span class="sxs-lookup"><span data-stu-id="96512-104">This example uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="96512-105">[fixed](../../../csharp/language-reference/keywords/fixed-statement.md) 陳述式用來宣告來源和目的陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="96512-105">The [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="96512-106">這會將來源和目的陣列的位置「釘選」到記憶體中，讓記憶體回收不會移動它們。</span><span class="sxs-lookup"><span data-stu-id="96512-106">This *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="96512-107">`fixed` 區塊完成時，會取消釘選陣列的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="96512-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="96512-108">因為這個範例中的 `Copy` 方法使用 `unsafe` 關鍵字，所以必須使用 **/unsafe** 編譯器選項進行編譯。</span><span class="sxs-lookup"><span data-stu-id="96512-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the **/unsafe** compiler option.</span></span> <span data-ttu-id="96512-109">若要在 Visual Studio 中設定選項，請以滑鼠右鍵按一下專案名稱，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="96512-109">To set the option in Visual Studio, right-click the project name, and then click **Properties**.</span></span> <span data-ttu-id="96512-110">在 [建置] 索引標籤上，選取 [容許 Unsafe 程式碼]。</span><span class="sxs-lookup"><span data-stu-id="96512-110">On the **Build** tab, select **Allow unsafe code**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96512-111">範例</span><span class="sxs-lookup"><span data-stu-id="96512-111">Example</span></span>  
 <span data-ttu-id="96512-112">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="96512-112">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]</span></span>  
  
 <span data-ttu-id="96512-113">[!code-cs[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="96512-113">[!code-cs[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96512-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96512-114">See Also</span></span>  
 <span data-ttu-id="96512-115">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="96512-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="96512-116">[Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="96512-116">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="96512-117">[/unsafe (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="96512-117">[/unsafe (C# Compiler Options)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) </span></span>  
 [<span data-ttu-id="96512-118">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="96512-118">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)

