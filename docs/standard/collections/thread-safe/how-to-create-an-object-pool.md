---
title: 使用 ConcurrentBag 建立物件集區
ms.date: 05/01/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
ms.openlocfilehash: 2c060dc901f8d06a5f9c51db1cd563cb28e4fda3
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728464"
---
# <a name="create-an-object-pool-by-using-a-concurrentbag"></a>使用 ConcurrentBag 建立物件集區

這個範例示範如何使用<xref:System.Collections.Concurrent.ConcurrentBag%601>來執行物件集區。 在需要多個類別執行個體的情況下，物件集區可以改善應用程式效能，而且類別的建立或終結成本相當高。 用戶端程式要求新的物件時，物件集區會先嘗試提供已建立並傳回給集區的物件。 如果沒有，則只會建立新的物件。

<xref:System.Collections.Concurrent.ConcurrentBag%601>是用來儲存物件，因為它支援快速插入和移除，特別是當相同執行緒同時新增和移除專案時。 此範例無法進一步擴大來建置 bag 資料結構所實作的 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>，這與 <xref:System.Collections.Concurrent.ConcurrentQueue%601> 和 <xref:System.Collections.Concurrent.ConcurrentStack%601> 相同。

> [!TIP]
> 本文定義如何使用基礎並行類型來撰寫您自己的物件集區，以儲存要重複使用的物件。 不過，此<xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType>類型已經存在於<xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName>命名空間之下。 在建立您自己的執行之前，請考慮使用可用的類型，其中包含許多額外的功能。

## <a name="example"></a>範例

[!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
[!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]

## <a name="see-also"></a>另請參閱

- [安全線程集合](../../../../docs/standard/collections/thread-safe/index.md)
