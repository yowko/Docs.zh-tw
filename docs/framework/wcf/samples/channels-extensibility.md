---
title: 通道擴充性
ms.date: 03/30/2017
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
ms.openlocfilehash: 1a734c305e2a6f2fc759647ab5bdf380f7c7eeee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253830"
---
# <a name="channels-extensibility"></a><span data-ttu-id="de19f-102">通道擴充性</span><span class="sxs-lookup"><span data-stu-id="de19f-102">Channels Extensibility</span></span>

<span data-ttu-id="de19f-103">本節包含示範自訂通道的範例。</span><span class="sxs-lookup"><span data-stu-id="de19f-103">This section contains samples that demonstrate custom channels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="de19f-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="de19f-104">In This Section</span></span>  

 [<span data-ttu-id="de19f-105">本機通道</span><span class="sxs-lookup"><span data-stu-id="de19f-105">Local Channel</span></span>](local-channel.md)  
 <span data-ttu-id="de19f-106">示範本機通道，這是用於相同應用程式域內通訊的 WCF 傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="de19f-106">Demonstrates the local channel, a WCF transport channel that is used for communication within the same application domain.</span></span>  
  
 [<span data-ttu-id="de19f-107">可靠的安全設定檔</span><span class="sxs-lookup"><span data-stu-id="de19f-107">Reliable Secure Profile</span></span>](reliable-secure-profile.md)  
 <span data-ttu-id="de19f-108">示範如何撰寫 WCF 和可靠的安全設定檔 (RSP) 。</span><span class="sxs-lookup"><span data-stu-id="de19f-108">Demonstrates how to compose WCF and Reliable Secure Profile (RSP).</span></span>  
  
 [<span data-ttu-id="de19f-109">自訂通道發送器</span><span class="sxs-lookup"><span data-stu-id="de19f-109">Custom Channel Dispatcher</span></span>](custom-channel-dispatcher.md)  
 <span data-ttu-id="de19f-110">示範如何使用自訂的方式，直接實作 <xref:System.ServiceModel.ServiceHostBase> 來建立通道堆疊，以及如何在 Web 主機環境中建立自訂通道發送器。</span><span class="sxs-lookup"><span data-stu-id="de19f-110">Demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span>  
  
 [<span data-ttu-id="de19f-111">區塊處理通道</span><span class="sxs-lookup"><span data-stu-id="de19f-111">Chunking Channel</span></span>](chunking-channel.md)  
 <span data-ttu-id="de19f-112">示範如何限制用來緩衝使用 WCF 傳送之大型訊息的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="de19f-112">Demonstrates how to limit the amount of memory used to buffer large messages sent using WCF.</span></span>
  
 [<span data-ttu-id="de19f-113">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="de19f-113">HttpCookieSession</span></span>](httpcookiesession.md)  
 <span data-ttu-id="de19f-114">示範如何將自訂通訊協定通道建置成在工作階段管理使用 HTTP Cookie。</span><span class="sxs-lookup"><span data-stu-id="de19f-114">Demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span>  
  
 [<span data-ttu-id="de19f-115">自訂訊息攔截器</span><span class="sxs-lookup"><span data-stu-id="de19f-115">Custom Message Interceptor</span></span>](custom-message-interceptor.md)  
 <span data-ttu-id="de19f-116">示範如何實作建立通道處理站和通道接聽程式的自訂繫結項目，以攔截執行階段堆疊中特定點的所有傳入與傳出訊息。</span><span class="sxs-lookup"><span data-stu-id="de19f-116">Demonstrates how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span>
