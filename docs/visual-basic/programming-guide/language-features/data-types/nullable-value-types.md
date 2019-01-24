---
title: 可為 Null 的實值類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: 522526392dd12ede729fe8b96677029c05af57c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665691"
---
# <a name="nullable-value-types-visual-basic"></a>可為 Null 的實值類型 (Visual Basic)
有時候您使用實值型別，在某些情況下沒有已定義的值。 比方說，在資料庫中的欄位可能要區分具有指派的值有意義，而不需指派的值。 實值型別可以擴充為一般值或 null 值。 呼叫這類延伸模組*可為 null 的型別*。  
  
 每個可為 null 的型別建構自泛型<xref:System.Nullable%601>結構。 請考慮追蹤資料庫，與工作相關的活動。 下列範例會建構可為 null`Boolean`輸入，並宣告該類型的變數。 您可以透過三種方式撰寫宣告︰  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]  
  
 變數`ridesBusToWork`可以保存的值`True`，值為`False`，或完全沒有值。 其初始預設值為任何值，這在此情況下可能表示的資訊有尚未取得此人。 相反地，`False`可能表示在取得的資訊，以及個人未搭乘匯流排運作。  
  
 您可以使用可為 null 的型別，宣告變數和屬性，而您可以宣告具有可為 null 的型別之項目的陣列。 您可以使用可為 null 的型別做為參數，宣告程序，而且您可以傳回 null 的型別，從`Function`程序。  
  
 您無法建構為 null 的類型，例如陣列、 參考型別上`String`，或類別。 基礎類型必須是實值型別。 如需詳細資訊，請參閱 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
## <a name="using-a-nullable-type-variable"></a>使用可為 Null 的型別變數  
 最重要的可為 null 的型別成員是其<xref:System.Nullable%601.HasValue%2A>和<xref:System.Nullable%601.Value%2A>屬性。 可為 null 的型別中，變數<xref:System.Nullable%601.HasValue%2A>會告訴您變數是否包含定義的值。 如果<xref:System.Nullable%601.HasValue%2A>已`True`，您可以讀取的值從<xref:System.Nullable%601.Value%2A>。 請注意，同時<xref:System.Nullable%601.HasValue%2A>並<xref:System.Nullable%601.Value%2A>是`ReadOnly`屬性。  
  
### <a name="default-values"></a>預設值  
 當您宣告變數與可為 null 的型別，其<xref:System.Nullable%601.HasValue%2A>屬性具有預設值是`False`。 這表示預設變數有任何已定義的值，而不是其基礎值型別的預設值。 在下列範例中，變數`numberOfChildren`最初的預設值即使沒有任何定義的值，`Integer`類型為 0。  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]  
  
 Null 值可用於指出為未定義或未知的值。 如果`numberOfChildren`已宣告為`Integer`，會有任何可能資訊不是目前可用的值。  
  
### <a name="storing-values"></a>儲存值  
 您可以變數或可為 null 的類型屬性中儲存值以一般方式。 下列範例會將值指派給變數`numberOfChildren`前一個範例中宣告。  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]  
  
 如果變數或屬性的可為 null 的型別包含定義的值，您可能會導致它還原成其初始狀態不提供 指派的值。 您可以將變數或屬性，以設定`Nothing`，如下列範例所示。  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]  
  
> [!NOTE]
>  雖然您可以指派`Nothing`為 null 的型別變數，您不能測試它的`Nothing`使用等號。 使用等號比較`someVar = Nothing`，一律評估為`Nothing`。 您可以測試的變數<xref:System.Nullable%601.HasValue%2A>屬性`False`，或使用測試`Is`或`IsNot`運算子。  
  
### <a name="retrieving-values"></a>擷取值  
 若要擷取的值可為 null 類型的變數，您應該先測試其<xref:System.Nullable%601.HasValue%2A>屬性，以確認它有值。 如果您嘗試讀取值時<xref:System.Nullable%601.HasValue%2A>已`False`，Visual Basic 會擲回<xref:System.InvalidOperationException>例外狀況。 下列範例顯示建議用來讀取變數`numberOfChildren`的先前的範例。  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]  
  
## <a name="comparing-nullable-types"></a>比較可為 Null 的類型  
 可為 null 時`Boolean`布林運算式中使用變數，可能造成`True`， `False`，或`Nothing`。 以下是針對的真值表`And`和`Or`。 因為`b1`和`b2`現在有三個可能的值，有九個的組合，來評估。  
  
|b1|b2|b1 和 b2|b1 或 b2|  
|--------|--------|---------------|--------------|  
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|  
|`Nothing`|`True`|`Nothing`|`True`|  
|`Nothing`|`False`|`False`|`Nothing`|  
|`True`|`Nothing`|`Nothing`|`True`|  
|`True`|`True`|`True`|`True`|  
|`True`|`False`|`False`|`True`|  
|`False`|`Nothing`|`False`|`Nothing`|  
|`False`|`True`|`False`|`True`|  
|`False`|`False`|`False`|`False`|  
  
 布林值變數或運算式的值何時`Nothing`，它既不是`true`也`false`。 請參考下列範例。  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]  
  
 在此範例中，`b1 And b2`評估為`Nothing`。 如此一來，`Else`子句會在每個執行`If`陳述式，並輸出如下所示：  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  `AndAlso` 並`OrElse`，其中使用最少運算評估，必須評估其第二個運算元，當第一個評估為`Nothing`。  
  
## <a name="propagation"></a>傳播  
 如果一或兩個運算元的算術、 比較、 shift 鍵或型別作業可為 null，作業的結果也是可為 null。 如果這兩個運算元都有值不是`Nothing`，作業會對基礎值的運算元，如同它們都不是 null 的型別。 在下列範例中，變數`compare1`和`sum1`隱含型別。 如果您將滑鼠指標停留時，您會看到編譯器推斷兩者都是可為 null 的型別。  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]  
  
 如果一個或兩個運算元的值為`Nothing`，結果會是`Nothing`。  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]  
  
## <a name="using-nullable-types-with-data"></a>使用可為 Null 的類型與資料  
 資料庫可以是其中一個最重要的位置，使用可為 null 的類型。 並非所有的資料庫物件目前支援可為 null 的型別，但設計工具所產生的資料表配接器。 請參閱中的 < TableAdapter 支援可為 Null 的型別 > [TableAdapter 概觀](/visualstudio/data-tools/tableadapter-overview)。
  
## <a name="see-also"></a>另請參閱
- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [使用可為 Null 的型別](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [TableAdapter 概觀](/visualstudio/data-tools/tableadapter-overview)
- [If 運算子](../../../../visual-basic/language-reference/operators/if-operator.md)
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)
