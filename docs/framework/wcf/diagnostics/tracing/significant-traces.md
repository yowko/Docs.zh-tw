---
title: 重大追蹤
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: 9ad7c217b528cb2ad22169c1aea6391462bab1ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248666"
---
# <a name="significant-traces"></a>重大追蹤

本主題列出 Windows Communication Foundation (WCF) 所發出的一些主要追蹤。  
  
## <a name="significant-traces"></a>重大追蹤  
  
|追蹤|描述|  
|-----------|-----------------|  
|訊息記錄追蹤。|當追蹤來源已啟用時，當訊息記錄功能記錄 WCF 訊息時，就會發出此追蹤 `System.ServiceModel.MessageLogging` 。 按一下此追蹤以顯示訊息。 用於訊息的可配置記錄點有四個：`ServiceLevelSendRequest`、`TransportSend`、`TransportReceive`、`ServiceLevelReceiveRequest`，並由訊息記錄中的訊息來源指示。|  
|已接收訊息追蹤|如果在 `System.ServiceModel` 資訊或詳細資訊層級啟用追蹤來源，則會在收到 WCF 訊息時發出此追蹤。 必須有這個追蹤，才能在活動圖形檢視中看到訊息相互關聯箭頭。|  
|已傳送訊息追蹤|如果在 `System.ServiceModel` 資訊或詳細資訊層級啟用追蹤來源，則會在傳送 WCF 訊息時發出此追蹤。 必須有這個追蹤，才能在活動圖形檢視中看到訊息相互關聯箭頭。|  
|取得 ChannelEndpointElement|此追蹤在資訊層的建構通道處理站中發出。 它提供用戶端正在交涉的端點描述 (遠端位址、繫結、合約名稱)。|  
|取得 ServiceElement|此追蹤在資訊層的建構服務主機中發出。 它提供服務合約與繫結的描述。|  
|SocketConnection 建立|此追蹤會在用戶端執行第一次處理動作時發出，並在服務的接收位元組活動中發出。 它會提供本機與遠端 IP 位址， 也會在資訊層發出。|
