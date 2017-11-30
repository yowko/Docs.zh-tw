---
title: "以合作方式取消執行緒"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 482f48b347af1a4f76231abcb15abc2f4dba168b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="canceling-threads-cooperatively"></a>以合作方式取消執行緒
在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]之前，.NET Framework 不會提供內建，以便在執行緒啟動後以合作方式加以取消。 不過，在[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，您可以使用取消語彙基元來取消執行緒，就如同您可以使用它們來取消<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>物件或 PLINQ 查詢。 雖然<xref:System.Threading.Thread?displayProperty=nameWithType>類別不提供取消語彙基元的內建支援，您可以將權杖傳遞至執行緒程序使用<xref:System.Threading.Thread>建構函式<xref:System.Threading.ParameterizedThreadStart>委派。 下列範例示範如何進行這項操作。  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>另請參閱  
 [使用執行緒和執行緒處理](../../../docs/standard/threading/using-threads-and-threading.md)
