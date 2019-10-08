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
ms.openlocfilehash: 8eab7db00515f55b086b5e1beddd149f966cb27a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72001932"
---
# <a name="join-clause-visual-basic"></a>Join 子句 (Visual Basic)
將兩個集合合併成單一集合。 聯結作業是以相符的索引鍵為基礎，並使用 `Equals` 運算子。  
  
## <a name="syntax"></a>語法  
  
```vb  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a>組件  
 `element`  
 必要項。 要聯結之集合的控制項變數。  
  
 `collection`  
 必要項。 要與 `Join` 運算子左邊所識別之集合結合的集合。 @No__t 0 子句可以嵌套在另一個 `Join` 子句或 @no__t 2 子句中。  
  
 `joinClause`  
 選擇性。 一或多個額外的 `Join` 子句，可進一步精簡查詢。  
  
 `groupJoinClause`  
 選擇性。 一或多個額外的 `Group Join` 子句，可進一步精簡查詢。  
  
 `key1` `Equals` `key2`  
 必要項。 識別要聯結之集合的索引鍵。 您必須使用 `Equals` 運算子來比較所聯結之集合中的索引鍵。 您可以使用 `And` 運算子來結合聯結條件，以識別多個索引鍵。 `key1` 必須來自 `Join` 運算子左邊的集合。 `key2` 必須來自 `Join` 運算子右邊的集合。  
  
 聯結條件中使用的索引鍵可以是包含集合中一個以上專案的運算式。 不過，每個索引鍵運算式只能包含其各自集合中的專案。  
  
## <a name="remarks"></a>備註  
 @No__t-0 子句會根據聯結的集合中相符的索引鍵值，結合兩個集合。 產生的集合可以包含從 `Join` 運算子左側識別之集合中的任何值組合，以及在 `Join` 子句中識別的集合。 查詢只會傳回符合 `Equals` 運算子所指定之條件的結果。 這相當於 SQL 中的 @no__t 0。  
  
 您可以在查詢中使用多個 `Join` 子句，將兩個或更多個集合聯結至單一集合。  
  
 您可以執行隱含聯結來結合集合，而不使用 `Join` 子句。 若要這麼做，請在您的 `From` 子句中包含多個 `In` 子句，並指定一個 `Where` 子句來識別您要用於聯結的索引鍵。  
  
 您可以使用 `Group Join` 子句，將集合合併成單一階層式集合。 這就像是 SQL 中的 @no__t 0。  
  
## <a name="example"></a>範例  
 下列程式碼範例會執行隱含聯結，以結合客戶清單與訂單。  
  
 [!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]  
  
## <a name="example"></a>範例  
 下列程式碼範例使用 `Join` 子句來聯結兩個集合。  
  
 [!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]  
  
 這個範例會產生類似下列的輸出：  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用具有兩個索引鍵資料行的 @no__t 0 子句來聯結兩個集合。  
  
 [!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]  
  
 此範例會產生類似下列的輸出：  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Group Join 子句](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
