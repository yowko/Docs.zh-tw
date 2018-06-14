---
title: 使用 AsyncCallback 委派和狀態物件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 259f7de52dff04af043554382a5bad35355d9926
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567233"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>使用 AsyncCallback 委派和狀態物件
當您使用 <xref:System.AsyncCallback> 委派以處理不同執行緒中非同步作業的結果，可以使用狀態物件傳遞回呼之間的資訊以擷取最終結果。 本主題透過展開[使用 AsyncCallback 委派結束非同步作業](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)中的範例來示範該做法。  
  
## <a name="example"></a>範例  
 下列範例示範在 <xref:System.Net.Dns> 類別中使用非同步方法，以擷取使用者指定電腦的網域名稱系統 (DNS) 資訊。 此範例定義和使用 `HostRequest` 類別來儲存狀態資訊。 為使用者所輸入的每個電腦名稱建立 `HostRequest` 物件。 此物件會傳遞給 <xref:System.Net.Dns.BeginGetHostByName%2A> 方法。 每次要求完成時都會呼叫 `ProcessDnsInformation` 方法。 使用 <xref:System.IAsyncResult.AsyncState%2A> 屬性擷取 `HostRequest` 物件。 `ProcessDnsInformation` 方法會使用 `HostRequest` 物件儲存要求傳回的 <xref:System.Net.IPHostEntry> 或要求所擲回的 <xref:System.Net.Sockets.SocketException>。 當所有要求都完成時，應用程式會逐一查看 `HostRequest` 物件並顯示 DNS 資訊或 <xref:System.Net.Sockets.SocketException> 錯誤訊息。  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>請參閱  
 [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [使用 AsyncCallback 委派結束非同步作業](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
