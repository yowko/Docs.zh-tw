---
title: "LINQ 和字串 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 94e9627efb183c08bbb67a7e6e82df9132ebdef2
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="linq-and-strings-visual-basic"></a><span data-ttu-id="d5442-102">LINQ 和字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5442-102">LINQ and Strings (Visual Basic)</span></span>
<span data-ttu-id="d5442-103">LINQ 可用於查詢及轉換字串與字串集合。</span><span class="sxs-lookup"><span data-stu-id="d5442-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="d5442-104">它可以是文字檔案中的半結構化資料特別有用。</span><span class="sxs-lookup"><span data-stu-id="d5442-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="d5442-105">LINQ 查詢可以結合傳統字串函數和規則運算式。</span><span class="sxs-lookup"><span data-stu-id="d5442-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="d5442-106">例如，您可以使用<xref:System.String.Split%2A>或<xref:System.Text.RegularExpressions.Regex.Split%2A>方法來建立，您可以再查詢或使用 LINQ 修改的字串陣列。</xref:System.Text.RegularExpressions.Regex.Split%2A> </xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="d5442-106">For example, you can use the <xref:System.String.Split%2A> or <xref:System.Text.RegularExpressions.Regex.Split%2A> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="d5442-107">您可以使用<xref:System.Text.RegularExpressions.Regex.IsMatch%2A>方法中的`where`LINQ 查詢子句。</xref:System.Text.RegularExpressions.Regex.IsMatch%2A></span><span class="sxs-lookup"><span data-stu-id="d5442-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="d5442-108">您可以使用 LINQ 查詢或修改<xref:System.Text.RegularExpressions.MatchCollection>規則運算式所傳回的結果。</xref:System.Text.RegularExpressions.MatchCollection></span><span class="sxs-lookup"><span data-stu-id="d5442-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>  
  
 <span data-ttu-id="d5442-109">您也可以使用本節中所述的技巧來轉換成 XML 的半結構化的文字資料。</span><span class="sxs-lookup"><span data-stu-id="d5442-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="d5442-110">如需詳細資訊，請參閱[How to︰ 從 CSV 檔案產生的 XML](how-to-generate-xml-from-csv-files.md)。</span><span class="sxs-lookup"><span data-stu-id="d5442-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>  
  
 <span data-ttu-id="d5442-111">本章節中的範例分為兩類︰</span><span class="sxs-lookup"><span data-stu-id="d5442-111">The examples in this section fall into two categories:</span></span>  
  
