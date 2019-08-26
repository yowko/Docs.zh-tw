---
title: 泛型和屬性 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 99a24a7069145dfad5ce6c9c91f2a8653eb9a224
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589635"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="fe054-102">泛型和屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="fe054-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="fe054-103">屬性可以使用與非泛型型別相同的方式，套用至泛型型別。</span><span class="sxs-lookup"><span data-stu-id="fe054-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="fe054-104">如需套用屬性的詳細資訊，請參閱[屬性](../concepts/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="fe054-104">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="fe054-105">自訂屬性只能參考開放式泛型型別 (未獲得任何型別引數的泛型型別) 和封閉式建構泛型型別 (為所有型別參數提供引數)。</span><span class="sxs-lookup"><span data-stu-id="fe054-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="fe054-106">下列範例使用這個自訂屬性：</span><span class="sxs-lookup"><span data-stu-id="fe054-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="fe054-107">屬性可以參考開放式泛型型別：</span><span class="sxs-lookup"><span data-stu-id="fe054-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="fe054-108">指定多個使用適當逗點數目的型別參數。</span><span class="sxs-lookup"><span data-stu-id="fe054-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="fe054-109">在此範例中，`GenericClass2` 有兩個型別參數：</span><span class="sxs-lookup"><span data-stu-id="fe054-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="fe054-110">屬性可以參考封閉式建構泛型型別：</span><span class="sxs-lookup"><span data-stu-id="fe054-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="fe054-111">參考泛型型別參數的屬性會造成編譯時期錯誤：</span><span class="sxs-lookup"><span data-stu-id="fe054-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="fe054-112">泛型型別無法繼承自 <xref:System.Attribute>：</span><span class="sxs-lookup"><span data-stu-id="fe054-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="fe054-113">若要取得執行階段的泛型型別或型別參數的相關資訊，您可以使用 <xref:System.Reflection> 的方法。</span><span class="sxs-lookup"><span data-stu-id="fe054-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="fe054-114">如需詳細資訊，請參閱[泛型和反映](./generics-and-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="fe054-114">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe054-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe054-115">See also</span></span>

- [<span data-ttu-id="fe054-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="fe054-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fe054-117">泛型</span><span class="sxs-lookup"><span data-stu-id="fe054-117">Generics</span></span>](./index.md)
- [<span data-ttu-id="fe054-118">屬性</span><span class="sxs-lookup"><span data-stu-id="fe054-118">Attributes</span></span>](../../../standard/attributes/index.md)
