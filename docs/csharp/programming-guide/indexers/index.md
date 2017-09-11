---
title: "索引子 (C# 程式設計手冊)"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.indexers
dev_langs:
- CSharp
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: 29
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
ms.openlocfilehash: 784308f3073114cd0c07cf15edae527a2654edec
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="1c9ec-102">索引子 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="1c9ec-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="1c9ec-103">索引子允許類別或結構的執行個體像陣列一樣地編製索引。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="1c9ec-104">您不需明確指定型別或執行個體成員，就能設定或擷取已索引的值。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="1c9ec-105">索引子和[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)類似，差異在於它們的存取子會採用參數。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-105">Indexers resemble [properties](../../../csharp/programming-guide/classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="1c9ec-106">下列範例定義具有簡單 [get](../../../csharp/language-reference/keywords/get.md) 和 [set](../../../csharp/language-reference/keywords/set.md) 存取子方法的泛型類別來指派和擷取值。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-106">The following example defines a generic class with simple [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="1c9ec-107">`Program` 類別會建立此類別的執行個體以儲存字串。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 <span data-ttu-id="1c9ec-108">[!code-cs[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1c9ec-108">[!code-cs[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c9ec-109">如需更多範例，請參閱[相關章節](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections)。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-109">For more examples, see [Related Sections](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="1c9ec-110">運算式主體定義</span><span class="sxs-lookup"><span data-stu-id="1c9ec-110">Expression Body Definitions</span></span>  
 
<span data-ttu-id="1c9ec-111">通常會利用索引子的 get 或 set 存取子來組成要傳回或設定值的陳述式。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-111">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="1c9ec-112">運算式主體成員提供簡化的語法來支援此案例。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-112">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="1c9ec-113">從 C# 6 開始，可將唯讀索引子實作為運算式主體成員，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-113">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

<span data-ttu-id="1c9ec-114">[!code-cs[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]</span><span class="sxs-lookup"><span data-stu-id="1c9ec-114">[!code-cs[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]</span></span>  

<span data-ttu-id="1c9ec-115">請注意，`=>` 會引進運算式主體，且不使用 `get` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-115">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="1c9ec-116">從 C# 7 開始，可同時將 get 和 set 存取子實作為運算式主體成員。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-116">Starting with C# 7, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="1c9ec-117">在此情況下，必須同時使用 `get` 和 `set` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-117">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="1c9ec-118">例如: </span><span class="sxs-lookup"><span data-stu-id="1c9ec-118">For example:</span></span>

<span data-ttu-id="1c9ec-119">[!code-cs[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="1c9ec-119">[!code-cs[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]</span></span>  
  
## <a name="indexers-overview"></a><span data-ttu-id="1c9ec-120">索引子概觀</span><span class="sxs-lookup"><span data-stu-id="1c9ec-120">Indexers Overview</span></span>  
  
-   <span data-ttu-id="1c9ec-121">索引子可以讓物件利用與陣列類似的方式編製索引。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-121">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
-   <span data-ttu-id="1c9ec-122">`get` 存取子會傳回值。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-122">A `get` accessor returns a value.</span></span> <span data-ttu-id="1c9ec-123">`set` 存取子會指派值。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-123">A `set` accessor assigns a value.</span></span>  
  
-   <span data-ttu-id="1c9ec-124">[this](../../../csharp/language-reference/keywords/this.md) 關鍵字是用來定義索引子。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-124">The [this](../../../csharp/language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
-   <span data-ttu-id="1c9ec-125">[value`set` 關鍵字是用來定義 ](../../../csharp/language-reference/keywords/value.md) 索引子要指派的值。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-125">The [value](../../../csharp/language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
-   <span data-ttu-id="1c9ec-126">索引子不一定要由整數值編製索引。您可自行決定如何定義特定的查詢機制。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-126">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
-   <span data-ttu-id="1c9ec-127">索引子可以多載。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-127">Indexers can be overloaded.</span></span>  
  
-   <span data-ttu-id="1c9ec-128">索引子可具有一個以上的型式參數，例如，存取二維陣列時。</span><span class="sxs-lookup"><span data-stu-id="1c9ec-128">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
##  <span data-ttu-id="1c9ec-129"><a name="BKMK_RelatedSections"></a> 相關章節</span><span class="sxs-lookup"><span data-stu-id="1c9ec-129"><a name="BKMK_RelatedSections"></a> Related Sections</span></span>  
  
-   [<span data-ttu-id="1c9ec-130">使用索引子</span><span class="sxs-lookup"><span data-stu-id="1c9ec-130">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="1c9ec-131">介面中的索引子</span><span class="sxs-lookup"><span data-stu-id="1c9ec-131">Indexers in Interfaces</span></span>](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [<span data-ttu-id="1c9ec-132">屬性與索引子之間的比較</span><span class="sxs-lookup"><span data-stu-id="1c9ec-132">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [<span data-ttu-id="1c9ec-133">限制存取子的存取範圍</span><span class="sxs-lookup"><span data-stu-id="1c9ec-133">Restricting Accessor Accessibility</span></span>](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="1c9ec-134">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1c9ec-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1c9ec-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c9ec-135">See Also</span></span>  
 <span data-ttu-id="1c9ec-136">[C# 程式設計指南](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1c9ec-136">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="1c9ec-137">屬性</span><span class="sxs-lookup"><span data-stu-id="1c9ec-137">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

