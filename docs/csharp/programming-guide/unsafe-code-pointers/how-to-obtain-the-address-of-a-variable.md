---
title: 操作說明：取得變數位址 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: 3e2eac468643b755c6db2d6055427baa7ce2b7a7
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241771"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="8f764-102">操作說明：取得變數位址 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="8f764-102">How to: obtain the address of a variable (C# Programming Guide)</span></span>

<span data-ttu-id="8f764-103">若要取得評估為固定變數之一元運算式的位址，請使用傳址運算子 `&`：</span><span class="sxs-lookup"><span data-stu-id="8f764-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator `&`:</span></span>  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="8f764-104">傳址運算子只能套用至變數。</span><span class="sxs-lookup"><span data-stu-id="8f764-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="8f764-105">如果變數是可移動的變數，您可以使用 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)暫時修正變數，然後再取得其位址。</span><span class="sxs-lookup"><span data-stu-id="8f764-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="8f764-106">您必須負責確保變數已初始化。</span><span class="sxs-lookup"><span data-stu-id="8f764-106">It's your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="8f764-107">如果變數未初始化，編譯器不會發出錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="8f764-107">The compiler doesn't issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="8f764-108">您無法取得常數或值的位址。</span><span class="sxs-lookup"><span data-stu-id="8f764-108">You can't get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f764-109">範例</span><span class="sxs-lookup"><span data-stu-id="8f764-109">Example</span></span>  
 <span data-ttu-id="8f764-110">在此範例中，`int`、`p` 的指標會宣告並指派 `number` 整數變數的位址。</span><span class="sxs-lookup"><span data-stu-id="8f764-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="8f764-111">`number` 變數會初始化，作為指派給 `*p` 的結果。</span><span class="sxs-lookup"><span data-stu-id="8f764-111">The variable `number` is initialized as a result of the assignment to `*p`.</span></span> <span data-ttu-id="8f764-112">如果您將這個指派陳述式標記為註解，即會移除 `number` 變數的初始化，而不會發出任何編譯時錯誤。</span><span class="sxs-lookup"><span data-stu-id="8f764-112">If you comment out this assignment statement, the initialization of the variable `number` is removed, but no compile-time error is issued.</span></span>  

> [!NOTE]
> <span data-ttu-id="8f764-113">請使用 [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項來編譯此範例。</span><span class="sxs-lookup"><span data-stu-id="8f764-113">Compile this example with the [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="8f764-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8f764-114">See Also</span></span>

- [<span data-ttu-id="8f764-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8f764-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8f764-116">指標運算式</span><span class="sxs-lookup"><span data-stu-id="8f764-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="8f764-117">指標型別</span><span class="sxs-lookup"><span data-stu-id="8f764-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="8f764-118">型別</span><span class="sxs-lookup"><span data-stu-id="8f764-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="8f764-119">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="8f764-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="8f764-120">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="8f764-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="8f764-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="8f764-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
