---
title: "使用 AsyncWaitHandle 封鎖應用程式執行"
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
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2660b3cbf7e8ee43a22edbfb66a4262684983b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>使用 AsyncWaitHandle 封鎖應用程式執行
無法繼續執行其他工作在等候非同步作業的結果時的應用程式必須封鎖直到作業完成為止。 您可以使用下列選項的其中一個來等候非同步作業完成時，封鎖您的應用程式主執行緒：  
  
-   使用<xref:System.IAsyncResult.AsyncWaitHandle%2A>屬性<xref:System.IAsyncResult>非同步作業所傳回**開始** *OperationName*方法。 本主題會示範這個方法。  
  
-   呼叫非同步作業的**結束** *OperationName*方法。 如需示範這種方法的範例，請參閱[封鎖應用程式執行，藉由結束非同步作業](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)。  
  
 使用一或多個應用程式<xref:System.Threading.WaitHandle>來封鎖，直到非同步作業已完成的物件通常會呼叫**開始** *OperationName*方法，執行任何可以完成的工作作業，然後再封鎖，直到非同步作業的結果不會完成。 應用程式可以在單一作業上封鎖透過呼叫其中一個<xref:System.Threading.WaitHandle.WaitOne%2A>方法使用<xref:System.IAsyncResult.AsyncWaitHandle%2A>。 若要封鎖等候一組非同步作業完成時，儲存相關聯<xref:System.IAsyncResult.AsyncWaitHandle%2A>中物件的陣列，呼叫其中一個<xref:System.Threading.WaitHandle.WaitAll%2A>方法。 若要封鎖等候任何一個的一組非同步作業完成時，儲存相關聯<xref:System.IAsyncResult.AsyncWaitHandle%2A>中物件的陣列，呼叫其中一個<xref:System.Threading.WaitHandle.WaitAny%2A>方法。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用 DNS 類別中的非同步方法，擷取指定使用者電腦的網域名稱系統資訊。 此範例示範封鎖使用<xref:System.Threading.WaitHandle>與非同步作業相關聯。 請注意， `null` (`Nothing`在 Visual Basic 中) 的傳遞<xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback`和`stateObject`參數因為這些並不需要使用這個方式時。  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
