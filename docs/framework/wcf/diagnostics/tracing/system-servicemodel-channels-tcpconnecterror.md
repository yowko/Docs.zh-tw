---
title: System.ServiceModel.Channels.TcpConnectError
ms.date: 03/30/2017
ms.assetid: 22d93797-072e-405d-a3e0-5c519ddf290b
ms.openlocfilehash: 68c3ecaf1009cf46db55b362cce0d1ab6c386c7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548059"
---
# <a name="systemservicemodelchannelstcpconnecterror"></a><span data-ttu-id="eded6-102">System.ServiceModel.Channels.TcpConnectError</span><span class="sxs-lookup"><span data-stu-id="eded6-102">System.ServiceModel.Channels.TcpConnectError</span></span>
<span data-ttu-id="eded6-103">TCP 連線作業失敗。</span><span class="sxs-lookup"><span data-stu-id="eded6-103">The TCP connect operation failed.</span></span>  
  
## <a name="description"></a><span data-ttu-id="eded6-104">描述</span><span class="sxs-lookup"><span data-stu-id="eded6-104">Description</span></span>  
 <span data-ttu-id="eded6-105">這個警告層級追蹤表示無法連接到 TCP 端點。</span><span class="sxs-lookup"><span data-stu-id="eded6-105">This warning level trace indicates a failure to connect to a TCP endpoint.</span></span> <span data-ttu-id="eded6-106">如果位於指定之 IP 位址和連接埠的遠端端點沒有回應，就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="eded6-106">This could happen if the remote endpoint is not responding at a given IP address and port.</span></span> <span data-ttu-id="eded6-107">如果後續對其他有效 IP 位址 (例如 IPv4 或 IPv6 位址，或其他代表指定主機名稱的 IP 位址) 的連線嘗試成功的話，則會忽略這個追蹤。</span><span class="sxs-lookup"><span data-stu-id="eded6-107">This trace can be ignored if subsequent attempts to connect to other valid IP addresses (such as IPv4 or IPv6 addresses, or other IP addresses representing a given hostname) succeed.</span></span> <span data-ttu-id="eded6-108">這個追內的例外狀況會顯示有關錯誤的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="eded6-108">The exception within this trace can reveal additional information about the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eded6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eded6-109">See also</span></span>
- [<span data-ttu-id="eded6-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="eded6-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="eded6-111">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="eded6-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="eded6-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="eded6-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
