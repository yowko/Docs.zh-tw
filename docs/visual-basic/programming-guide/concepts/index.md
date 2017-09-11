---
title: "程式設計概念 (Visual Basic)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: cc9cac84-61f6-476e-b8c7-9bae7749bd90
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 775e4512a5ff31c7059961f6332c6bdc0dc5247a
ms.openlocfilehash: 96c9ec0a5bd9f6b0b2a460e8be15b4f936432016
ms.contentlocale: zh-tw
ms.lasthandoff: 08/11/2017

---
# <a name="programming-concepts-visual-basic"></a><span data-ttu-id="afa12-102">程式設計概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-102">Programming Concepts (Visual Basic)</span></span>
<span data-ttu-id="afa12-103">本節說明 Visual Basic 語言的程式設計概念。</span><span class="sxs-lookup"><span data-stu-id="afa12-103">This section explains programming concepts in the Visual Basic language.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="afa12-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="afa12-104">In This Section</span></span>  
  
|<span data-ttu-id="afa12-105">標題</span><span class="sxs-lookup"><span data-stu-id="afa12-105">Title</span></span>|<span data-ttu-id="afa12-106">說明</span><span class="sxs-lookup"><span data-stu-id="afa12-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="afa12-107">組件和全域組件快取 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-107">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)|<span data-ttu-id="afa12-108">說明如何建立及使用組件。</span><span class="sxs-lookup"><span data-stu-id="afa12-108">Describes how to create and use assemblies.</span></span>|  
|[<span data-ttu-id="afa12-109">使用 Async 和 Await 進行非同步程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-109">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)|<span data-ttu-id="afa12-110">說明如何使用 [Async](../../../visual-basic/language-reference/modifiers/async.md) 和 [Await](../../../visual-basic/language-reference/operators/await-operator.md) 關鍵字撰寫非同步解決方案。</span><span class="sxs-lookup"><span data-stu-id="afa12-110">Describes how to write asynchronous solutions by using [Async](../../../visual-basic/language-reference/modifiers/async.md) and [Await](../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="afa12-111">其中包含逐步解說。</span><span class="sxs-lookup"><span data-stu-id="afa12-111">Includes a walkthrough.</span></span>|  
|[<span data-ttu-id="afa12-112">屬性概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-112">Attributes overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)|<span data-ttu-id="afa12-113">討論如何使用屬性提供關於程式設計元素的其他資訊，例如型別、欄位、方法及屬性。</span><span class="sxs-lookup"><span data-stu-id="afa12-113">Discusses how to provide additional information about programming elements such as types, fields, methods, and properties by using attributes.</span></span>|  
|[<span data-ttu-id="afa12-114">呼叫端資訊 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-114">Caller Information (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/caller-information.md)|<span data-ttu-id="afa12-115">說明如何取得方法呼叫端的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="afa12-115">Describes how to obtain information about the caller of a method.</span></span> <span data-ttu-id="afa12-116">此資訊包括原始程式碼的檔案路徑和行號，以及呼叫端的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="afa12-116">This information includes the file path and the line number of the source code and the member name of the caller.</span></span>|  
|[<span data-ttu-id="afa12-117">集合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-117">Collections (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/collections.md)|<span data-ttu-id="afa12-118">說明部分由 .NET Framework 提供的集合型別。</span><span class="sxs-lookup"><span data-stu-id="afa12-118">Describes some of the types of collections provided by the .NET Framework.</span></span> <span data-ttu-id="afa12-119">示範如何使用簡單集合及金鑰/值組集合。</span><span class="sxs-lookup"><span data-stu-id="afa12-119">Demonstrates how to use simple collections and collections of key/value pairs.</span></span>|  
|[<span data-ttu-id="afa12-120">共變數和反變數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-120">Covariance and Contravariance (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)|<span data-ttu-id="afa12-121">示範如何在介面及委派中啟用泛型型別參數的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="afa12-121">Shows how to enable implicit conversion of generic type parameters in interfaces and delegates.</span></span>|  
|[<span data-ttu-id="afa12-122">運算式樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-122">Expression Trees (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/expression-trees/index.md)|<span data-ttu-id="afa12-123">說明如何使用運算式樹狀結構來啟用可執行程式碼的動態修改。</span><span class="sxs-lookup"><span data-stu-id="afa12-123">Explains how you can use expression trees to enable dynamic modification of executable code.</span></span>|  
|[<span data-ttu-id="afa12-124">迭代器 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-124">Iterators (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/iterators.md)|<span data-ttu-id="afa12-125">說明可用來逐步執行集合，並逐一傳回元素的迭代器。</span><span class="sxs-lookup"><span data-stu-id="afa12-125">Describes iterators, which are used to step through collections and return elements one at a time.</span></span>|  
|[<span data-ttu-id="afa12-126">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-126">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)|<span data-ttu-id="afa12-127">討論 Visual Basic 語言語法中的強大查詢能力，以及查詢關聯式資料庫、XML 文件、資料集和記憶體內部集合的模型。</span><span class="sxs-lookup"><span data-stu-id="afa12-127">Discusses the powerful query capabilities in the language syntax of Visual Basic, and themodel for querying relational databases, XML documents, datasets, and in-memory collections.</span></span>|  
|[<span data-ttu-id="afa12-128">物件導向程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-128">Object-Oriented Programming (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/object-oriented-programming.md)|<span data-ttu-id="afa12-129">說明一般的物件導向概念，包括封裝、繼承和多型。</span><span class="sxs-lookup"><span data-stu-id="afa12-129">Describes common object-oriented concepts, including encapsulation, inheritance, and polymorphism.</span></span>|  
|[<span data-ttu-id="afa12-130">反映 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-130">Reflection (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/reflection.md)|<span data-ttu-id="afa12-131">說明如何使用反映來動態建立型別的執行個體、將型別繫結至現有的物件，或從現有的物件取得型別，並叫用其方法或存取其欄位及屬性。</span><span class="sxs-lookup"><span data-stu-id="afa12-131">Explains how to use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span>|
|[<span data-ttu-id="afa12-132">序列化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-132">Serialization (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/serialization/index.md)|<span data-ttu-id="afa12-133">說明二進位、XML 及 SOAP 序列化的重要概念。</span><span class="sxs-lookup"><span data-stu-id="afa12-133">Describes key concepts in binary, XML, and SOAP serialization.</span></span>|  
|[<span data-ttu-id="afa12-134">執行緒 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa12-134">Threading (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/threading/index.md)|<span data-ttu-id="afa12-135">提供 .NET 執行緒模式的概觀，並示範如何撰寫能同時執行多個工作的程式碼，以提升應用程式的效能和回應性。</span><span class="sxs-lookup"><span data-stu-id="afa12-135">Provides an overview of the .NET threading model and shows how to write code that performs multiple tasks at the same time to improve the performance and responsiveness of your applications.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="afa12-136">相關章節</span><span class="sxs-lookup"><span data-stu-id="afa12-136">Related Sections</span></span>  
  
|||  
|---|---|  
|[<span data-ttu-id="afa12-137">效能秘訣</span><span class="sxs-lookup"><span data-stu-id="afa12-137">Performance Tips</span></span>](../../../framework/performance/performance-tips.md) | <span data-ttu-id="afa12-138">討論數個可能協助您提升應用程式效能的基本規則。</span><span class="sxs-lookup"><span data-stu-id="afa12-138">Discusses several basic rules that may help you increase the performance of your application.</span></span>|

