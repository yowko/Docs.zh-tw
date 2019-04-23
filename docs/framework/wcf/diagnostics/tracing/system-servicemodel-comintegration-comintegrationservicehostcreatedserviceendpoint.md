---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: d56bbf145c85902d8e5f1fd21f760633121da6da
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115280"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="e3438-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="e3438-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="e3438-103">無法移動或刪除訊息。</span><span class="sxs-lookup"><span data-stu-id="e3438-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e3438-104">描述</span><span class="sxs-lookup"><span data-stu-id="e3438-104">Description</span></span>  
 <span data-ttu-id="e3438-105">此追蹤表示嘗試移動、刪除或拒絕 MSMQ 訊息時，發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e3438-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="e3438-106">MSMQ 訊息會採用由 Windows Communication Foundation (WCF) （當使用 NetMsmqBinding 或 MsmqIntegrationBinding）。這個追蹤所選的值與相關`ReceiveErrorHandling`NetMsmqBinding 或 MsmqIntegrationBinding 上的屬性。</span><span class="sxs-lookup"><span data-stu-id="e3438-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="e3438-107">此追蹤不代表整體系統失敗。</span><span class="sxs-lookup"><span data-stu-id="e3438-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="e3438-108">但是，它代表某個訊息的選定有害訊息處置作業失敗。</span><span class="sxs-lookup"><span data-stu-id="e3438-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="e3438-109">請參閱[有害訊息處理](https://go.microsoft.com/fwlink/?LinkID=99546)如需詳細資訊訊息何時變為有害，以及如何將服務設定為適當地處理它們。</span><span class="sxs-lookup"><span data-stu-id="e3438-109">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3438-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3438-110">See also</span></span>

- [<span data-ttu-id="e3438-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="e3438-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="e3438-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="e3438-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e3438-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="e3438-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
