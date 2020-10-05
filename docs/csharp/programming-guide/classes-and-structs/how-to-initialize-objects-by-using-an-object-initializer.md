---
title: '如何使用物件初始化運算式初始化物件-c # 程式設計手冊'
description: '瞭解如何在 c # 中使用物件初始化運算式來初始化類型物件，而不需要叫用函式。 使用物件初始化運算式來定義匿名型別。'
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 97f537a8361c612580cc9bb41cef327e310287c2
ms.sourcegitcommit: d66641bc7c14ad7d02300316e9e7e84a875a0a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2020
ms.locfileid: "91712666"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="87686-104">如何使用物件初始化運算式初始化物件 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="87686-104">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="87686-105">您可以使用物件初始設定式以宣告方式初始化類型物件，而不需要明確叫用該類型的建構函式。</span><span class="sxs-lookup"><span data-stu-id="87686-105">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="87686-106">下列範例示範如何搭配具名物件使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="87686-106">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="87686-107">編譯器會先存取無參數實例的函式，然後處理成員初始化，藉以處理物件初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="87686-107">The compiler processes object initializers by first accessing the parameterless instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="87686-108">因此，如果無參數建構函式在類別中宣告為 `private`，需要公用存取的物件初始設定式將會失敗。</span><span class="sxs-lookup"><span data-stu-id="87686-108">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="87686-109">如果您要定義匿名型別，則必須使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="87686-109">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="87686-110">如需詳細資訊，請參閱 [如何在查詢中傳回元素屬性的子集](how-to-return-subsets-of-element-properties-in-a-query.md)。</span><span class="sxs-lookup"><span data-stu-id="87686-110">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87686-111">範例</span><span class="sxs-lookup"><span data-stu-id="87686-111">Example</span></span>  

<span data-ttu-id="87686-112">下列範例示範如何使用物件初始設定式，來初始化新的 `StudentName` 類型。</span><span class="sxs-lookup"><span data-stu-id="87686-112">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="87686-113">此範例會設定 `StudentName` 類型中的屬性：</span><span class="sxs-lookup"><span data-stu-id="87686-113">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="87686-114">物件初始設定式可用來設定物件中的索引子。</span><span class="sxs-lookup"><span data-stu-id="87686-114">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="87686-115">下列範例定義 `BaseballTeam` 類別，該類別使用索引子來取得及設定不同位置的球員。</span><span class="sxs-lookup"><span data-stu-id="87686-115">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="87686-116">初始設定式可以根據位置縮寫，或用於每個位置棒球計分卡的數字，來指派球員：</span><span class="sxs-lookup"><span data-stu-id="87686-116">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="87686-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87686-117">See also</span></span>

- [<span data-ttu-id="87686-118">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="87686-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="87686-119">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="87686-119">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
