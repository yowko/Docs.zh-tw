---
title: "通道擴充性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e0cf92edc4ec05df3e5e8c25b90bcf253e94ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="channels-extensibility"></a><span data-ttu-id="47d6b-102">通道擴充性</span><span class="sxs-lookup"><span data-stu-id="47d6b-102">Channels Extensibility</span></span>
<span data-ttu-id="47d6b-103">本節包含示範自訂通道的範例。</span><span class="sxs-lookup"><span data-stu-id="47d6b-103">This section contains samples that demonstrate custom channels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47d6b-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="47d6b-104">In This Section</span></span>  
 [<span data-ttu-id="47d6b-105">本機通道</span><span class="sxs-lookup"><span data-stu-id="47d6b-105">Local Channel</span></span>](../../../../docs/framework/wcf/samples/local-channel.md)  
 <span data-ttu-id="47d6b-106">示範邏輯通道，也就是在相同的應用程式網域中，用於通訊的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="47d6b-106">Demonstrates the local channel, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transport channel that is used for communication within the same application domain.</span></span>  
  
 [<span data-ttu-id="47d6b-107">可靠的安全設定檔</span><span class="sxs-lookup"><span data-stu-id="47d6b-107">Reliable Secure Profile</span></span>](../../../../docs/framework/wcf/samples/reliable-secure-profile.md)  
 <span data-ttu-id="47d6b-108">示範如何撰寫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 與可靠的安全設定檔 (Reliable Secure Profile，RSP)。</span><span class="sxs-lookup"><span data-stu-id="47d6b-108">Demonstrates how to compose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and Reliable Secure Profile (RSP).</span></span>  
  
 [<span data-ttu-id="47d6b-109">自訂通道發送器</span><span class="sxs-lookup"><span data-stu-id="47d6b-109">Custom Channel Dispatcher</span></span>](../../../../docs/framework/wcf/samples/custom-channel-dispatcher.md)  
 <span data-ttu-id="47d6b-110">示範如何使用自訂的方式，直接實作 <xref:System.ServiceModel.ServiceHostBase> 來建立通道堆疊，以及如何在 Web 主機環境中建立自訂通道發送器。</span><span class="sxs-lookup"><span data-stu-id="47d6b-110">Demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span>  
  
 [<span data-ttu-id="47d6b-111">區塊處理通道</span><span class="sxs-lookup"><span data-stu-id="47d6b-111">Chunking Channel</span></span>](../../../../docs/framework/wcf/samples/chunking-channel.md)  
 <span data-ttu-id="47d6b-112">示範如何限制使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 緩衝大型訊息所使用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="47d6b-112">Demonstrates how to limit the amount of memory used to buffer large messages sent using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="47d6b-113">HTTP 確認通道</span><span class="sxs-lookup"><span data-stu-id="47d6b-113">HTTP Acknowledgement Channel</span></span>](../../../../docs/framework/wcf/samples/http-acknowledgement-channel.md)  
 <span data-ttu-id="47d6b-114">示範變更單向訊息模式的層次通道。</span><span class="sxs-lookup"><span data-stu-id="47d6b-114">Demonstrates a layered channel which changes the one-way messaging pattern.</span></span>  
  
 [<span data-ttu-id="47d6b-115">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="47d6b-115">HttpCookieSession</span></span>](../../../../docs/framework/wcf/samples/httpcookiesession.md)  
 <span data-ttu-id="47d6b-116">示範如何將自訂通訊協定通道建置成在工作階段管理使用 HTTP Cookie。</span><span class="sxs-lookup"><span data-stu-id="47d6b-116">Demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span>  
  
 [<span data-ttu-id="47d6b-117">自訂訊息攔截器</span><span class="sxs-lookup"><span data-stu-id="47d6b-117">Custom Message Interceptor</span></span>](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)  
 <span data-ttu-id="47d6b-118">示範如何實作建立通道處理站和通道接聽程式的自訂繫結項目，以攔截執行階段堆疊中特定點的所有傳入與傳出訊息。</span><span class="sxs-lookup"><span data-stu-id="47d6b-118">Demonstrates how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span>
