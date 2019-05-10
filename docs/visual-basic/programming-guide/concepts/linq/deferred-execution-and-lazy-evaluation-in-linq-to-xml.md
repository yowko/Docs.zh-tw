---
title: 延後的執行和延遲評估，在 LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: a8d3bec16fa8ca7f5c587a9fdbb6caac53b74efe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641993"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>延後的執行和延遲評估，在 LINQ to XML (Visual Basic)
若要使用延後執行，通常會實作查詢和座標軸運算。 本主題說明延後執行的條件與優點以及一些實作考量。  
  
## <a name="deferred-execution"></a>延後執行  
 延後執行是指延遲評估運算式，直到實際需要其「實現的」值為止。 當您必須管理大型資料集合，尤其是在包含一系列鏈結之查詢或管理的程式中時，延後執行會明顯改善效能。 在最好的情況下，延後執行僅能單一逐一查看來源集合。  
  
 LINQ 技術可讓延後執行大量用於 <xref:System.Linq?displayProperty=nameWithType> 核心類別的成員以及各種 LINQ 命名空間中的擴充方法，例如，<xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>。  
  
## <a name="eager-vs-lazy-evaluation"></a>急切評估與延遲評估之比較  
 當您撰寫實作延後執行的方法時，您也必須決定要使用延遲評估或急切評估來實作方法。  
  
- 若為「延遲評估」，來源集合的單一項目會在每次呼叫 Iterator 時進行處理。 這是實作 Iterator 的一般方式。  
  
- 若為「急切評估」，第一次呼叫 Iterator 時，就會處理整個集合。 同時，可能也需要來源集合的暫存副本。 例如，<xref:System.Linq.Enumerable.OrderBy%2A> 方法必須在傳回第一個項目前，排序整個集合。  
  
 延遲評估通常會產生較好的效能，因為它會平均分散整個集合評估的負荷處理，並將暫存資料的使用率降到最低。 當然，對於某些運算而言，沒有具體化中繼結果之外的其他選擇。  
  
## <a name="next-steps"></a>後續步驟  
 此教學課程中的下一個主題說明延後執行：  
  
- [延後的執行範例 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>另請參閱

- [教學課程：延後的執行 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
- [概念和術語 （函數式轉換） (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)
- [彙總作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
