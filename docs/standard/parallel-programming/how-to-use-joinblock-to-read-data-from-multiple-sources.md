---
title: 作法：使用 JoinBlock 從多個來源讀取資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, joining blocks in
- dataflow blocks, joining in TPL
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7becba9c7626e79f9d001a6a21ed92a336e9d11
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591988"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>作法：使用 JoinBlock 從多個來源讀取資料
本文件將說明，如何在有多個來源的資料可用時，使用 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 類別執行作業。 另外也會示範如何使用非窮盡模式，讓多個聯結區塊更有效率地共用資料來源。

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>範例  
 下列範例會定義三個資源類型 `NetworkResource`、`FileResource` 和 `MemoryResource`，並且在有可用資源時執行作業。 這個範例需要 `NetworkResource` 和 `MemoryResource` 配對，以便執行第一個作業，而且需要 `FileResource` 和 `MemoryResource` 配對，以便執行第二個作業。 為了要讓這些作業在所有必要的資源可供使用時發生，這個範例會使用 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 類別。 當 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 物件接收來自所有來源的資料時，它會將該資料傳播至其目標，也就是這個範例中的 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件。 這兩個 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 物件都會從 `MemoryResource` 物件的共用集區讀取。  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 為了要讓 `MemoryResource` 物件共用集區的使用更有效率，這個範例會指定 <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> 物件並將其 <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> 屬性設定為 `False`，建立以非窮盡模式執行的 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 物件。 非窮盡聯結區塊會延後所有傳入訊息，直到每個來源都有一個為止。 如果有任一個延後的訊息被另一個區塊所接受，聯結區塊就會重新啟動處理序。 非窮盡模式會在其他區塊等待資料的同時，讓共用一個或多個來源區塊的聯結區塊往前進行。 在這個範例中，如果 `MemoryResource` 物件已加入至 `memoryResources` 集區，則要接收其第二個資料來源的第一個聯結區塊就能繼續往前進行。 如果這個範例是使用窮盡模式，也就是預設值，則聯結區塊可能會採用 `MemoryResource` 物件並等待可供使用的第二個資源。 不過，如果其他聯結區塊都有自己的第二個資料來源可用，就無法繼續往前進行，因為 `MemoryResource` 物件已由另一個聯結區塊佔用。  
  
## <a name="robust-programming"></a>穩固程式設計  
 使用非窮盡聯結還可以協助您防止應用程式中發生死結。 在軟體應用程式中，當兩個或多個處理序都保留資源，且互相等候另一個處理序釋放某些其他資源時，就會發生「死結」。 假設有一個應用程式定義了兩個 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 物件。 這兩個物件都會從兩個共用來源區塊讀取資料。 在窮盡模式下，如果其中一個聯結區塊是從第一個來源讀取，而第二個聯結區塊是從第二個來源讀取，則應用程式可能會發生死結，因為這兩個聯結區塊會互相等候彼此釋放其資源。 在非窮盡模式下，每個聯結區塊只會在所有資料都可用時才從其來源讀取，因此可排除死結的情況發生。  
  
## <a name="see-also"></a>另請參閱

- [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
