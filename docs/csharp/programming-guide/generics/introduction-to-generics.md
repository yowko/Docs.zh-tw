---
title: 泛型簡介 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: 0d7ecb7f7fd0bb0985234cdc2cf8d37b53323c86
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595479"
---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="460e5-102">泛型簡介 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="460e5-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="460e5-103">泛型類別和方法將再使用性、型別安全和效率三者結合在一起，發揮了非泛型類別和方法所無法提供的功能。</span><span class="sxs-lookup"><span data-stu-id="460e5-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="460e5-104">泛型最常搭配在其上操作的集合和方法使用。</span><span class="sxs-lookup"><span data-stu-id="460e5-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="460e5-105">.NET Framework 2.0 版類別庫提供了新的命名空間 <xref:System.Collections.Generic>，其中包含數個新的泛型集合類別。</span><span class="sxs-lookup"><span data-stu-id="460e5-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="460e5-106">建議以 .NET Framework 2.0 和更新版本為目標的所有應用程式都使用新的泛型集合類別，而不是舊版的非泛型集合類別，例如 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="460e5-106">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="460e5-107">如需詳細資訊，請參閱 [.NET 的泛型](../../../standard/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="460e5-107">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="460e5-108">當然，您也可以建立自訂的泛型型別和方法，自行處理泛型化的問題，並設計型別安全且有效率的模式。</span><span class="sxs-lookup"><span data-stu-id="460e5-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="460e5-109">下列程式碼範例顯示一個簡單的泛型連結清單類別，以供示範之用</span><span class="sxs-lookup"><span data-stu-id="460e5-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="460e5-110">(在大部分情況下，您應該使用 .NET Framework 類別庫提供的 <xref:System.Collections.Generic.List%601> 類別，而不要自行建立類別)。在幾個位置會使用型別參數 `T`，這些位置一般會使用具象類型來表示清單中儲存的項目類型。</span><span class="sxs-lookup"><span data-stu-id="460e5-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="460e5-111">這個參數可以用於下列方面：</span><span class="sxs-lookup"><span data-stu-id="460e5-111">It is used in the following ways:</span></span>  
  
- <span data-ttu-id="460e5-112">作為 `AddHead` 方法中的方法參數類型。</span><span class="sxs-lookup"><span data-stu-id="460e5-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
- <span data-ttu-id="460e5-113">作為巢狀 `Node` 類別中 `Data` 屬性的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="460e5-113">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
- <span data-ttu-id="460e5-114">作為巢狀類別中私用成員 `data` 的類型。</span><span class="sxs-lookup"><span data-stu-id="460e5-114">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="460e5-115">請注意，T 可用於巢狀 `Node` 類別。</span><span class="sxs-lookup"><span data-stu-id="460e5-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="460e5-116">當 `GenericList<T>` 以具象類型具現化時 (例如具現化為 `GenericList<int>`)，所出現的每個 `T` 都會以 `int` 取代。</span><span class="sxs-lookup"><span data-stu-id="460e5-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="460e5-117">下列程式碼範例示範用戶端程式碼如何使用泛型 `GenericList<T>` 類別建立整數清單。</span><span class="sxs-lookup"><span data-stu-id="460e5-117">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="460e5-118">您只要變更型別引數，就能輕鬆修改下列的程式碼來建立字串清單或任何其他自訂類型的清單：</span><span class="sxs-lookup"><span data-stu-id="460e5-118">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="460e5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="460e5-119">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="460e5-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="460e5-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="460e5-121">泛型</span><span class="sxs-lookup"><span data-stu-id="460e5-121">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
