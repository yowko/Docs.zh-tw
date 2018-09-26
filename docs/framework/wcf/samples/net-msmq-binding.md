---
title: Net MSMQ 繫結
ms.date: 03/30/2017
ms.assetid: fe4bb696-f57c-4cb3-9b7e-9d95fe6b8323
ms.openlocfilehash: ee32ea09eed28c1c7cd5df2df2d13fd5f41f4b22
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200967"
---
# <a name="net-msmq-binding"></a><span data-ttu-id="1a95b-102">Net MSMQ 繫結</span><span class="sxs-lookup"><span data-stu-id="1a95b-102">Net MSMQ Binding</span></span>
<span data-ttu-id="1a95b-103">本節包含示範使用端點項目之 MSMQ 繫結屬性的範例。</span><span class="sxs-lookup"><span data-stu-id="1a95b-103">This section contains samples that demonstrate using MSMQ binding attributes of an endpoint element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1a95b-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="1a95b-104">In This Section</span></span>  
 [<span data-ttu-id="1a95b-105">異動 MSMQ 繫結</span><span class="sxs-lookup"><span data-stu-id="1a95b-105">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 <span data-ttu-id="1a95b-106">示範如何使用訊息佇列 (MSMQ) 執行交易佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="1a95b-106">Demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>  
  
 [<span data-ttu-id="1a95b-107">變動性佇列通訊</span><span class="sxs-lookup"><span data-stu-id="1a95b-107">Volatile Queued Communication</span></span>](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
 <span data-ttu-id="1a95b-108">示範如何透過訊息佇列 (MSMQ) 傳輸來執行變動性佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="1a95b-108">Demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span>  
  
 [<span data-ttu-id="1a95b-109">無效信件佇列</span><span class="sxs-lookup"><span data-stu-id="1a95b-109">Dead Letter Queues</span></span>](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
 <span data-ttu-id="1a95b-110">示範如何處理已傳遞失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="1a95b-110">Demonstrates how to handle and process messages that have failed delivery.</span></span>  
  
 [<span data-ttu-id="1a95b-111">MSMQ 4.0 中的有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="1a95b-111">Poison Message Handling in MSMQ 4.0</span></span>](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md)  
 <span data-ttu-id="1a95b-112">示範如何使用 MSMQ 4.0 在服務中執行有害訊息處理。</span><span class="sxs-lookup"><span data-stu-id="1a95b-112">Demonstrates how to perform poison message handling in a service using MSMQ 4.0.</span></span>  
  
 [<span data-ttu-id="1a95b-113">工作階段和佇列</span><span class="sxs-lookup"><span data-stu-id="1a95b-113">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 <span data-ttu-id="1a95b-114">示範如何透過訊息佇列 (MSMQ) 傳輸，傳送和接收佇列通訊中的一組相關訊息。</span><span class="sxs-lookup"><span data-stu-id="1a95b-114">Demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span>  
  
 [<span data-ttu-id="1a95b-115">雙向通訊</span><span class="sxs-lookup"><span data-stu-id="1a95b-115">Two-Way Communication</span></span>](../../../../docs/framework/wcf/samples/two-way-communication.md)  
 <span data-ttu-id="1a95b-116">示範如何透過 MSMQ 執行交易雙向佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="1a95b-116">Demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span>
  
 [<span data-ttu-id="1a95b-117">SRMP</span><span class="sxs-lookup"><span data-stu-id="1a95b-117">SRMP</span></span>](../../../../docs/framework/wcf/samples/srmp.md)  
 <span data-ttu-id="1a95b-118">示範如何使用訊息佇列 (MSMQ) 透過 HTTP 執行交易佇列通訊。</span><span class="sxs-lookup"><span data-stu-id="1a95b-118">Demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 [<span data-ttu-id="1a95b-119">訊息佇列上的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="1a95b-119">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
 <span data-ttu-id="1a95b-120">示範如何實作應用程式，該應用程式使用適用於用戶端並具有 X.509v3 憑證驗證的 WS-Security，並透過 MSMQ 使用伺服器的 X.509v3 憑證來要求伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="1a95b-120">Demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span>
