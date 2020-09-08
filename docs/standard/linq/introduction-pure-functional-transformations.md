---
title: 純功能性轉換簡介-LINQ to XML
description: 熟悉功能性轉換，包括基礎概念和支援的語言結構。
ms.date: 07/20/2015
ms.assetid: 8495c9d9-2d02-4aa0-8a10-9e8794b985fe
ms.openlocfilehash: a2284c1ddff0234bc33f974ee001dde9819cf627
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552813"
---
# <a name="introduction-to-pure-functional-transformations-linq-to-xml"></a><span data-ttu-id="0fe7d-103"> (LINQ to XML) 的純功能性轉換簡介</span><span class="sxs-lookup"><span data-stu-id="0fe7d-103">Introduction to pure functional transformations (LINQ to XML)</span></span>

<span data-ttu-id="0fe7d-104">本節說明功能性轉換，包括基礎的概念與支援的語言建構。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-104">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="0fe7d-105">其中包含程式設計的物件導向與功能性轉換方法，包括如何轉換到後者的建議。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-105">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="0fe7d-106">雖然在許多程式設計案例中都可以使用功能性轉換，但是此處使用 XML 轉換做為具體範例。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-106">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>

 <span data-ttu-id="0fe7d-107">[教學課程：操作 WordprocessingML 檔中的內容](xml-shape-wordprocessingml-documents.md)教學課程提供一系列的範例，每個範例都是在上一個範例中建立的。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-107">The [Tutorial: Manipulate content in a WordprocessingML document](xml-shape-wordprocessingml-documents.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="0fe7d-108">這些範例會示範純功能性轉換方法以管理 XML。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-108">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span> <span data-ttu-id="0fe7d-109">本教學課程假設您有 c # 或 Visual Basic 的實用知識。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-109">This tutorial assumes a working knowledge of C# or Visual Basic.</span></span> <span data-ttu-id="0fe7d-110">本教學課程中不會提供語言結構的詳細語義，但是會適當地提供語言檔的連結。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-110">Detailed semantics of the language constructs aren't provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>

 <span data-ttu-id="0fe7d-111">同時也假設具備資訊科學基本概念與 XML (包括 XML 命名空間) 的實用知識。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-111">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0fe7d-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="0fe7d-112">In this section</span></span>

|<span data-ttu-id="0fe7d-113">發行項</span><span class="sxs-lookup"><span data-stu-id="0fe7d-113">Article</span></span>|<span data-ttu-id="0fe7d-114">描述</span><span class="sxs-lookup"><span data-stu-id="0fe7d-114">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="0fe7d-115">概念和術語 (功能性轉換) </span><span class="sxs-lookup"><span data-stu-id="0fe7d-115">Concepts and terminology (functional transformation)</span></span>](concepts-terminology-functional-transformation.md)|<span data-ttu-id="0fe7d-116">說明純功能性轉換的概念與術語。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-116">Introduces the concepts and terminology of pure functional transformations.</span></span>|
|[<span data-ttu-id="0fe7d-117">功能性程式設計與命令式程式設計</span><span class="sxs-lookup"><span data-stu-id="0fe7d-117">Functional programming vs. imperative programming</span></span>](functional-vs-imperative-programming.md)|<span data-ttu-id="0fe7d-118">比較與對照功能性程式設計與更傳統的命令性 (程序性) 程式設計。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-118">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|
|[<span data-ttu-id="0fe7d-119">重構為純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="0fe7d-119">Refactor into pure functions</span></span>](refactor-pure-functions.md)|<span data-ttu-id="0fe7d-120">說明純虛擬函式，並顯示純虛擬函式與非純虛擬函式的範例。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-120">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|
|[<span data-ttu-id="0fe7d-121">功能性轉換的適用性</span><span class="sxs-lookup"><span data-stu-id="0fe7d-121">Applicability of functional transformation</span></span>](applicability-functional-transformation.md)|<span data-ttu-id="0fe7d-122">描述功能性轉換的典型案例。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-122">Describes typical scenarios for functional transformations.</span></span>|
|[<span data-ttu-id="0fe7d-123">XML 的功能性轉換</span><span class="sxs-lookup"><span data-stu-id="0fe7d-123">Functional transformation of XML</span></span>](functional-transformation-xml.md)|<span data-ttu-id="0fe7d-124">描述轉換 XML 樹狀內容中的功能性轉換。</span><span class="sxs-lookup"><span data-stu-id="0fe7d-124">Describes functional transformations in the context of transforming XML trees.</span></span>|
