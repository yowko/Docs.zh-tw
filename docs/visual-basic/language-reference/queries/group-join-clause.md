---
title: Group Join 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 3da4ca2db299a65b2c0f1fa259bbaabe4f53aa33
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821943"
---
# <a name="group-join-clause-visual-basic"></a>Group Join 子句 (Visual Basic)
將兩個集合合併成單一階層式集合。 聯結作業根據對應索引鍵。  
  
## <a name="syntax"></a>語法  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`element`|必要項。 要聯結之集合的控制變數。|  
|`type`|選擇性。 `element` 的類型。 如果沒有`type`指定的型別`element`從推斷而來`collection`。|  
|`collection`|必要項。 要結合的左側集合的集合`Group Join`運算子。 A`Group Join`子句可以巢狀方式置於`Join`子句或以其他`Group Join`子句。|  
|`key1` `Equals` `key2`|必要項。 識別要聯結之集合的索引鍵。 您必須使用`Equals`運算子來比較所聯結之集合中的索引鍵。 您可以使用合併聯結條件`And`運算子來識別多個索引鍵。 `key1`參數必須是從左側集合`Join`運算子。 `key2`參數必須是從右邊的集合`Join`運算子。<br /><br /> 聯結條件中使用索引鍵可以包含一個以上的項目從集合的運算式。 不過，每個索引鍵的運算式可以包含從其個別集合的項目。|  
|`expressionList`|必要項。 識別如何彙總集合中的項目群組的一或多個運算式。 若要識別群組結果的成員名稱，請使用`Group`關鍵字 (`<alias> = Group`)。 您也可以包含將套用至群組的彙總函式。|  
  
## <a name="remarks"></a>備註  
 `Group Join`子句結合兩個集合根據比對所聯結之集合中的索引鍵值。 產生的集合可以包含第二個集合中符合第一個集合的索引鍵值參考項目集合的成員。 您也可以指定要套用至群組項目的第二個集合中的彙總函式。 彙總函式的相關資訊，請參閱[彙總子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 例如，考慮，主管的集合和員工的集合。 從這兩個集合的項目具有 ManagerID 屬性可識別直屬特定經理的員工。 聯結作業的結果會包含每個經理和員工具有相符的 ManagerID 值的結果。 從結果`Group Join`作業會包含管理員的完整清單。 每個管理員結果必須參考已符合特定經理的員工清單的成員。  
  
 所產生的集合`Group Join`作業可包含一個值，識別集合中的任意組合`From`子句和運算式中識別`Into`子句`Group Join`子句。 如需有效運算式的詳細資訊`Into`子句，請參閱 < [Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 A`Group Join`作業會傳回所有結果，從集合所識別的左邊`Group Join`運算子。 這是，則為 true，即使有聯結集合中的沒有相符項目。 這就像是`LEFT OUTER JOIN`SQL 中。  
  
 您可以使用`Join`子句結合成單一集合的集合。 這相當於`INNER JOIN`SQL 中。  
  
## <a name="example"></a>範例  
 下列程式碼範例以使用聯結兩個集合`Group Join`子句。  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Join 子句](../../../visual-basic/language-reference/queries/join-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By 子句](../../../visual-basic/language-reference/queries/group-by-clause.md)
