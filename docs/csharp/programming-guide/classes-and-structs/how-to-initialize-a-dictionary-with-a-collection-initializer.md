---
title: 如何使用集合初始設定式來初始化字典 - C# 程式設計手冊
description: '瞭解如何使用 Add 方法或索引初始化運算式，以 c # 初始化字典。 這個範例會顯示這兩個選項。'
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 667b39076f01ab59eb64cf31d7c1dbb921500135
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099334"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="b452e-104">如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b452e-104">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="b452e-105"><xref:System.Collections.Generic.Dictionary%602> 包含索引鍵/值組的集合。</span><span class="sxs-lookup"><span data-stu-id="b452e-105">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="b452e-106">其 <xref:System.Collections.Generic.Dictionary%602.Add%2A> 方法採用兩個參數，其中之一供索引鍵之用，而另一個則供值之用。</span><span class="sxs-lookup"><span data-stu-id="b452e-106">Its <xref:System.Collections.Generic.Dictionary%602.Add%2A> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="b452e-107">若要初始化 <xref:System.Collections.Generic.Dictionary%602> 或任何其 `Add` 方法採用多個參數的所有集合，其中一個方式是將每個參數集以大括弧括住，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b452e-107">One way to initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, is to enclose each set of parameters in braces as shown in the following example.</span></span> <span data-ttu-id="b452e-108">另一個選項是使用索引子初始設定式，也會顯示在下列範例中。</span><span class="sxs-lookup"><span data-stu-id="b452e-108">Another option is to use an index initializer, also shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="b452e-109">範例</span><span class="sxs-lookup"><span data-stu-id="b452e-109">Example</span></span>

<span data-ttu-id="b452e-110">在下列程式碼範例中，<xref:System.Collections.Generic.Dictionary%602> 會使用類型 `StudentName` 的執行個體進行初始化。</span><span class="sxs-lookup"><span data-stu-id="b452e-110">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  <span data-ttu-id="b452e-111">第一個初始化使用 `Add` 方法和兩個引數。</span><span class="sxs-lookup"><span data-stu-id="b452e-111">The first initialization uses the `Add` method with two arguments.</span></span> <span data-ttu-id="b452e-112">編譯器會針對每組 `int` 索引鍵和 `StudentName` 值產生 `Add` 呼叫。</span><span class="sxs-lookup"><span data-stu-id="b452e-112">The compiler generates a call to `Add` for each of the pairs of `int` keys and `StudentName` values.</span></span> <span data-ttu-id="b452e-113">第二個使用 `Dictionary` 類別的公用讀取/寫入索引子方法：</span><span class="sxs-lookup"><span data-stu-id="b452e-113">The second uses a public read / write indexer method of the `Dictionary` class:</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

<span data-ttu-id="b452e-114">請注意，在第一個宣告中，該集合的每個項目中都有兩組大括弧。</span><span class="sxs-lookup"><span data-stu-id="b452e-114">Note the two pairs of braces in each element of the collection in the first declaration.</span></span> <span data-ttu-id="b452e-115">最內層的括弧會括住的物件初始化運算式 `StudentName` ，而最外層的大括弧則會將將加入的索引鍵/值組的初始化運算式括住 `students` <xref:System.Collections.Generic.Dictionary%602> 。</span><span class="sxs-lookup"><span data-stu-id="b452e-115">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="b452e-116">最後，會以括號括住目錄的整個集合初始設定式。</span><span class="sxs-lookup"><span data-stu-id="b452e-116">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span> <span data-ttu-id="b452e-117">在第二個初始化中，指派左側是索引鍵，右側是其值，並使用 `StudentName` 的物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="b452e-117">In the second initialization, the left side of the assignment is the key and the right side is the value, using an object initializer for `StudentName`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b452e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b452e-118">See also</span></span>

- [<span data-ttu-id="b452e-119">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b452e-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b452e-120">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="b452e-120">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
