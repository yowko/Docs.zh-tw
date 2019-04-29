---
title: 重大追蹤
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: c230c65b4d3fd45c4905d4ae5f4cbbf90e10faad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784942"
---
# <a name="significant-traces"></a>重大追蹤
本主題列出一些主要由 Windows Communication Foundation (WCF)，就發出的追蹤。  
  
## <a name="significant-traces"></a>重大追蹤  
  
|追蹤|描述|  
|-----------|-----------------|  
|訊息記錄追蹤。|WCF 訊息記錄的訊息記錄時，就會發出追蹤時，功能`System.ServiceModel.MessageLogging`已啟用追蹤來源。 按一下此追蹤以顯示訊息。 用於訊息的可配置記錄點有四個：`ServiceLevelSendRequest`、`TransportSend`、`TransportReceive`、`ServiceLevelReceiveRequest`，並由訊息記錄中的訊息來源指示。|  
|已接收訊息追蹤|如果接收 WCF 訊息時，就會發出此追蹤`System.ServiceModel`資訊或詳細資訊層級啟用追蹤來源。 必須有這個追蹤，才能在活動圖形檢視中看到訊息相互關聯箭頭。|  
|已傳送訊息追蹤|如果傳送 WCF 訊息時，就會發出此追蹤`System.ServiceModel`資訊或詳細資訊層級啟用追蹤來源。 必須有這個追蹤，才能在活動圖形檢視中看到訊息相互關聯箭頭。|  
|取得 ChannelEndpointElement|此追蹤在資訊層的建構通道處理站中發出。 它提供用戶端正在交涉的端點描述 (遠端位址、繫結、合約名稱)。|  
|取得 ServiceElement|此追蹤在資訊層的建構服務主機中發出。 它提供服務合約與繫結的描述。|  
|SocketConnection 建立|此追蹤會在用戶端執行第一次處理動作時發出，並在服務的接收位元組活動中發出。 它會提供本機與遠端 IP 位址， 也會在資訊層發出。|
