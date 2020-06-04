---
title: Join 子句
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
ms.openlocfilehash: f73dc31bbbb9014a8a1a315de406c53fa58d1c65
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359770"
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

需要 `element`。 要聯結之集合的控制項變數。

`collection`  
必要。 要與運算子左邊所識別之集合結合的集合 `Join` 。 `Join`子句可以嵌套在另一個 `Join` 子句或 `Group Join` 子句中。

`joinClause`  
選擇性。 一或多個額外 `Join` 的子句，可進一步精簡查詢。

`groupJoinClause`  
選擇性。 一或多個額外 `Group Join` 的子句，可進一步精簡查詢。

`key1` `Equals` `key2`  
必要。 識別要聯結之集合的索引鍵。 您必須使用 `Equals` 運算子來比較所聯結之集合中的索引鍵。 您可以使用 `And` 運算子來識別多個索引鍵，以結合聯結條件。 `key1`必須來自運算子左邊的集合 `Join` 。 `key2`必須來自運算子右邊的集合 `Join` 。

聯結條件中使用的索引鍵可以是包含集合中一個以上專案的運算式。 不過，每個索引鍵運算式只能包含其各自集合中的專案。

## <a name="remarks"></a>備註

`Join`子句會根據聯結的集合中相符的索引鍵值，結合兩個集合。 產生的集合可以包含運算子左邊所識別之集合中的任何值組合 `Join` ，以及在子句中識別的集合 `Join` 。 查詢只會傳回符合運算子所指定條件的結果 `Equals` 。 這相當於 `INNER JOIN` SQL 中的。

您可以 `Join` 在查詢中使用多個子句，將兩個或更多個集合聯結至單一集合。

您可以執行隱含聯結來結合沒有子句的集合 `Join` 。 若要這麼做，請 `In` 在子句中包含多個子句， `From` 並指定一個 `Where` 子句來識別您想要用於聯結的索引鍵。

您可以使用 `Group Join` 子句，將集合合併成單一階層式集合。 這就像 `LEFT OUTER JOIN` SQL 中的。

## <a name="example"></a>範例

下列程式碼範例會執行隱含聯結，以結合客戶清單與訂單。

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a>範例

下列程式碼範例會使用子句聯結兩個集合 `Join` 。

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

這個範例會產生類似下列的輸出：

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a>範例

下列程式碼範例會使用子句搭配兩個索引鍵資料行來聯結兩個集合 `Join` 。

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

此範例會產生類似下列的輸出：

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](index.md)
- [Select 子句](select-clause.md)
- [From 子句](from-clause.md)
- [Group Join 子句](group-join-clause.md)
- [Where 子句](where-clause.md)
