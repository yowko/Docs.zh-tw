---
title: 指標比較 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 5185bd5e1686858452efcc7c89e2c1977e094386
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969202"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="0f417-102">指標比較 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="0f417-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="0f417-103">您可以套用下列運算子來比較任何類型的指標：</span><span class="sxs-lookup"><span data-stu-id="0f417-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="0f417-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="0f417-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="0f417-105">比較運算子會比較兩個運算元的位址，就像它們是不帶正負號的整數一樣。</span><span class="sxs-lookup"><span data-stu-id="0f417-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f417-106">範例</span><span class="sxs-lookup"><span data-stu-id="0f417-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#16)]  
  
 [!code-csharp[csProgGuidePointers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#17)]  
  
## <a name="sample-output"></a><span data-ttu-id="0f417-107">範例輸出</span><span class="sxs-lookup"><span data-stu-id="0f417-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="0f417-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f417-108">See also</span></span>

- [<span data-ttu-id="0f417-109">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0f417-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0f417-110">指標運算式</span><span class="sxs-lookup"><span data-stu-id="0f417-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="0f417-111">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="0f417-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="0f417-112">指標操作</span><span class="sxs-lookup"><span data-stu-id="0f417-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [<span data-ttu-id="0f417-113">指標型別</span><span class="sxs-lookup"><span data-stu-id="0f417-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="0f417-114">型別</span><span class="sxs-lookup"><span data-stu-id="0f417-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="0f417-115">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="0f417-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="0f417-116">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="0f417-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="0f417-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="0f417-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
