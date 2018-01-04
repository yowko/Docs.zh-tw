---
title: "Net MSMQ 繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe4bb696-f57c-4cb3-9b7e-9d95fe6b8323
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f6282dfbf5e67f91167e5abf0640641000994d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="net-msmq-binding"></a><span data-ttu-id="7c62a-102">Net MSMQ 繫結</span><span class="sxs-lookup"><span data-stu-id="7c62a-102">Net MSMQ Binding</span></span>
<span data-ttu-id="7c62a-103">本節包含示範使用端點項目之 MSMQ 繫結屬性的範例。</span><span class="sxs-lookup"><span data-stu-id="7c62a-103">This section contains samples that demonstrate using MSMQ binding attributes of an endpoint element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c62a-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="7c62a-104">In This Section</span></span>  
 [<span data-ttu-id="7c62a-105">異動 MSMQ 繫結</span><span class="sxs-lookup"><span data-stu-id="7c62a-105">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 <span data-ttu-id="7c62a-106">示範如何使用訊息佇列 (MSMQ) 執行交易佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="7c62a-106">Demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>  
  
 [<span data-ttu-id="7c62a-107">變動性佇列通訊</span><span class="sxs-lookup"><span data-stu-id="7c62a-107">Volatile Queued Communication</span></span>](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
 <span data-ttu-id="7c62a-108">示範如何透過訊息佇列 (MSMQ) 傳輸來執行變動性佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="7c62a-108">Demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span>  
  
 [<span data-ttu-id="7c62a-109">無效信件佇列</span><span class="sxs-lookup"><span data-stu-id="7c62a-109">Dead Letter Queues</span></span>](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
 <span data-ttu-id="7c62a-110">示範如何處理已傳遞失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="7c62a-110">Demonstrates how to handle and process messages that have failed delivery.</span></span>  
  
 [<span data-ttu-id="7c62a-111">MSMQ 4.0 中的有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="7c62a-111">Poison Message Handling in MSMQ 4.0</span></span>](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md)  
 <span data-ttu-id="7c62a-112">示範如何使用 MSMQ 4.0 在服務中執行有害訊息處理。</span><span class="sxs-lookup"><span data-stu-id="7c62a-112">Demonstrates how to perform poison message handling in a service using MSMQ 4.0.</span></span>  
  
 [<span data-ttu-id="7c62a-113">工作階段和佇列</span><span class="sxs-lookup"><span data-stu-id="7c62a-113">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 <span data-ttu-id="7c62a-114">示範如何透過訊息佇列 (MSMQ) 傳輸，傳送和接收佇列通訊中的一組相關訊息。</span><span class="sxs-lookup"><span data-stu-id="7c62a-114">Demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span>  
  
 [<span data-ttu-id="7c62a-115">雙向通訊</span><span class="sxs-lookup"><span data-stu-id="7c62a-115">Two-Way Communication</span></span>](../../../../docs/framework/wcf/samples/two-way-communication.md)  
 <span data-ttu-id="7c62a-116">示範如何透過 MSMQ 執行交易雙向佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="7c62a-116">Demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span>  
  
 [<span data-ttu-id="7c62a-117">異動批次處理</span><span class="sxs-lookup"><span data-stu-id="7c62a-117">Transacted Batching</span></span>](../../../../docs/framework/wcf/samples/transacted-batching.md)  
 <span data-ttu-id="7c62a-118">示範如何使用訊息佇列 (MSMQ) 批次處理交易讀取作業。</span><span class="sxs-lookup"><span data-stu-id="7c62a-118">Demonstrates how to batch transacted reads by using Message Queuing (MSMQ).</span></span>  
  
 [<span data-ttu-id="7c62a-119">SRMP</span><span class="sxs-lookup"><span data-stu-id="7c62a-119">SRMP</span></span>](../../../../docs/framework/wcf/samples/srmp.md)  
 <span data-ttu-id="7c62a-120">示範如何使用訊息佇列 (MSMQ) 透過 HTTP 執行交易佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="7c62a-120">Demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 [<span data-ttu-id="7c62a-121">訊息佇列上的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="7c62a-121">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
 <span data-ttu-id="7c62a-122">示範如何實作應用程式，該應用程式使用適用於用戶端並具有 X.509v3 憑證驗證的 WS-Security，並透過 MSMQ 使用伺服器的 X.509v3 憑證來要求伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="7c62a-122">Demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span>  
  
 [<span data-ttu-id="7c62a-123">ReceiveContext 產品產生器</span><span class="sxs-lookup"><span data-stu-id="7c62a-123">ReceiveContext Product Generator</span></span>](../../../../docs/framework/wcf/samples/receivecontext-enabled-wcf-channels.md)  
 <span data-ttu-id="7c62a-124">示範啟用 <xref:System.ServiceModel.Channels.ReceiveContext> 之 WCF 通道的用處。</span><span class="sxs-lookup"><span data-stu-id="7c62a-124">Demonstrates the usefulness of <xref:System.ServiceModel.Channels.ReceiveContext>-enabled WCF channels.</span></span>
