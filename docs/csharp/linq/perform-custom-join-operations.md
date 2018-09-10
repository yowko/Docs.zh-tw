---
title: 執行自訂的聯結作業 (C# 中的 LINQ)
description: 了解如何在 C# 中執行自訂的 LINQ 聯結作業。
ms.date: 12/1/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: a0e08396c006f68949357c50a28b3b0982f0dd83
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44217421"
---
# <a name="perform-custom-join-operations"></a>執行自訂的聯結作業

此範例示範如何執行無法使用 `join` 子句的聯結作業。 在查詢運算式中，`join` 子句限於等聯結並已最佳化，是目前為止最常見的聯結運算類型。 執行等聯結時，使用 `join` 子句可能一律會獲得最佳效能。

不過，`join` 子句不能用在下列情況︰

- 不等式運算式中預測有聯結時 (非等聯結)。

- 多個等式或不等式運算式中預測有聯結時。

- 當您必須在聯結作業之前，引入右側 (內部) 序列的暫時範圍變數時。

 若要執行非等聯結的聯結，您可以使用多個 `from` 子句個別引入每個資料來源。 然後，在 `where` 子句中套用述詞運算式，設定每個來源的變數範圍。 運算式也可以採用方法呼叫的形式。

> [!NOTE]
> 請勿將這類的自訂聯結運算與使用多個 `from` 子句來存取內部集合相混淆。 如需詳細資訊，請參閱 [join 子句](../language-reference/keywords/join-clause.md)。

## <a name="example"></a>範例

下例的第一種方法示範簡單的交叉聯結。 交叉聯結必須謹慎使用，因為它們會產生非常龐大的結果集。 不過，它們在某些針對執行額外查詢建立來源序列的情況下很有用。

第二個方法會產生一系列類別識別碼列在左側 [類別] 清單中的所有產品。 請注意使用 `let` 子句和 `Contains` 方法來建立暫存陣列。 您也可以在查詢前建立陣列，並排除第一個 `from` 子句。

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a>範例

在下例中，如果內部 (右側) 序列不能出現在 join 子句之前，查詢必須根據相符的索引鍵聯結兩個序列。 如果此聯結是使用 `join` 子句執行，則每個項目都必須呼叫 `Split` 方法。 使用多個 `from` 子句可讓查詢避免重複方法呼叫的額外負荷。 不過，由於 `join` 已最佳化，在此特例中可能仍比使用多個 `from` 子句快。 結果主要隨方法呼叫的昂貴程度而不同。

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a>另請參閱

- [Language-Integrated Query (LINQ)](index.md)  
- [join 子句](../language-reference/keywords/join-clause.md)  
- [排序 Join 子句的結果](order-the-results-of-a-join-clause.md)  