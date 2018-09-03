---
title: 如何：使用指標存取陣列元素 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 6d334459b0d530ec37925c98abfd061c04ce1290
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485647"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a><span data-ttu-id="d8f9c-102">如何：使用指標存取陣列元素 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d8f9c-102">How to: Access an Array Element with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="d8f9c-103">在不安全的內容中，您可以使用指標元素存取來存取記憶體中的元素，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="d8f9c-103">In an unsafe context, you can access an element in memory by using pointer element access, as shown in the following example:</span></span>  
  
```csharp  
char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 <span data-ttu-id="d8f9c-104">方括弧中的運算式必須以隱含方式轉換成 `int`、`uint`、`long` 或 `ulong`。</span><span class="sxs-lookup"><span data-stu-id="d8f9c-104">The expression in square brackets must be implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="d8f9c-105">作業 p[e] 相當於 \*(p+e)。</span><span class="sxs-lookup"><span data-stu-id="d8f9c-105">The operation p[e] is equivalent to \*(p+e).</span></span> <span data-ttu-id="d8f9c-106">如同 C 和 C++，指標元素存取不會檢查超出範圍的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8f9c-106">Like C and C++, the pointer element access does not check for out-of-bounds errors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8f9c-107">範例</span><span class="sxs-lookup"><span data-stu-id="d8f9c-107">Example</span></span>  
 <span data-ttu-id="d8f9c-108">在此範例中，123 記憶體位置是配置在字元陣列 `charPointer`。</span><span class="sxs-lookup"><span data-stu-id="d8f9c-108">In this example, 123 memory locations are allocated to a character array, `charPointer`.</span></span> <span data-ttu-id="d8f9c-109">陣列是用來顯示兩個 [for](../../../csharp/language-reference/keywords/for.md) 迴圈中的小寫字母和大寫字母。</span><span class="sxs-lookup"><span data-stu-id="d8f9c-109">The array is used to display the lowercase letters and the uppercase letters in two [for](../../../csharp/language-reference/keywords/for.md) loops.</span></span>  
  
 <span data-ttu-id="d8f9c-110">請注意，運算式 `charPointer[i]` 相當於運算式 `*(charPointer + i)`，而且您可以使用任一運算式取得相同的結果。</span><span class="sxs-lookup"><span data-stu-id="d8f9c-110">Notice that the expression `charPointer[i]` is equivalent to the expression `*(charPointer + i)`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]  
  
 <span data-ttu-id="d8f9c-111">**大寫字母：**</span><span class="sxs-lookup"><span data-stu-id="d8f9c-111">**Uppercase letters:**</span></span>  
<span data-ttu-id="d8f9c-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span><span class="sxs-lookup"><span data-stu-id="d8f9c-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span></span>  
<span data-ttu-id="d8f9c-113">**小寫字母：**</span><span class="sxs-lookup"><span data-stu-id="d8f9c-113">**Lowercase letters:**</span></span>  
<span data-ttu-id="d8f9c-114">**abcdefghijklmnopqrstuvwxyz**</span><span class="sxs-lookup"><span data-stu-id="d8f9c-114">**abcdefghijklmnopqrstuvwxyz**</span></span>   
## <a name="see-also"></a><span data-ttu-id="d8f9c-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8f9c-115">See Also</span></span>  
 [<span data-ttu-id="d8f9c-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d8f9c-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d8f9c-117">指標運算式</span><span class="sxs-lookup"><span data-stu-id="d8f9c-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="d8f9c-118">指標型別</span><span class="sxs-lookup"><span data-stu-id="d8f9c-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="d8f9c-119">型別</span><span class="sxs-lookup"><span data-stu-id="d8f9c-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="d8f9c-120">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="d8f9c-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="d8f9c-121">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="d8f9c-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="d8f9c-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="d8f9c-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
