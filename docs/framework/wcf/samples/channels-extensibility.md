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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bcda7f9edc741e8f0c9c56214119255ca2777d77
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="channels-extensibility"></a><span data-ttu-id="c6f25-102">通道擴充性</span><span class="sxs-lookup"><span data-stu-id="c6f25-102">Channels Extensibility</span></span>
<span data-ttu-id="c6f25-103">本節包含示範自訂通道的範例。</span><span class="sxs-lookup"><span data-stu-id="c6f25-103">This section contains samples that demonstrate custom channels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6f25-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="c6f25-104">In This Section</span></span>  
 [<span data-ttu-id="c6f25-105">本機通道</span><span class="sxs-lookup"><span data-stu-id="c6f25-105">Local Channel</span></span>](../../../../docs/framework/wcf/samples/local-channel.md)  
 <span data-ttu-id="c6f25-106">示範邏輯通道，也就是在相同的應用程式網域中，用於通訊的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="c6f25-106">Demonstrates the local channel, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transport channel that is used for communication within the same application domain.</span></span>  
  
 [<span data-ttu-id="c6f25-107">可靠的安全設定檔</span><span class="sxs-lookup"><span data-stu-id="c6f25-107">Reliable Secure Profile</span></span>](../../../../docs/framework/wcf/samples/reliable-secure-profile.md)  
 <span data-ttu-id="c6f25-108">示範如何撰寫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 與可靠的安全設定檔 (Reliable Secure Profile，RSP)。</span><span class="sxs-lookup"><span data-stu-id="c6f25-108">Demonstrates how to compose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and Reliable Secure Profile (RSP).</span></span>  
  
 [<span data-ttu-id="c6f25-109">自訂通道發送器</span><span class="sxs-lookup"><span data-stu-id="c6f25-109">Custom Channel Dispatcher</span></span>](../../../../docs/framework/wcf/samples/custom-channel-dispatcher.md)  
 <span data-ttu-id="c6f25-110">示範如何使用自訂的方式，直接實作 <xref:System.ServiceModel.ServiceHostBase> 來建立通道堆疊，以及如何在 Web 主機環境中建立自訂通道發送器。</span><span class="sxs-lookup"><span data-stu-id="c6f25-110">Demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span>  
  
 [<span data-ttu-id="c6f25-111">區塊處理通道</span><span class="sxs-lookup"><span data-stu-id="c6f25-111">Chunking Channel</span></span>](../../../../docs/framework/wcf/samples/chunking-channel.md)  
 <span data-ttu-id="c6f25-112">示範如何限制使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 緩衝大型訊息所使用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="c6f25-112">Demonstrates how to limit the amount of memory used to buffer large messages sent using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="c6f25-113">HTTP 確認通道</span><span class="sxs-lookup"><span data-stu-id="c6f25-113">HTTP Acknowledgement Channel</span></span>](../../../../docs/framework/wcf/samples/http-acknowledgement-channel.md)  
 <span data-ttu-id="c6f25-114">示範變更單向訊息模式的層次通道。</span><span class="sxs-lookup"><span data-stu-id="c6f25-114">Demonstrates a layered channel which changes the one-way messaging pattern.</span></span>  
  
 [<span data-ttu-id="c6f25-115">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="c6f25-115">HttpCookieSession</span></span>](../../../../docs/framework/wcf/samples/httpcookiesession.md)  
 <span data-ttu-id="c6f25-116">示範如何將自訂通訊協定通道建置成在工作階段管理使用 HTTP Cookie。</span><span class="sxs-lookup"><span data-stu-id="c6f25-116">Demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span>  
  
 [<span data-ttu-id="c6f25-117">自訂訊息攔截器</span><span class="sxs-lookup"><span data-stu-id="c6f25-117">Custom Message Interceptor</span></span>](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)  
 <span data-ttu-id="c6f25-118">示範如何實作建立通道處理站和通道接聽程式的自訂繫結項目，以攔截執行階段堆疊中特定點的所有傳入與傳出訊息。</span><span class="sxs-lookup"><span data-stu-id="c6f25-118">Demonstrates how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span>
