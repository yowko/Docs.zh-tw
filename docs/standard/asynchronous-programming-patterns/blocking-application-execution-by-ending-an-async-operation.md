---
title: "以結束非同步作業的方式封鎖應用程式執行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
dev_langs:
- csharp
- vb
ms.openlocfilehash: ccca6e1e4f6b5cdf098018b59426fb2262e2b346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>以結束非同步作業的方式封鎖應用程式執行
無法繼續執行其他工作在等候非同步作業的結果時的應用程式必須封鎖直到作業完成為止。 您可以使用下列選項的其中一個來等候非同步作業完成時，封鎖您的應用程式主執行緒：  
  
-   呼叫非同步作業**結束** *OperationName*方法。 本主題會示範這個方法。  
  
-   使用<xref:System.IAsyncResult.AsyncWaitHandle%2A>屬性<xref:System.IAsyncResult>非同步作業所傳回**開始** *OperationName*方法。 如需示範這種方法的範例，請參閱[使用 AsyncWaitHandle 封鎖應用程式執行](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)。  
  
 使用應用程式**結束** *OperationName*通常呼叫方法來封鎖，直到非同步作業完成為止，將**開始** *OperationName*方法，執行任何工作，可以作業的結果的情況下完成，然後呼叫**結束** *OperationName*。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用中的非同步方法<xref:System.Net.Dns>類別來擷取指定使用者電腦的網域名稱系統資訊。 請注意， `null` (`Nothing`在 Visual Basic 中) 的傳遞<xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback`和`stateObject`參數因為使用這個方式時，不需要這些引數。  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
