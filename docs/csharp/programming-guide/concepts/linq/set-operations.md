---
title: 設定作業 (C#)
description: '瞭解在 c # 中以 LINQ 執行設定作業的設定作業和標準查詢運算子方法。'
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: ab2608b267113ad5d47a33e64cd9a5e21496f668
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302369"
---
# <a name="set-operations-c"></a>設定作業 (C#)
LINQ 中的設定作業指的是產生結果集的查詢作業，而結果集是根據相同或不同集合 (集) 內是否有對等項目而定。  
  
 下節列出執行設定作業的標準查詢運算子方法。  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|C# 查詢運算式語法|相關資訊|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|移除集合中的重複值。|不適用。|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Except|傳回集差異，表示未出現在第二個集合中的某個集合中的項目。|不適用。|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Intersect|傳回集交集，表示出現在這兩個集合中的項目。|不適用。|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Union|傳回集聯集，表示出現在兩個集合中任一集合的唯一項目。|不適用。|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>比較設定作業  
  
### <a name="distinct"></a>Distinct  
 下列範例描述 <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> 方法在字元序列上的行為。 所傳回的序列包含輸入序列中的唯一項目。  
  
 ![顯示 Distinct&#40;&#41; 之行為的圖形。](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a>Except  
 下列範例描述的行為 <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> 。 所傳回的序列只包含第一個輸入序列中不在第二個輸入序列中的項目。  
  
 ![圖形：顯示&#40;&#41; 以外的動作。](./media/set-operations/except-behavior-graphic.png "顯示 Except 的行為。")  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a>Intersect  
 下列範例描述的行為 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> 。 所傳回的序列包含兩個輸入序列共有的項目。  
  
 ![顯示兩種序列交集的圖形。](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a>Union  
 下列範例描述兩個字元序列的 union 運算。 所傳回的序列包含兩個輸入序列中的唯一項目。  
  
 ![顯示兩個序列聯集的圖形。](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a>另請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (C#)](./standard-query-operators-overview.md)
- [如何合併和比較字串集合（LINQ）（c #）](./how-to-combine-and-compare-string-collections-linq.md)
- [如何尋找兩個清單之間的集合差異（LINQ）（c #）](./how-to-find-the-set-difference-between-two-lists-linq.md)
