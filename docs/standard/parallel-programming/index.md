---
title: "以 .NET Framework 進行平行程式設計"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a3509229efc57b1f6b1244671df65b2f21964e65
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---
# <a name="parallel-programming-in-the-net-framework"></a>以 .NET Framework 進行平行程式設計
許多個人電腦和工作站都具有兩個或四個核心 (即 CPU)，而能夠同時執行多個執行緒。 不久的將來，電腦應該會具有更多的核心。 若要利用現今和未來的硬體優勢，您可以將您的程式碼平行化，以便將工作分散到多個處理器。 在過去，平行化作業需要在低階操作執行緒和鎖定。 [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] 和 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 提供新的執行階段、新的類別庫類型和新的診斷工具，以加強支援平行程式設計。 這些功能簡化了平行開發作業，讓您能夠利用簡單常見的語法，撰寫效率高、精細且具彈性的平行程式碼，而不需要直接使用執行緒或執行緒集區。 下圖提供 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 中平行程式設計架構的高階概觀。  
  
 ![.NET 平行程式設計架構](../../../docs/standard/parallel-programming/media/tpl-architecture.png "TPL_Architecture")  
  
## <a name="related-topics"></a>相關主題  
  
|技術|描述|  
|----------------|-----------------|  
|[工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|提供 <xref:System.Threading.Tasks.Parallel?displayProperty=fullName> 類別 (包含平行版本的 `For` 和 `ForEach` 迴圈) 及 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 類別 (表示表達非同步作業較好的方式) 的文件。|  
|[平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|平行實作的 LINQ to Objects，在許多情節中可大幅改善效能。|  
|[適用於平行程式設計的資料結構](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|提供安全執行緒集合類別、輕量型同步處理類型和延遲初始設定類型的文件連結。|  
|[平行診斷工具](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|提供 Visual Studio 偵錯工具視窗 (適用於工作和平行堆疊) 和[並行視覺化檢視](/visualstudio/profiling/concurrency-visualizer) (由 [!INCLUDE[vsprvsts](../../../includes/vsprvsts-md.md)] 分析工具中一組可供您進行偵錯和微調平行程式碼效能的檢視所組成) 的文件連結。|  
|[PLINQ 和 TPL 的自訂 Partitioner](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|說明 Partitioner 的運作方式，以及如何設定預設 Partitioner 或建立新的 Partitioner。|  
|[工作排程器](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65)|說明排程器的運作方式以及如何設定預設排程器。|  
|[PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|提供 C# 和 Visual Basic 中之 Lambda 運算式的簡短概觀，並且顯示如何在 PLINQ 和工作平行程式庫中使用這些運算式。|  
|[進一步閱讀](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|提供以 .NET Framework 進行平行程式設計的其他文件和範例資源連結。|  
  
## <a name="see-also"></a>另請參閱  
 [平行程式設計模式：了解及套用使用 .NET Framework 4 的平行模式 (英文)](http://go.microsoft.com/fwlink/?LinkID=185142)   
 [使用 .NET Framework 進行平行程式設計的範例](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)

