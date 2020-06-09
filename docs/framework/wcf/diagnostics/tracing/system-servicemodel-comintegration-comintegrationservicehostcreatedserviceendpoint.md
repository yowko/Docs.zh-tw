---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 8b81cdcaf74aca044260495867b2c4f1de517682
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593746"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="876fa-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="876fa-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="876fa-103">無法移動或刪除訊息。</span><span class="sxs-lookup"><span data-stu-id="876fa-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="876fa-104">描述</span><span class="sxs-lookup"><span data-stu-id="876fa-104">Description</span></span>  
 <span data-ttu-id="876fa-105">此追蹤表示嘗試移動、刪除或拒絕 MSMQ 訊息時，發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="876fa-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="876fa-106">MSMQ 訊息是由 Windows Communication Foundation （WCF）（搭配 NetMsmqBinding 或 MsmqIntegrationBinding 使用時）所採用。此追蹤與 `ReceiveErrorHandling` NetMsmqBinding 或 MsmqIntegrationBinding 上的屬性所選擇的值有關。</span><span class="sxs-lookup"><span data-stu-id="876fa-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="876fa-107">此追蹤不代表整體系統失敗。</span><span class="sxs-lookup"><span data-stu-id="876fa-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="876fa-108">但是，它代表某個訊息的選定有害訊息處置作業失敗。</span><span class="sxs-lookup"><span data-stu-id="876fa-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="876fa-109">如需訊息何時會變成有害的詳細資訊，以及如何設定您的服務來適當地處理它們，請參閱[有害訊息處理](../../feature-details/poison-message-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="876fa-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="876fa-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="876fa-110">See also</span></span>

- [<span data-ttu-id="876fa-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="876fa-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="876fa-112">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="876fa-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="876fa-113">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="876fa-113">Administration and Diagnostics</span></span>](../index.md)
