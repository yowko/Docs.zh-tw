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
ms.openlocfilehash: bb44ad85347b494b63dde964b2b407d8f038f2b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nullable-value-types-visual-basic"></a>可為 Null 的實值類型 (Visual Basic)
有時候您使用實值型別，在某些情況下沒有已定義的值。 例如，資料庫中的欄位可能區分有意義的值，而不需指派的值。 實值型別可以擴充為一般值或 null 值。 呼叫這類延伸模組*null 的型別*。  
  
 每個可為 null 的類型從泛型建構<xref:System.Nullable%601>結構。 考慮有個資料庫，以追蹤工作相關的活動。 下列範例會建構 null`Boolean`輸入，並宣告該類型的變數。 您可以撰寫宣告三種方式：  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]  
  
 變數`ridesBusToWork`可以保存的值`True`，值為`False`，或完全沒有值。 它的初始預設值是沒有值，這在此情況下，可能表示，資訊有尚未取得此人。 相反地，`False`可能表示已取得的資訊，以及個人未搭乘運作匯流排。  
  
 您可以使用可為 null 的類型，宣告變數和屬性，而且您可以宣告具有可為 null 的型別之項目的陣列。 您可以使用可為 null 的類型作為參數，宣告程序，您可以傳回 null 的型別，從`Function`程序。  
  
 您無法建構 null 的型別，例如陣列、 在參考類型上`String`，或類別。 基礎類型必須是實值類型。 如需詳細資訊，請參閱[實值類型和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
## <a name="using-a-nullable-type-variable"></a>使用可為 Null 的類型變數  
 最重要的可為 null 的型別成員是其<xref:System.Nullable%601.HasValue%2A>和<xref:System.Nullable%601.Value%2A>屬性。 Null 的型別變數<xref:System.Nullable%601.HasValue%2A>會告訴您變數是否包含定義的值。 如果<xref:System.Nullable%601.HasValue%2A>是`True`，您可以從中讀取值<xref:System.Nullable%601.Value%2A>。 請注意，兩者<xref:System.Nullable%601.HasValue%2A>和<xref:System.Nullable%601.Value%2A>是`ReadOnly`屬性。  
  
### <a name="default-values"></a>預設值  
 當您宣告變數時有可為 null 的型別，其<xref:System.Nullable%601.HasValue%2A>屬性具有預設值是`False`。 這表示預設變數有任何已定義的值，而非基礎值型別的預設值。 在下列範例中，變數`numberOfChildren`一開始它沒有已定義的值，即使預設值為`Integer`類型為 0。  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]  
  
 Null 值可用於指出未定義或未知的值。 如果`numberOfChildren`已經宣告為`Integer`，會有任何可能表示資訊不是目前可用的值。  
  
### <a name="storing-values"></a>儲存值  
 您儲存值的變數或屬性，可為 null 的型別中的常見方式。 下列範例會將值指派給變數`numberOfChildren`前一個範例中宣告。  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]  
  
 如果變數或可為 null 類型的屬性包含已定義的值，您可以讓它還原為其初始狀態不需要指定的值。 您可以將變數或屬性，以設定`Nothing`，如下列範例所示。  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]  
  
> [!NOTE]
>  雖然您可以指派`Nothing`不能為 null 的型別變數，測試為`Nothing`使用等號。 使用等號比較`someVar = Nothing`，一律評估為`Nothing`。 您可以測試變數<xref:System.Nullable%601.HasValue%2A>屬性`False`，或使用測試`Is`或`IsNot`運算子。  
  
### <a name="retrieving-values"></a>擷取值  
 若要擷取的值可為 null 類型的變數，您應該先測試其<xref:System.Nullable%601.HasValue%2A>屬性來確認它有值。 如果您嘗試讀取的值時<xref:System.Nullable%601.HasValue%2A>是`False`，Visual Basic 會擲回<xref:System.InvalidOperationException>例外狀況。 下列範例將示範建議用來讀取變數`numberOfChildren`的上一個範例。  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]  
  
## <a name="comparing-nullable-types"></a>比較可為 Null 的類型  
 可為 null 時`Boolean`布林運算式中使用變數，而導致`True`， `False`，或`Nothing`。 下列是資料表的事實資料表`And`和`Or`。 因為`b1`和`b2`現在有三個可能的值，有九個組合，來評估。  
  
|B1|B2|b1 和 b2|b1 或 b2|  
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
  
 布林值變數或運算式的值時`Nothing`，既不是`true`也`false`。 請參考下列範例。  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]  
  
 在此範例中，`b1 And b2`評估為`Nothing`。 如此一來，`Else`子句在每個執行`If`陳述式，並輸出如下所示：  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  `AndAlso` 和`OrElse`，其中使用最少運算評估，必須評估第二個運算元，當第一個評估為`Nothing`。  
  
## <a name="propagation"></a>傳播  
 如果一或兩個運算元的算術、 比較、 shift 鍵或型別作業可為 null 時，作業的結果也是可為 null。 如果兩個運算元的值不`Nothing`，作業不會對基礎值的運算元，如同它們都不是 null 的型別。 在下列範例中，變數`compare1`和`sum1`隱含型別。 如果您將滑鼠指標停留時，您會看到編譯器推斷可為 null 的類型，兩者都是。  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]  
  
 如果一或兩個運算元的值為`Nothing`，結果會是`Nothing`。  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]  
  
## <a name="using-nullable-types-with-data"></a>使用可為 Null 的類型與資料  
 若要使用可為 null 的型別最重要的其中一個資料庫。 並非所有的資料庫物件目前支援可為 null 的類型，但設計工具產生的資料表配接器。 請參閱中的 < TableAdapter 支援可為 Null 的類型 > [TableAdapter 概觀](/visualstudio/data-tools/tableadapter-overview)。
  
## <a name="see-also"></a>另請參閱  
 <xref:System.InvalidOperationException>  
 <xref:System.Nullable%601.HasValue%2A>  
 [使用可為 Null 的型別](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [TableAdapter 概觀](/visualstudio/data-tools/tableadapter-overview)  
 [If 運算子](../../../../visual-basic/language-reference/operators/if-operator.md)  
 [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)
