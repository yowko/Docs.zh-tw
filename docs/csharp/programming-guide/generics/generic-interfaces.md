---
title: 泛型介面 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 7fc79874c8e1ff24c38d288d3f6708e2851419e3
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423468"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="d9da7-102">泛型介面 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d9da7-102">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="d9da7-103">定義表示集合中項目的泛型集合類別或泛型類別的介面，通常會很有用。</span><span class="sxs-lookup"><span data-stu-id="d9da7-103">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="d9da7-104">泛型類別的喜好設定會使用泛型介面，例如 <xref:System.IComparable%601> 而不是 <xref:System.IComparable>，以避免實值型別的 boxing 和 unboxing 作業。</span><span class="sxs-lookup"><span data-stu-id="d9da7-104">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="d9da7-105">.NET Framework 類別庫會定義數個泛型介面，搭配 <xref:System.Collections.Generic> 命名空間中的集合類別使用。</span><span class="sxs-lookup"><span data-stu-id="d9da7-105">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="d9da7-106">將介面指定為型別參數的條件約束時，只能使用使用實作介面的類型。</span><span class="sxs-lookup"><span data-stu-id="d9da7-106">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="d9da7-107">下列程式碼範例示範衍生自 `GenericList<T>` 類別的 `SortedList<T>` 類別。</span><span class="sxs-lookup"><span data-stu-id="d9da7-107">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="d9da7-108">如需詳細資訊，請參閱[泛型簡介](../../../csharp/programming-guide/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d9da7-108">For more information, see [Introduction to Generics](../../../csharp/programming-guide/generics/index.md).</span></span> <span data-ttu-id="d9da7-109">`SortedList<T>` 會新增條件約束 `where T : IComparable<T>`。</span><span class="sxs-lookup"><span data-stu-id="d9da7-109">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="d9da7-110">這可讓 `SortedList<T>` 的 `BubbleSort` 方法使用 List 元素上的泛型 <xref:System.IComparable%601.CompareTo%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d9da7-110">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="d9da7-111">在此範例中，List 元素是簡單的類別 `Person`，它會實作 `IComparable<Person>`。</span><span class="sxs-lookup"><span data-stu-id="d9da7-111">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 <span data-ttu-id="d9da7-112">多個介面可以指定為單一類型上的條件約束，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d9da7-112">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 <span data-ttu-id="d9da7-113">介面可以定義多個型別參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d9da7-113">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 <span data-ttu-id="d9da7-114">適用於類別的繼承規則也適用於介面：</span><span class="sxs-lookup"><span data-stu-id="d9da7-114">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 <span data-ttu-id="d9da7-115">如果泛型介面是反變數的，泛型介面就可以繼承自非泛型介面，這表示該介面只會使用自己的型別參數當作傳回值。</span><span class="sxs-lookup"><span data-stu-id="d9da7-115">Generic interfaces can inherit from non-generic interfaces if the generic interface is contravariant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="d9da7-116">在 .NET Framework 類別庫中，<xref:System.Collections.Generic.IEnumerable%601> 繼承自 <xref:System.Collections.IEnumerable>，因為在 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 的傳回值和 <xref:System.Collections.Generic.IEnumerator%601.Current%2A> 屬性 getter 中，<xref:System.Collections.Generic.IEnumerable%601> 只會使用 `T`。</span><span class="sxs-lookup"><span data-stu-id="d9da7-116">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="d9da7-117">實體類別可以實作封閉式建構介面，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d9da7-117">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 <span data-ttu-id="d9da7-118">泛型類別可以實作泛型介面或封閉式建構介面，只要類別參數清單提供介面需要的所有引數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d9da7-118">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 <span data-ttu-id="d9da7-119">控制方法多載的規則，和用於泛型類別、泛型結構或泛型介面中的方法的規則一樣。</span><span class="sxs-lookup"><span data-stu-id="d9da7-119">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="d9da7-120">如需詳細資訊，請參閱[泛型方法](../../../csharp/programming-guide/generics/generic-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="d9da7-120">For more information, see [Generic Methods](../../../csharp/programming-guide/generics/generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9da7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9da7-121">See also</span></span>

- [<span data-ttu-id="d9da7-122">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d9da7-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d9da7-123">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="d9da7-123">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="d9da7-124">interface</span><span class="sxs-lookup"><span data-stu-id="d9da7-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)
- [<span data-ttu-id="d9da7-125">泛型</span><span class="sxs-lookup"><span data-stu-id="d9da7-125">Generics</span></span>](~/docs/standard/generics/index.md)
