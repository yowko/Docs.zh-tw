---
title: 索引子 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 130cc68906be433afc906cfb22759f4ae3dba447
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589453"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="f3427-102">索引子 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f3427-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="f3427-103">索引子允許類別或結構的執行個體像陣列一樣地編製索引。</span><span class="sxs-lookup"><span data-stu-id="f3427-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="f3427-104">您不需明確指定型別或執行個體成員，就能設定或擷取已索引的值。</span><span class="sxs-lookup"><span data-stu-id="f3427-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="f3427-105">索引子和[屬性](../classes-and-structs/properties.md)類似，差異在於它們的存取子會採用參數。</span><span class="sxs-lookup"><span data-stu-id="f3427-105">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="f3427-106">下列範例定義具有簡單 [get](../../language-reference/keywords/get.md) 和 [set](../../language-reference/keywords/set.md) 存取子方法的泛型類別來指派和擷取值。</span><span class="sxs-lookup"><span data-stu-id="f3427-106">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="f3427-107">`Program` 類別會建立此類別的執行個體以儲存字串。</span><span class="sxs-lookup"><span data-stu-id="f3427-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="f3427-108">如需更多範例，請參閱[相關章節](./index.md#BKMK_RelatedSections)。</span><span class="sxs-lookup"><span data-stu-id="f3427-108">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="f3427-109">運算式主體定義</span><span class="sxs-lookup"><span data-stu-id="f3427-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="f3427-110">通常會利用索引子的 get 或 set 存取子來組成要傳回或設定值的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f3427-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="f3427-111">運算式主體成員提供簡化的語法來支援此案例。</span><span class="sxs-lookup"><span data-stu-id="f3427-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="f3427-112">從 C# 6 開始，可將唯讀索引子實作為運算式主體成員，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f3427-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="f3427-113">請注意，`=>` 會引進運算式主體，且不使用 `get` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f3427-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="f3427-114">從 C# 7.0 開始，可同時將 get 和 set 存取子實作為運算式主體成員。</span><span class="sxs-lookup"><span data-stu-id="f3427-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="f3427-115">在此情況下，必須同時使用 `get` 和 `set` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f3427-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="f3427-116">例如：</span><span class="sxs-lookup"><span data-stu-id="f3427-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="f3427-117">索引子概觀</span><span class="sxs-lookup"><span data-stu-id="f3427-117">Indexers Overview</span></span>  
  
- <span data-ttu-id="f3427-118">索引子可以讓物件利用與陣列類似的方式編製索引。</span><span class="sxs-lookup"><span data-stu-id="f3427-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="f3427-119">`get` 存取子會傳回值。</span><span class="sxs-lookup"><span data-stu-id="f3427-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="f3427-120">`set` 存取子會指派值。</span><span class="sxs-lookup"><span data-stu-id="f3427-120">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="f3427-121">[this](../../language-reference/keywords/this.md) 關鍵字是用來定義索引子。</span><span class="sxs-lookup"><span data-stu-id="f3427-121">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="f3427-122">[value`set` 關鍵字是用來定義 ](../../language-reference/keywords/value.md) 索引子要指派的值。</span><span class="sxs-lookup"><span data-stu-id="f3427-122">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="f3427-123">索引子不一定要由整數值編製索引。您可自行決定如何定義特定的查詢機制。</span><span class="sxs-lookup"><span data-stu-id="f3427-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="f3427-124">索引子可以多載。</span><span class="sxs-lookup"><span data-stu-id="f3427-124">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="f3427-125">索引子可具有一個以上的型式參數，例如，存取二維陣列時。</span><span class="sxs-lookup"><span data-stu-id="f3427-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="BKMK_RelatedSections"></a> <span data-ttu-id="f3427-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="f3427-126">Related Sections</span></span>  
  
- [<span data-ttu-id="f3427-127">使用索引子</span><span class="sxs-lookup"><span data-stu-id="f3427-127">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="f3427-128">介面中的索引子</span><span class="sxs-lookup"><span data-stu-id="f3427-128">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="f3427-129">屬性與索引子之間的比較</span><span class="sxs-lookup"><span data-stu-id="f3427-129">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="f3427-130">限制存取子的存取範圍</span><span class="sxs-lookup"><span data-stu-id="f3427-130">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="f3427-131">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f3427-131">C# Language Specification</span></span>  

<span data-ttu-id="f3427-132">如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)中的[索引子](~/_csharplang/spec/classes.md#indexers)。</span><span class="sxs-lookup"><span data-stu-id="f3427-132">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="f3427-133">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="f3427-133">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f3427-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3427-134">See also</span></span>

- [<span data-ttu-id="f3427-135">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f3427-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f3427-136">屬性</span><span class="sxs-lookup"><span data-stu-id="f3427-136">Properties</span></span>](../classes-and-structs/properties.md)
