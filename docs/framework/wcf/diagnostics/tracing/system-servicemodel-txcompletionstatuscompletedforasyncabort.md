---
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.date: 03/30/2017
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
ms.openlocfilehash: 3d43524b7141a134b9560e92da66ef2349b8119a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631275"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="cfb02-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="cfb02-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="cfb02-103">發生非同步中止，指定作業的指定異動已完成。</span><span class="sxs-lookup"><span data-stu-id="cfb02-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cfb02-104">描述</span><span class="sxs-lookup"><span data-stu-id="cfb02-104">Description</span></span>  
 <span data-ttu-id="cfb02-105">目前的交易因另一個參與者有意「中止」、發生逾時或交易參與者內的其他錯誤而中止。</span><span class="sxs-lookup"><span data-stu-id="cfb02-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="cfb02-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="cfb02-106">Troubleshooting</span></span>  
 <span data-ttu-id="cfb02-107">如果這是未預期的中止，請檢查所有系統記錄檔以判斷中止的真正原因。</span><span class="sxs-lookup"><span data-stu-id="cfb02-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb02-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfb02-108">See also</span></span>
- [<span data-ttu-id="cfb02-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="cfb02-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="cfb02-110">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="cfb02-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="cfb02-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="cfb02-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
