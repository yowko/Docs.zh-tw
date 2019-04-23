---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: ac1dacef94d6446aa407e4a390b9561d033af1bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087465"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="29590-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="29590-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="29590-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="29590-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="29590-104">描述</span><span class="sxs-lookup"><span data-stu-id="29590-104">Description</span></span>  
 <span data-ttu-id="29590-105">已在處理訊息時切換執行緒。</span><span class="sxs-lookup"><span data-stu-id="29590-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="29590-106">訊息處理可能會因為下列原因而暫停：</span><span class="sxs-lookup"><span data-stu-id="29590-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="29590-107">ConcurrencyMode 是單一或可重新進入，且服務正在處理另一個訊息。</span><span class="sxs-lookup"><span data-stu-id="29590-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="29590-108">交易已啟用且服務正在處理另一個交易。</span><span class="sxs-lookup"><span data-stu-id="29590-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="29590-109">同步處理內容不是最新的。</span><span class="sxs-lookup"><span data-stu-id="29590-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29590-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29590-110">See also</span></span>

- [<span data-ttu-id="29590-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="29590-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="29590-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="29590-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="29590-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="29590-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
