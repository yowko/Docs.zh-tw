---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 8615cca7d4ed8ea1f40baa9502e7136d4349eb9c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256309"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="fe1fd-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="fe1fd-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>

<span data-ttu-id="fe1fd-103">嘗試重複使用共用連線失敗。</span><span class="sxs-lookup"><span data-stu-id="fe1fd-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="fe1fd-104">在指定的逾時期間內，進行另一次嘗試。</span><span class="sxs-lookup"><span data-stu-id="fe1fd-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fe1fd-105">描述</span><span class="sxs-lookup"><span data-stu-id="fe1fd-105">Description</span></span>  

 <span data-ttu-id="fe1fd-106">這個告知性追蹤表示嘗試重複使用共用連線時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="fe1fd-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="fe1fd-107">因為共用連線不相容、尚未就緒或不是使用中，可能就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="fe1fd-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="fe1fd-108">若在指定的逾時值之內額外嘗試重複使用其他的共用連線，會建立新的連線，以防找不到可用的連線。</span><span class="sxs-lookup"><span data-stu-id="fe1fd-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe1fd-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe1fd-109">See also</span></span>

- [<span data-ttu-id="fe1fd-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="fe1fd-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="fe1fd-111">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="fe1fd-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="fe1fd-112">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="fe1fd-112">Administration and Diagnostics</span></span>](../index.md)
