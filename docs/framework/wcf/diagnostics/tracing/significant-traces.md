---
title: 重大追蹤
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: 2dc5010874285ba14dae625fcbf92740eb1707b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="significant-traces"></a>重大追蹤
本主題列出了一些主要 Windows Communication Foundation (WCF)，就發出的追蹤。  
  
## <a name="significant-traces"></a>重大追蹤  
  
|追蹤|描述|  
|-----------|-----------------|  
|訊息記錄追蹤。|當 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 資訊由啟用 `System.ServiceModel.MessageLogging` 追蹤來源時的訊息記錄功能記錄時，發出此追蹤。 按一下此追蹤以顯示訊息。 用於訊息的可配置記錄點有四個：`ServiceLevelSendRequest`、`TransportSend`、`TransportReceive`、`ServiceLevelReceiveRequest`，並由訊息記錄中的訊息來源指示。|  
|已接收訊息追蹤|如果已在資訊層級或詳細資訊層級啟用 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 追蹤來源而收到 `System.ServiceModel` 訊息時，便會發出此追蹤。 必須有這個追蹤，才能在活動圖形檢視中看到訊息相互關聯箭頭。|  
|已傳送訊息追蹤|如果在資訊層級或詳細資訊層級啟用 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 追蹤來源，則當傳送 `System.ServiceModel` 訊息時，會發出此追蹤。 必須有這個追蹤，才能在活動圖形檢視中看到訊息相互關聯箭頭。|  
|取得 ChannelEndpointElement|此追蹤在資訊層的建構通道處理站中發出。 它提供用戶端正在交涉的端點描述 (遠端位址、繫結、合約名稱)。|  
|取得 ServiceElement|此追蹤在資訊層的建構服務主機中發出。 它提供服務合約與繫結的描述。|  
|SocketConnection 建立|此追蹤會在用戶端執行第一次處理動作時發出，並在服務的接收位元組活動中發出。 它會提供本機與遠端 IP 位址， 也會在資訊層發出。|
