---
title: HOW TO：使用物件初始設定式初始化物件 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 2ac4242eb1bd24fd54cc1eca97acb96f39cc050b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607026"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="cec5f-102">HOW TO：使用物件初始設定式初始化物件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="cec5f-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>

<span data-ttu-id="cec5f-103">您可以使用物件初始設定式以宣告方式初始化類型物件，而不需要明確叫用該類型的建構函式。</span><span class="sxs-lookup"><span data-stu-id="cec5f-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="cec5f-104">下列範例示範如何搭配具名物件使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="cec5f-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="cec5f-105">編譯器會先存取預設執行個體建構函式，再處理成員初始化，來處理物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="cec5f-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="cec5f-106">因此，如果預設建構函式在類別中宣告為 `private`，需要公用存取的物件初始設定式將會失敗。</span><span class="sxs-lookup"><span data-stu-id="cec5f-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="cec5f-107">如果您要定義匿名型別，則必須使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="cec5f-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="cec5f-108">如需詳細資訊，請參閱[＜How to：在查詢中傳回項目屬性的子集](how-to-return-subsets-of-element-properties-in-a-query.md)。</span><span class="sxs-lookup"><span data-stu-id="cec5f-108">For more information, see [How to: Return Subsets of Element Properties in a Query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cec5f-109">範例</span><span class="sxs-lookup"><span data-stu-id="cec5f-109">Example</span></span>  

<span data-ttu-id="cec5f-110">下列範例示範如何使用物件初始設定式，來初始化新的 `StudentName` 類型。</span><span class="sxs-lookup"><span data-stu-id="cec5f-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="cec5f-111">此範例會設定 `StudentName` 類型中的屬性：</span><span class="sxs-lookup"><span data-stu-id="cec5f-111">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp-interactive[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="cec5f-112">物件初始設定式可用來設定物件中的索引子。</span><span class="sxs-lookup"><span data-stu-id="cec5f-112">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="cec5f-113">下列範例定義 `BaseballTeam` 類別，該類別使用索引子來取得及設定不同位置的球員。</span><span class="sxs-lookup"><span data-stu-id="cec5f-113">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="cec5f-114">初始設定式可以根據位置縮寫，或用於每個位置棒球計分卡的數字，來指派球員：</span><span class="sxs-lookup"><span data-stu-id="cec5f-114">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp-interactive[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="cec5f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cec5f-115">See also</span></span>

- [<span data-ttu-id="cec5f-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cec5f-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cec5f-117">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="cec5f-117">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
