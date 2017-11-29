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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1176af676673e19eb2d8cd54cc4d2d254c7ba324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="d583c-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="d583c-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="d583c-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="d583c-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="d583c-104">描述</span><span class="sxs-lookup"><span data-stu-id="d583c-104">Description</span></span>  
 <span data-ttu-id="d583c-105">已在處理訊息時切換執行緒。</span><span class="sxs-lookup"><span data-stu-id="d583c-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="d583c-106">訊息處理可能會因為下列原因而暫停：</span><span class="sxs-lookup"><span data-stu-id="d583c-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="d583c-107">ConcurrencyMode 是單一或可重新進入，且服務正在處理另一個訊息。</span><span class="sxs-lookup"><span data-stu-id="d583c-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="d583c-108">交易已啟用且服務正在處理另一個交易。</span><span class="sxs-lookup"><span data-stu-id="d583c-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="d583c-109">同步處理內容不是最新的。</span><span class="sxs-lookup"><span data-stu-id="d583c-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d583c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d583c-110">See Also</span></span>  
 [<span data-ttu-id="d583c-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="d583c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="d583c-112">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="d583c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="d583c-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="d583c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
