---
title: System.ServiceModel.Channels.TcpConnectError
ms.date: 03/30/2017
ms.assetid: 22d93797-072e-405d-a3e0-5c519ddf290b
ms.openlocfilehash: 0bfd35e2b3ca421745701a91f2a5bfc91f3063aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091443"
---
# <a name="systemservicemodelchannelstcpconnecterror"></a><span data-ttu-id="dbe53-102">System.ServiceModel.Channels.TcpConnectError</span><span class="sxs-lookup"><span data-stu-id="dbe53-102">System.ServiceModel.Channels.TcpConnectError</span></span>
<span data-ttu-id="dbe53-103">TCP 連線作業失敗。</span><span class="sxs-lookup"><span data-stu-id="dbe53-103">The TCP connect operation failed.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dbe53-104">描述</span><span class="sxs-lookup"><span data-stu-id="dbe53-104">Description</span></span>  
 <span data-ttu-id="dbe53-105">這個警告層級追蹤表示無法連接到 TCP 端點。</span><span class="sxs-lookup"><span data-stu-id="dbe53-105">This warning level trace indicates a failure to connect to a TCP endpoint.</span></span> <span data-ttu-id="dbe53-106">如果位於指定之 IP 位址和連接埠的遠端端點沒有回應，就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="dbe53-106">This could happen if the remote endpoint is not responding at a given IP address and port.</span></span> <span data-ttu-id="dbe53-107">如果後續對其他有效 IP 位址 (例如 IPv4 或 IPv6 位址，或其他代表指定主機名稱的 IP 位址) 的連線嘗試成功的話，則會忽略這個追蹤。</span><span class="sxs-lookup"><span data-stu-id="dbe53-107">This trace can be ignored if subsequent attempts to connect to other valid IP addresses (such as IPv4 or IPv6 addresses, or other IP addresses representing a given hostname) succeed.</span></span> <span data-ttu-id="dbe53-108">這個追內的例外狀況會顯示有關錯誤的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="dbe53-108">The exception within this trace can reveal additional information about the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe53-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbe53-109">See also</span></span>

- [<span data-ttu-id="dbe53-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="dbe53-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="dbe53-111">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="dbe53-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="dbe53-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="dbe53-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
