---
title: LINQ 和字串 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
ms.openlocfilehash: 7e0ebe64494182191dafa033ecbc38bad17180be
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818952"
---
# <a name="linq-and-strings-visual-basic"></a><span data-ttu-id="36565-102">LINQ 和字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36565-102">LINQ and Strings (Visual Basic)</span></span>
<span data-ttu-id="36565-103">您可以使用 LINQ 查詢及轉換字串與字串集合。</span><span class="sxs-lookup"><span data-stu-id="36565-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="36565-104">針對文字檔案中的半結構化資料，這種做法特別有用。</span><span class="sxs-lookup"><span data-stu-id="36565-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="36565-105">LINQ 查詢可以結合傳統字串函式和規則運算式。</span><span class="sxs-lookup"><span data-stu-id="36565-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="36565-106">例如，您可以使用 <xref:System.String.Split%2A> 或 <xref:System.Text.RegularExpressions.Regex.Split%2A> 方法，來建立您接著可以使用 LINQ 查詢或修改的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="36565-106">For example, you can use the <xref:System.String.Split%2A> or <xref:System.Text.RegularExpressions.Regex.Split%2A> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="36565-107">您可以在 LINQ 查詢的 `where` 子句中使用 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="36565-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="36565-108">您可以使用 LINQ 查詢或修改規則運算式所傳回的 <xref:System.Text.RegularExpressions.MatchCollection> 結果。</span><span class="sxs-lookup"><span data-stu-id="36565-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>  
  
 <span data-ttu-id="36565-109">您也可以使用本節所述的技巧，將半結構化的文字資料轉換成 XML。</span><span class="sxs-lookup"><span data-stu-id="36565-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="36565-110">如需詳細資訊，請參閱[如何：從 CSV 檔案產生 XML](how-to-generate-xml-from-csv-files.md)。</span><span class="sxs-lookup"><span data-stu-id="36565-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>  
  
 <span data-ttu-id="36565-111">本節中的範例分為兩類：</span><span class="sxs-lookup"><span data-stu-id="36565-111">The examples in this section fall into two categories:</span></span>  
  
