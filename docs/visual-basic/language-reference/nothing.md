---
title: Nothing 關鍵字
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 3bd4681341a33cc8db4ecbc2b284be243db56549
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344170"
---
# <a name="nothing-keyword-visual-basic"></a>無關鍵詞（Visual Basic）

表示任何資料類型的預設值。 若是參考型別，預設值為 `null` 參考。 對於實數值型別，預設值取決於實數值型別是否可為 null。

> [!NOTE]
> 針對不可為 null 的實數值型別，Visual Basic 中的 `Nothing` 與C#中的 `null` 不同。 在 Visual Basic 中，如果您將不可為 null 的實數值型別變數設定為 `Nothing`，則變數會設定為其宣告類型的預設值。 在C#中，如果您將不可為 null 的實數值型別的變數指派給 `null`，就會發生編譯時期錯誤。

## <a name="remarks"></a>備註

`Nothing` 代表資料類型的預設值。 預設值取決於變數是實數值型別或參考型別。

實*值型*別的變數直接包含它的值。 實值型別包括所有數值資料類型、`Boolean`、`Char`、`Date`、所有結構和所有列舉。 *參考型別*的變數會將物件實例的參考儲存在記憶體中。 參考型別包括類別、陣列、委派和字串。 如需詳細資訊，請參閱 [Value Types and Reference Types](../programming-guide/language-features/data-types/value-types-and-reference-types.md)。

如果變數是實值型別，則 `Nothing` 的行為取決於變數是否為可為 null 的資料型別。 若要表示可為 null 的實值型別，請將 `?` 修飾詞加入至型別名稱。 將 `Nothing` 指派給可為 null 的變數會將值設為 `null`。 如需詳細資訊和範例，請參閱[可為 null 的實數值型別](../programming-guide/language-features/data-types/nullable-value-types.md)。

如果變數是不可為 null 的實數值型別，請將 `Nothing` 指派給它，將其設定為其宣告類型的預設值。 如果該類型包含變數成員，則會將它們全部設定為預設值。 下列範例會針對純量類型說明這種情況。

[!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]

如果變數是參考型別，將 `Nothing` 指派給變數，就會將它設定為變數類型的 `null` 參考。 設定為 `null` 參考的變數未與任何物件相關聯。 下列範例為其示範：

[!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]

檢查是否 `null`參考（或可為 null 的實數值型別）變數時，請勿使用 `= Nothing` 或 `<> Nothing`。 一律使用 `Is Nothing` 或 `IsNot Nothing`。

對於 Visual Basic 中的字串，空字串等於 `Nothing`。 因此，`"" = Nothing` 為 true。

下列範例會顯示使用 `Is` 和 `IsNot` 運算子的比較：

[!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]

如果您在未使用 `As` 子句的情況下宣告變數，並將它設定為 `Nothing`，則變數的類型會是 `Object`。 `Dim something = Nothing`的範例。 當 `Option Strict` 為 on，且 `Option Infer` 為 off 時，就會發生編譯時期錯誤。

當您將 `Nothing` 指派給物件變數時，它就不會再參考任何物件實例。 如果變數先前已參考實例，將其設定為 `Nothing` 不會終止實例本身。 實例會終止，而且只有在垃圾收集行程（GC）偵測到沒有任何使用中的參考之後，才會釋放與它相關聯的記憶體和系統資源。

`Nothing` 不同于 <xref:System.DBNull> 物件，代表未初始化的 variant 或不存在的資料庫資料行。

## <a name="see-also"></a>請參閱

- [Dim 陳述式](./statements/dim-statement.md)
- [物件存留期：物件的建立和終結](../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Visual Basic 中的存留期](../programming-guide/language-features/declared-elements/lifetime.md)
- [Is 運算子](./operators/is-operator.md)
- [IsNot 運算子](./operators/isnot-operator.md)
- [可為 Null 的值類型](../programming-guide/language-features/data-types/nullable-value-types.md)
