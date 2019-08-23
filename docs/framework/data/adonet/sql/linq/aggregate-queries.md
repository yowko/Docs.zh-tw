---
title: 彙總查詢
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: b7b38306903313825056c02fc3c3fb8c98e07e17
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964114"
---
# <a name="aggregate-queries"></a>彙總查詢
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援 `Average`、`Count`、`Max`、`Min` 和 `Sum` 彙總運算子。 請注意，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的彙總運算子有下列特性：  
  
- 彙總查詢會立即執行。  
  
     如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。  
  
- 彙總查詢通常會傳回數字，而不是集合。  
  
     如需詳細資訊, 請參閱[匯總作業](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120))。  
  
- 您不可以對匿名型別呼叫彙總。  
  
 下列主題中的範例衍生自 Northwind 範例資料庫。 如需詳細資訊, 請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [傳回數值序列的平均值](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 示範如何使用 <xref:System.Linq.Enumerable.Average%2A> 運算子。  
  
 [計算序列中的項目數目](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 示範如何使用 <xref:System.Linq.Enumerable.Count%2A> 運算子。  
  
 [尋找數值序列中的最大值](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 示範如何使用 <xref:System.Linq.Enumerable.Max%2A> 運算子。  
  
 [尋找數值序列中的最小值](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 示範如何使用 <xref:System.Linq.Enumerable.Min%2A> 運算子。  
  
 [計算數值序列中各值的總和](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 示範如何使用 <xref:System.Linq.Enumerable.Sum%2A> 運算子。  
  
## <a name="related-sections"></a>相關章節  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 提供 Visual Basic 和 C# 中之 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢的連結。  
  
 [查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 提供在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中設計 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢之概念說明主題的連結。  
  
 [LINQ 查詢簡介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 說明查詢在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中的運作方式。
