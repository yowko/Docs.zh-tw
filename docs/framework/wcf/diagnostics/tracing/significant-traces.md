---
title: "重大追蹤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 95b4794848927b9319ddb07d75461f5d5e71e1f5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="significant-traces"></a><span data-ttu-id="f97a2-102">重大追蹤</span><span class="sxs-lookup"><span data-stu-id="f97a2-102">Significant Traces</span></span>
<span data-ttu-id="f97a2-103">此主題會列出 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 發出的其中一些主要追蹤。</span><span class="sxs-lookup"><span data-stu-id="f97a2-103">This topic lists some of the major traces emitted by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span></span>  
  
## <a name="significant-traces"></a><span data-ttu-id="f97a2-104">重大追蹤</span><span class="sxs-lookup"><span data-stu-id="f97a2-104">Significant Traces</span></span>  
  
|<span data-ttu-id="f97a2-105">追蹤</span><span class="sxs-lookup"><span data-stu-id="f97a2-105">Trace</span></span>|<span data-ttu-id="f97a2-106">描述</span><span class="sxs-lookup"><span data-stu-id="f97a2-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f97a2-107">訊息記錄追蹤。</span><span class="sxs-lookup"><span data-stu-id="f97a2-107">Message log trace</span></span>|<span data-ttu-id="f97a2-108">當 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 資訊由啟用 `System.ServiceModel.MessageLogging` 追蹤來源時的訊息記錄功能記錄時，發出此追蹤。</span><span class="sxs-lookup"><span data-stu-id="f97a2-108">The trace is emitted when a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message is logged by the message logging feature when the `System.ServiceModel.MessageLogging` trace source is enabled.</span></span> <span data-ttu-id="f97a2-109">按一下此追蹤以顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="f97a2-109">Clicking this trace displays the message.</span></span> <span data-ttu-id="f97a2-110">用於訊息的可配置記錄點有四個：`ServiceLevelSendRequest`、`TransportSend`、`TransportReceive`、`ServiceLevelReceiveRequest`，並由訊息記錄中的訊息來源指示。</span><span class="sxs-lookup"><span data-stu-id="f97a2-110">There are four configurable logging points for a message: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, also indicated by the Message Source attribute in the message log trace.</span></span>|  
|<span data-ttu-id="f97a2-111">已接收訊息追蹤</span><span class="sxs-lookup"><span data-stu-id="f97a2-111">Message received trace</span></span>|<span data-ttu-id="f97a2-112">如果已在資訊層級或詳細資訊層級啟用 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 追蹤來源而收到 `System.ServiceModel` 訊息時，便會發出此追蹤。</span><span class="sxs-lookup"><span data-stu-id="f97a2-112">This trace is emitted when a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message is received if the `System.ServiceModel` trace source is enabled at information or verbose level.</span></span> <span data-ttu-id="f97a2-113">必須有這個追蹤，才能在活動圖形檢視中看到訊息相互關聯箭頭。</span><span class="sxs-lookup"><span data-stu-id="f97a2-113">This trace is necessary to see the message correlation arrow in the activity graph view.</span></span>|  
|<span data-ttu-id="f97a2-114">已傳送訊息追蹤</span><span class="sxs-lookup"><span data-stu-id="f97a2-114">Message sent trace</span></span>|<span data-ttu-id="f97a2-115">如果在資訊層級或詳細資訊層級啟用 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 追蹤來源，則當傳送 `System.ServiceModel` 訊息時，會發出此追蹤。</span><span class="sxs-lookup"><span data-stu-id="f97a2-115">This trace is emitted when a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message is sent if the `System.ServiceModel` trace source is enabled at information or verbose level.</span></span> <span data-ttu-id="f97a2-116">必須有這個追蹤，才能在活動圖形檢視中看到訊息相互關聯箭頭。</span><span class="sxs-lookup"><span data-stu-id="f97a2-116">This trace is necessary to see the message correlation arrow in the activity graph view.</span></span>|  
|<span data-ttu-id="f97a2-117">取得 ChannelEndpointElement</span><span class="sxs-lookup"><span data-stu-id="f97a2-117">Get ChannelEndpointElement</span></span>|<span data-ttu-id="f97a2-118">此追蹤在資訊層的建構通道處理站中發出。</span><span class="sxs-lookup"><span data-stu-id="f97a2-118">This trace is emitted in Construct channel factory, at information level.</span></span> <span data-ttu-id="f97a2-119">它提供用戶端正在交涉的端點描述 (遠端位址、繫結、合約名稱)。</span><span class="sxs-lookup"><span data-stu-id="f97a2-119">It provides a description of the endpoint the client is talking to (remote address, binding, contract name).</span></span>|  
|<span data-ttu-id="f97a2-120">取得 ServiceElement</span><span class="sxs-lookup"><span data-stu-id="f97a2-120">Get ServiceElement</span></span>|<span data-ttu-id="f97a2-121">此追蹤在資訊層的建構服務主機中發出。</span><span class="sxs-lookup"><span data-stu-id="f97a2-121">This trace is emitted in Construct service host, at Information level.</span></span> <span data-ttu-id="f97a2-122">它提供服務合約與繫結的描述。</span><span class="sxs-lookup"><span data-stu-id="f97a2-122">It provides a description of the service contract and binding.</span></span>|  
|<span data-ttu-id="f97a2-123">SocketConnection 建立</span><span class="sxs-lookup"><span data-stu-id="f97a2-123">SocketConnection create</span></span>|<span data-ttu-id="f97a2-124">此追蹤會在用戶端執行第一次處理動作時發出，並在服務的接收位元組活動中發出。</span><span class="sxs-lookup"><span data-stu-id="f97a2-124">This trace is emitted in the first Process action performed by the client and in the Receive bytes activity on the service.</span></span> <span data-ttu-id="f97a2-125">它會提供本機與遠端 IP 位址，</span><span class="sxs-lookup"><span data-stu-id="f97a2-125">It provides the local and remote IP addresses.</span></span> <span data-ttu-id="f97a2-126">也會在資訊層發出。</span><span class="sxs-lookup"><span data-stu-id="f97a2-126">It is emitted at Information level.</span></span>|
