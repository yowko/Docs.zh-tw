---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 093a76a0157948520c2f0d8bf6145b6f78966906
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695461"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="b5548-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="b5548-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="b5548-103">嘗試重複使用共用連線失敗。</span><span class="sxs-lookup"><span data-stu-id="b5548-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="b5548-104">在指定的逾時期間內，進行另一次嘗試。</span><span class="sxs-lookup"><span data-stu-id="b5548-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b5548-105">描述</span><span class="sxs-lookup"><span data-stu-id="b5548-105">Description</span></span>  
 <span data-ttu-id="b5548-106">這個告知性追蹤表示嘗試重複使用共用連線時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b5548-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="b5548-107">因為共用連線不相容、尚未就緒或不是使用中，可能就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="b5548-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="b5548-108">若在指定的逾時值之內額外嘗試重複使用其他的共用連線，會建立新的連線，以防找不到可用的連線。</span><span class="sxs-lookup"><span data-stu-id="b5548-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5548-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5548-109">See also</span></span>
- [<span data-ttu-id="b5548-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="b5548-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="b5548-111">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="b5548-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b5548-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="b5548-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
