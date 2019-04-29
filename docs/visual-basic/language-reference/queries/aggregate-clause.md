---
title: Aggregate 子句 (Visual Basic)
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
ms.openlocfilehash: 21781db637c71abbbe9366bc95b6ee4c89ac2246
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61712626"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate 子句 (Visual Basic)
適用於一或多個彙總函式集合。  
  
## <a name="syntax"></a>語法  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`element`|必要項。 變數，可用來逐一查看集合的元素。|  
|`type`|選擇性。 `element` 的類型。 如果未不指定任何類型，類型`element`推斷從`collection`。|  
|`collection`|必要項。 指的是要處理的集合。|  
|`clause`|選擇性。 一或多個查詢子句，例如`Where`子句，來限定要套用的彙總子句或子句的查詢結果。|  
|`expressionList`|必要項。 一或多個以逗點分隔運算式可識別要套用至集合的彙總函式。 您可以將別名套用至指定成員名稱的查詢結果的彙總函式。 如果未不提供任何別名，則會使用彙總函式的名稱。 如需範例，請參閱本主題稍後的彙總函式的相關章節。|  
  
## <a name="remarks"></a>備註  
 `Aggregate`子句可以用來在您的查詢中包含彙總函式。 彙總函式會執行檢查及計算值的集合，並傳回單一值。 您可以使用查詢結果型別的成員，以存取計算的值。 您可以使用標準彙總函式`All`， `Any`， `Average`， `Count`， `LongCount`， `Max`， `Min`，以及`Sum`函式。 這些函式是熟悉的開發人員已熟悉 SQL 中的彙總。 它們都是以本主題的下一節所述。  
  
 查詢結果中包含的彙總函式的結果為查詢結果型別的欄位。 您可以提供彙總函式的結果，以指定的查詢結果型別，用以保存彙總值的成員名稱的別名。 如果未不提供任何別名，則會使用彙總函式的名稱。  
  
 `Aggregate`子句可以開始查詢，或者它可以包含在查詢中的其他子句。 如果`Aggregate`子句開始查詢，則結果為單一值中指定的彙總函式的結果`Into`子句。 如果一個以上的彙總函式中指定`Into`子句，查詢會傳回個別屬性來參考每個彙總函式的結果的單一類型`Into`子句。 如果`Aggregate`子句會包含在查詢中的其他子句，查詢集合中傳回的型別就會有不同的屬性來參考每個彙總函式的結果`Into`子句。  
  
## <a name="aggregate-functions"></a>彙總函式

以下是適用於標準彙總函式`Aggregate`子句。  
  
### <a name="all"></a>全部

會傳回`true`如果在集合中的所有項目符合指定的條件; 否則會傳回`false`。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>任何

會傳回`true`如果在集合中的任何項目符合指定的條件; 否則會傳回`false`。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>平均

計算集合中的所有項目的平均值，或計算提供的運算式，針對集合中的所有項目。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>計數

計算集合中的項目數。 您可以提供選擇性`Boolean`運算式來計算只在集合中符合條件的項目數目。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>群組

查詢結果的群組是指`Group By`或`Group Join`子句。 `Group`函式是僅適用於`Into`子句`Group By`或`Group Join`子句。 如需詳細資訊和範例，請參閱 <<c0> [ 群組的子句](../../../visual-basic/language-reference/queries/group-by-clause.md)並[Group Join 子句](../../../visual-basic/language-reference/queries/group-join-clause.md)。

### <a name="longcount"></a>LongCount

計算集合中的項目數。 您可以提供選擇性`Boolean`運算式來計算只在集合中符合條件的項目數目。 傳回結果做`Long`。 如需範例，請參閱`Count`彙總函式。

### <a name="max"></a>最大

從集合中的最大值或是計算集合中的所有項目的而提供的運算式。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>最小

計算集合的最小值或計算提供的運算式，針對集合中的所有項目。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>Sum

集合中的所有項目的總和或是計算集合中的所有項目的而提供的運算式。 以下是一個範例：

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>範例  

下列範例示範如何使用`Aggregate`子句，以套用彙總函式，將查詢結果。  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>建立使用者定義彙總函式

 您也可以加入擴充方法，以查詢運算式中包含您自己自訂的彙總函式<xref:System.Collections.Generic.IEnumerable%601>型別。 計算或參考您彙總函式的可列舉集合上的作業，接著可以執行您的自訂方法。 如需擴充方法的詳細資訊，請參閱[擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。  
  
 例如，下列範例顯示自訂的彙總函式會計算數字集合的中間值。 有兩個多載`Median`擴充方法。 第一個多載接受，做為輸入，型別集合`IEnumerable(Of Double)`。 如果`Median`彙總函式會呼叫類型的查詢欄位`Double`，會呼叫這個方法。 第二個多載`Median`方法可以傳遞任何泛型型別。 泛型多載`Median`方法會採用第二個參數會參考`Func(Of T, Double)`投影的類型 （集合） 的值類型的對應值的 lambda 運算式`Double`。 然後它會委派其他多載的中間值的計算`Median`方法。 如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 下列範例顯示範例查詢來呼叫`Median`彙總類型的集合上的函式`Integer`，和型別集合`Double`。 查詢會呼叫`Median`彙總類型的集合上的函式`Double`呼叫的多載`Median`做為輸入，接受型別集合的方式來`Double`。 查詢會呼叫`Median`彙總類型的集合上的函式`Integer`呼叫的泛型多載`Median`方法。  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By 子句](../../../visual-basic/language-reference/queries/group-by-clause.md)
