---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: aeeba38eaf674453f4c87cf62f5088c55b5fde2d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290812"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="5c4fc-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="5c4fc-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>

<span data-ttu-id="5c4fc-103">無法移動或刪除訊息。</span><span class="sxs-lookup"><span data-stu-id="5c4fc-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5c4fc-104">描述</span><span class="sxs-lookup"><span data-stu-id="5c4fc-104">Description</span></span>  

 <span data-ttu-id="5c4fc-105">此追蹤表示嘗試移動、刪除或拒絕 MSMQ 訊息時，發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5c4fc-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="5c4fc-106">當搭配 NetMsmqBinding 或 MsmqIntegrationBinding) 使用時，Windows Communication Foundation (WCF)  (會採用 MSMQ 訊息。這項追蹤與 `ReceiveErrorHandling` NetMsmqBinding 或 MsmqIntegrationBinding 上的屬性所選擇的值有關。</span><span class="sxs-lookup"><span data-stu-id="5c4fc-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="5c4fc-107">此追蹤不代表整體系統失敗。</span><span class="sxs-lookup"><span data-stu-id="5c4fc-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="5c4fc-108">但是，它代表某個訊息的選定有害訊息處置作業失敗。</span><span class="sxs-lookup"><span data-stu-id="5c4fc-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="5c4fc-109">如需訊息何時變成有害的詳細資訊，以及如何設定您的服務以適當地處理它們，請參閱 [有害訊息處理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="5c4fc-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c4fc-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c4fc-110">See also</span></span>

- [<span data-ttu-id="5c4fc-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="5c4fc-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="5c4fc-112">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="5c4fc-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="5c4fc-113">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="5c4fc-113">Administration and Diagnostics</span></span>](../index.md)
