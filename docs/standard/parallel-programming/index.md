---
title: .NET 的平行程式設計
description: 瞭解 .NET 中的平行程式設計。 使用 .NET 執行時間、類別庫類型和診斷工具來簡化 .NET 開發。
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
ms.openlocfilehash: 02087cf58720388c64d8aba5424db0b54828219a
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661961"
---
# <a name="parallel-programming-in-net"></a>.NET 的平行程式設計

許多個人電腦和工作站都具有多個 CPU 核心，以便能夠同時執行多個執行緒。 若要利用硬體優勢，您可以將您的程式碼平行化，以便將工作分散到多個處理器。

在過去，平行化作業需要在低階操作執行緒和鎖定。 Visual Studio 與 .NET Framework 提供了執行階段、類別庫類型和診斷工具，以加強支援平行程式設計。 從 .NET Framework 4 引進的這些功能簡化了平行開發。 您能夠利用簡單常見的語法，撰寫效率高、精細且具彈性的平行程式碼，而不需要直接使用執行緒或執行緒集區。

下圖提供 .NET Framework 中平行程式設計架構的高階概觀：

![.NET 平行程式設計架構](./media/tpl-architecture.png)

## <a name="related-topics"></a>[相關主題]

|技術|描述|
|----------------|-----------------|
|[工作平行程式庫 (TPL)](task-parallel-library-tpl.md)|提供 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 類別 (包含平行版本的 `For` 和 `ForEach` 迴圈) 及 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類別 (表示表達非同步作業較好的方式) 的文件。|
|[平行 LINQ (PLINQ)](introduction-to-plinq.md)|平行實作的 LINQ to Objects，在許多情節中可大幅改善效能。|
|[平行程式設計的資料結構](data-structures-for-parallel-programming.md)|提供安全執行緒集合類別、輕量型同步處理類型和延遲初始設定類型的文件連結。|
|[平行診斷工具](parallel-diagnostic-tools.md)|提供工作與平行堆疊的 Visual Studio 偵錯工具視窗文件連結，以及[並行視覺化工具](/visualstudio/profiling/concurrency-visualizer)的連結。|
|[PLINQ 和 TPL 的自訂 Partitioner](custom-partitioners-for-plinq-and-tpl.md)|說明 Partitioner 的運作方式，以及如何設定預設 Partitioner 或建立新的 Partitioner。|
|[工作排程器](xref:System.Threading.Tasks.TaskScheduler)|說明排程器的運作方式以及如何設定預設排程器。|
|[PLINQ 和 TPL 中的 Lambda 運算式](lambda-expressions-in-plinq-and-tpl.md)|提供 C# 和 Visual Basic 中之 Lambda 運算式的簡短概觀，並且顯示如何在 PLINQ 和工作平行程式庫中使用這些運算式。|
|[進一步閱讀](for-further-reading-parallel-programming.md)|提供以 .NET 進行平行程式設計的額外資訊和範例資源連結。|

## <a name="see-also"></a>另請參閱

- [非同步總覽](../async.md)
- [Managed 執行緒](../threading/index.md)
