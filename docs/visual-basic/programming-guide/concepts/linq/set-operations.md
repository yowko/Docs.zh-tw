---
title: 設定作業
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: b6ff14794343ae7623ee38894cef02cfc0a2a597
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406816"
---
# <a name="set-operations-visual-basic"></a>設定作業（Visual Basic）

LINQ 中的設定作業指的是產生結果集的查詢作業，而結果集是根據相同或不同集合 (集) 內是否有對等項目而定。

下節列出執行設定作業的標準查詢運算子方法。

## <a name="methods"></a>方法

|方法名稱|Description|Visual Basic 查詢運算式語法|相關資訊|
|-----------------|-----------------|------------------------------------------|----------------------|
|Distinct|移除集合中的重複值。|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|Except|傳回集差異，表示未出現在第二個集合中的某個集合中的項目。|不適用。|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|Intersect|傳回集交集，表示出現在這兩個集合中的項目。|不適用。|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|Union|傳回集聯集，表示出現在兩個集合中任一集合的唯一項目。|不適用。|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a>比較設定作業

### <a name="distinct"></a>Distinct

下圖說明一連串字元的 <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> 方法行為。 所傳回的序列包含輸入序列中的唯一項目。

![顯示 Distinct&#40;&#41; 之行為的圖形。](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a>Except

下圖說明 <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> 的行為。 所傳回的序列只包含第一個輸入序列中不在第二個輸入序列中的項目。

![圖形：顯示&#40;&#41; 以外的動作。](./media/set-operations/except-behavior-graphic.png "顯示 Except 的行為。")

### <a name="intersect"></a>Intersect

下圖說明 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> 的行為。 所傳回的序列包含兩個輸入序列共有的項目。

![顯示兩種序列交集的圖形。](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a>Union

下圖說明兩個字元序列的聯合作業。 所傳回的序列包含兩個輸入序列中的唯一項目。

![顯示兩個序列聯集的圖形。](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a>查詢運算式語法範例

下列範例會 `Distinct` 在 LINQ 查詢中使用子句，從整數清單中傳回唯一的數位。

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a>另請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)
- [Distinct 子句](../../../language-reference/queries/distinct-clause.md)
- [如何：合併和比較字串集合（LINQ）（Visual Basic）](how-to-combine-and-compare-string-collections-linq.md)
- [如何：尋找兩個清單之間的集合差異（LINQ）（Visual Basic）](how-to-find-the-set-difference-between-two-lists-linq.md)
