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
ms.openlocfilehash: 184077f2689eb64e4373d407913eefcc03b795c2
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005730"
---
# <a name="group-join-clause-visual-basic"></a>Group Join 子句 (Visual Basic)
將兩個集合合併成單一階層式集合。 聯結作業是以相符的索引鍵為基礎。  
  
## <a name="syntax"></a>語法  
  
```vb  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`element`|必要項。 要聯結之集合的控制項變數。|  
|`type`|選擇性。 `element` 的類型。 如果未指定 `type`，則會從 `collection` 推斷 `element` 的類型。|  
|`collection`|必要項。 要與 `Group Join` 運算子左邊的集合結合的集合。 @No__t 0 子句可以嵌套在 @no__t 1 子句或另一個 `Group Join` 子句中。|  
|`key1` `Equals` `key2`|必要項。 識別要聯結之集合的索引鍵。 您必須使用 `Equals` 運算子來比較所聯結之集合中的索引鍵。 您可以使用 `And` 運算子來結合聯結條件，以識別多個索引鍵。 @No__t-0 參數必須來自 `Join` 運算子左邊的集合。 @No__t-0 參數必須來自 `Join` 運算子右邊的集合。<br /><br /> 聯結條件中使用的索引鍵可以是包含集合中一個以上專案的運算式。 不過，每個索引鍵運算式只能包含其各自集合中的專案。|  
|`expressionList`|必要項。 一或多個運算式，可識別如何匯總集合中的元素群組。 若要識別群組結果的成員名稱，請使用 `Group` 關鍵字（`<alias> = Group`）。 您也可以包含將套用至群組的彙總函式。|  
  
## <a name="remarks"></a>備註  
 @No__t-0 子句會根據聯結的集合中相符的索引鍵值，結合兩個集合。 產生的集合可以包含一個成員，其參考第二個集合中符合第一個集合之索引鍵值的元素集合。 您也可以指定彙總函式，以套用至第二個集合中的群組元素。 如需彙總函式的詳細資訊，請參閱[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 例如，假設有一組經理和員工集合。 這兩個集合中的元素都具有 ManagerID 屬性，可識別向特定經理報告的員工。 聯結作業的結果會包含每個經理和員工的結果，並具有相符的 ManagerID 值。 @No__t-0 作業的結果會包含完整的管理員清單。 每個管理員結果都有一個成員，參考與特定經理相符的員工清單。  
  
 由 @no__t 0 作業所產生的集合可以包含在 `From` 子句中識別之集合中的任何值組合，以及在 `Group Join` 子句的 `Into` 子句中識別的運算式。 如需 `Into` 子句之有效運算式的詳細資訊，請參閱[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 @No__t-0 作業會從 `Group Join` 運算子左側識別的集合傳回所有結果。 即使聯結的集合中沒有相符專案，也是如此。 這就像是 SQL 中的 @no__t 0。  
  
 您可以使用 `Join` 子句，將集合結合成單一集合。 這相當於 SQL 中的 @no__t 0。  
  
## <a name="example"></a>範例  
 下列程式碼範例使用 `Group Join` 子句來聯結兩個集合。  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Join 子句](../../../visual-basic/language-reference/queries/join-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By 子句](../../../visual-basic/language-reference/queries/group-by-clause.md)
