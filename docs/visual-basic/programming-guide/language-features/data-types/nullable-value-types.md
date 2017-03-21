---
title: "可為 null 的實值類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Nullable
dev_langs:
- VB
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: 23
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9cdf1864fe955a082936596821ee84c831b86444
ms.lasthandoff: 03/13/2017

---
# <a name="nullable-value-types-visual-basic"></a>可為 Null 的實值類型 (Visual Basic)
有時候您使用實值型別，在某些情況下沒有已定義的值。 例如，在資料庫中的欄位可能區別有意義的值，而不需指定的值。 實值型別可以擴充為一般值或 null 值。 這類延伸模組會呼叫*null 的型別*。  
  
 每個可為 null 的型別建構自泛型<xref:System.Nullable%601>結構。</xref:System.Nullable%601> 假設資料庫會追蹤與工作相關的活動。 下列範例會建構可為 null`Boolean`輸入，並宣告該類型的變數。 您可以撰寫宣告三種方式︰  
  
 [!code-vb[VbVbalrNullableValue #&1;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]  
  
 變數`ridesBusToWork`可以保存的值`True`，值為`False`，或根本沒有值。 它的初始預設值是沒有值，這在此情況下，可能表示，資訊有尚未取得此人。 相反地，`False`可能代表在取得的資訊，以及個人未搭乘公車上班。  
  
 您可以使用可為 null 的型別宣告變數和屬性，而且您可以宣告具有 null 的型別之項目的陣列。 您可以做為參數，可為 null 的型別宣告的程序，您可以傳回 null 的型別，從`Function`程序。  
  
 您無法建構 null 的型別，例如陣列、 參考型別上`String`，或類別。 基礎型別必須是實值型別。 如需詳細資訊，請參閱[實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
## <a name="using-a-nullable-type-variable"></a>使用 Null 的型別變數  
 最重要的 null 的型別成員是其<xref:System.Nullable%601.HasValue%2A>和<xref:System.Nullable%601.Value%2A>屬性。</xref:System.Nullable%601.Value%2A> </xref:System.Nullable%601.HasValue%2A> Null 的型別變數<xref:System.Nullable%601.HasValue%2A>會告訴您變數是否包含定義的值。</xref:System.Nullable%601.HasValue%2A> 如果<xref:System.Nullable%601.HasValue%2A>是`True`，您可以讀取的值從<xref:System.Nullable%601.Value%2A>.</xref:System.Nullable%601.Value%2A> </xref:System.Nullable%601.HasValue%2A> 請注意，兩者<xref:System.Nullable%601.HasValue%2A>和<xref:System.Nullable%601.Value%2A>是`ReadOnly`屬性。</xref:System.Nullable%601.Value%2A> </xref:System.Nullable%601.HasValue%2A>  
  
### <a name="default-values"></a>預設值  
 當您宣告變數時使用可為 null 的型別，其<xref:System.Nullable%601.HasValue%2A>屬性的預設值為`False`。</xref:System.Nullable%601.HasValue%2A> 這表示預設變數有任何已定義的值，而非基礎值型別的預設值。 在下列範例中，變數`numberOfChildren`一開始的預設值即使沒有任何定義的值，`Integer`類型為 0。  
  
 [!code-vb[VbVbalrNullableValue #&2;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]  
  
 Null 值可用於指出未定義或未知的值。 如果`numberOfChildren`已宣告為`Integer`，有沒有可能表示資訊不是目前可用的值。  
  
### <a name="storing-values"></a>儲存值  
 您儲存值的變數或屬性，可為 null 的型別中的一般方式。 下列範例會將值指派給變數`numberOfChildren`前一個範例中宣告。  
  
 [!code-vb[VbVbalrNullableValue #&3;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]  
  
 如果變數或屬性，可為 null 的型別包含已定義的值，您可以讓它將會還原為其初始狀態的不擁有指派的值。 您可以將變數或屬性來設定`Nothing`，如下列範例所示。  
  
 [!code-vb[VbVbalrNullableValue #&4;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]  
  
> [!NOTE]
>  雖然您可以指派`Nothing`為 null 的型別變數，您無法測試應用程式的`Nothing`使用等號。 使用等號比較`someVar = Nothing`，一律評估為`Nothing`。 您可以測試變數<xref:System.Nullable%601.HasValue%2A>屬性`False`，或使用測試`Is`或`IsNot`運算子。</xref:System.Nullable%601.HasValue%2A>  
  
### <a name="retrieving-values"></a>擷取值  
 若要擷取的值可為 null 型別的變數，您應該先測試其<xref:System.Nullable%601.HasValue%2A>屬性來確認它有值。</xref:System.Nullable%601.HasValue%2A> 如果您嘗試讀取的值時<xref:System.Nullable%601.HasValue%2A>是`False`，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會擲回<xref:System.InvalidOperationException>例外狀況。</xref:System.InvalidOperationException> </xref:System.Nullable%601.HasValue%2A> 下列範例將示範建議的方式讀取變數`numberOfChildren`的上一個範例。  
  
 [!code-vb[VbVbalrNullableValue #&5;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]  
  
## <a name="comparing-nullable-types"></a>比較可為 Null 的型別  
 可為 null 時`Boolean`布林運算式中使用變數，就可能造成`True`， `False`，或`Nothing`。 下列是資料表的事實資料表`And`和`Or`。 因為`b1`和`b2`現在有三個可能的值，有九個組合，來評估。  
  
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
  
 布林值變數或運算式的值時`Nothing`，它不是上述`true`或`false`。 請參考下列範例。  
  
 [!code-vb[VbVbalrNullableValue #&6;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]  
  
 在此範例中，`b1 And b2`評估為`Nothing`。 如此一來，`Else`子句會在每個執行`If`陳述式，並將輸出如下所示︰  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  `AndAlso`和`OrElse`，哪些使用最少運算評估，必須評估其第二個運算元，當第一個評估為`Nothing`。  
  
## <a name="propagation"></a>傳播  
 如果一或兩個運算元的算術、 比較、 shift 鍵或型別作業可為 null，運算的結果也是可為 null。 如果兩個運算元的值不是`Nothing`，如同它們都不是運算元的基礎值上執行作業可為 null 的型別。 在下列範例中，變數`compare1`和`sum1`隱含型別。 如果您將滑鼠指標停留時，您會看到編譯器推斷兩者都是可為 null 的型別。  
  
 [!code-vb[VbVbalrNullableValue #&7;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]  
  
 如果一或兩個運算元的值為`Nothing`，結果會是`Nothing`。  
  
 [!code-vb[VbVbalrNullableValue #&8;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]  
  
## <a name="using-nullable-types-with-data"></a>可為 Null 的型別中使用資料  
 資料庫是其中一個最重要的地方使用可為 null 的型別。 並非所有的資料庫物件目前支援可為 null 的型別，但是設計工具產生的資料表配接器。 請參閱中的 「 TableAdapter 支援可為 Null 的型別 」 [TableAdapter 概觀](https://docs.microsoft.com/visualstudio/data-tools/tableadapter-overview)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.InvalidOperationException></xref:System.InvalidOperationException>   
 <xref:System.Nullable%601.HasValue%2A></xref:System.Nullable%601.HasValue%2A>   
 [使用可為 Null 的型別](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)   
 [資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [TableAdapter 概觀](https://docs.microsoft.com/visualstudio/data-tools/tableadapter-overview)   
 [如果運算子](../../../../visual-basic/language-reference/operators/if-operator.md)   
 [區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)
