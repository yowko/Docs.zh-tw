---
title: 參考傳回值
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: f2a92c584dbb12a322e28435d797fa4d7c2f6dbb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186929"
---
# <a name="support-for-reference-return-values-visual-basic"></a>支援參考傳回值（可視基本值）

從 C# 7.0 開始，C# 語言支援*參考傳回值*。 理解引用傳回值的一種方法是，它們是通過引用傳遞給方法的參數的相反。 修改引用傳遞的參數時，更改將反映在調用方上的變數的值中。 當方法向調用方提供引用傳回值時，調用方對引用傳回值所做的修改將反映在被呼叫者法的資料中。

Visual Basic 不允許使用引用傳回值編寫方法，但它確實允許您使用引用傳回值。 換句話說，可以調用具有引用傳回值的方法並修改該傳回值，對引用傳回值的更改將反映在被調用的方法的資料中。

## <a name="modifying-the-ref-return-value-directly"></a>直接修改 ref 傳回值

對於始終成功且沒有`ByRef`參數的方法，可以直接修改引用傳回值。 為此，通過將新值分配給返回引用傳回值的運算式。

下面的 C# 示例定義了一`NumericValue.IncrementValue`個方法，該方法將內部值遞增並返回為引用傳回值。

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

然後，調用方在以下 Visual Basic 示例中修改引用傳回值。 請注意，使用 方法調用`NumericValue.IncrementValue`的行不會為 方法分配值。 相反，它將值分配給方法返回的引用傳回值。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>使用説明器方法

在其他情況下，直接修改方法調用的引用傳回值可能並不總是可取的。 例如，返回字串的搜索方法可能並不總是找到匹配項。 在這種情況下，僅當搜索成功時，才要修改引用傳回值。

以下 C# 示例說明了此方案。 它定義用`Sentence`C# 編寫的類包括一`FindNext`個方法，該方法在以指定的子字串開頭的句子中查找下一個單詞。 字串會以參考傳回值傳回，而參考所傳遞至方法的 `Boolean` 變數會指出搜尋是否成功。 引用傳回值指示除了讀取返回的值外，調用方還可以修改它，並且該修改反映在`Sentence`類內部包含的資料中。

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

在這種情況下，直接修改引用傳回值不可靠，因為方法調用可能無法找到匹配項並返回句子中的第一個單詞。 在這種情況下，調用方將無意中修改句子的第一個單詞。 調用方返回 （`null`或`Nothing`視覺基本值） 可以防止這種情況。 但是在這種情況下，嘗試修改其值為`Nothing`的字串將引發 。 <xref:System.NullReferenceException> 如果調用方也可以阻止 返回<xref:System.String.Empty?displayProperty=nameWithType>，但這需要調用方定義其值為<xref:System.String.Empty?displayProperty=nameWithType>的字串變數。 雖然調用方可以修改該字串，但修改本身沒有用處，因為修改後的字串與`Sentence`類存儲的句子中的單詞沒有關系。

處理此方案的最佳方法是通過引用説明器方法傳遞引用傳回值。 然後，説明器方法包含邏輯，以確定方法調用是否成功，如果成功，則修改引用傳回值。 下面的示例提供了一個可能的實現。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>另請參閱

- [按值和引用傳遞參數](passing-arguments-by-value-and-by-reference.md)
- [Visual Basic 中的程序](index.md)
