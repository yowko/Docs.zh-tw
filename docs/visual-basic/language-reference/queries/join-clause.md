---
title: Join 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: 2186954ab6536988271629c4feba0a40563bfc3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603908"
---
# <a name="join-clause-visual-basic"></a>Join 子句 (Visual Basic)
將兩個集合合併成單一集合。 根據相符索引鍵的聯結作業，並使用`Equals`運算子。  
  
## <a name="syntax"></a>語法  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a>組件  
 `element`  
 必要。 所要加入之控制項的變數。  
  
 `collection`  
 必要。 結合集合所識別的左邊集合`Join`運算子。 A`Join`子句可以巢狀方式置於另一個`Join`子句，或在`Group Join`子句。  
  
 `joinClause`  
 選擇性。 一個以上的額外`Join`子句來進一步精簡查詢。  
  
 `groupJoinClause`  
 選擇性。 一個以上的額外`Group Join`子句來進一步精簡查詢。  
  
 `key1` `Equals` `key2`  
 必要。 識別要聯結之集合的索引鍵。 您必須使用`Equals`運算子來比較所聯結之集合中的索引鍵。 您可以使用合併聯結條件`And`運算子來識別多個索引鍵。 `key1` 從集合上的左側必須是`Join`運算子。 `key2` 從集合中的右側必須是`Join`運算子。  
  
 聯結條件中使用的索引鍵可以是包含一個以上的項目集合中的運算式。 不過，每個索引鍵的運算式可以包含從其各自集合的項目。  
  
## <a name="remarks"></a>備註  
 `Join`子句結合兩個比對所聯結之集合中的索引鍵值為基礎的集合。 產生的集合可以包含任何的組合值集合所識別的左邊`Join`運算子和識別集合中`Join`子句。 查詢會傳回的結果的條件指定由`Equals`運算子成立。 這相當於`INNER JOIN`SQL 中。  
  
 您可以使用多個`Join`来聯結成為單一集合的兩個或多個集合的查詢中的子句。  
  
 您可以執行隱含聯結來結合集合不含`Join`子句。 若要這樣做，包括多個`In`子句中的您`From`子句，並指定`Where`識別您想要用於聯結的索引鍵的子句。  
  
 您可以使用`Group Join`子句結合成單一階層式集合的集合。 這就相當於`LEFT OUTER JOIN`SQL 中。  
  
## <a name="example"></a>範例  
 下列程式碼範例會執行隱含聯結以結合其訂單的客戶清單。  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用聯結兩個集合`Join`子句。  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 這個範例會產生類似下面的輸出：  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用聯結兩個集合`Join`具有兩個索引鍵資料行子句。  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 此範例會產生類似下面的輸出：  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [查詢](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Group Join 子句](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
