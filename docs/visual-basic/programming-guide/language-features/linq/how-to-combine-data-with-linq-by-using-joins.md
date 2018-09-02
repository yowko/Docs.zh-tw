---
title: 如何：使用 Joins 以 LINQ 合併資料 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 4db5d288d79379b677bb19b2eba0d094e0d71bc8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422338"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>如何：使用 Joins 以 LINQ 合併資料 (Visual Basic)
Visual Basic 提供`Join`和`Group Join`查詢子句可讓您結合多個集合之間的一般值為基礎的集合的內容。 這些值稱為*金鑰*值。 開發人員熟悉關聯式資料庫概念會辨識`Join`INNER JOIN 子句和`Group Join`做為有效，LEFT OUTER JOIN 子句。  
  
 本主題中的範例將示範幾種方式使用合併資料`Join`和`Group Join`查詢子句。  
  
## <a name="create-a-project-and-add-sample-data"></a>建立專案，並將範例資料  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>若要建立包含範例資料和類型的專案  
  
1.  若要執行本主題中的範例，請開啟 Visual Studio，並加入新的 Visual Basic 主控台應用程式專案。 按兩下建立 Visual basic 的 Module1.vb 檔案。  
  
2.  在本主題使用範例`Person`和`Pet`類型和下列程式碼範例中的資料。 此程式碼複製到預設`Module1`Visual Basic 所建立的模組。  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>使用 Join 子句執行內部聯結  
 INNER JOIN 結合來自兩個集合的資料。 會包含符合指定的索引鍵值的項目。 會排除任何兩個集合的項目，在另一個集合中沒有相符的項目。  
  
 在 Visual Basic 中的 LINQ 提供執行內部聯結的兩個選項： 隱含聯結和明確聯結。  
  
 隱含聯結指定的集合加入`From`子句，並指出在比對的索引鍵欄位`Where`子句。 Visual Basic 隱含聯結兩個集合根據指定的索引鍵欄位。  
  
 您可以使用，以指定明確的聯結`Join`子句，當您想要特定的對哪一個索引鍵欄位在聯結中使用。 在此情況下，`Where`子句仍可用來篩選查詢結果。  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>若要執行使用 Join 子句的 Inner Join  
  
1.  將下列程式碼加入`Module1`若要查看這兩個隱含和明確內部聯結的範例專案中的模組。  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>使用 Group Join 子句來執行左方外部聯結  
 左外部聯結中包含的所有項目左側集合的聯結，以及僅比對從聯結的右方集合的值。 從查詢結果會排除任何從聯結的右方集合的項目左邊的集合中沒有相符的項目。  
  
 `Group Join`子句執行時，實際上，LEFT OUTER JOIN。 通常稱左外部聯結和之間的差異`Group Join`是的子句會傳回`Group Join`右側集合中的每個項目左邊的集合中的聯結子句群組結果。 在關聯式資料庫中，左外部聯結會傳回已取消群組的結果，在查詢中的每個項目會造成在其中包含符合的項目，從這兩個聯結的集合。 在此情況下，從聯結的左側集合的項目會重複的每個相符的項目，從右邊的集合。 您會看到看起來像這樣當您完成下一個程序。  
  
 您可以擷取的結果`Group Join`做為已取消群組的結果，藉由擴充您的查詢傳回的項目，針對每個群組的查詢結果的查詢。 若要這麼做，您必須確定您查詢上`DefaultIfEmpty`的群組集合的方法。 這可確保，從聯結的左側集合的項目仍然包含在查詢結果即使它們有沒有符合的結果，從右邊的集合。 您可以將程式碼加入您的查詢，以從聯結的右方集合沒有相符的值時提供預設的結果值。  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>若要執行左方外部聯結使用 Group Join 子句  
  
1.  將下列程式碼加入`Module1`以查看群組的左方外部聯結和已取消群組的左方外部聯結的範例專案中的模組。  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>使用複合索引鍵執行聯結  
 您可以使用`And`中的關鍵字`Join`或`Group Join`子句來識別比對時所要使用的多個索引鍵欄位值所聯結之集合中。 `And`關鍵字會指定所有指定的索引鍵欄位必須符合要加入的項目。  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>若要使用複合索引鍵執行聯結  
  
1.  將下列程式碼加入`Module1`即可查看使用複合索引鍵的聯結的範例專案中的模組。  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a>執行程式碼  
  
#### <a name="to-add-code-to-run-the-examples"></a>加入程式碼以執行範例  
  
1.  取代`Sub Main`在`Module1`下列的程式碼，以執行本主題中的範例專案中的模組。  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  按 F5 執行範例。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Join 子句](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [Group Join 子句](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [查詢](../../../../visual-basic/language-reference/queries/index.md)  
 [使用 LINQ 轉換資料 (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
