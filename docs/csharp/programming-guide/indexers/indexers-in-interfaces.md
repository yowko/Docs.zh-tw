---
title: 介面中的索引子 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 120b6e72a6ab906437c593d6eb33024d1df8f52b
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207898"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="a8e0f-102">介面中的索引子 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="a8e0f-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="a8e0f-103">索引子可以宣告於 [interface](../../../csharp/language-reference/keywords/interface.md) 上。</span><span class="sxs-lookup"><span data-stu-id="a8e0f-103">Indexers can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="a8e0f-104">介面索引子的存取子在下列方面與[類別](../../../csharp/language-reference/keywords/class.md)索引子的存取子不同：</span><span class="sxs-lookup"><span data-stu-id="a8e0f-104">Accessors of interface indexers differ from the accessors of [class](../../../csharp/language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
-   <span data-ttu-id="a8e0f-105">介面存取子不會使用修飾詞。</span><span class="sxs-lookup"><span data-stu-id="a8e0f-105">Interface accessors do not use modifiers.</span></span>  
  
-   <span data-ttu-id="a8e0f-106">介面存取子沒有主體。</span><span class="sxs-lookup"><span data-stu-id="a8e0f-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="a8e0f-107">因此，存取子的目的是指出索引子是讀寫、唯讀還是唯寫。</span><span class="sxs-lookup"><span data-stu-id="a8e0f-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="a8e0f-108">介面索引子存取子的範例如下：</span><span class="sxs-lookup"><span data-stu-id="a8e0f-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 <span data-ttu-id="a8e0f-109">索引子的簽章必須與相同介面中所宣告之其他所有索引子的簽章不同。</span><span class="sxs-lookup"><span data-stu-id="a8e0f-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8e0f-110">範例</span><span class="sxs-lookup"><span data-stu-id="a8e0f-110">Example</span></span>  
 <span data-ttu-id="a8e0f-111">下列範例示範如何實作介面索引子。</span><span class="sxs-lookup"><span data-stu-id="a8e0f-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 <span data-ttu-id="a8e0f-112">在上述範例中，您可以使用介面成員的完整名稱來使用明確介面成員實作。</span><span class="sxs-lookup"><span data-stu-id="a8e0f-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="a8e0f-113">例如: </span><span class="sxs-lookup"><span data-stu-id="a8e0f-113">For example:</span></span>  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="a8e0f-114">不過，類別實作具有相同索引子簽章的多個介面時，只需要完整名稱，即可避免模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="a8e0f-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="a8e0f-115">例如，如果 `Employee` 類別實作 `ICitizen` 和 `IEmployee` 這兩個介面，而且這兩個介面都具有相同的索引子簽章，則需要明確介面成員實作。</span><span class="sxs-lookup"><span data-stu-id="a8e0f-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="a8e0f-116">也就是說，下列索引子宣告：</span><span class="sxs-lookup"><span data-stu-id="a8e0f-116">That is, the following indexer declaration:</span></span>  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="a8e0f-117">在 `IEmployee` 介面上實作索引子，而下列宣告：</span><span class="sxs-lookup"><span data-stu-id="a8e0f-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="a8e0f-118">在 `ICitizen` 介面上實作索引子。</span><span class="sxs-lookup"><span data-stu-id="a8e0f-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8e0f-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="a8e0f-119">See Also</span></span>  
 [<span data-ttu-id="a8e0f-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a8e0f-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a8e0f-121">索引子</span><span class="sxs-lookup"><span data-stu-id="a8e0f-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="a8e0f-122">屬性</span><span class="sxs-lookup"><span data-stu-id="a8e0f-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="a8e0f-123">介面</span><span class="sxs-lookup"><span data-stu-id="a8e0f-123">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
