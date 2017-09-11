---
title: "[] 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '[]_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: 20
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
ms.openlocfilehash: b49d41af0dd4dc34b1b74c62ce8779aa31d69f77
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="b2279-102">[] 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b2279-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="b2279-103">方括號 (`[]`) 可用於陣列、索引子和屬性，</span><span class="sxs-lookup"><span data-stu-id="b2279-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="b2279-104">也可與指標搭配使用。</span><span class="sxs-lookup"><span data-stu-id="b2279-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2279-105">備註</span><span class="sxs-lookup"><span data-stu-id="b2279-105">Remarks</span></span>  
 <span data-ttu-id="b2279-106">陣列類型是後面接著 `[]` 的類型：</span><span class="sxs-lookup"><span data-stu-id="b2279-106">An array type is a type followed by `[]`:</span></span>  
  
 <span data-ttu-id="b2279-107">[!code-cs[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b2279-107">[!code-cs[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="b2279-108">若要存取某個陣列項目，請以方括號括住所需項目的索引：</span><span class="sxs-lookup"><span data-stu-id="b2279-108">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 <span data-ttu-id="b2279-109">[!code-cs[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="b2279-109">[!code-cs[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]</span></span>  
  
 <span data-ttu-id="b2279-110">如果陣列索引超出範圍，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b2279-110">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="b2279-111">陣列索引運算子無法多載；不過，類型可以定義索引子，以及接受一或多個參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2279-111">The array indexing operator cannot be overloaded; however, types can define indexers, and properties that take one or more parameters.</span></span> <span data-ttu-id="b2279-112">索引子參數會由方括號括住，就像陣列索引一樣；但索引子參數可以宣告為任何類型，而不像陣列索引必須是整數型別。</span><span class="sxs-lookup"><span data-stu-id="b2279-112">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="b2279-113">例如，.NET Framework 定義 `Hashtable` 類型，該類型會建立任意類型之索引鍵和值的關聯：</span><span class="sxs-lookup"><span data-stu-id="b2279-113">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 <span data-ttu-id="b2279-114">[!code-cs[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="b2279-114">[!code-cs[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]</span></span>  
  
 <span data-ttu-id="b2279-115">方括號也可用來指定[屬性](../../../csharp/programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="b2279-115">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 <span data-ttu-id="b2279-116">[!code-cs[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="b2279-116">[!code-cs[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]</span></span>  
  
 <span data-ttu-id="b2279-117">您可以使用方括號來指定指標的索引：</span><span class="sxs-lookup"><span data-stu-id="b2279-117">You can use square brackets to index off a pointer:</span></span>  
  
 <span data-ttu-id="b2279-118">[!code-cs[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="b2279-118">[!code-cs[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]</span></span>  
  
 <span data-ttu-id="b2279-119">不會執行任何界限檢查。</span><span class="sxs-lookup"><span data-stu-id="b2279-119">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b2279-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b2279-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b2279-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2279-121">See Also</span></span>  
 <span data-ttu-id="b2279-122">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b2279-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b2279-123">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b2279-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b2279-124">[C# 運算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="b2279-124">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="b2279-125">[陣列](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="b2279-125">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="b2279-126">[索引子](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="b2279-126">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 <span data-ttu-id="b2279-127">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="b2279-127">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 [<span data-ttu-id="b2279-128">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="b2279-128">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)

