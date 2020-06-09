---
title: System.ServiceModel.Channels.FailedPipeConnect
ms.date: 03/30/2017
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
ms.openlocfilehash: 790a15e5401850f2767cb06f5f321ad80c674f2b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84582409"
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a><span data-ttu-id="506a4-102">System.ServiceModel.Channels.FailedPipeConnect</span><span class="sxs-lookup"><span data-stu-id="506a4-102">System.ServiceModel.Channels.FailedPipeConnect</span></span>
<span data-ttu-id="506a4-103">嘗試連接具名管道端點失敗。</span><span class="sxs-lookup"><span data-stu-id="506a4-103">An attempt to connect to the named pipe endpoint failed.</span></span> <span data-ttu-id="506a4-104">在指定的逾時期間內，進行另一次嘗試。</span><span class="sxs-lookup"><span data-stu-id="506a4-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="506a4-105">描述</span><span class="sxs-lookup"><span data-stu-id="506a4-105">Description</span></span>  
 <span data-ttu-id="506a4-106">這個告知性追蹤表示無法連接到具名通道端點。</span><span class="sxs-lookup"><span data-stu-id="506a4-106">This informational trace indicates a failure to connect to a named pipe endpoint.</span></span> <span data-ttu-id="506a4-107">如果具名通道端點找不到或忙碌中，可能就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="506a4-107">This could happen if the named pipe endpoint is not found or is busy.</span></span> <span data-ttu-id="506a4-108">進行額外的嘗試，每個嘗試之間相隔短暫的時間，直到成功或 OpenTimeout 到期為止。</span><span class="sxs-lookup"><span data-stu-id="506a4-108">Additional attempts are made, each separated by a short amount of time, until one succeeds or the OpenTimeout expires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="506a4-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="506a4-109">See also</span></span>

- [<span data-ttu-id="506a4-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="506a4-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="506a4-111">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="506a4-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="506a4-112">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="506a4-112">Administration and Diagnostics</span></span>](../index.md)