## <a name="querying-a-block-of-text"></a><span data-ttu-id="d5442-112">查詢文字的區塊</span><span class="sxs-lookup"><span data-stu-id="d5442-112">Querying a Block of Text</span></span>  
 <span data-ttu-id="d5442-113">您可以查詢、 分析及修改文字區塊，將它們分割為可查詢的較小的字串陣列中，使用<xref:System.String.Split%2A>方法或<xref:System.Text.RegularExpressions.Regex.Split%2A>方法。</xref:System.Text.RegularExpressions.Regex.Split%2A> </xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="d5442-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A> method.</span></span> <span data-ttu-id="d5442-114">您可以將原始程式文字分割成單字、 句子、 段落、 網頁或其他準則，然後再執行額外的分割，如果您在查詢中需要它們。</span><span class="sxs-lookup"><span data-stu-id="d5442-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>  
  
 [<span data-ttu-id="d5442-115">如何︰ 統計某個字在字串 (LINQ) (Visual Basic) 中的出現次數</span><span class="sxs-lookup"><span data-stu-id="d5442-115">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 <span data-ttu-id="d5442-116">示範如何使用 LINQ 進行簡單查詢文字。</span><span class="sxs-lookup"><span data-stu-id="d5442-116">Shows how to use LINQ for simple querying over text.</span></span>  
  
 [<span data-ttu-id="d5442-117">如何︰ 查詢包含一組指定的文字 (LINQ) (Visual Basic) 的句子</span><span class="sxs-lookup"><span data-stu-id="d5442-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 <span data-ttu-id="d5442-118">示範如何分割任意界限上的文字檔，以及如何針對每個部分執行查詢。</span><span class="sxs-lookup"><span data-stu-id="d5442-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>  
  
 [<span data-ttu-id="d5442-119">如何︰ 查詢字串 (LINQ) (Visual Basic) 中的字元</span><span class="sxs-lookup"><span data-stu-id="d5442-119">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>](how-to-query-for-characters-in-a-string-linq.md)  
 <span data-ttu-id="d5442-120">示範字串是可查詢型別。</span><span class="sxs-lookup"><span data-stu-id="d5442-120">Demonstrates that a string is a queryable type.</span></span>  
  
 [<span data-ttu-id="d5442-121">如何︰ 合併 LINQ 查詢與規則運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5442-121">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)  
 <span data-ttu-id="d5442-122">示範如何使用 LINQ 查詢中的規則運算式的複雜的模式比對篩選的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="d5442-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>  
  
## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="d5442-123">查詢文字格式的半結構化的資料</span><span class="sxs-lookup"><span data-stu-id="d5442-123">Querying Semi-Structured Data in Text Format</span></span>  
 <span data-ttu-id="d5442-124">一系列的行數，通常使用類似的格式，例如 tab 或逗號分隔的檔案或固定長度的程式碼行，且包含許多不同類型的文字檔案。</span><span class="sxs-lookup"><span data-stu-id="d5442-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="d5442-125">文字檔案讀入記憶體之後，您可以使用 LINQ 來查詢及/或修改程式碼行。</span><span class="sxs-lookup"><span data-stu-id="d5442-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="d5442-126">LINQ 查詢也簡化了結合多個來源資料的工作。</span><span class="sxs-lookup"><span data-stu-id="d5442-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>  
  
 [<span data-ttu-id="d5442-127">如何︰ 尋找兩個清單 (LINQ) (Visual Basic) 之間的差異</span><span class="sxs-lookup"><span data-stu-id="d5442-127">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)  
 <span data-ttu-id="d5442-128">顯示如何尋找，但未在另一份清單中出現的所有字串。</span><span class="sxs-lookup"><span data-stu-id="d5442-128">Shows how to find all the strings that are present in one list but not the other.</span></span>  
  
 [<span data-ttu-id="d5442-129">如何︰ 排序或篩選文字資料，依任何字或欄位 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5442-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 <span data-ttu-id="d5442-130">示範如何根據任何字或欄位的文字行的排序。</span><span class="sxs-lookup"><span data-stu-id="d5442-130">Shows how to sort text lines based on any word or field.</span></span>  
  
 [<span data-ttu-id="d5442-131">如何︰ 重新排列分隔檔案 (LINQ) (Visual Basic) 的欄位</span><span class="sxs-lookup"><span data-stu-id="d5442-131">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>](how-to-reorder-the-fields-of-a-delimited-file.md)  
 <span data-ttu-id="d5442-132">示範如何在.csv 檔案中的資料行中的欄位重新排列。</span><span class="sxs-lookup"><span data-stu-id="d5442-132">Shows how to reorder fields in a line in a .csv file.</span></span>  
  
 [<span data-ttu-id="d5442-133">如何︰ 合併和比較字串集合 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5442-133">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)  
 <span data-ttu-id="d5442-134">示範如何結合各種方式的字串清單。</span><span class="sxs-lookup"><span data-stu-id="d5442-134">Shows how to combine string lists in various ways.</span></span>  
  
 [<span data-ttu-id="d5442-135">如何︰ 填入物件集合，從多個來源 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5442-135">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 <span data-ttu-id="d5442-136">示範如何使用多個文字檔案做為資料來源建立物件集合。</span><span class="sxs-lookup"><span data-stu-id="d5442-136">Shows how to create object collections by using multiple text files as data sources.</span></span>  
  
 [<span data-ttu-id="d5442-137">如何︰ 將內容從不同的檔案 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5442-137">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)  
 <span data-ttu-id="d5442-138">示範如何使用相符的索引鍵來在兩個清單的字串結合成單一字串。</span><span class="sxs-lookup"><span data-stu-id="d5442-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>  
  
 [<span data-ttu-id="d5442-139">如何︰ 使用群組 (LINQ) (Visual Basic)，將檔案分割成許多檔案</span><span class="sxs-lookup"><span data-stu-id="d5442-139">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 <span data-ttu-id="d5442-140">示範如何使用單一檔案做為資料來源建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="d5442-140">Shows how to create new files by using a single file as a data source.</span></span>  
  
 [<span data-ttu-id="d5442-141">如何︰ 計算 CSV 文字檔案 (LINQ) (Visual Basic) 中的資料行值</span><span class="sxs-lookup"><span data-stu-id="d5442-141">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 <span data-ttu-id="d5442-142">示範如何執行算術運算的.csv 檔案中的文字資料。</span><span class="sxs-lookup"><span data-stu-id="d5442-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5442-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5442-143">See Also</span></span>  
 <span data-ttu-id="d5442-144">[語言整合查詢 (LINQ) (Visual Basic)](index.md) </span><span class="sxs-lookup"><span data-stu-id="d5442-144">[Language-Integrated Query (LINQ) (Visual Basic)](index.md) </span></span>  
<span data-ttu-id="d5442-145"> [如何：從 CSV 檔案產生 XML](how-to-generate-xml-from-csv-files.md)</span><span class="sxs-lookup"><span data-stu-id="d5442-145"> [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md)</span></span>

