---
title: LINQ 和字串 (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: c7a1b86cc611d5f38ceab814b4594f5ad953fbc4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480635"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="a0b07-102">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-102">LINQ and strings (C#)</span></span>

<span data-ttu-id="a0b07-103">您可以使用 LINQ 查詢及轉換字串與字串集合。</span><span class="sxs-lookup"><span data-stu-id="a0b07-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="a0b07-104">針對文字檔案中的半結構化資料，這種做法特別有用。</span><span class="sxs-lookup"><span data-stu-id="a0b07-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="a0b07-105">LINQ 查詢可以結合傳統字串函式和規則運算式。</span><span class="sxs-lookup"><span data-stu-id="a0b07-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="a0b07-106">例如，您可以使用 <xref:System.String.Split%2A?displayProperty=nameWithType> 或 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> 方法，來建立您接著可以使用 LINQ 查詢或修改的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="a0b07-106">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="a0b07-107">您可以在 LINQ 查詢的 `where` 子句中使用 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a0b07-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="a0b07-108">您可以使用 LINQ 查詢或修改規則運算式所傳回的 <xref:System.Text.RegularExpressions.MatchCollection> 結果。</span><span class="sxs-lookup"><span data-stu-id="a0b07-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="a0b07-109">您也可以使用本節所述的技巧，將半結構化的文字資料轉換成 XML。</span><span class="sxs-lookup"><span data-stu-id="a0b07-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="a0b07-110">如需詳細資訊，請參閱[如何：從 CSV 檔案產生 XML](how-to-generate-xml-from-csv-files.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b07-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>

<span data-ttu-id="a0b07-111">本節中的範例分為兩類：</span><span class="sxs-lookup"><span data-stu-id="a0b07-111">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="a0b07-112">查詢文字區塊</span><span class="sxs-lookup"><span data-stu-id="a0b07-112">Querying a block of text</span></span>

<span data-ttu-id="a0b07-113">您可以查詢和分析文字區塊，並使用 <xref:System.String.Split%2A?displayProperty=nameWithType> 方法或 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> 方法將它們分割為可查詢的較小字串陣列來進行修改。</span><span class="sxs-lookup"><span data-stu-id="a0b07-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a0b07-114">您可以將原始程式文字分割成單字、句子、段落、頁面或任何其他準則，再依據您的查詢需求執行其他分割。</span><span class="sxs-lookup"><span data-stu-id="a0b07-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="a0b07-115">如何：統計某個字在字串中出現的次數 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-115">How to: Count Occurrences of a Word in a String (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="a0b07-116">示範如何使用 LINQ 進行簡單的文字查詢。</span><span class="sxs-lookup"><span data-stu-id="a0b07-116">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="a0b07-117">如何：查詢包含指定字組的句子 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="a0b07-118">示範如何分割任意界限上的文字檔，以及如何針對每個部分執行查詢。</span><span class="sxs-lookup"><span data-stu-id="a0b07-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="a0b07-119">如何：查詢字串中的字元 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-119">How to: Query for Characters in a String (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="a0b07-120">示範當字串為可查詢型別時的情況。</span><span class="sxs-lookup"><span data-stu-id="a0b07-120">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="a0b07-121">如何：使用規則運算式合併 LINQ 查詢 (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-121">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="a0b07-122">示範如何在 LINQ 查詢中使用規則運算式，針對篩選的查詢結果進行複雜模式比對。</span><span class="sxs-lookup"><span data-stu-id="a0b07-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="a0b07-123">查詢半結構化的文字格式資料</span><span class="sxs-lookup"><span data-stu-id="a0b07-123">Querying semi-structured data in text format</span></span>

<span data-ttu-id="a0b07-124">通常，許多不同類型的文字檔案是由具有類似格式的數行所構成，例如 Tab 或逗號分隔的檔案或固定長度的行。</span><span class="sxs-lookup"><span data-stu-id="a0b07-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="a0b07-125">將文字檔案讀入記憶體之後，您可以使用 LINQ 來查詢及/或修改這些行。</span><span class="sxs-lookup"><span data-stu-id="a0b07-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="a0b07-126">LINQ 查詢也簡化了多種來源資料的結合工作。</span><span class="sxs-lookup"><span data-stu-id="a0b07-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="a0b07-127">如何：尋找兩個清單之間的集合差異 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-127">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="a0b07-128">顯示如何尋找某份清單中有、但另一份清單中卻沒有的所有字串。</span><span class="sxs-lookup"><span data-stu-id="a0b07-128">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="a0b07-129">如何：依任何字或欄位排序或篩選文字資料 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="a0b07-130">示範如何依任何字或欄位排序文字行。</span><span class="sxs-lookup"><span data-stu-id="a0b07-130">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="a0b07-131">如何：重新排列有分隔符號之檔案中的欄位 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-131">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="a0b07-132">示範如何重新排列 .csv 檔案行中的欄位。</span><span class="sxs-lookup"><span data-stu-id="a0b07-132">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="a0b07-133">如何：合併和比較字串集合 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-133">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="a0b07-134">示範結合字串清單的各種方式。</span><span class="sxs-lookup"><span data-stu-id="a0b07-134">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="a0b07-135">如何：從多個來源填入物件集合 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-135">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="a0b07-136">示範如何將多個文字檔案作為資料來源以建立物件集合。</span><span class="sxs-lookup"><span data-stu-id="a0b07-136">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="a0b07-137">如何：從不同的檔案聯結內容 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-137">How to: Join Content from Dissimilar Files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="a0b07-138">示範如何使用相符的索引鍵，將兩份清單中的字串結合為單一字串。</span><span class="sxs-lookup"><span data-stu-id="a0b07-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="a0b07-139">如何：使用群組將檔案分割成許多檔案 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-139">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="a0b07-140">示範如何將單一檔案作為資料來源以建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="a0b07-140">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="a0b07-141">如何：計算 CSV 文字檔案中的資料行值 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-141">How to: Compute Column Values in a CSV Text File (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="a0b07-142">示範如何針對 .csv 檔案中的文字資料執行數學計算。</span><span class="sxs-lookup"><span data-stu-id="a0b07-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0b07-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0b07-143">See also</span></span>

- [<span data-ttu-id="a0b07-144">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0b07-144">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="a0b07-145">如何：從 CSV 檔案產生 XML</span><span class="sxs-lookup"><span data-stu-id="a0b07-145">How to: Generate XML from CSV Files</span></span>](how-to-generate-xml-from-csv-files.md)
