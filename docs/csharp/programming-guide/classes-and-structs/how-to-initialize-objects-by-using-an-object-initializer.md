---
title: '如何使用物件初始化運算式初始化物件-c # 程式設計手冊'
description: '瞭解如何在 c # 中使用物件初始化運算式來初始化類型物件，而不需要叫用函式。 使用物件初始化運算式來定義匿名型別。'
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 032bbbff3ad356f9718053e8ba54a53559ef1ace
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95098680"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="1c225-104">如何使用物件初始化運算式初始化物件 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="1c225-104">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="1c225-105">您可以使用物件初始設定式以宣告方式初始化類型物件，而不需要明確叫用該類型的建構函式。</span><span class="sxs-lookup"><span data-stu-id="1c225-105">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="1c225-106">下列範例示範如何搭配具名物件使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="1c225-106">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="1c225-107">編譯器會先存取無參數實例的函式，然後處理成員初始化，藉以處理物件初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="1c225-107">The compiler processes object initializers by first accessing the parameterless instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="1c225-108">因此，如果無參數建構函式在類別中宣告為 `private`，需要公用存取的物件初始設定式將會失敗。</span><span class="sxs-lookup"><span data-stu-id="1c225-108">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="1c225-109">如果您要定義匿名型別，則必須使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="1c225-109">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="1c225-110">如需詳細資訊，請參閱 [如何在查詢中傳回元素屬性的子集](how-to-return-subsets-of-element-properties-in-a-query.md)。</span><span class="sxs-lookup"><span data-stu-id="1c225-110">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c225-111">範例</span><span class="sxs-lookup"><span data-stu-id="1c225-111">Example</span></span>  

<span data-ttu-id="1c225-112">下列範例示範如何使用物件初始設定式，來初始化新的 `StudentName` 類型。</span><span class="sxs-lookup"><span data-stu-id="1c225-112">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="1c225-113">此範例會設定 `StudentName` 類型中的屬性：</span><span class="sxs-lookup"><span data-stu-id="1c225-113">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="1c225-114">物件初始設定式可用來設定物件中的索引子。</span><span class="sxs-lookup"><span data-stu-id="1c225-114">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="1c225-115">下列範例定義 `BaseballTeam` 類別，該類別使用索引子來取得及設定不同位置的球員。</span><span class="sxs-lookup"><span data-stu-id="1c225-115">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="1c225-116">初始設定式可以根據位置縮寫，或用於每個位置棒球計分卡的數字，來指派球員：</span><span class="sxs-lookup"><span data-stu-id="1c225-116">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="1c225-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c225-117">See also</span></span>

- [<span data-ttu-id="1c225-118">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1c225-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1c225-119">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="1c225-119">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
