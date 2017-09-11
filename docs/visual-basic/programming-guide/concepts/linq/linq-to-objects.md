---
title: "LINQ to Objects (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 82094ee6232ef5b1884f1b4b15eacb635be758aa
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="2b694-102">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b694-102">LINQ to Objects (Visual Basic)</span></span>
<span data-ttu-id="2b694-103">詞彙 「 LINQ 到物件 」 指的是使用 LINQ 查詢與任何<xref:System.Collections.IEnumerable>或<xref:System.Collections.Generic.IEnumerable%601>集合，而不使用中繼的 LINQ 提供者或 API，例如[LINQ to SQL](https://msdn.microsoft.com/library/bb386976)或[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)。</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="2b694-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) or [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span> <span data-ttu-id="2b694-104">您可以使用 LINQ 來查詢任何可列舉集合，例如<xref:System.Collections.Generic.List%601>， <xref:System.Array>，或<xref:System.Collections.Generic.Dictionary%602>.</xref:System.Collections.Generic.Dictionary%602> </xref:System.Array> </xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="2b694-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="2b694-105">可能是使用者定義的集合，或可能傳回的.NET Framework API。</span><span class="sxs-lookup"><span data-stu-id="2b694-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="2b694-106">基本上，LINQ to Objects 代表集合的新方法。</span><span class="sxs-lookup"><span data-stu-id="2b694-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="2b694-107">在舊的方法中，您必須撰寫複雜的 `For Each` 迴圈，以指定如何從集合擷取資料。</span><span class="sxs-lookup"><span data-stu-id="2b694-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="2b694-108">在 LINQ 方法中，您可以撰寫描述您想要擷取的宣告式程式碼。</span><span class="sxs-lookup"><span data-stu-id="2b694-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="2b694-109">此外，LINQ 查詢提供三個主要的好處，超越傳統`For Each`迴圈︰</span><span class="sxs-lookup"><span data-stu-id="2b694-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1.  <span data-ttu-id="2b694-110">它們更加簡潔易懂 (尤其是在篩選多個條件時)。</span><span class="sxs-lookup"><span data-stu-id="2b694-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2.  <span data-ttu-id="2b694-111">它們只要使用最少的應用程式程式碼，即可提供強大的篩選、排序及群組功能。</span><span class="sxs-lookup"><span data-stu-id="2b694-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3.  <span data-ttu-id="2b694-112">它們只需要一點修改，甚至不用修改，便可以移植到其他資料來源。</span><span class="sxs-lookup"><span data-stu-id="2b694-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="2b694-113">一般而言，越複雜您想要的資料上執行的作業，您會發現使用 LINQ 取代傳統反覆項目技術更多的好處。</span><span class="sxs-lookup"><span data-stu-id="2b694-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="2b694-114">本章節的目的在於示範一些精選的範例的 LINQ 方法。</span><span class="sxs-lookup"><span data-stu-id="2b694-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="2b694-115">而不是要提供詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="2b694-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2b694-116">本章節內容</span><span class="sxs-lookup"><span data-stu-id="2b694-116">In This Section</span></span>  
 [<span data-ttu-id="2b694-117">LINQ 和字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b694-117">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 <span data-ttu-id="2b694-118">說明如何使用 LINQ，查詢及轉換字串與字串集合。</span><span class="sxs-lookup"><span data-stu-id="2b694-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="2b694-119">此外也包含示範這些原理的主題連結。</span><span class="sxs-lookup"><span data-stu-id="2b694-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="2b694-120">LINQ 和反映 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b694-120">LINQ and Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 <span data-ttu-id="2b694-121">示範如何 LINQ 會使用反映的範例連結。</span><span class="sxs-lookup"><span data-stu-id="2b694-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="2b694-122">LINQ 和檔案目錄 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b694-122">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 <span data-ttu-id="2b694-123">說明如何使用 LINQ 與檔案系統互動。</span><span class="sxs-lookup"><span data-stu-id="2b694-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="2b694-124">此外也包含示範這些概念的主題連結。</span><span class="sxs-lookup"><span data-stu-id="2b694-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="2b694-125">如何︰ 使用 LINQ (Visual Basic) 查詢 ArrayList</span><span class="sxs-lookup"><span data-stu-id="2b694-125">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="2b694-126">示範如何以 C# 查詢 ArrayList。</span><span class="sxs-lookup"><span data-stu-id="2b694-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="2b694-127">如何︰ 新增 LINQ 查詢 (Visual Basic) 的自訂方法</span><span class="sxs-lookup"><span data-stu-id="2b694-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="2b694-128">說明如何擴充方法，您可以加入的擴充方法使用 LINQ 查詢的集合<xref:System.Collections.Generic.IEnumerable%601>介面。</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="2b694-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="2b694-129">語言整合查詢 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b694-129">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="2b694-130">提供主題連結，說明 LINQ，並提供執行查詢的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="2b694-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
