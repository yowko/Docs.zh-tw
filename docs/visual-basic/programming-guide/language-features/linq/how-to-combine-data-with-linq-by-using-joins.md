---
title: 如何：使用 Join 透過 LINQ 合併資料
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: de8c4ec3ab8a0f2335c034231c661380420fd31b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405000"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>如何：使用 Joins 以 LINQ 合併資料 (Visual Basic)
Visual Basic 提供 `Join` 和 `Group Join` 查詢子句，可讓您根據集合之間的通用值，結合多個集合的內容。 這些值稱為索引*鍵值*。 熟悉關係資料庫概念的開發人員會將 `Join` 子句辨識為內部聯結，並將 `Group Join` 子句視為有效的左方外部聯結。  
  
 本主題中的範例將示範使用 `Join` 和查詢子句結合資料的幾種方式 `Group Join` 。  
  
## <a name="create-a-project-and-add-sample-data"></a>建立專案並新增範例資料  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>若要建立包含範例資料和類型的專案  
  
1. 若要執行本主題中的範例，請開啟 Visual Studio 並加入新的 Visual Basic 主控台應用程式專案。 按兩下 Visual Basic 所建立的 Module1 檔案。  
  
2. 本主題中的範例會使用 `Person` 下列程式碼範例中的和 `Pet` 類型和資料。 將此程式碼複製到 `Module1` Visual Basic 所建立的預設模組。  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>使用 Join 子句執行內部聯結  
 內部聯結結合兩個集合中的資料。 包含指定之索引鍵值相符的專案。 不會排除任何集合中任何來自其他集合之相符專案的專案。  
  
 在 Visual Basic 中，LINQ 提供兩個選項來執行內部聯結：隱含聯結和明確聯結。  
  
 隱含聯結會指定要聯結在子句中的集合 `From` ，並在子句中識別相符的索引鍵欄位 `Where` 。 Visual Basic 會根據指定的索引鍵欄位，隱含地聯結兩個集合。  
  
 `Join`當您想要特定于聯結中使用的索引鍵欄位時，可以使用子句來指定明確聯結。 在此情況下， `Where` 子句仍然可以用來篩選查詢結果。  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>若要使用 Join 子句來執行內部聯結  
  
1. 將下列程式碼新增至 `Module1` 專案中的模組，以查看隱含和明確內部聯結的範例。  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>使用 Group Join 子句執行左方外部聯結  
 左方外部聯結包含來自聯結之左側集合中的所有專案，以及僅符合聯結之右端集合的值。 在左側集合中沒有相符專案的任何聯結之右端集合中的任何專案，都會從查詢結果中排除。  
  
 `Group Join`子句會執行左外部聯結。 通常所謂的「左方外部聯結」和「子句」傳回的差異在於， `Group Join` `Group Join` 子句會針對左側集合中的每個專案，從聯結的右端集合中將結果分組。 在關係資料庫中，左方外部聯結會傳回未分組的結果，其中查詢結果中的每個專案都包含聯結中兩個集合的相符專案。 在此情況下，會針對右側集合中的每個相符專案，重複聯結之左側集合中的專案。 當您完成下一個程式時，您會看到這看起來的樣子。  
  
 您可以藉 `Group Join` 由擴充您的查詢來傳回每個群組查詢結果的專案，藉此將查詢的結果當做未分組的結果來取得。 若要完成這項工作，您必須確定查詢已 `DefaultIfEmpty` 群組集合的方法。 這可確保聯結的左側集合中的專案仍會包含在查詢結果中，即使它們沒有來自右邊集合的相符結果。 您可以將程式碼加入至查詢，以便在聯結的右側集合中沒有相符的值時，提供預設的結果值。  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>若要使用 Group Join 子句來執行左方外部聯結  
  
1. 將下列程式碼新增至 `Module1` 專案中的模組，以查看群組左方外部聯結和取消分組左方外部聯結的範例。  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>使用複合索引鍵執行聯結  
 您可以 `And` 在或子句中使用 `Join` 關鍵字 `Group Join` ，以識別要聯結之集合中的值相符時，所要使用的多個索引鍵欄位。 `And`關鍵字會指定所有指定的索引鍵欄位必須符合才能聯結的專案。  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>若要使用複合索引鍵執行聯結  
  
1. 將下列程式碼加入至 `Module1` 專案中的模組，以查看使用複合索引鍵之聯結的範例。  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>執行程式碼  
  
#### <a name="to-add-code-to-run-the-examples"></a>若要加入程式碼以執行範例  
  
1. 使用下列程式碼取代專案中模組中的， `Sub Main` `Module1` 以執行本主題中的範例。  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. 按 F5 執行範例。  
  
## <a name="see-also"></a>另請參閱

- [LINQ](index.md)
- [Visual Basic 中的 LINQ 簡介](introduction-to-linq.md)
- [Join 子句](../../../language-reference/queries/join-clause.md)
- [Group Join 子句](../../../language-reference/queries/group-join-clause.md)
- [From 子句](../../../language-reference/queries/from-clause.md)
- [Where 子句](../../../language-reference/queries/where-clause.md)
- [查詢](../../../language-reference/queries/index.md)
- [使用 LINQ 轉換資料 (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
