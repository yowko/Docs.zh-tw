---
title: System.ServiceModel.Channels.FailedPipeConnect
ms.date: 03/30/2017
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
ms.openlocfilehash: 22d2605c3c96c0e030f9e435293de42094965cb7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627938"
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a><span data-ttu-id="b0f99-102">System.ServiceModel.Channels.FailedPipeConnect</span><span class="sxs-lookup"><span data-stu-id="b0f99-102">System.ServiceModel.Channels.FailedPipeConnect</span></span>
<span data-ttu-id="b0f99-103">嘗試連接具名管道端點失敗。</span><span class="sxs-lookup"><span data-stu-id="b0f99-103">An attempt to connect to the named pipe endpoint failed.</span></span> <span data-ttu-id="b0f99-104">在指定的逾時期間內，進行另一次嘗試。</span><span class="sxs-lookup"><span data-stu-id="b0f99-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b0f99-105">描述</span><span class="sxs-lookup"><span data-stu-id="b0f99-105">Description</span></span>  
 <span data-ttu-id="b0f99-106">這個告知性追蹤表示無法連接到具名通道端點。</span><span class="sxs-lookup"><span data-stu-id="b0f99-106">This informational trace indicates a failure to connect to a named pipe endpoint.</span></span> <span data-ttu-id="b0f99-107">如果具名通道端點找不到或忙碌中，可能就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="b0f99-107">This could happen if the named pipe endpoint is not found or is busy.</span></span> <span data-ttu-id="b0f99-108">進行額外的嘗試，每個嘗試之間相隔短暫的時間，直到成功或 OpenTimeout 到期為止。</span><span class="sxs-lookup"><span data-stu-id="b0f99-108">Additional attempts are made, each separated by a short amount of time, until one succeeds or the OpenTimeout expires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f99-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0f99-109">See also</span></span>
- [<span data-ttu-id="b0f99-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="b0f99-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="b0f99-111">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="b0f99-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b0f99-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="b0f99-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
