---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 68c69de839ccbd51de9f0bfa74be018f877f7731
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085887"
---
# <a name="httplistener"></a><span data-ttu-id="2ceaa-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="2ceaa-102">HttpListener</span></span>
<span data-ttu-id="2ceaa-103"><xref:System.Net.HttpListener> 類別提供以程式設計方式控制的 HTTP 通訊協定接聽程式。</span><span class="sxs-lookup"><span data-stu-id="2ceaa-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="2ceaa-104">此接聽程式可在 <xref:System.Net.HttpListener> 物件的存留期內作用，並且在您的應用程式中執行。</span><span class="sxs-lookup"><span data-stu-id="2ceaa-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="2ceaa-105">HTTP.SYS</span><span class="sxs-lookup"><span data-stu-id="2ceaa-105">HTTP.SYS</span></span>  
 <span data-ttu-id="2ceaa-106"><xref:System.Net.HttpListener> 類別是以 HTTP.sys 為基礎，這是可處理 Windows 的所有 HTTP 流量的核心模式接聽程式。</span><span class="sxs-lookup"><span data-stu-id="2ceaa-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="2ceaa-107">HTTP.sys 提供連線管理、頻寬節流和 Web 伺服器記錄。</span><span class="sxs-lookup"><span data-stu-id="2ceaa-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="2ceaa-108">使用 `HttpCfg.exe` 工具來加入 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="2ceaa-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="2ceaa-109">如需詳細資訊，請參閱[伺服器](https://go.microsoft.com/fwlink/?LinkID=178285)文件中有關 [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) 工具的文件。</span><span class="sxs-lookup"><span data-stu-id="2ceaa-109">For more information, see the documentation on the [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](https://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ceaa-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="2ceaa-110">See Also</span></span>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [<span data-ttu-id="2ceaa-111">HTTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="2ceaa-111">HTTP Server</span></span>](https://go.microsoft.com/fwlink/?LinkID=178285)  
 [<span data-ttu-id="2ceaa-112">網際網路資訊中的安全性增強功能</span><span class="sxs-lookup"><span data-stu-id="2ceaa-112">Security Enhancements in Internet Information</span></span>](https://go.microsoft.com/fwlink/?LinkID=178286)  
 [<span data-ttu-id="2ceaa-113">HttpListener ASPX 主機應用程式範例</span><span class="sxs-lookup"><span data-stu-id="2ceaa-113">HttpListener ASPX Host Application Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179560)  
 [<span data-ttu-id="2ceaa-114">HttpListener 技術範例</span><span class="sxs-lookup"><span data-stu-id="2ceaa-114">HttpListener Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179558)  
 [<span data-ttu-id="2ceaa-115">網路程式設計範例</span><span class="sxs-lookup"><span data-stu-id="2ceaa-115">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
