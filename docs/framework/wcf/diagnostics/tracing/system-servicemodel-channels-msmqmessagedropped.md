---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 6e8b134f61d2dc9bd5daf541db4ec81604166baa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260379"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="b84e7-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="b84e7-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>

<span data-ttu-id="b84e7-103">MSMQ 已捨棄訊息。</span><span class="sxs-lookup"><span data-stu-id="b84e7-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b84e7-104">描述</span><span class="sxs-lookup"><span data-stu-id="b84e7-104">Description</span></span>  

 <span data-ttu-id="b84e7-105">此追蹤表示已捨棄 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="b84e7-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="b84e7-106">當 Windows Communication Foundation (WCF)  (搭配 NetMsmqBinding 或 MsmqIntegrationBinding) 無法處理時，可以卸載 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="b84e7-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="b84e7-107">這類訊息稱為有害訊息。</span><span class="sxs-lookup"><span data-stu-id="b84e7-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="b84e7-108">當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Drop` 時，就會捨棄有害訊息。</span><span class="sxs-lookup"><span data-stu-id="b84e7-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="b84e7-109">捨棄的訊息會從佇列中移除，無法再復原。</span><span class="sxs-lookup"><span data-stu-id="b84e7-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="b84e7-110">如需訊息何時變成有害的詳細資訊，以及如何設定您的服務以適當地處理它們，請參閱 [有害訊息處理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="b84e7-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b84e7-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b84e7-111">See also</span></span>

- [<span data-ttu-id="b84e7-112">追蹤</span><span class="sxs-lookup"><span data-stu-id="b84e7-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="b84e7-113">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="b84e7-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b84e7-114">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="b84e7-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="b84e7-115">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="b84e7-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
