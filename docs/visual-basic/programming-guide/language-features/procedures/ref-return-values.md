---
title: Ref 傳回值 (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: ba649c4beaf3ec70a8c118f823fe8f25651a05a7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198298"
---
# <a name="support-for-reference-return-values-visual-basic"></a>支援參考傳回值 (Visual Basic)

開頭為C#7.0 中，C#語言支援*參考傳回值*。 若要了解參考傳回值的方法之一是它們是相反的由參考傳遞至方法的引數。 修改參考所傳遞的引數時，所做的變更會反映在變數的值，呼叫端上。 當方法呼叫端提供參考傳回值時，將參考傳回值對呼叫端所作的修改會反映在呼叫的方法的資料。

Visual Basic 不允許您撰寫方法，以參考傳回值，但能讓您使用參考傳回值。 換句話說，您可以呼叫具有參考傳回值的方法，並修改該傳回值，並將參考傳回值的變更會反映在呼叫的方法的資料。

## <a name="modifying-the-ref-return-value-directly"></a>直接修改 ref 傳回值

方法永遠成功，而且沒有任何`ByRef`參數，您可以直接修改參考傳回值。 您可以將新的值指派給傳回的參考傳回值的運算式。 

下列C#範例會定義`NumericValue.IncrementValue`方法遞增內部的值並將其傳回做為參考傳回值。 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

參考傳回值，然後修改下列 Visual Basic 範例中的呼叫端。 請注意，該程式行使用`NumericValue.IncrementValue`方法呼叫不會將值指派給方法。 相反地，它會指派值給方法所傳回的參考傳回值。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>使用 helper 方法

在其他情況下，直接修改參考傳回值的方法呼叫不一定需要。 比方說，傳回的字串搜尋方法，可能不會永遠發現相符項目。 在此情況下，您想要修改參考傳回值，只有當搜尋已成功。

下列C#範例說明此案例。 它會定義`Sentence`撰寫的類別C#包含`FindNext`方法，可在句子開頭為指定的子字串中尋找下一個字。 字串會以參考傳回值傳回，而參考所傳遞至方法的 `Boolean` 變數會指出搜尋是否成功。 將參考傳回值會指出，呼叫端不只可以讀取傳回的值;他或她還可以修改它，而且該修改會反映在內部中包含的資料`Sentence`類別。

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

直接修改參考傳回值在此情況下不可靠，因為在方法呼叫可能會失敗，以尋找相符項目並傳回句子中的第一個字。 在此情況下，呼叫端會不小心修改第一個字的句子。 這可能導致傳回呼叫端`null`(或`Nothing`Visual Basic 中)。 但在此情況下，嘗試修改的字串，其值是`Nothing`會擲回<xref:System.NullReferenceException>。 如果也無法阻止傳回呼叫端<xref:System.String.Empty?displayProperty=nameWithType>，但這需要呼叫端定義其值的字串變數<xref:System.String.Empty?displayProperty=nameWithType>。 雖然呼叫者可以修改該字串，本身的修改毫無意義可言，因為修改的字串文字並沒有關聯性中所儲存的句子`Sentence`類別。

若要解決這種情況，最好是將參考傳回值傳址方式傳遞的 helper 方法。 Helper 方法則會包含邏輯，以判斷是否方法呼叫成功，如果有，修改參考傳回值。 下列範例會提供可能的實作。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>另請參閱

[值和傳參考方式傳遞引數](passing-arguments-by-value-and-by-reference.md)   
[Visual Basic 中的程序](index.md)   


