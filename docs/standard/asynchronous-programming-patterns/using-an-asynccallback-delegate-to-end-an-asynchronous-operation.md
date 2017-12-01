---
title: "使用 AsyncCallback 委派結束非同步作業"
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
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbe170588776daa97fec4c736d4b1bdd871de518
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>使用 AsyncCallback 委派結束非同步作業
應用程式可以執行其他工作在等候非同步作業的結果時，不應該封鎖，等待，直到作業完成。 使用下列選項的其中一個來繼續等候非同步作業完成時執行的指示：  
  
-   使用<xref:System.AsyncCallback>委派以處理不同的執行緒中的非同步作業的結果。 本主題會示範這個方法。  
  
-   使用<xref:System.IAsyncResult.IsCompleted%2A>屬性<xref:System.IAsyncResult>非同步作業所傳回**開始** *OperationName*方法來判斷作業是否完成。 如需示範這種方法的範例，請參閱[輪詢非同步作業的狀態](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用中的非同步方法<xref:System.Net.Dns>類別來擷取指定使用者電腦的網域名稱系統 (DNS) 資訊。 這個範例會建立<xref:System.AsyncCallback>委派，參考`ProcessDnsInformation`方法。 這個方法是針對每個非同步要求的 DNS 資訊一次呼叫。  
  
 請注意，在使用者指定的主機會傳遞至<xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object>參數。 如需示範如何定義及使用更複雜的狀態物件的範例，請參閱[使用 AsyncCallback 委派和狀態物件](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)。  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>另請參閱  
 [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [使用 IAsyncResult 呼叫非同步方法](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [使用 AsyncCallback 委派和狀態物件](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
