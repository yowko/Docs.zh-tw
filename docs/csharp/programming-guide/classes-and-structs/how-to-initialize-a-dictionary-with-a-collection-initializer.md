---
title: 如何使用集合初始設定式來初始化字典 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 22f80365b974df66999ac68f7bc2a9ffa7d445a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596813"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="cfdac-102">如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="cfdac-102">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="cfdac-103"><xref:System.Collections.Generic.Dictionary%602> 包含索引鍵/值組的集合。</span><span class="sxs-lookup"><span data-stu-id="cfdac-103">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="cfdac-104">其 <xref:System.Collections.Generic.Dictionary%602.Add*> 方法採用兩個參數，其中之一供索引鍵之用，而另一個則供值之用。</span><span class="sxs-lookup"><span data-stu-id="cfdac-104">Its <xref:System.Collections.Generic.Dictionary%602.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="cfdac-105">若要初始化 <xref:System.Collections.Generic.Dictionary%602> 或任何其 `Add` 方法採用多個參數的所有集合，其中一個方式是將每個參數集以大括弧括住，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cfdac-105">One way to initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, is to enclose each set of parameters in braces as shown in the following example.</span></span> <span data-ttu-id="cfdac-106">另一個選項是使用索引子初始設定式，也會顯示在下列範例中。</span><span class="sxs-lookup"><span data-stu-id="cfdac-106">Another option is to use an index initializer, also shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="cfdac-107">範例</span><span class="sxs-lookup"><span data-stu-id="cfdac-107">Example</span></span>

<span data-ttu-id="cfdac-108">在下列程式碼範例中，<xref:System.Collections.Generic.Dictionary%602> 會使用類型 `StudentName` 的執行個體進行初始化。</span><span class="sxs-lookup"><span data-stu-id="cfdac-108">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  <span data-ttu-id="cfdac-109">第一個初始化使用 `Add` 方法和兩個引數。</span><span class="sxs-lookup"><span data-stu-id="cfdac-109">The first initialization uses the `Add` method with two arguments.</span></span> <span data-ttu-id="cfdac-110">編譯器會針對每組 `int` 索引鍵和 `StudentName` 值產生 `Add` 呼叫。</span><span class="sxs-lookup"><span data-stu-id="cfdac-110">The compiler generates a call to `Add` for each of the pairs of `int` keys and `StudentName` values.</span></span> <span data-ttu-id="cfdac-111">第二個使用 `Dictionary` 類別的公用讀取/寫入索引子方法：</span><span class="sxs-lookup"><span data-stu-id="cfdac-111">The second uses a public read / write indexer method of the `Dictionary` class:</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

<span data-ttu-id="cfdac-112">請注意，在第一個宣告中，該集合的每個項目中都有兩組大括弧。</span><span class="sxs-lookup"><span data-stu-id="cfdac-112">Note the two pairs of braces in each element of the collection in the first declaration.</span></span> <span data-ttu-id="cfdac-113">最內層括號會括住 `StudentName` 的物件初始設定式，最外層括號會括住機碼值組，這組值會新增至 `students` <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="cfdac-113">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="cfdac-114">最後，會以括號括住目錄的整個集合初始設定式。</span><span class="sxs-lookup"><span data-stu-id="cfdac-114">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span> <span data-ttu-id="cfdac-115">在第二個初始化中，指派左側是索引鍵，右側是其值，並使用 `StudentName` 的物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="cfdac-115">In the second initialization, the left side of the assignment is the key and the right side is the value, using an object initializer for `StudentName`.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfdac-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfdac-116">See also</span></span>

- [<span data-ttu-id="cfdac-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cfdac-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cfdac-118">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="cfdac-118">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
