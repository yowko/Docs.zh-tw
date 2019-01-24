---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: ba067303d861bbd7d88c67f6fd868bd808e07dfd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528676"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="a5a6a-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="a5a6a-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="a5a6a-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="a5a6a-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="a5a6a-104">描述</span><span class="sxs-lookup"><span data-stu-id="a5a6a-104">Description</span></span>  
 <span data-ttu-id="a5a6a-105">已在處理訊息時切換執行緒。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="a5a6a-106">訊息處理可能會因為下列原因而暫停：</span><span class="sxs-lookup"><span data-stu-id="a5a6a-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="a5a6a-107">ConcurrencyMode 是單一或可重新進入，且服務正在處理另一個訊息。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="a5a6a-108">異動已啟用且服務正在處理另一個異動。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="a5a6a-109">同步處理內容不是最新的。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a6a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5a6a-110">See also</span></span>
- [<span data-ttu-id="a5a6a-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="a5a6a-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="a5a6a-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="a5a6a-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a5a6a-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="a5a6a-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
