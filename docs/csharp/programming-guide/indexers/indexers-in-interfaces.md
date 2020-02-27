---
title: 介面中的索引子 - C# 程式設計指南
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627834"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="b2d51-102">介面中的索引子 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b2d51-102">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="b2d51-103">索引子可以宣告於 [interface](../../language-reference/keywords/interface.md) 上。</span><span class="sxs-lookup"><span data-stu-id="b2d51-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="b2d51-104">介面索引子的存取子在下列方面與[類別](../../language-reference/keywords/class.md)索引子的存取子不同：</span><span class="sxs-lookup"><span data-stu-id="b2d51-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="b2d51-105">介面存取子不會使用修飾詞。</span><span class="sxs-lookup"><span data-stu-id="b2d51-105">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="b2d51-106">介面存取子通常沒有主體。</span><span class="sxs-lookup"><span data-stu-id="b2d51-106">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="b2d51-107">存取子的目的是要指出索引子是讀寫、唯讀或僅寫入。</span><span class="sxs-lookup"><span data-stu-id="b2d51-107">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="b2d51-108">您可以為介面中定義的索引子提供實作為，但這很罕見。</span><span class="sxs-lookup"><span data-stu-id="b2d51-108">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="b2d51-109">索引子通常會定義用來存取資料欄位的 API，而且資料欄位不能在介面中定義。</span><span class="sxs-lookup"><span data-stu-id="b2d51-109">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="b2d51-110">介面索引子存取子的範例如下：</span><span class="sxs-lookup"><span data-stu-id="b2d51-110">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="b2d51-111">索引子的簽章必須與相同介面中所宣告之其他所有索引子的簽章不同。</span><span class="sxs-lookup"><span data-stu-id="b2d51-111">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="b2d51-112">範例</span><span class="sxs-lookup"><span data-stu-id="b2d51-112">Example</span></span>

<span data-ttu-id="b2d51-113">下列範例示範如何實作介面索引子。</span><span class="sxs-lookup"><span data-stu-id="b2d51-113">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="b2d51-114">在上述範例中，您可以使用介面成員的完整名稱來使用明確介面成員實作。</span><span class="sxs-lookup"><span data-stu-id="b2d51-114">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="b2d51-115">例如：</span><span class="sxs-lookup"><span data-stu-id="b2d51-115">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="b2d51-116">不過，類別實作具有相同索引子簽章的多個介面時，只需要完整名稱，即可避免模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="b2d51-116">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="b2d51-117">例如，如果 `Employee` 類別實作 `ICitizen` 和 `IEmployee` 這兩個介面，而且這兩個介面都具有相同的索引子簽章，則需要明確介面成員實作。</span><span class="sxs-lookup"><span data-stu-id="b2d51-117">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="b2d51-118">也就是說，下列索引子宣告：</span><span class="sxs-lookup"><span data-stu-id="b2d51-118">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
``

implements the indexer on the `IEmployee` interface, while the following declaration:

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="b2d51-119">在 `ICitizen` 介面上實作索引子。</span><span class="sxs-lookup"><span data-stu-id="b2d51-119">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2d51-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2d51-120">See also</span></span>

- [<span data-ttu-id="b2d51-121">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b2d51-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b2d51-122">索引子</span><span class="sxs-lookup"><span data-stu-id="b2d51-122">Indexers</span></span>](./index.md)
- [<span data-ttu-id="b2d51-123">屬性</span><span class="sxs-lookup"><span data-stu-id="b2d51-123">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="b2d51-124">介面</span><span class="sxs-lookup"><span data-stu-id="b2d51-124">Interfaces</span></span>](../interfaces/index.md)
