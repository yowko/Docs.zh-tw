---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: e4c8040d2350e3824b5d68dc6f32376007792a7f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235112"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="f9dda-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="f9dda-102">System.ServiceModel.MessageProcessingPaused</span></span>

<span data-ttu-id="f9dda-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="f9dda-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="f9dda-104">描述</span><span class="sxs-lookup"><span data-stu-id="f9dda-104">Description</span></span>  

 <span data-ttu-id="f9dda-105">已在處理訊息時切換執行緒。</span><span class="sxs-lookup"><span data-stu-id="f9dda-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="f9dda-106">訊息處理可能會因為下列原因而暫停：</span><span class="sxs-lookup"><span data-stu-id="f9dda-106">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="f9dda-107">ConcurrencyMode 是單一或可重新進入，且服務正在處理另一個訊息。</span><span class="sxs-lookup"><span data-stu-id="f9dda-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="f9dda-108">交易已啟用且服務正在處理另一個交易。</span><span class="sxs-lookup"><span data-stu-id="f9dda-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="f9dda-109">同步處理內容不是最新的。</span><span class="sxs-lookup"><span data-stu-id="f9dda-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9dda-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9dda-110">See also</span></span>

- [<span data-ttu-id="f9dda-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="f9dda-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="f9dda-112">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="f9dda-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f9dda-113">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="f9dda-113">Administration and Diagnostics</span></span>](../index.md)
