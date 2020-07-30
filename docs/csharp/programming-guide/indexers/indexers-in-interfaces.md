---
title: 介面中的索引子 - C# 程式設計指南
description: '您可以在 c # 中的介面上宣告索引子。 瞭解介面索引子的存取子與類別索引子的存取子有何不同。'
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: ec77843bdf3181a543bd6c02cfb034b21ded1ae7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303097"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="997d7-104">介面中的索引子 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="997d7-104">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="997d7-105">索引子可以宣告於 [interface](../../language-reference/keywords/interface.md) 上。</span><span class="sxs-lookup"><span data-stu-id="997d7-105">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="997d7-106">介面索引子的存取子在下列方面與[類別](../../language-reference/keywords/class.md)索引子的存取子不同：</span><span class="sxs-lookup"><span data-stu-id="997d7-106">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="997d7-107">介面存取子不會使用修飾詞。</span><span class="sxs-lookup"><span data-stu-id="997d7-107">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="997d7-108">介面存取子通常沒有主體。</span><span class="sxs-lookup"><span data-stu-id="997d7-108">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="997d7-109">存取子的目的是要指出索引子是讀寫、唯讀或僅寫入。</span><span class="sxs-lookup"><span data-stu-id="997d7-109">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="997d7-110">您可以為介面中定義的索引子提供實作為，但這很罕見。</span><span class="sxs-lookup"><span data-stu-id="997d7-110">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="997d7-111">索引子通常會定義用來存取資料欄位的 API，而且資料欄位不能在介面中定義。</span><span class="sxs-lookup"><span data-stu-id="997d7-111">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="997d7-112">介面索引子存取子的範例如下：</span><span class="sxs-lookup"><span data-stu-id="997d7-112">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="997d7-113">索引子的簽章必須與相同介面中所宣告之其他所有索引子的簽章不同。</span><span class="sxs-lookup"><span data-stu-id="997d7-113">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="997d7-114">範例</span><span class="sxs-lookup"><span data-stu-id="997d7-114">Example</span></span>

<span data-ttu-id="997d7-115">下列範例示範如何實作介面索引子。</span><span class="sxs-lookup"><span data-stu-id="997d7-115">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="997d7-116">在上述範例中，您可以使用介面成員的完整名稱來使用明確介面成員實作。</span><span class="sxs-lookup"><span data-stu-id="997d7-116">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="997d7-117">例如：</span><span class="sxs-lookup"><span data-stu-id="997d7-117">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="997d7-118">不過，類別實作具有相同索引子簽章的多個介面時，只需要完整名稱，即可避免模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="997d7-118">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="997d7-119">例如，如果 `Employee` 類別實作 `ICitizen` 和 `IEmployee` 這兩個介面，而且這兩個介面都具有相同的索引子簽章，則需要明確介面成員實作。</span><span class="sxs-lookup"><span data-stu-id="997d7-119">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="997d7-120">也就是說，下列索引子宣告：</span><span class="sxs-lookup"><span data-stu-id="997d7-120">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
```

<span data-ttu-id="997d7-121">在 `IEmployee` 介面上實作索引子，而下列宣告：</span><span class="sxs-lookup"><span data-stu-id="997d7-121">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="997d7-122">在 `ICitizen` 介面上實作索引子。</span><span class="sxs-lookup"><span data-stu-id="997d7-122">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="997d7-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="997d7-123">See also</span></span>

- [<span data-ttu-id="997d7-124">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="997d7-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="997d7-125">索引子</span><span class="sxs-lookup"><span data-stu-id="997d7-125">Indexers</span></span>](./index.md)
- [<span data-ttu-id="997d7-126">屬性</span><span class="sxs-lookup"><span data-stu-id="997d7-126">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="997d7-127">介面</span><span class="sxs-lookup"><span data-stu-id="997d7-127">Interfaces</span></span>](../interfaces/index.md)
