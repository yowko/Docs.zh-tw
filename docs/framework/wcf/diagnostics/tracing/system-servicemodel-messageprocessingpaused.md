---
title: System.ServiceModel.MessageProcessingPaused
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 33d05eaa94ec0efdf6d18d03d9d38bda6f0c9eb7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="6e3e7-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="6e3e7-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="6e3e7-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="6e3e7-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="6e3e7-104">描述</span><span class="sxs-lookup"><span data-stu-id="6e3e7-104">Description</span></span>  
 <span data-ttu-id="6e3e7-105">已在處理訊息時切換執行緒。</span><span class="sxs-lookup"><span data-stu-id="6e3e7-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="6e3e7-106">訊息處理可能會因為下列原因而暫停：</span><span class="sxs-lookup"><span data-stu-id="6e3e7-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="6e3e7-107">ConcurrencyMode 是單一或可重新進入，且服務正在處理另一個訊息。</span><span class="sxs-lookup"><span data-stu-id="6e3e7-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="6e3e7-108">交易已啟用且服務正在處理另一個交易。</span><span class="sxs-lookup"><span data-stu-id="6e3e7-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="6e3e7-109">同步處理內容不是最新的。</span><span class="sxs-lookup"><span data-stu-id="6e3e7-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e3e7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e3e7-110">See Also</span></span>  
 [<span data-ttu-id="6e3e7-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="6e3e7-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="6e3e7-112">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="6e3e7-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="6e3e7-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="6e3e7-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
