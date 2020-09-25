---
title: LINQ to Objects (C#)
description: '深入瞭解 c # 中的 LINQ to Objects，其 <T> 會在沒有中繼 LINQ 提供者或 API 的情況下，使用具有任何 IEnumerable 或 ienumerable 集合的 LINQ 查詢。'
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: 575708f14487670a4371d470dcdcf650b03c3175
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202522"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="ac798-103">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="ac798-103">LINQ to Objects (C#)</span></span>

<span data-ttu-id="ac798-104">詞彙 "LINQ to Objects" 是指直接搭配使用 LINQ 查詢與任何 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601> 集合，而不要使用中繼 LINQ 提供者或 API (例如 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) 或 [LINQ to XML](../../../../standard/linq/linq-xml-overview.md))。</span><span class="sxs-lookup"><span data-stu-id="ac798-104">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../standard/linq/linq-xml-overview.md).</span></span> <span data-ttu-id="ac798-105">您可以使用 LINQ 查詢任何可列舉的集合，例如 <xref:System.Collections.Generic.List%601>、<xref:System.Array> 或 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="ac798-105">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="ac798-106">集合可能是使用者定義的，也可能是由 .NET API 傳回。</span><span class="sxs-lookup"><span data-stu-id="ac798-106">The collection may be user-defined or may be returned by a .NET API.</span></span>  
  
 <span data-ttu-id="ac798-107">基本上，LINQ to Objects 代表使用集合的新方法。</span><span class="sxs-lookup"><span data-stu-id="ac798-107">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="ac798-108">在舊的方法中，您必須撰寫複雜的 `foreach` 迴圈，以指定如何從集合擷取資料。</span><span class="sxs-lookup"><span data-stu-id="ac798-108">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="ac798-109">在 LINQ 方法中，您會撰寫描述所要擷取內容的宣告式程式碼。</span><span class="sxs-lookup"><span data-stu-id="ac798-109">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="ac798-110">此外，LINQ 查詢還提供三種超越傳統 `foreach` 迴圈的主要優點：</span><span class="sxs-lookup"><span data-stu-id="ac798-110">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
- <span data-ttu-id="ac798-111">它們更加簡潔易懂 (尤其是在篩選多個條件時)。</span><span class="sxs-lookup"><span data-stu-id="ac798-111">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
- <span data-ttu-id="ac798-112">它們只要使用最少的應用程式程式碼，即可提供強大的篩選、排序及群組功能。</span><span class="sxs-lookup"><span data-stu-id="ac798-112">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
- <span data-ttu-id="ac798-113">它們只需要一點修改，甚至不用修改，便可以移植到其他資料來源。</span><span class="sxs-lookup"><span data-stu-id="ac798-113">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="ac798-114">一般來說，您想要對資料執行的作業越複雜，您就可以使用 LINQ 而不是傳統的反復專案技術來實現更多好處。</span><span class="sxs-lookup"><span data-stu-id="ac798-114">In general, the more complex the operation you want to perform on the data, the more benefit you'll realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="ac798-115">本節的目的是要透過一些精選的範例，示範 LINQ 方法，</span><span class="sxs-lookup"><span data-stu-id="ac798-115">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="ac798-116">這並非詳盡的設計。</span><span class="sxs-lookup"><span data-stu-id="ac798-116">It's not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac798-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="ac798-117">In This Section</span></span>  

 [<span data-ttu-id="ac798-118">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="ac798-118">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="ac798-119">說明如何使用 LINQ 查詢及轉換字串與字串集合。</span><span class="sxs-lookup"><span data-stu-id="ac798-119">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="ac798-120">也包含示範這些原則的文章連結。</span><span class="sxs-lookup"><span data-stu-id="ac798-120">Also includes links to articles that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="ac798-121">LINQ 和反映 (C#)</span><span class="sxs-lookup"><span data-stu-id="ac798-121">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="ac798-122">示範 LINQ 如何使用反映的範例連結。</span><span class="sxs-lookup"><span data-stu-id="ac798-122">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="ac798-123">LINQ 和檔案目錄 (C#)</span><span class="sxs-lookup"><span data-stu-id="ac798-123">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="ac798-124">說明如何使用 LINQ 與檔案系統互動。</span><span class="sxs-lookup"><span data-stu-id="ac798-124">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="ac798-125">也包含示範這些概念的文章連結。</span><span class="sxs-lookup"><span data-stu-id="ac798-125">Also includes links to articles that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="ac798-126">如何使用 LINQ (c # ) 查詢 ArrayList </span><span class="sxs-lookup"><span data-stu-id="ac798-126">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="ac798-127">示範如何以 C# 查詢 ArrayList。</span><span class="sxs-lookup"><span data-stu-id="ac798-127">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="ac798-128">如何新增 LINQ 查詢的自訂方法 (c # ) </span><span class="sxs-lookup"><span data-stu-id="ac798-128">How to add custom methods for LINQ queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="ac798-129">說明如何透過將擴充方法加入至 <xref:System.Collections.Generic.IEnumerable%601> 介面，來延伸您可以用於 LINQ 查詢的方法組。</span><span class="sxs-lookup"><span data-stu-id="ac798-129">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="ac798-130">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ac798-130">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="ac798-131">提供文章的連結，說明 LINQ 並提供執行查詢的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="ac798-131">Provides links to articles that explain LINQ and provide examples of code that perform queries.</span></span>
