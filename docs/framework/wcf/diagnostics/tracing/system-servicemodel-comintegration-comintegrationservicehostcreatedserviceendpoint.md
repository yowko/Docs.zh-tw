---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: f89dd1373d67714046f8cb958582c3a5dea04456
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674782"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="8f7d7-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="8f7d7-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="8f7d7-103">無法移動或刪除訊息。</span><span class="sxs-lookup"><span data-stu-id="8f7d7-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8f7d7-104">描述</span><span class="sxs-lookup"><span data-stu-id="8f7d7-104">Description</span></span>  
 <span data-ttu-id="8f7d7-105">此追蹤表示嘗試移動、刪除或拒絕 MSMQ 訊息時，發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8f7d7-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="8f7d7-106">MSMQ 消息受雇于 Windows 通信基金會 （WCF）（當與 NetMmq 綁定或 Msmq 集成綁定一起使用時）。此跟蹤與 NetMmqBinding`ReceiveErrorHandling`或 Msmq集成綁定上屬性的選定值相關。</span><span class="sxs-lookup"><span data-stu-id="8f7d7-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="8f7d7-107">此追蹤不代表整體系統失敗。</span><span class="sxs-lookup"><span data-stu-id="8f7d7-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="8f7d7-108">但是，它代表某個訊息的選定有害訊息處置作業失敗。</span><span class="sxs-lookup"><span data-stu-id="8f7d7-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="8f7d7-109">有關消息何時成為病毒以及如何佈建服務以正確處理它們的詳細資訊，請參閱[毒消息處理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="8f7d7-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f7d7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f7d7-110">See also</span></span>

- [<span data-ttu-id="8f7d7-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="8f7d7-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="8f7d7-112">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="8f7d7-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8f7d7-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="8f7d7-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
