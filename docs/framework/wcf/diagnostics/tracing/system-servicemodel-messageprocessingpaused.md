---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 85bec8255e0d20d6e76ea354e5b8c42b83d7d8e6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598147"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="3092e-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="3092e-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="3092e-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="3092e-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="3092e-104">描述</span><span class="sxs-lookup"><span data-stu-id="3092e-104">Description</span></span>  
 <span data-ttu-id="3092e-105">已在處理訊息時切換執行緒。</span><span class="sxs-lookup"><span data-stu-id="3092e-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="3092e-106">訊息處理可能會因為下列原因而暫停：</span><span class="sxs-lookup"><span data-stu-id="3092e-106">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="3092e-107">ConcurrencyMode 是單一或可重新進入，且服務正在處理另一個訊息。</span><span class="sxs-lookup"><span data-stu-id="3092e-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="3092e-108">交易已啟用且服務正在處理另一個交易。</span><span class="sxs-lookup"><span data-stu-id="3092e-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="3092e-109">同步處理內容不是最新的。</span><span class="sxs-lookup"><span data-stu-id="3092e-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3092e-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="3092e-110">See also</span></span>

- [<span data-ttu-id="3092e-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="3092e-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="3092e-112">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="3092e-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="3092e-113">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="3092e-113">Administration and Diagnostics</span></span>](../index.md)
