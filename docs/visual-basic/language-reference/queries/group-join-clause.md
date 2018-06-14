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
ms.openlocfilehash: 094281b0afb34451ae8539e4eb967043b21d379c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604753"
---
# <a name="group-join-clause-visual-basic"></a>Group Join 子句 (Visual Basic)
將兩個集合合併成單一階層式集合。 聯結作業會根據相符索引鍵。  
  
## <a name="syntax"></a>語法  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`element`|必要。 所要加入之控制項的變數。|  
|`type`|選擇性。 `element` 的類型。 如果沒有`type`指定的型別`element`推斷從`collection`。|  
|`collection`|必要。 結合集合上的左半部集合`Group Join`運算子。 A`Group Join`子句可以巢狀方式置於`Join`子句或另一個`Group Join`子句。|  
|`key1` `Equals` `key2`|必要。 識別要聯結之集合的索引鍵。 您必須使用`Equals`運算子來比較所聯結之集合中的索引鍵。 您可以使用合併聯結條件`And`運算子來識別多個索引鍵。 `key1`參數必須是從集合上的左半部`Join`運算子。 `key2`參數必須是從集合中的右邊`Join`運算子。<br /><br /> 聯結條件中使用的索引鍵可以是包含一個以上的項目集合中的運算式。 不過，每個索引鍵的運算式可以包含從其各自集合的項目。|  
|`expressionList`|必要。 識別如何彙總集合中的項目群組的一或多個運算式。 若要識別群組結果的成員名稱，請使用`Group`關鍵字 (`<alias> = Group`)。 您也可以包含將套用至群組的彙總函式。|  
  
## <a name="remarks"></a>備註  
 `Group Join`子句結合兩個比對所聯結之集合中的索引鍵值為基礎的集合。 產生的集合可以包含比對從第一個集合的索引鍵值的第二個集合中參考的項目集合的成員。 您也可以指定要套用至群組項目的第二個集合的彙總函式。 彙總函式的相關資訊，請參閱[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 例如，考慮，主管的集合，並在員工集合。 從這兩個集合的項目具有 ManagerID 屬性可識別直屬特定經理的員工。 聯結作業的結果會包含每個經理和員工 ManagerID 值相符的結果。 從結果`Group Join`作業會包含完整的經理清單。 每個管理員結果必須參考已符合特定經理的員工清單內的成員。  
  
 所產生的集合`Group Join`作業可以包含值從集合中所識別的任何組合`From`子句和運算式中識別`Into`子句`Group Join`子句。 如需有效運算式`Into`子句，請參閱[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 A`Group Join`作業會傳回所有結果，從集合所識別的左邊`Group Join`運算子。 即使沒有符合所要加入集合中的成員，也是如此。 這就相當於`LEFT OUTER JOIN`SQL 中。  
  
 您可以使用`Join`子句結合成單一集合的集合。 這相當於`INNER JOIN`SQL 中。  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用聯結兩個集合`Group Join`子句。  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [查詢](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Join 子句](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Group By 子句](../../../visual-basic/language-reference/queries/group-by-clause.md)
