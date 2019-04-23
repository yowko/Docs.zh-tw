---
title: System.ServiceModel.TxAsyncAbort
ms.date: 03/30/2017
ms.assetid: bce47ff2-abd0-4b58-8667-ebf1ef3580b8
ms.openlocfilehash: a6989da7b457e819a49d7c27e8732c7f33dc51b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133922"
---
# <a name="systemservicemodeltxasyncabort"></a><span data-ttu-id="90e2d-102">System.ServiceModel.TxAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="90e2d-102">System.ServiceModel.TxAsyncAbort</span></span>
<span data-ttu-id="90e2d-103">指定的異動已非同步中止。</span><span class="sxs-lookup"><span data-stu-id="90e2d-103">The specified transaction was asynchronously aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="90e2d-104">描述</span><span class="sxs-lookup"><span data-stu-id="90e2d-104">Description</span></span>  
 <span data-ttu-id="90e2d-105">目前的異動因另一個參與者有意「中止」、發生逾時或異動參與者內的其他錯誤而中止。</span><span class="sxs-lookup"><span data-stu-id="90e2d-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="90e2d-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="90e2d-106">Troubleshooting</span></span>  
 <span data-ttu-id="90e2d-107">檢查所有的系統記錄檔，查看這個中止是否為非預期中的，以判斷中止的真正原因。</span><span class="sxs-lookup"><span data-stu-id="90e2d-107">Check all system logs if this abort is unexpected to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e2d-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90e2d-108">See also</span></span>

- [<span data-ttu-id="90e2d-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="90e2d-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="90e2d-110">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="90e2d-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="90e2d-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="90e2d-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
