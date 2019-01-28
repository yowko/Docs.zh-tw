---
title: 隱含類型陣列 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 2b52bca57bde2fd198fd1621cb8a8f7dfc73ec9e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740758"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="301a1-102">隱含類型陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="301a1-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="301a1-103">您可以建立隱含型別陣列，其中陣列執行個體的類型是從陣列初始設定式中所指定的項目推斷而來。</span><span class="sxs-lookup"><span data-stu-id="301a1-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="301a1-104">任何隱含型別變數的規則也適用於隱含型別陣列。</span><span class="sxs-lookup"><span data-stu-id="301a1-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="301a1-105">如需詳細資訊，請參閱[隱含類型區域變數](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="301a1-105">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
 <span data-ttu-id="301a1-106">隱含型別的陣列以及匿名型別與物件和集合初始設定式通常用於查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="301a1-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>  
  
 <span data-ttu-id="301a1-107">下列範例示範如何建立隱含型別陣列：</span><span class="sxs-lookup"><span data-stu-id="301a1-107">The following examples show how to create an implicitly-typed array:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 <span data-ttu-id="301a1-108">在上述範例中，請注意，使用隱含型別陣列時，在初始化陳述式左邊未使用方括弧。</span><span class="sxs-lookup"><span data-stu-id="301a1-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="301a1-109">也請注意不規則陣列是使用 `new []` 進行初始化，就像一維陣列一樣。</span><span class="sxs-lookup"><span data-stu-id="301a1-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="301a1-110">物件初始設定式中的隱含型別陣列</span><span class="sxs-lookup"><span data-stu-id="301a1-110">Implicitly-typed Arrays in Object Initializers</span></span>

 <span data-ttu-id="301a1-111">當您建立包含陣列的匿名型別時，在類型的物件初始設定式中，陣列必須是隱含型別。</span><span class="sxs-lookup"><span data-stu-id="301a1-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="301a1-112">在下列範例中，`contacts` 是隱含型別的匿名型別陣列，且每個都會包含名為 `PhoneNumbers` 的陣列。</span><span class="sxs-lookup"><span data-stu-id="301a1-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="301a1-113">請注意，`var` 關鍵字未用於物件初始設定式內。</span><span class="sxs-lookup"><span data-stu-id="301a1-113">Note that the `var` keyword is not used inside the object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="301a1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="301a1-114">See also</span></span>

- [<span data-ttu-id="301a1-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="301a1-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="301a1-116">隱含型別區域變數</span><span class="sxs-lookup"><span data-stu-id="301a1-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="301a1-117">陣列</span><span class="sxs-lookup"><span data-stu-id="301a1-117">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="301a1-118">匿名類型</span><span class="sxs-lookup"><span data-stu-id="301a1-118">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="301a1-119">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="301a1-119">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="301a1-120">var</span><span class="sxs-lookup"><span data-stu-id="301a1-120">var</span></span>](../../../csharp/language-reference/keywords/var.md)
- [<span data-ttu-id="301a1-121">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="301a1-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
