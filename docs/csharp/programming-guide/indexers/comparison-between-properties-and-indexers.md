---
title: 屬性與索引子之間的比較 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: a8b347be33ea6acbdf8a78a7af45fd3d0c27f8fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="1757b-102">屬性與索引子之間的比較 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="1757b-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="1757b-103">索引子就像是屬性。</span><span class="sxs-lookup"><span data-stu-id="1757b-103">Indexers are like properties.</span></span> <span data-ttu-id="1757b-104">除了下表所列的差異外，所有為屬性存取子定義的規則也適用於索引子存取子。</span><span class="sxs-lookup"><span data-stu-id="1757b-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="1757b-105">屬性</span><span class="sxs-lookup"><span data-stu-id="1757b-105">Property</span></span>|<span data-ttu-id="1757b-106">索引子</span><span class="sxs-lookup"><span data-stu-id="1757b-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="1757b-107">允許方法接受呼叫，就像是公用資料成員一樣。</span><span class="sxs-lookup"><span data-stu-id="1757b-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="1757b-108">允許使用物件本身的陣列標記法，存取物件的內部集合元素。</span><span class="sxs-lookup"><span data-stu-id="1757b-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="1757b-109">透過簡單名稱存取。</span><span class="sxs-lookup"><span data-stu-id="1757b-109">Accessed through a simple name.</span></span>|<span data-ttu-id="1757b-110">透過索引存取。</span><span class="sxs-lookup"><span data-stu-id="1757b-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="1757b-111">可以是靜態或執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="1757b-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="1757b-112">必須是執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="1757b-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="1757b-113">屬性的 [get](../../../csharp/language-reference/keywords/get.md) 存取子沒有參數。</span><span class="sxs-lookup"><span data-stu-id="1757b-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="1757b-114">索引子的 `get` 存取子擁有與索引子相同的型式參數清單。</span><span class="sxs-lookup"><span data-stu-id="1757b-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="1757b-115">屬性的 [set](../../../csharp/language-reference/keywords/set.md) 存取子包含隱含的 `value` 參數。</span><span class="sxs-lookup"><span data-stu-id="1757b-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="1757b-116">索引子的 `set` 存取子擁有與索引子相同的型式參數清單，同時也擁有 [value](../../../csharp/language-reference/keywords/value.md) 參數。</span><span class="sxs-lookup"><span data-stu-id="1757b-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="1757b-117">支援縮短的語法與[自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1757b-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="1757b-118">不支援縮短的語法。</span><span class="sxs-lookup"><span data-stu-id="1757b-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1757b-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="1757b-119">See Also</span></span>  
 [<span data-ttu-id="1757b-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1757b-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1757b-121">索引子</span><span class="sxs-lookup"><span data-stu-id="1757b-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="1757b-122">屬性</span><span class="sxs-lookup"><span data-stu-id="1757b-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
