---
title: 程式設計概念 (C#)
description: '使用本節中的資源，以瞭解 c # 語言的程式設計概念，包括物件導向程式設計。'
ms.date: 07/20/2015
ms.assetid: 3227afd5-4794-484b-b83b-0f1f94a0476b
ms.openlocfilehash: 5594bd93d70a4f9cf0ab6136b011a5cceea7bf3f
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609391"
---
# <a name="programming-concepts-c"></a><span data-ttu-id="e6e22-103">程式設計概念 (C#)</span><span class="sxs-lookup"><span data-stu-id="e6e22-103">Programming Concepts (C#)</span></span>

<span data-ttu-id="e6e22-104">本節說明 C# 語言的程式設計概念。</span><span class="sxs-lookup"><span data-stu-id="e6e22-104">This section explains programming concepts in the C# language.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e6e22-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="e6e22-105">In This Section</span></span>  
  
|<span data-ttu-id="e6e22-106">標題</span><span class="sxs-lookup"><span data-stu-id="e6e22-106">Title</span></span>|<span data-ttu-id="e6e22-107">說明</span><span class="sxs-lookup"><span data-stu-id="e6e22-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e6e22-108">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="e6e22-108">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)|<span data-ttu-id="e6e22-109">說明如何建立及使用組件。</span><span class="sxs-lookup"><span data-stu-id="e6e22-109">Describes how to create and use assemblies.</span></span>|  
|[<span data-ttu-id="e6e22-110">使用 Async 和 Await 進行非同步程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="e6e22-110">Asynchronous Programming with async and await (C#)</span></span>](./async/index.md)|<span data-ttu-id="e6e22-111">說明如何使用 C# 中的 [async](../../language-reference/keywords/async.md) 和 [await](../../language-reference/operators/await.md) 關鍵字撰寫非同步解決方案。</span><span class="sxs-lookup"><span data-stu-id="e6e22-111">Describes how to write asynchronous solutions by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/operators/await.md) keywords in C#.</span></span> <span data-ttu-id="e6e22-112">其中包含逐步解說。</span><span class="sxs-lookup"><span data-stu-id="e6e22-112">Includes a walkthrough.</span></span>|  
|[<span data-ttu-id="e6e22-113">屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="e6e22-113">Attributes (C#)</span></span>](./attributes/index.md)|<span data-ttu-id="e6e22-114">討論如何使用屬性提供關於程式設計元素的其他資訊，例如型別、欄位、方法及屬性。</span><span class="sxs-lookup"><span data-stu-id="e6e22-114">Discusses how to provide additional information about programming elements such as types, fields, methods, and properties by using attributes.</span></span>|  
|[<span data-ttu-id="e6e22-115">集合 (C#)</span><span class="sxs-lookup"><span data-stu-id="e6e22-115">Collections (C#)</span></span>](./collections.md)|<span data-ttu-id="e6e22-116">描述 .NET 所提供的一些集合類型。</span><span class="sxs-lookup"><span data-stu-id="e6e22-116">Describes some of the types of collections provided by .NET.</span></span> <span data-ttu-id="e6e22-117">示範如何使用簡單集合及金鑰/值組集合。</span><span class="sxs-lookup"><span data-stu-id="e6e22-117">Demonstrates how to use simple collections and collections of key/value pairs.</span></span>|  
|[<span data-ttu-id="e6e22-118">共變數和反變數 (C#)</span><span class="sxs-lookup"><span data-stu-id="e6e22-118">Covariance and Contravariance (C#)</span></span>](./covariance-contravariance/index.md)|<span data-ttu-id="e6e22-119">示範如何在介面及委派中啟用泛型型別參數的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="e6e22-119">Shows how to enable implicit conversion of generic type parameters in interfaces and delegates.</span></span>|  
|[<span data-ttu-id="e6e22-120">運算式樹狀架構 (C#)</span><span class="sxs-lookup"><span data-stu-id="e6e22-120">Expression Trees (C#)</span></span>](./expression-trees/index.md)|<span data-ttu-id="e6e22-121">說明如何使用運算式樹狀結構來啟用可執行程式碼的動態修改。</span><span class="sxs-lookup"><span data-stu-id="e6e22-121">Explains how you can use expression trees to enable dynamic modification of executable code.</span></span>|  
|[<span data-ttu-id="e6e22-122">迭代器 (C#)</span><span class="sxs-lookup"><span data-stu-id="e6e22-122">Iterators (C#)</span></span>](./iterators.md)|<span data-ttu-id="e6e22-123">說明可用來逐步執行集合，並逐一傳回元素的迭代器。</span><span class="sxs-lookup"><span data-stu-id="e6e22-123">Describes iterators, which are used to step through collections and return elements one at a time.</span></span>|  
|[<span data-ttu-id="e6e22-124">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e6e22-124">Language-Integrated Query (LINQ) (C#)</span></span>](./linq/index.md)|<span data-ttu-id="e6e22-125">討論 C# 語言語法中的強大查詢能力，以及查詢關聯式資料庫、XML 文件、資料集，以及記憶體內部集合的模型。</span><span class="sxs-lookup"><span data-stu-id="e6e22-125">Discusses the powerful query capabilities in the language syntax of C#, and the model for querying relational databases, XML documents, datasets, and in-memory collections.</span></span>|  
|[<span data-ttu-id="e6e22-126">反映 (C#)</span><span class="sxs-lookup"><span data-stu-id="e6e22-126">Reflection (C#)</span></span>](./reflection.md)|<span data-ttu-id="e6e22-127">說明如何使用反映來動態建立型別的執行個體、將型別繫結至現有的物件，或從現有的物件取得型別，並叫用其方法或存取其欄位及屬性。</span><span class="sxs-lookup"><span data-stu-id="e6e22-127">Explains how to use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span>|  
|[<span data-ttu-id="e6e22-128">序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="e6e22-128">Serialization (C#)</span></span>](./serialization/index.md)|<span data-ttu-id="e6e22-129">說明二進位、XML 及 SOAP 序列化的重要概念。</span><span class="sxs-lookup"><span data-stu-id="e6e22-129">Describes key concepts in binary, XML, and SOAP serialization.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="e6e22-130">相關章節</span><span class="sxs-lookup"><span data-stu-id="e6e22-130">Related Sections</span></span>  
  
|||  
|---|---|  
|[<span data-ttu-id="e6e22-131">效能秘訣</span><span class="sxs-lookup"><span data-stu-id="e6e22-131">Performance Tips</span></span>](../../../framework/performance/performance-tips.md) | <span data-ttu-id="e6e22-132">討論數個可能協助您提升應用程式效能的基本規則。</span><span class="sxs-lookup"><span data-stu-id="e6e22-132">Discusses several basic rules that may help you increase the performance of your application.</span></span>|
