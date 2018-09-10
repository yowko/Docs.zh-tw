---
title: '[] 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 19283a795f8cfc444dfcb186dcecc0ea86eb27fd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500448"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b4afd-102">[] 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b4afd-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="b4afd-103">方括號 (`[]`) 可用於陣列、索引子和屬性，</span><span class="sxs-lookup"><span data-stu-id="b4afd-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="b4afd-104">也可與指標搭配使用。</span><span class="sxs-lookup"><span data-stu-id="b4afd-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4afd-105">備註</span><span class="sxs-lookup"><span data-stu-id="b4afd-105">Remarks</span></span>  
 <span data-ttu-id="b4afd-106">陣列類型是後面接著 `[]` 的類型：</span><span class="sxs-lookup"><span data-stu-id="b4afd-106">An array type is a type followed by `[]`:</span></span>  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 <span data-ttu-id="b4afd-107">若要存取某個陣列項目，請以方括號括住所需項目的索引：</span><span class="sxs-lookup"><span data-stu-id="b4afd-107">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 <span data-ttu-id="b4afd-108">如果陣列索引超出範圍，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b4afd-108">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="b4afd-109">陣列索引運算子無法多載；不過，類型可以定義接受一或多個參數的索引子。</span><span class="sxs-lookup"><span data-stu-id="b4afd-109">The array indexing operator cannot be overloaded; however, types can define indexers that take one or more parameters.</span></span> <span data-ttu-id="b4afd-110">索引子參數會由方括號括住，就像陣列索引一樣；但索引子參數可以宣告為任何類型，而不像陣列索引必須是整數型別。</span><span class="sxs-lookup"><span data-stu-id="b4afd-110">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="b4afd-111">例如，.NET Framework 定義 `Hashtable` 類型，該類型會建立任意類型之索引鍵和值的關聯：</span><span class="sxs-lookup"><span data-stu-id="b4afd-111">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 <span data-ttu-id="b4afd-112">方括號也可用來指定[屬性](../../../csharp/programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="b4afd-112">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 <span data-ttu-id="b4afd-113">您可以使用方括號來指定指標的索引：</span><span class="sxs-lookup"><span data-stu-id="b4afd-113">You can use square brackets to index off a pointer:</span></span>  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 <span data-ttu-id="b4afd-114">不會執行任何界限檢查。</span><span class="sxs-lookup"><span data-stu-id="b4afd-114">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b4afd-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b4afd-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b4afd-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4afd-116">See Also</span></span>

- [<span data-ttu-id="b4afd-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="b4afd-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b4afd-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b4afd-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b4afd-119">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="b4afd-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="b4afd-120">陣列</span><span class="sxs-lookup"><span data-stu-id="b4afd-120">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="b4afd-121">索引子</span><span class="sxs-lookup"><span data-stu-id="b4afd-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="b4afd-122">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="b4afd-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="b4afd-123">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="b4afd-123">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
