---
title: "輪詢非同步作業的狀態"
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
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1f7f74a8b38c06f6a042d55c0def76ddfc5da77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>輪詢非同步作業的狀態
應用程式可以執行其他工作在等候非同步作業的結果時，不應該封鎖，等待，直到作業完成。 使用下列選項的其中一個來繼續等候非同步作業完成時執行的指示：  
  
-   使用<xref:System.IAsyncResult.IsCompleted%2A>屬性<xref:System.IAsyncResult>非同步作業所傳回**開始** *OperationName*方法來判斷作業是否完成。 這種方法稱為輪詢，本主題所示。  
  
-   使用<xref:System.AsyncCallback>委派以處理不同的執行緒中的非同步作業的結果。 如需示範這種方法的範例，請參閱[使用 AsyncCallback 委派結束非同步作業](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用中的非同步方法<xref:System.Net.Dns>類別來擷取指定使用者電腦的網域名稱系統資訊。 這個範例會啟動非同步作業，然後再列印 句點 ("。") 在主控台中，直到作業完成為止。 請注意， **null** (**Nothing**在 Visual Basic 中) 的傳遞<xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback>和<xref:System.Object>參數因為使用這個方式時，不需要這些引數。  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>另請參閱  
 [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
