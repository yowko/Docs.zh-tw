---
title: Aggregate Clause
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 326c3306368ceca2122e912556efd84e4bfef1f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412997"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate 子句 (Visual Basic)
將一個或多個彙總函式套用至集合。  
  
## <a name="syntax"></a>語法  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`element`|必要。 變數，用來逐一查看集合的元素。|  
|`type`|選擇性。 `element` 的類型。 如果未指定類型，則 `element` 會從推斷的類型 `collection` 。|  
|`collection`|必要。 參考要在其上操作的集合。|  
|`clause`|選擇性。 一或多個查詢子句（例如 `Where` 子句），用以縮小查詢結果的範圍，以將匯總子句套用至。|  
|`expressionList`|必要。 一或多個以逗號分隔的運算式，可識別要套用至集合的彙總函式。 您可以將別名套用至彙總函式，以指定查詢結果的成員名稱。 如果未提供別名，則會使用彙總函式的名稱。 如需範例，請參閱本主題稍後的關於彙總函式的一節。|  
  
## <a name="remarks"></a>備註  
 `Aggregate`子句可以用來在查詢中包含彙總函式。 彙總函式會對一組值執行檢查和計算，並傳回單一值。 您可以使用查詢結果類型的成員來存取計算的值。 您可以使用的標準彙總函式為 `All` 、 `Any` 、 `Average` 、、、 `Count` 、 `LongCount` `Max` `Min` 和 `Sum` 函數。 這些函式對於熟悉 SQL 中匯總的開發人員而言是很熟悉的。 本主題的下一節將說明這些功能。  
  
 彙總函式的結果會當做查詢結果類型的欄位，包含在查詢結果中。 您可以提供彙總函式結果的別名，以指定將保留匯總值之查詢結果類型的成員名稱。 如果未提供別名，則會使用彙總函式的名稱。  
  
 `Aggregate`子句可以開始查詢，也可以在查詢中包含為額外的子句。 如果 `Aggregate` 子句開始查詢，則結果會是單一值，這是子句中指定之彙總函式的結果 `Into` 。 如果在子句中指定了一個以上的彙總函式 `Into` ，則查詢會傳回具有個別屬性的單一類型，以參考子句中每個彙總函式的結果 `Into` 。 如果 `Aggregate` 子句包含為查詢中的其他子句，在查詢集合中傳回的型別將會有個別的屬性來參考子句中每個彙總函式的結果 `Into` 。  
  
## <a name="aggregate-functions"></a>彙總函式

以下是可搭配子句使用的標準彙總函式 `Aggregate` 。  
  
### <a name="all"></a>全部

`true`如果集合中的所有元素都符合指定的條件，則傳回，否則傳回 `false` 。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>任意

`true`如果集合中有任何元素符合指定的條件，則傳回，否則傳回 `false` 。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>Average

計算集合中所有專案的平均值，或計算集合中所有元素的提供運算式。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>Count

計算集合中的元素數目。 您可以提供選擇性 `Boolean` 運算式，只計算集合中滿足條件的元素數目。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>群組

是指群組為或子句結果的查詢結果 `Group By` `Group Join` 。 `Group`函數只在 `Into` 或子句的子句中有效 `Group By` `Group Join` 。 如需詳細資訊和範例，請參閱[Group By 子句](group-by-clause.md)和[group Join 子句](group-join-clause.md)。

### <a name="longcount"></a>LongCount

計算集合中的元素數目。 您可以提供選擇性 `Boolean` 運算式，只計算集合中滿足條件的元素數目。 以的形式傳回結果 `Long` 。 如需範例，請參閱 `Count` 彙總函式。

### <a name="max"></a>最大值

計算集合中的最大值，或針對集合中的所有元素計算提供的運算式。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>最小值

計算集合中的最小值，或針對集合中的所有元素計算提供的運算式。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>Sum

計算集合中所有專案的總和，或針對集合中的所有元素計算提供的運算式。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>範例  

下列範例顯示如何使用 `Aggregate` 子句，將彙總函式套用至查詢結果。  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>建立使用者定義彙總函式

 您可以藉由將擴充方法加入至類型，在查詢運算式中包含您自己的自訂彙總函式 <xref:System.Collections.Generic.IEnumerable%601> 。 然後，您的自訂方法就可以在已參考彙總函式的可列舉集合上執行計算或作業。 如需擴充方法的詳細資訊，請參閱[擴充方法](../../programming-guide/language-features/procedures/extension-methods.md)。  
  
 例如，下列範例顯示的自訂彙總函式會計算數位集合的中間值。 擴充方法有兩個多載 `Median` 。 第一個多載會接受型別為的集合，做為輸入 `IEnumerable(Of Double)` 。 如果 `Median` 針對型別的查詢欄位呼叫彙總函式 `Double` ，就會呼叫這個方法。 方法的第二個多載 `Median` 可以傳遞任何泛型型別。 方法的泛型多載 `Median` 會使用參考 lambda 運算式的第二個參數， `Func(Of T, Double)` 以投影類型的值（從集合）做為類型的對應值 `Double` 。 然後，它會將中間值的計算委派給方法的其他多載 `Median` 。 如需 lambda 運算式的詳細資訊，請參閱[Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 下列範例會顯示 `Median` 在類型的集合上呼叫彙總函式的範例查詢 `Integer` ，以及類型的集合 `Double` 。 在 `Median` 類型的集合上呼叫彙總函式的查詢，會 `Double` 呼叫接受當做 `Median` 輸入之類型集合的方法多載 `Double` 。 在 `Median` 類型的集合上呼叫彙總函式的查詢，會 `Integer` 呼叫方法的泛型多載 `Median` 。  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](index.md)
- [Select 子句](select-clause.md)
- [From 子句](from-clause.md)
- [Where 子句](where-clause.md)
- [Group By 子句](group-by-clause.md)
