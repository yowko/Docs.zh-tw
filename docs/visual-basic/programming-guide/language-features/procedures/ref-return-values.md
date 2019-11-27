---
title: Ref 傳回值
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: 2d2a302a899fbde549161469f281d3e580bcb71f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352542"
---
# <a name="support-for-reference-return-values-visual-basic"></a>支援參考傳回值（Visual Basic）

從C# 7.0 開始， C#語言支援參考傳回*值*。 瞭解參考傳回值的其中一種方式是，它們與以傳址方式傳遞至方法的引數相反。 當修改以傳址方式傳遞的引數時，變更會反映在呼叫端的變數值中。 當方法提供參考傳回值給呼叫端時，呼叫端對參考傳回值所做的修改會反映在被呼叫的方法資料中。

Visual Basic 不允許您撰寫具有參考傳回值的方法，但它可讓您使用參考傳回值。 換句話說，您可以呼叫具有參考傳回值的方法，並修改該傳回值，而參考傳回值的變更會反映在被呼叫的方法資料中。

## <a name="modifying-the-ref-return-value-directly"></a>直接修改 ref 傳回值

對於一律成功且沒有 `ByRef` 參數的方法，您可以直接修改參考傳回值。 若要這麼做，您可以將新值指派給傳回參考傳回值的運算式。

下列C#範例會定義會遞增內部值，並將其傳回為參考傳回值的 `NumericValue.IncrementValue` 方法。

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

然後，下列 Visual Basic 範例中的呼叫者會修改參考傳回值。 請注意，具有 `NumericValue.IncrementValue` 方法呼叫的行會不會將值指派給方法。 相反地，它會將值指派給方法所傳回的參考傳回值。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>使用 helper 方法

在其他情況下，直接修改方法呼叫的參考傳回值可能不一定是理想的做法。 例如，傳回字串的搜尋方法可能不一定會找到相符的結果。 在這種情況下，您只想要在搜尋成功時修改參考傳回值。

下列C#範例說明此案例。 它會定義以C#撰寫的 `Sentence` 類別，其中包含 `FindNext` 方法，可在以指定子字串開頭的句子中尋找下一個單字。 字串會以參考傳回值傳回，而參考所傳遞至方法的 `Boolean` 變數會指出搜尋是否成功。 參考傳回值表示呼叫端不能唯讀取傳回的值。他或她也可以修改它，這項修改會反映在 `Sentence` 類別內部所包含的資料中。

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

在此情況下，直接修改參考傳回值並不可靠，因為方法呼叫可能會找不到相符的結果，並傳回句子中的第一個單字。 在這種情況下，呼叫端不會不慎修改句子的第一個單字。 這可能是因為呼叫端傳回 `null` （或 Visual Basic 中 `Nothing`）而導致的。 但是在這種情況下，嘗試修改值 `Nothing` 的字串會擲回 <xref:System.NullReferenceException>。 如果呼叫端也可以防止傳回 <xref:System.String.Empty?displayProperty=nameWithType>，但這需要呼叫者定義其值為 <xref:System.String.Empty?displayProperty=nameWithType>的字串變數。 雖然呼叫者可以修改該字串，但修改本身沒有任何用途，因為修改過的字串與 `Sentence` 類別所儲存之句子中的單字沒有任何關聯性。

處理這種情況的最佳方式，就是將參考傳回值傳遞至 helper 方法。 Helper 方法接著會包含邏輯，以判斷方法呼叫是否成功，如果有的話，則會修改參考傳回值。 下列範例提供可能的執行方式。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>另請參閱

- [依值和傳址方式傳遞引數](passing-arguments-by-value-and-by-reference.md)
- [Visual Basic 中的程序](index.md)
