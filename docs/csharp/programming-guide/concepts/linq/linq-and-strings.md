---
title: LINQ 和字串 (C#)
description: 'LINQ 可以查詢及轉換字串與字串集合。 您可以結合 LINQ 查詢與 c # 字串函式和正則運算式。'
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: 0500d821335659fa29dd4809513f38dac0a8b193
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556716"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="cb0c1-104">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="cb0c1-104">LINQ and strings (C#)</span></span>

<span data-ttu-id="cb0c1-105">您可以使用 LINQ 查詢及轉換字串與字串集合。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-105">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="cb0c1-106">針對文字檔案中的半結構化資料，這種做法特別有用。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-106">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="cb0c1-107">LINQ 查詢可以結合傳統字串函式和規則運算式。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-107">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="cb0c1-108">例如，您可以使用 <xref:System.String.Split%2A?displayProperty=nameWithType> 或 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> 方法，來建立您接著可以使用 LINQ 查詢或修改的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-108">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="cb0c1-109">您可以在 LINQ 查詢的 `where` 子句中使用 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-109">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="cb0c1-110">您可以使用 LINQ 查詢或修改規則運算式所傳回的 <xref:System.Text.RegularExpressions.MatchCollection> 結果。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-110">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="cb0c1-111">您也可以使用本節所述的技巧，將半結構化的文字資料轉換成 XML。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-111">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="cb0c1-112">如需詳細資訊，請參閱 [如何從 CSV 檔案產生 XML](../../../../standard/linq/generate-xml-csv-files.md)。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-112">For more information, see [How to generate XML from CSV files](../../../../standard/linq/generate-xml-csv-files.md).</span></span>

<span data-ttu-id="cb0c1-113">本節中的範例分為兩類：</span><span class="sxs-lookup"><span data-stu-id="cb0c1-113">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="cb0c1-114">查詢文字區塊</span><span class="sxs-lookup"><span data-stu-id="cb0c1-114">Querying a block of text</span></span>

<span data-ttu-id="cb0c1-115">您可以查詢和分析文字區塊，並使用 <xref:System.String.Split%2A?displayProperty=nameWithType> 方法或 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> 方法將它們分割為可查詢的較小字串陣列來進行修改。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-115">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cb0c1-116">您可以將原始程式文字分割成單字、句子、段落、頁面或任何其他準則，再依據您的查詢需求執行其他分割。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-116">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="cb0c1-117">如何在字串中計算單字的出現次數 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="cb0c1-117">How to count occurrences of a word in a string (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="cb0c1-118">示範如何使用 LINQ 進行簡單的文字查詢。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-118">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="cb0c1-119">如何查詢包含指定字組的句子 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="cb0c1-119">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="cb0c1-120">示範如何分割任意界限上的文字檔，以及如何針對每個部分執行查詢。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-120">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="cb0c1-121">如何查詢字串中的字元 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="cb0c1-121">How to query for characters in a string (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="cb0c1-122">示範當字串為可查詢型別時的情況。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-122">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="cb0c1-123">如何使用正則運算式合併 LINQ 查詢 (c # ) </span><span class="sxs-lookup"><span data-stu-id="cb0c1-123">How to combine LINQ queries with regular expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="cb0c1-124">示範如何在 LINQ 查詢中使用規則運算式，針對篩選的查詢結果進行複雜模式比對。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-124">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="cb0c1-125">查詢半結構化的文字格式資料</span><span class="sxs-lookup"><span data-stu-id="cb0c1-125">Querying semi-structured data in text format</span></span>

<span data-ttu-id="cb0c1-126">通常，許多不同類型的文字檔案是由具有類似格式的數行所構成，例如 Tab 或逗號分隔的檔案或固定長度的行。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-126">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="cb0c1-127">將文字檔案讀入記憶體之後，您可以使用 LINQ 來查詢及/或修改這些行。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-127">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="cb0c1-128">LINQ 查詢也簡化了多種來源資料的結合工作。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-128">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="cb0c1-129">如何尋找兩個清單之間的集合差異 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="cb0c1-129">How to find the set difference between two lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="cb0c1-130">顯示如何尋找某份清單中有、但另一份清單中卻沒有的所有字串。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-130">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="cb0c1-131">如何依任何字或欄位排序或篩選文字資料 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="cb0c1-131">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="cb0c1-132">示範如何依任何字或欄位排序文字行。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-132">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="cb0c1-133">如何重新排列分隔檔的欄位 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="cb0c1-133">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="cb0c1-134">示範如何重新排列 .csv 檔案行中的欄位。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-134">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="cb0c1-135">如何結合和比較字串集合 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="cb0c1-135">How to combine and compare string collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="cb0c1-136">示範結合字串清單的各種方式。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-136">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="cb0c1-137">如何從多個來源填入物件集合 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="cb0c1-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="cb0c1-138">示範如何將多個文字檔案作為資料來源以建立物件集合。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-138">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="cb0c1-139">如何從不同的檔案聯結內容 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="cb0c1-139">How to join content from dissimilar files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="cb0c1-140">示範如何使用相符的索引鍵，將兩份清單中的字串結合為單一字串。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-140">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="cb0c1-141">如何使用群組 (LINQ)  (c # 將檔案分割成許多檔案 ) </span><span class="sxs-lookup"><span data-stu-id="cb0c1-141">How to split a file into many files by using groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="cb0c1-142">示範如何將單一檔案作為資料來源以建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-142">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="cb0c1-143">如何計算 CSV 文字檔中的資料行值 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="cb0c1-143">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="cb0c1-144">示範如何針對 .csv 檔案中的文字資料執行數學計算。</span><span class="sxs-lookup"><span data-stu-id="cb0c1-144">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb0c1-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb0c1-145">See also</span></span>

- [<span data-ttu-id="cb0c1-146">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cb0c1-146">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="cb0c1-147">如何從 CSV 檔案產生 XML</span><span class="sxs-lookup"><span data-stu-id="cb0c1-147">How to generate XML from CSV files</span></span>](../../../../standard/linq/generate-xml-csv-files.md)
