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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a79d1427331070da9c545fdd3175115fe187e879
ms.lasthandoff: 03/13/2017

---
# <a name="linq-and-strings-visual-basic"></a>LINQ 和字串 (Visual Basic)
LINQ 可用於查詢及轉換字串與字串集合。 它可以是文字檔案中的半結構化資料特別有用。 LINQ 查詢可以結合傳統字串函數和規則運算式。 例如，您可以使用<xref:System.String.Split%2A>或<xref:System.Text.RegularExpressions.Regex.Split%2A>方法來建立，您可以再查詢或使用 LINQ 修改的字串陣列。</xref:System.Text.RegularExpressions.Regex.Split%2A> </xref:System.String.Split%2A> 您可以使用<xref:System.Text.RegularExpressions.Regex.IsMatch%2A>方法中的`where`LINQ 查詢子句。</xref:System.Text.RegularExpressions.Regex.IsMatch%2A> 您可以使用 LINQ 查詢或修改<xref:System.Text.RegularExpressions.MatchCollection>規則運算式所傳回的結果。</xref:System.Text.RegularExpressions.MatchCollection>  
  
 您也可以使用本節中所述的技巧來轉換成 XML 的半結構化的文字資料。 如需詳細資訊，請參閱[How to︰ 從 CSV 檔案產生的 XML](how-to-generate-xml-from-csv-files.md)。  
  
 本章節中的範例分為兩類︰  
  
## <a name="querying-a-block-of-text"></a>查詢文字的區塊  
 您可以查詢、 分析及修改文字區塊，將它們分割為可查詢的較小的字串陣列中，使用<xref:System.String.Split%2A>方法或<xref:System.Text.RegularExpressions.Regex.Split%2A>方法。</xref:System.Text.RegularExpressions.Regex.Split%2A> </xref:System.String.Split%2A> 您可以將原始程式文字分割成單字、 句子、 段落、 網頁或其他準則，然後再執行額外的分割，如果您在查詢中需要它們。  
  
 [如何︰ 統計某個字在字串 (LINQ) (Visual Basic) 中的出現次數](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 示範如何使用 LINQ 進行簡單查詢文字。  
  
 [如何︰ 查詢包含一組指定的文字 (LINQ) (Visual Basic) 的句子](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 示範如何分割任意界限上的文字檔，以及如何針對每個部分執行查詢。  
  
 [如何︰ 查詢字串 (LINQ) (Visual Basic) 中的字元](how-to-query-for-characters-in-a-string-linq.md)  
 示範字串是可查詢型別。  
  
 [如何︰ 合併 LINQ 查詢與規則運算式 (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)  
 示範如何使用 LINQ 查詢中的規則運算式的複雜的模式比對篩選的查詢結果。  
  
## <a name="querying-semi-structured-data-in-text-format"></a>查詢文字格式的半結構化的資料  
 一系列的行數，通常使用類似的格式，例如 tab 或逗號分隔的檔案或固定長度的程式碼行，且包含許多不同類型的文字檔案。 文字檔案讀入記憶體之後，您可以使用 LINQ 來查詢及/或修改程式碼行。 LINQ 查詢也簡化了結合多個來源資料的工作。  
  
 [如何︰ 尋找兩個清單 (LINQ) (Visual Basic) 之間的差異](how-to-find-the-set-difference-between-two-lists-linq.md)  
 顯示如何尋找，但未在另一份清單中出現的所有字串。  
  
 [如何︰ 排序或篩選文字資料，依任何字或欄位 (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 示範如何根據任何字或欄位的文字行的排序。  
  
 [如何︰ 重新排列分隔檔案 (LINQ) (Visual Basic) 的欄位](how-to-reorder-the-fields-of-a-delimited-file.md)  
 示範如何在.csv 檔案中的資料行中的欄位重新排列。  
  
 [如何︰ 合併和比較字串集合 (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)  
 示範如何結合各種方式的字串清單。  
  
 [如何︰ 填入物件集合，從多個來源 (LINQ) (Visual Basic)](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 示範如何使用多個文字檔案做為資料來源建立物件集合。  
  
 [如何︰ 將內容從不同的檔案 (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md)  
 示範如何使用相符的索引鍵來在兩個清單的字串結合成單一字串。  
  
 [如何︰ 使用群組 (LINQ) (Visual Basic)，將檔案分割成許多檔案](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 示範如何使用單一檔案做為資料來源建立新的檔案。  
  
 [如何︰ 計算 CSV 文字檔案 (LINQ) (Visual Basic) 中的資料行值](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 示範如何執行算術運算的.csv 檔案中的文字資料。  
  
## <a name="see-also"></a>另請參閱  
 [語言整合查詢 (LINQ) (Visual Basic)](index.md)   
 [如何：從 CSV 檔案產生 XML](how-to-generate-xml-from-csv-files.md)

