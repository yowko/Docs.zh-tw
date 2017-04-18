---
title: "延後執行與延遲評估在 LINQ to XML (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3b7318eb9853d633d152b93fafcf9570ccd03835
ms.lasthandoff: 03/13/2017


---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>延後的執行與延遲評估在 LINQ to XML (Visual Basic)
若要使用延後執行，通常會實作查詢和座標軸運算。 本主題說明延後執行的條件與優點以及一些實作考量。  
  
## <a name="deferred-execution"></a>延後執行  
 延後執行指延遲評估的運算式，直到其*實現*實際需要的值為止。 當您必須管理大型資料集合，尤其是在包含一系列鏈結之查詢或管理的程式中時，延後執行會明顯改善效能。 在最好的情況下，延後執行僅能單一逐一查看來源集合。  
  
 LINQ 技術可讓延後執行大量用於這兩個成員中的核心<xref:System.Linq?displayProperty=fullName>類別和擴充方法，在各種 LINQ 命名空間，例如<xref:System.Xml.Linq.Extensions?displayProperty=fullName>.</xref:System.Xml.Linq.Extensions?displayProperty=fullName> </xref:System.Linq?displayProperty=fullName>  
  
## <a name="eager-vs-lazy-evaluation"></a>急切評估與延遲評估之比較  
 當您撰寫實作延後執行的方法時，您也必須決定要使用延遲評估或急切評估來實作方法。  
  
-   在*延遲評估*，來源集合的單一項目會在每次呼叫 iterator 進行處理。 這是實作 Iterator 的一般方式。  
  
-   在*急切評估*，迭代器的第一個呼叫會導致處理整個集合。 同時，可能也需要來源集合的暫存副本。 例如，<xref:System.Linq.Enumerable.OrderBy%2A>方法必須在傳回第一個項目，排序整個集合。</xref:System.Linq.Enumerable.OrderBy%2A>  
  
 延遲評估通常會產生較好的效能，因為它會平均分散整個集合評估的負荷處理，並將暫存資料的使用率降到最低。 當然，對於某些運算而言，沒有具體化中繼結果之外的其他選擇。  
  
## <a name="next-steps"></a>後續步驟  
 此教學課程中的下一個主題說明延後執行：  
  
-   [延後的執行範例 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>另請參閱  
 [教學課程︰ 延後執行 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)   
 [概念和術語 （功能轉換） (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)   
 [彙總作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
