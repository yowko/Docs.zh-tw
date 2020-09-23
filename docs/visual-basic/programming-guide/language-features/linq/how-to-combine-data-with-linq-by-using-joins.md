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
ms.openlocfilehash: ebda8d3b7fa2e712c337ed2c1fadc580bed7fe61
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075066"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>如何：使用 Joins 以 LINQ 合併資料 (Visual Basic)

Visual Basic 提供 `Join` 和 `Group Join` 查詢子句，讓您能夠根據集合之間的通用值來合併多個集合的內容。 這些值稱為*索引鍵值。* 熟悉關係資料庫概念的開發人員會將 `Join` 子句辨識為內部聯結，而將 `Group Join` 子句視為有效的左方外部聯結。  
  
 本主題中的範例將示範使用 `Join` 和查詢子句來合併資料的幾種方式 `Group Join` 。  
  
## <a name="create-a-project-and-add-sample-data"></a>建立專案並新增範例資料  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>若要建立包含範例資料和類型的專案  
  
1. 若要執行本主題中的範例，請開啟 Visual Studio 並加入新的 Visual Basic 主控台應用程式專案。 按兩下 Visual Basic 所建立的 [Module1] 檔案。  
  
2. 本主題中的範例會使用 `Person` 下列程式碼範例中的和 `Pet` 類型與資料。 將此程式碼複製到 `Module1` Visual Basic 所建立的預設模組。  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>使用 Join 子句執行內部聯結  

 內部聯結結合兩個集合的資料。 包含指定之索引鍵值相符專案的專案。 不會排除任何在另一個集合中沒有相符專案的集合專案。  
  
 在 Visual Basic 中，LINQ 提供兩個選項來執行內部聯結：隱含聯結和明確聯結。  
  
 隱含聯結會指定要在子句中聯結的集合 `From` ，並識別子句中相符的索引鍵欄位 `Where` 。 Visual Basic 會根據指定的索引鍵欄位，隱含地聯結兩個集合。  
  
 `Join`當您想要指定要在聯結中使用的索引鍵欄位時，可以使用子句來指定明確聯結。 在此情況下，您 `Where` 仍然可以使用子句來篩選查詢結果。  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>使用 Join 子句執行內部聯結  
  
1. 將下列程式碼新增至 `Module1` 專案中的模組，以查看隱含和明確內部聯結的範例。  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>使用 Group Join 子句執行左方外部聯結  

 左方外部聯結包含從聯結的左邊集合中的所有專案，而且只會比對聯結右邊集合中的值。 從查詢結果中排除沒有相符專案之聯結的右方集合中的任何專案，都是從查詢結果中排除。  
  
 `Group Join`子句實際上會執行左方外部聯結。 通常所謂的左方外部聯結和子句傳回專案之間的差異在於， `Group Join` `Group Join` 子句會針對左側集合中的每個專案，從聯結的右手邊集合來群組結果。 在關係資料庫中，左方外部聯結會傳回未分組的結果，其中查詢結果中的每個專案都包含聯結中兩個集合的相符專案。 在此情況下，會從右側集合中的每個相符專案重複聯結之左邊集合的專案。 當您完成下一個程式時，將會看到這類內容。  
  
 您可以藉 `Group Join` 由擴充查詢來傳回每個群組查詢結果的專案，以將查詢的結果取出為未分組的結果。 若要完成這項工作，您必須確定查詢 `DefaultIfEmpty` 群組集合的方法。 這樣可確保聯結的左邊集合中的專案仍會包含在查詢結果中，即使它們沒有右邊集合的相符結果。 您可以將程式碼加入至查詢，以在聯結的右方集合沒有相符的值時提供預設的結果值。  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>使用 Group Join 子句執行左方外部聯結  
  
1. 將下列程式碼新增至 `Module1` 專案中的模組，以查看群組左方外部聯結和未分組左方外部聯結的範例。  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>使用複合索引鍵執行聯結  

 您可以 `And` 在或子句中使用 `Join` 關鍵字 `Group Join` ，以識別要在聯結的集合中比對值時要使用的多個索引鍵欄位。 `And`關鍵字指定所有指定的索引鍵欄位必須符合，才能聯結專案。  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>使用複合索引鍵執行聯結  
  
1. 將下列程式碼新增至 `Module1` 專案中的模組，以查看使用複合索引鍵的聯結範例。  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>執行程式碼  
  
#### <a name="to-add-code-to-run-the-examples"></a>加入程式碼以執行範例  
  
1. `Sub Main` `Module1` 以下列程式碼取代您專案中模組的，以執行本主題中的範例。  
  
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
