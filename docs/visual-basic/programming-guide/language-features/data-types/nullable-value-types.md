---
title: 可以為 null 的實值型別
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
ms.openlocfilehash: beed8262c50dc68330b8f03aa3d864ed2f8df0d5
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249678"
---
# <a name="nullable-value-types-visual-basic"></a>可為 Null 的實值類型 (Visual Basic)

有時，使用在某些情況下沒有定義值的數值型別。 例如，資料庫中的欄位可能必須區分具有有意義的賦值和沒有賦值。 可以擴展數值型別以獲取其正常值或空值。 這種擴展稱為*空類型*。

每個空數值型別都是從泛型<xref:System.Nullable%601>結構構造的。 考慮跟蹤與工作相關的活動的資料庫。 下面的示例構造一個可`Boolean`null 的類型，並聲明該類型的變數。 您可以通過三種方式編寫聲明：

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

變數`ridesBusToWork`可以保存`True`值 ，`False`或根本不值。 其初始預設值根本沒有值，在這種情況下，這可能意味著尚未為此人獲取資訊。 相反，`False`可能意味著資訊已經獲得，並且此人不坐公共汽車去上班。

可以使用空值型別宣告變數和屬性，也可以聲明具有空數值型別的元素的陣列。 您可以將具有空數值型別的過程聲明為參數，也可以從`Function`過程返回空數值型別。

不能在參考型別（如陣列、a`String`或 類）上構造可 null 類型。 基礎類型必須是數值型別。 如需詳細資訊，請參閱 [Value Types and Reference Types](value-types-and-reference-types.md)。

## <a name="using-a-nullable-type-variable"></a>使用可空類型變數

空數值型別最重要的成員是其<xref:System.Nullable%601.HasValue%2A>和<xref:System.Nullable%601.Value%2A>屬性。 對於空數值型別的變數，<xref:System.Nullable%601.HasValue%2A>告訴您該變數是否包含定義的值。 如果是<xref:System.Nullable%601.HasValue%2A>`True`，則可以從<xref:System.Nullable%601.Value%2A>讀取 值。 請注意，兩<xref:System.Nullable%601.HasValue%2A>者<xref:System.Nullable%601.Value%2A>都是`ReadOnly`屬性。

### <a name="default-values"></a>預設值

當您聲明具有空數值型別的變數時，其<xref:System.Nullable%601.HasValue%2A>屬性的預設值為`False`。 這意味著預設情況下，變數沒有定義的值，而不是其基礎數值型別的預設值。 在下面的示例中，變數`numberOfChildren`最初沒有定義的值，即使`Integer`類型的預設值為 0。

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

空值可用於指示未定義或未知值。 如果`numberOfChildren`已聲明為`Integer`，則沒有任何值可以指示資訊當前不可用。

### <a name="storing-values"></a>存儲值

以典型方式將值存儲在可 null 數值型別的變數或屬性中。 下面的示例將值分配給上一個示例中聲明`numberOfChildren`的變數。

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

如果空數值型別的變數或屬性包含已定義的值，則可能導致它恢復到未分配值的初始狀態。 為此，通過將變數或屬性設置為`Nothing`（）來執行此操作，如下例所示。

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> 儘管可以分配給`Nothing`null 數值型別的變數，但不能`Nothing`使用等號來測試它。 使用等號`someVar = Nothing`的比較， 始終計算為`Nothing`。 可以使用<xref:System.Nullable%601.HasValue%2A>或`False``Is``IsNot`運算子測試變數的屬性， 或測試。

### <a name="retrieving-values"></a>檢索值

若要檢索 null 數值型別的變數的值，應首先測試其<xref:System.Nullable%601.HasValue%2A>屬性以確認其具有值。 如果嘗試讀取值時<xref:System.Nullable%601.HasValue%2A>為`False`，Visual Basic 將引發異常<xref:System.InvalidOperationException>。 下面的示例顯示了讀取前面示例變數`numberOfChildren`的建議方法。

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>比較可消除類型

當布林運算式`Boolean`中使用空變數時，結果可以是`True`，`False`或`Nothing`。 下面是`And`和`Or`的真情況表。 因為`b1`現在有`b2`三個可能的值，因此有九個組合需要計算。

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

當布林變數或運算式的值為`Nothing`時，它既不是 ，`true`也不是`false`。 請思考一下下列範例。

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

在此示例中，`b1 And b2`計算 到`Nothing`。 因此，子`Else`句在每個`If`語句中執行，輸出如下所示：

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso`和`OrElse`，使用短路評估時，必須評估其第二個運算元， 當第一個`Nothing`計算到 。

## <a name="propagation"></a>傳播

如果算術、比較、移位或類型操作的一個或兩個運算元是空數值型別，則操作的結果也是空數值型別。 如果兩個運算元的值都不是`Nothing`，則對運算元的基礎值執行操作，就像兩者都不是空數值型別一樣。 在下面的示例中，變數`compare1`和`sum1`隱式類型。 如果將滑鼠指標放在滑鼠指標上，您將看到編譯器推斷它們兩個指標的空數值型別。

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

如果一個或兩個運算元的值`Nothing`為 ， 則結果將為`Nothing`。

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>將可空類型與資料一起使用

資料庫是使用空數值型別的最重要位置之一。 並非所有資料庫物件當前都支援空數值型別，但設計器生成的表配接器支援。 有關[空類型的表配接器支援，請參閱表配接器支援](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)。

## <a name="see-also"></a>另請參閱

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [資料類型](index.md)
- [值類型和參考類型](value-types-and-reference-types.md)
- [資料類型的疑難排解](troubleshooting-data-types.md)
- [使用 TableAdapter 填入資料集](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [If 運算子](../../../language-reference/operators/if-operator.md)
- [區域型別推斷](../variables/local-type-inference.md)
- [Is 運算子](../../../language-reference/operators/is-operator.md)
- [IsNot 運算子](../../../language-reference/operators/isnot-operator.md)
- [空數值型別 （C#）](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
