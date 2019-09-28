---
title: 可為 null 的實數值型別-Visual Basic
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
ms.openlocfilehash: 072496a560775a8f79274f1d44dd389d6ed5b40d
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351772"
---
# <a name="nullable-value-types-visual-basic"></a>可為 Null 的實值類型 (Visual Basic)

有時候，您在某些情況下會使用沒有已定義值的實值型別。 例如，資料庫中的欄位可能必須區別具有有意義且沒有指派值的指派值。 實值型別可以擴充以接受其一般值或 null 值。 這種延伸模組稱為*可為 null 的型*別。

每個可為 null 的型別都是由泛型 <xref:System.Nullable%601> 結構所構成。 請考慮一個追蹤工作相關活動的資料庫。 下列範例會建立可為 null 的 `Boolean` 型別，並宣告該型別的變數。 您可以用三種方式撰寫宣告：

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

變數 `ridesBusToWork` 可以保留值 `True`、`False` 的值，或完全沒有值。 其初始預設值完全沒有值，在此情況下可能表示尚未取得此人員的資訊。 相反地，`False` 可能表示已取得資訊，而且該人員不會使匯流排運作。

您可以使用可為 null 的型別來宣告變數和屬性，也可以宣告具有可為 null 類型之元素的陣列。 您可以使用可為 null 的類型來宣告具有參數的程式，也可以從 `Function` 程式傳回可為 null 的類型。

您無法在參考型別（例如陣列、`String` 或類別）上，建立可為 null 的型別。 基礎類型必須是實數值型別。 如需詳細資訊，請參閱 [Value Types and Reference Types](value-types-and-reference-types.md)。

## <a name="using-a-nullable-type-variable"></a>使用可為 Null 的型別變數

可為 null 的型別最重要的成員是它的 <xref:System.Nullable%601.HasValue%2A> 和 @no__t 1 屬性。 對於可為 null 之類型的變數，<xref:System.Nullable%601.HasValue%2A> 會告訴您該變數是否包含已定義的值。 如果 <xref:System.Nullable%601.HasValue%2A> 是 `True`，您可以從 <xref:System.Nullable%601.Value%2A> 讀取值。 請注意，<xref:System.Nullable%601.HasValue%2A> 和 <xref:System.Nullable%601.Value%2A> 都是 `ReadOnly` 屬性。

### <a name="default-values"></a>預設值

當您宣告具有可為 null 之類型的變數時，其 <xref:System.Nullable%601.HasValue%2A> 屬性的預設值為 `False`。 這表示根據預設，變數沒有已定義的值，而不是其基礎數值型別的預設值。 在下列範例中，`numberOfChildren` 的變數一開始沒有已定義的值，即使 `Integer` 類型的預設值為0也一樣。

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Null 值適用于表示未定義或未知的值。 如果 `numberOfChildren` 已宣告為 `Integer`，則不會有任何可能表示資訊目前無法使用的值。

### <a name="storing-values"></a>儲存值

您可以用一般方式，將值儲存在可為 null 之型別的變數或屬性中。 下列範例會將值指派給在上一個範例中宣告 `numberOfChildren` 的變數。

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

如果可為 null 之型別的變數或屬性包含已定義的值，您可以將它還原成其初始狀態，而不會指派值。 若要這麼做，請將變數或屬性設定為 `Nothing`，如下列範例所示。

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> 雖然您可以將 `Nothing` 指派給可為 null 之型別的變數，但是您無法使用等號來測試它是否為 `Nothing`。 使用等號的比較 `someVar = Nothing`，一律會評估為 `Nothing`。 您可以測試 `False` 的變數 <xref:System.Nullable%601.HasValue%2A> 屬性，或使用 `Is` 或 `IsNot` 運算子進行測試。

### <a name="retrieving-values"></a>正在抓取值

若要取出可為 null 之型別的變數值，您應該先測試其 @no__t 0 屬性，以確認它有值。 如果您嘗試在 <xref:System.Nullable%601.HasValue%2A> `False` 時讀取此值，Visual Basic 會擲回 <xref:System.InvalidOperationException> 例外狀況。 下列範例顯示在先前範例中讀取變數 `numberOfChildren` 的建議方式。

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>比較可為 Null 的類型

當可為 null 的 `Boolean` 變數用於布林運算式時，結果可以是 `True`、`False` 或 `Nothing`。 以下是 `And` 和 `Or` 的事實資料表。 因為 `b1` 和 `b2` 現在有三個可能的值，所以有九個組合可供評估。

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

當布林變數或運算式的值為 `Nothing` 時，不會 `true`，也不會 `false`。 請參考下列範例。

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

在此範例中，`b1 And b2` 會評估為 `Nothing`。 因此，會在每個 `If` 語句中執行 `Else` 子句，輸出如下：

`Expression is not true`

`Expression is not false`

> [!NOTE]
> 當第一個評估為 `Nothing` 時，`AndAlso` 和 `OrElse` （使用最少線路評估）必須評估其第二個運算元。

## <a name="propagation"></a>傳播

如果算術、比較、移位或類型運算的其中一個或兩個運算元可為 null，則作業的結果也會是可為 null。 如果這兩個運算元都有不 `Nothing` 的值，則會在運算元的基礎值上執行運算，就如同兩者都不是可為 null 的型別一樣。 在下列範例中，`compare1` 和 `sum1` 的變數會以隱含方式輸入。 如果您將滑鼠指標停留在其上方，您會看到編譯器會為這兩個專案推斷可為 null 的類型。

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

如果其中一個或兩個運算元的值為 `Nothing`，則結果會 `Nothing`。

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>搭配資料使用可為 Null 的類型

資料庫是使用可為 null 類型的其中一個最重要的地方。 並非所有資料庫物件目前都支援可為 null 的類型，但設計工具產生的資料表介面卡。 [如需可為 null 的類型，請參閱 TableAdapter 支援](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)。

## <a name="see-also"></a>另請參閱

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [資料類型](index.md)
- [Value Types and Reference Types](value-types-and-reference-types.md)
- [資料類型的疑難排解](troubleshooting-data-types.md)
- [使用 TableAdapter 填入資料集](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [If 運算子](../../../language-reference/operators/if-operator.md)
- [區域類型推斷](../variables/local-type-inference.md)
- [Is 運算子](../../../language-reference/operators/is-operator.md)
- [IsNot 運算子](../../../language-reference/operators/isnot-operator.md)
- [使用可為 Null 的C#實數值型別（）](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
