---
title: 屬性與索引子之間的比較 - C# 程式設計指南
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712126"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="f0c30-102">屬性與索引子之間的比較 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f0c30-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="f0c30-103">索引子就像是屬性。</span><span class="sxs-lookup"><span data-stu-id="f0c30-103">Indexers are like properties.</span></span> <span data-ttu-id="f0c30-104">除了下表所列的差異外，所有為屬性存取子定義的規則也適用於索引子存取子。</span><span class="sxs-lookup"><span data-stu-id="f0c30-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="f0c30-105">屬性</span><span class="sxs-lookup"><span data-stu-id="f0c30-105">Property</span></span>|<span data-ttu-id="f0c30-106">索引器</span><span class="sxs-lookup"><span data-stu-id="f0c30-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="f0c30-107">允許方法接受呼叫，就像是公用資料成員一樣。</span><span class="sxs-lookup"><span data-stu-id="f0c30-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="f0c30-108">允許使用物件本身的陣列標記法，存取物件的內部集合元素。</span><span class="sxs-lookup"><span data-stu-id="f0c30-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="f0c30-109">透過簡單名稱存取。</span><span class="sxs-lookup"><span data-stu-id="f0c30-109">Accessed through a simple name.</span></span>|<span data-ttu-id="f0c30-110">透過索引存取。</span><span class="sxs-lookup"><span data-stu-id="f0c30-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="f0c30-111">可以是靜態或執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="f0c30-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="f0c30-112">必須是執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="f0c30-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="f0c30-113">屬性的 [get](../../language-reference/keywords/get.md) 存取子沒有參數。</span><span class="sxs-lookup"><span data-stu-id="f0c30-113">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="f0c30-114">索引子的 `get` 存取子擁有與索引子相同的型式參數清單。</span><span class="sxs-lookup"><span data-stu-id="f0c30-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="f0c30-115">屬性的 [set](../../language-reference/keywords/set.md) 存取子包含隱含的 `value` 參數。</span><span class="sxs-lookup"><span data-stu-id="f0c30-115">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="f0c30-116">索引子的 `set` 存取子擁有與索引子相同的型式參數清單，同時也擁有 [value](../../language-reference/keywords/value.md) 參數。</span><span class="sxs-lookup"><span data-stu-id="f0c30-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="f0c30-117">支援縮短的語法與[自動實作的屬性](../classes-and-structs/auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f0c30-117">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="f0c30-118">支援針對僅取得索引子使用運算式主體的成員。</span><span class="sxs-lookup"><span data-stu-id="f0c30-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0c30-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0c30-119">See also</span></span>

- [<span data-ttu-id="f0c30-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f0c30-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f0c30-121">索引子</span><span class="sxs-lookup"><span data-stu-id="f0c30-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="f0c30-122">屬性</span><span class="sxs-lookup"><span data-stu-id="f0c30-122">Properties</span></span>](../classes-and-structs/properties.md)
