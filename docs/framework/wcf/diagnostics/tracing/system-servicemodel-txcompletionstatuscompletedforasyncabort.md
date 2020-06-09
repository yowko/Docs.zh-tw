---
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.date: 03/30/2017
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
ms.openlocfilehash: 8371dba79573f480b264ed6185b8cf0098e3cb2a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576573"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="49640-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="49640-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="49640-103">發生非同步中止，指定作業的指定異動已完成。</span><span class="sxs-lookup"><span data-stu-id="49640-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="49640-104">描述</span><span class="sxs-lookup"><span data-stu-id="49640-104">Description</span></span>  
 <span data-ttu-id="49640-105">目前的異動因另一個參與者有意「中止」、發生逾時或異動參與者內的其他錯誤而中止。</span><span class="sxs-lookup"><span data-stu-id="49640-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="49640-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="49640-106">Troubleshooting</span></span>  
 <span data-ttu-id="49640-107">如果這是未預期的中止，請檢查所有系統記錄檔以判斷中止的真正原因。</span><span class="sxs-lookup"><span data-stu-id="49640-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49640-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="49640-108">See also</span></span>

- [<span data-ttu-id="49640-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="49640-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="49640-110">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="49640-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="49640-111">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="49640-111">Administration and Diagnostics</span></span>](../index.md)
