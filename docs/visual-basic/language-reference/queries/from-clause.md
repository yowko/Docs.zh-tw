---
title: From 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 781902f1bf28bd029c8d9825aee155a6691cbae9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004775"
---
# <a name="from-clause-visual-basic"></a>From 子句 (Visual Basic)
指定一個或多個範圍變數，以及要查詢的集合。  
  
## <a name="syntax"></a>語法  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`element`|必要。 用來逐一查看集合元素的*範圍變數*。 當查詢逐一查看 `collection`時，會使用範圍變數來參考 `collection` 的每個成員。 必須是可列舉的類型。|  
|`type`|選擇性。 `element` 的類型。 如果未指定 `type`，就會從 `collection`推斷 `element` 的類型。|  
|`collection`|必要。 參考要查詢的集合。 必須是可列舉的類型。|  
  
## <a name="remarks"></a>備註  
 `From` 子句是用來識別查詢的來源資料，以及用來從來源集合參考元素的變數。 這些變數稱為「*範圍變數*」。 查詢需要 `From` 子句，但使用 `Aggregate` 子句來識別只傳回匯總結果的查詢時除外。 如需詳細資訊，請參閱[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 您可以在查詢中指定多個 `From` 子句，以識別要聯結的多個集合。 當指定多個集合時，會個別反復查看它們，或者您可以聯結它們（如果它們是相關的）。 您可以使用 `Select` 子句，或使用 `Join` 或 `Group Join` 子句明確地聯結集合。 或者，您可以在單一 `From` 子句中指定多個範圍變數和集合，並以逗號分隔每個相關的範圍變數和集合與其他專案。 下列程式碼範例顯示 `From` 子句的兩個語法選項。  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 `From` 子句會定義查詢的範圍，這類似于 `For` 迴圈的範圍。 因此，查詢範圍中的每個 `element` 範圍變數都必須有唯一的名稱。 因為您可以為查詢指定多個 `From` 子句，所以後續的 `From` 子句可以參考 `From` 子句中的範圍變數，也可以參考上一個 `From` 子句中的範圍變數。 例如，下列範例顯示的是一個 nested `From` 子句，其中第二個子句中的集合是以第一個子句中範圍變數的屬性為基礎。  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 每個 `From` 子句後面都可以加上任何其他查詢子句的組合，以精簡查詢。 您可以利用下列方式來精簡查詢：  
  
- 使用 `From` 和 `Select` 子句，或使用 `Join` 或 `Group Join` 子句明確地結合多個集合。  
  
- 使用 `Where` 子句來篩選查詢結果。  
  
- 使用 `Order By` 子句來排序結果。  
  
- 使用 `Group By` 子句，將類似的結果群組在一起。  
  
- 使用 `Aggregate` 子句來識別要評估整個查詢結果的彙總函式。  
  
- 使用 `Let` 子句來引進反覆運算變數，其值是由運算式（而非集合）所決定。  
  
- 請使用 `Distinct` 子句來忽略重複的查詢結果。  
  
- 使用 `Skip`、`Take`、`Skip While`和 `Take While` 子句，識別要傳回之結果的各個部分。  
  
## <a name="example"></a>範例  
 下列查詢運算式會使用 `From` 子句，針對 `customers` 集合中的每個 `Customer` 物件，宣告範圍變數 `cust`。 `Where` 子句會使用範圍變數，將輸出限制為來自指定區域的客戶。 `For Each` 迴圈會在查詢結果中顯示每個客戶的公司名稱。  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>另請參閱

- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Distinct 子句](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Join 子句](../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join 子句](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Let 子句](../../../visual-basic/language-reference/queries/let-clause.md)
- [Skip 子句](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take 子句](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)
