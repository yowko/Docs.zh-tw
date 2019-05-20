---
title: 作法：在資料流程區塊中指定平行處理原則程度
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4395f6f8b59cca7b092a9d4d5d44c079244a29ef
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592015"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>作法：在資料流程區塊中指定平行處理原則程度
本文件描述如何設定 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> 屬性，讓執行資料流程區塊一次處理多個訊息。 如果您有執行長期執行計算的資料流程區塊，而且可受惠於平行處理訊息，這樣做就會很有用。 這個範例會使用 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> 類別同時執行多個資料流程作業，不過，您可以在 TPL 資料流程程式庫提供的任一個預先定義執行區塊類型 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> 中，指定平行處理原則的最大刻度。

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>範例  
 下列範例將會執行兩種資料流程計算，並且列印每個計算所需的經過時間。 第一個計算會將平行處理原則的最大刻度指定為 1，這是預設值。 平行處理原則的最大刻度為 1，會使資料流程區塊循序處理訊息。 第二個計算類似第一個，不過它會將平行處理原則的最大刻度指定為可用處理器的數目。 這樣就可讓資料流程區塊平行執行多個作業。  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 根據預設，每個預先定義的資料流程區塊都會依收到訊息的順序將訊息傳播出去。  當您指定大於 1 的平行處理原則的最大刻度時，儘管會同時處理多個訊息，這些訊息仍會依照收到的順序傳播出去。  
  
 因為 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> 屬性表示平行處理原則的最大刻度，所以資料流程區塊可能會以比您所指定刻度更小的平行處理原則來執行。 資料流程區塊可以使用較小刻度的平行處理原則因應功能上的需求，或是將缺少可用系統資源的情形納入考量。 資料流程區塊選擇的平行處理原則刻度絕不會大於您所指定的數字。  
  
## <a name="see-also"></a>另請參閱

- [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
