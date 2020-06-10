---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 5bfa31d0eaf3b00017512eddc60bfa99eda619e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84582578"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="2c4fa-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="2c4fa-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="2c4fa-103">嘗試重複使用共用連線失敗。</span><span class="sxs-lookup"><span data-stu-id="2c4fa-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="2c4fa-104">在指定的逾時期間內，進行另一次嘗試。</span><span class="sxs-lookup"><span data-stu-id="2c4fa-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2c4fa-105">描述</span><span class="sxs-lookup"><span data-stu-id="2c4fa-105">Description</span></span>  
 <span data-ttu-id="2c4fa-106">這個告知性追蹤表示嘗試重複使用共用連線時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2c4fa-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="2c4fa-107">因為共用連線不相容、尚未就緒或不是使用中，可能就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="2c4fa-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="2c4fa-108">若在指定的逾時值之內額外嘗試重複使用其他的共用連線，會建立新的連線，以防找不到可用的連線。</span><span class="sxs-lookup"><span data-stu-id="2c4fa-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c4fa-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="2c4fa-109">See also</span></span>

- [<span data-ttu-id="2c4fa-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="2c4fa-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="2c4fa-111">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="2c4fa-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2c4fa-112">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="2c4fa-112">Administration and Diagnostics</span></span>](../index.md)