## <a name="querying-a-block-of-text"></a><span data-ttu-id="36565-112">查詢文字區塊</span><span class="sxs-lookup"><span data-stu-id="36565-112">Querying a Block of Text</span></span>  
 <span data-ttu-id="36565-113">您可以查詢和分析文字區塊，並使用 <xref:System.String.Split%2A> 方法或 <xref:System.Text.RegularExpressions.Regex.Split%2A> 方法將它們分割為可查詢的較小字串陣列來進行修改。</span><span class="sxs-lookup"><span data-stu-id="36565-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A> method.</span></span> <span data-ttu-id="36565-114">您可以將原始程式文字分割成單字、句子、段落、頁面或任何其他準則，再依據您的查詢需求執行其他分割。</span><span class="sxs-lookup"><span data-stu-id="36565-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>  
  
 [<span data-ttu-id="36565-115">如何：計數的某個字在字串 (LINQ) (Visual Basic) 中的項目</span><span class="sxs-lookup"><span data-stu-id="36565-115">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 <span data-ttu-id="36565-116">示範如何使用 LINQ 進行簡單的文字查詢。</span><span class="sxs-lookup"><span data-stu-id="36565-116">Shows how to use LINQ for simple querying over text.</span></span>  
  
 [<span data-ttu-id="36565-117">如何：查詢包含指定的字組的 (LINQ) (Visual Basic) 的句子</span><span class="sxs-lookup"><span data-stu-id="36565-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 <span data-ttu-id="36565-118">示範如何分割任意界限上的文字檔，以及如何針對每個部分執行查詢。</span><span class="sxs-lookup"><span data-stu-id="36565-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>  
  
 [<span data-ttu-id="36565-119">如何：查詢字串 (LINQ) (Visual Basic) 中的字元</span><span class="sxs-lookup"><span data-stu-id="36565-119">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>](how-to-query-for-characters-in-a-string-linq.md)  
 <span data-ttu-id="36565-120">示範當字串為可查詢型別時的情況。</span><span class="sxs-lookup"><span data-stu-id="36565-120">Demonstrates that a string is a queryable type.</span></span>  
  
 [<span data-ttu-id="36565-121">如何：合併 LINQ 查詢與規則運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36565-121">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)  
 <span data-ttu-id="36565-122">示範如何在 LINQ 查詢中使用規則運算式，針對篩選的查詢結果進行複雜模式比對。</span><span class="sxs-lookup"><span data-stu-id="36565-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>  
  
## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="36565-123">查詢半結構化的文字格式資料</span><span class="sxs-lookup"><span data-stu-id="36565-123">Querying Semi-Structured Data in Text Format</span></span>  
 <span data-ttu-id="36565-124">通常，許多不同類型的文字檔案是由具有類似格式的數行所構成，例如 Tab 或逗號分隔的檔案或固定長度的行。</span><span class="sxs-lookup"><span data-stu-id="36565-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="36565-125">將文字檔案讀入記憶體之後，您可以使用 LINQ 來查詢及/或修改這些行。</span><span class="sxs-lookup"><span data-stu-id="36565-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="36565-126">LINQ 查詢也簡化了多種來源資料的結合工作。</span><span class="sxs-lookup"><span data-stu-id="36565-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>  
  
 [<span data-ttu-id="36565-127">如何：尋找兩個清單 (LINQ) (Visual Basic) 之間的集合差異</span><span class="sxs-lookup"><span data-stu-id="36565-127">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)  
 <span data-ttu-id="36565-128">顯示如何尋找某份清單中有、但另一份清單中卻沒有的所有字串。</span><span class="sxs-lookup"><span data-stu-id="36565-128">Shows how to find all the strings that are present in one list but not the other.</span></span>  
  
 [<span data-ttu-id="36565-129">如何：排序或篩選文字資料，依任何字或欄位 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36565-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 <span data-ttu-id="36565-130">示範如何依任何字或欄位排序文字行。</span><span class="sxs-lookup"><span data-stu-id="36565-130">Shows how to sort text lines based on any word or field.</span></span>  
  
 [<span data-ttu-id="36565-131">如何：重新排列欄位的分隔符號的檔案 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36565-131">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>](how-to-reorder-the-fields-of-a-delimited-file.md)  
 <span data-ttu-id="36565-132">示範如何重新排列 .csv 檔案行中的欄位。</span><span class="sxs-lookup"><span data-stu-id="36565-132">Shows how to reorder fields in a line in a .csv file.</span></span>  
  
 [<span data-ttu-id="36565-133">如何：合併和比較字串集合 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36565-133">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)  
 <span data-ttu-id="36565-134">示範結合字串清單的各種方式。</span><span class="sxs-lookup"><span data-stu-id="36565-134">Shows how to combine string lists in various ways.</span></span>  
  
 [<span data-ttu-id="36565-135">如何：填入物件集合，從多個來源 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36565-135">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 <span data-ttu-id="36565-136">示範如何將多個文字檔案作為資料來源以建立物件集合。</span><span class="sxs-lookup"><span data-stu-id="36565-136">Shows how to create object collections by using multiple text files as data sources.</span></span>  
  
 [<span data-ttu-id="36565-137">如何：將內容從不同的檔案 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36565-137">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)  
 <span data-ttu-id="36565-138">示範如何使用相符的索引鍵，將兩份清單中的字串結合為單一字串。</span><span class="sxs-lookup"><span data-stu-id="36565-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>  
  
 [<span data-ttu-id="36565-139">如何：使用群組 (LINQ) (Visual Basic)，將檔案分割成許多檔案</span><span class="sxs-lookup"><span data-stu-id="36565-139">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 <span data-ttu-id="36565-140">示範如何將單一檔案作為資料來源以建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="36565-140">Shows how to create new files by using a single file as a data source.</span></span>  
  
 [<span data-ttu-id="36565-141">如何：計算 CSV 文字檔案 (LINQ) (Visual Basic) 中的資料行值</span><span class="sxs-lookup"><span data-stu-id="36565-141">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 <span data-ttu-id="36565-142">示範如何針對 .csv 檔案中的文字資料執行數學計算。</span><span class="sxs-lookup"><span data-stu-id="36565-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36565-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36565-143">See also</span></span>

- [<span data-ttu-id="36565-144">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36565-144">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="36565-145">如何：從 CSV 檔案產生 XML</span><span class="sxs-lookup"><span data-stu-id="36565-145">How to: Generate XML from CSV Files</span></span>](how-to-generate-xml-from-csv-files.md)
