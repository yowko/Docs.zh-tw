---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 4b016f53a75d9527a5cd1bbadacacd650b7f35b0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601895"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="2e2b4-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="2e2b4-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="2e2b4-103">MSMQ 已捨棄訊息。</span><span class="sxs-lookup"><span data-stu-id="2e2b4-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2e2b4-104">描述</span><span class="sxs-lookup"><span data-stu-id="2e2b4-104">Description</span></span>  
 <span data-ttu-id="2e2b4-105">此追蹤表示已捨棄 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="2e2b4-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="2e2b4-106">當 Windows Communication Foundation （WCF）（與 NetMsmqBinding 或 MsmqIntegrationBinding 搭配使用）無法處理 MSMQ 訊息時，可以卸載它。</span><span class="sxs-lookup"><span data-stu-id="2e2b4-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="2e2b4-107">這類訊息稱為有害訊息。</span><span class="sxs-lookup"><span data-stu-id="2e2b4-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="2e2b4-108">當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Drop` 時，就會捨棄有害訊息。</span><span class="sxs-lookup"><span data-stu-id="2e2b4-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="2e2b4-109">捨棄的訊息會從佇列中移除，無法再復原。</span><span class="sxs-lookup"><span data-stu-id="2e2b4-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="2e2b4-110">如需訊息何時會變成有害的詳細資訊，以及如何設定您的服務來適當地處理它們，請參閱[有害訊息處理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="2e2b4-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e2b4-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="2e2b4-111">See also</span></span>

- [<span data-ttu-id="2e2b4-112">追蹤</span><span class="sxs-lookup"><span data-stu-id="2e2b4-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="2e2b4-113">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="2e2b4-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2e2b4-114">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="2e2b4-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="2e2b4-115">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="2e2b4-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
