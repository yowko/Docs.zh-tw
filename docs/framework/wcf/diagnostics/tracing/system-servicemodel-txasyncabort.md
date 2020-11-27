---
title: System.ServiceModel.TxAsyncAbort
ms.date: 03/30/2017
ms.assetid: bce47ff2-abd0-4b58-8667-ebf1ef3580b8
ms.openlocfilehash: fd21428279a68cd8480b6ff0617bb2a70033a40d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269947"
---
# <a name="systemservicemodeltxasyncabort"></a><span data-ttu-id="6039b-102">System.ServiceModel.TxAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="6039b-102">System.ServiceModel.TxAsyncAbort</span></span>

<span data-ttu-id="6039b-103">指定的異動已非同步中止。</span><span class="sxs-lookup"><span data-stu-id="6039b-103">The specified transaction was asynchronously aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6039b-104">描述</span><span class="sxs-lookup"><span data-stu-id="6039b-104">Description</span></span>  

 <span data-ttu-id="6039b-105">目前的異動因另一個參與者有意「中止」、發生逾時或異動參與者內的其他錯誤而中止。</span><span class="sxs-lookup"><span data-stu-id="6039b-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="6039b-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="6039b-106">Troubleshooting</span></span>  

 <span data-ttu-id="6039b-107">檢查所有的系統記錄檔，查看這個中止是否為非預期中的，以判斷中止的真正原因。</span><span class="sxs-lookup"><span data-stu-id="6039b-107">Check all system logs if this abort is unexpected to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6039b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6039b-108">See also</span></span>

- [<span data-ttu-id="6039b-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="6039b-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="6039b-110">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="6039b-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="6039b-111">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="6039b-111">Administration and Diagnostics</span></span>](../index.md)
