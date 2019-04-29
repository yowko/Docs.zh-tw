---
title: System.ServiceModel.TxAsyncAbort
ms.date: 03/30/2017
ms.assetid: bce47ff2-abd0-4b58-8667-ebf1ef3580b8
ms.openlocfilehash: a6989da7b457e819a49d7c27e8732c7f33dc51b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768747"
---
# <a name="systemservicemodeltxasyncabort"></a><span data-ttu-id="b5922-102">System.ServiceModel.TxAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="b5922-102">System.ServiceModel.TxAsyncAbort</span></span>
<span data-ttu-id="b5922-103">指定的異動已非同步中止。</span><span class="sxs-lookup"><span data-stu-id="b5922-103">The specified transaction was asynchronously aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b5922-104">描述</span><span class="sxs-lookup"><span data-stu-id="b5922-104">Description</span></span>  
 <span data-ttu-id="b5922-105">目前的異動因另一個參與者有意「中止」、發生逾時或異動參與者內的其他錯誤而中止。</span><span class="sxs-lookup"><span data-stu-id="b5922-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b5922-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="b5922-106">Troubleshooting</span></span>  
 <span data-ttu-id="b5922-107">檢查所有的系統記錄檔，查看這個中止是否為非預期中的，以判斷中止的真正原因。</span><span class="sxs-lookup"><span data-stu-id="b5922-107">Check all system logs if this abort is unexpected to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5922-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5922-108">See also</span></span>

- [<span data-ttu-id="b5922-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="b5922-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="b5922-110">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="b5922-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b5922-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="b5922-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
