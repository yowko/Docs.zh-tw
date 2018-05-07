---
title: Aggregate 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 1db4b7fdcf9c8a38c2c49eca9d874eccea90ab1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate 子句 (Visual Basic)
套用至集合的一個或多個彙總函式。  
  
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
|`element`|必要。 變數，可用來逐一查看集合的元素。|  
|`type`|選擇性。 `element` 的類型。 如果未不指定任何類型，類型`element`推斷從`collection`。|  
|`collection`|必要。 指的是集合上操作。|  
|`clause`|選擇性。 一或多個查詢子句，例如`Where`子句，來限定要套用彙總子句或子句來查詢結果。|  
|`expressionList`|必要。 一或多個逗號分隔的運算式，識別要套用至集合的彙總函式。 您可以將別名套用至指定成員名稱的查詢結果的彙總函式。 如果提供了沒有別名，就會使用彙總函式的名稱。 如需範例，請參閱本主題稍後的彙總函式的相關章節。|  
  
## <a name="remarks"></a>備註  
 `Aggregate`子句可以用來在查詢中包含彙總函式。 彙總函式會執行檢查及計算值的集合，並傳回單一值。 您可以使用查詢結果型別的成員，以存取計算的值。 您可以使用標準彙總函式`All`， `Any`， `Average`， `Count`， `LongCount`， `Max`， `Min`，和`Sum`函式。 這些函式是很熟悉的開發人員熟悉 SQL 中的彙總的。 本主題的下一節將描述這些。  
  
 查詢結果中包含彙總函式的結果做為查詢結果型別的欄位。 您可以提供彙總函式的結果來指定查詢結果類型會保留彙總值的成員名稱的別名。 如果提供了沒有別名，就會使用彙總函式的名稱。  
  
 `Aggregate`子句可以開始查詢，或者它可以包含為查詢中的其他子句。 如果`Aggregate`子句開始查詢，則結果為單一值，是在指定的彙總函式的結果`Into`子句。 如果一個以上的彙總函式中指定了`Into`子句，此查詢會傳回單一類型具有不同的屬性參考中的每個彙總函式的結果`Into`子句。 如果`Aggregate`子句做為包含在查詢中的其他子句，查詢集合中傳回的型別就會有不同的屬性，來參考每個彙總函式的結果`Into`子句。  
  
## <a name="aggregate-functions"></a>彙總函式  
 下列清單說明適用於標準彙總函式`Aggregate`子句。  
  
|功能|描述|  
|---|---|  
|`All`|傳回`true`如果集合中的所有元素都符合指定的條件; 否則會傳回`false`。 以下是一個範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]|  
|`Any`|傳回`true`如果集合中的任何項目符合指定的條件; 否則會傳回`false`。 以下是一個範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]|  
|`Average`|計算集合或針對集合中的所有項目提供的計算運算式中的所有項目的平均值。 以下是一個範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]|  
|`Count`|計算集合中的項目數目。 您可以提供選擇性`Boolean`運算式來計算只在集合中符合條件的項目數目。 以下是一個範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]|  
|`Group`|查詢結果的群組是指`Group By`或`Group Join`子句。 `Group`函式是只適用於`Into`子句`Group By`或`Group Join`子句。 如需詳細資訊和範例，請參閱[群組 By 子句](../../../visual-basic/language-reference/queries/group-by-clause.md)和[Group Join 子句](../../../visual-basic/language-reference/queries/group-join-clause.md)。|  
|`LongCount`|計算集合中的項目數目。 您可以提供選擇性`Boolean`運算式來計算只在集合中符合條件的項目數目。 傳回結果做`Long`。 如需範例，請參閱`Count`彙總函式。|  
|`Max`|從集合中，最大值或是計算集合中的所有項目的而提供的運算式。 以下是一個範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]|  
|`Min`|計算集合，從最小值或計算集合中的所有項目的而提供的運算式。 以下是一個範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]|  
|`Sum`|集合中的所有元素的總和或是計算集合中的所有項目的而提供的運算式。 以下是一個範例：<br /><br /> [!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]|  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用`Aggregate`子句套用至查詢結果的彙總函式。  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>建立使用者定義彙總函式  
 您也可以加入擴充方法，以在查詢運算式中包含您自己自訂的彙總函式<xref:System.Collections.Generic.IEnumerable%601>型別。 計算或已參照您彙總函式的可列舉集合上的作業，然後可以執行您的自訂方法。 如需擴充方法的詳細資訊，請參閱[擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。  
  
 例如，下列程式碼範例顯示自訂的彙總函式會計算數字集合的中間值。 有兩個多載`Median`擴充方法。 第一個多載接受，做為輸入，型別集合`IEnumerable(Of Double)`。 如果`Median`查詢欄位中的型別呼叫彙總函式`Double`，會呼叫這個方法。 第二個多載`Median`方法可以傳遞任何泛型型別。 泛型多載`Median`方法使用第二個參數參考`Func(Of T, Double)`投影的類型 （集合） 的值做為類型的對應值的 lambda 運算式`Double`。 然後它會委派的其他多載的中間值計算`Median`方法。 如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 下列程式碼範例顯示範例查詢來呼叫`Median`彙總函式類型集合上的`Integer`，和集合型別的`Double`。 呼叫此查詢`Median`彙總函式的集合型別上`Double`呼叫的多載`Median`做為輸入，接受型別集合的方式來`Double`。 呼叫此查詢`Median`彙總函式的集合型別上`Integer`泛型多載會呼叫`Median`方法。  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [查詢](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Group By 子句](../../../visual-basic/language-reference/queries/group-by-clause.md)
