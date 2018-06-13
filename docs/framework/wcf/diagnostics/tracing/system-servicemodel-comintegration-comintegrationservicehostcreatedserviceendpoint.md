---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 0a28eec659b48d5add4c53bc8c16972892e65099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487902"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="08ffa-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="08ffa-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="08ffa-103">無法移動或刪除訊息。</span><span class="sxs-lookup"><span data-stu-id="08ffa-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="08ffa-104">描述</span><span class="sxs-lookup"><span data-stu-id="08ffa-104">Description</span></span>  
 <span data-ttu-id="08ffa-105">此追蹤表示嘗試移動、刪除或拒絕 MSMQ 訊息時，發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="08ffa-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="08ffa-106">MSMQ 訊息被採用由 Windows Communication Foundation (WCF) （與 NetMsmqBinding 或 msmqintegrationbinding 配合使用） 時。這個追蹤所選擇的值與相關`ReceiveErrorHandling`NetMsmqBinding 或 MsmqIntegrationBinding 上的屬性。</span><span class="sxs-lookup"><span data-stu-id="08ffa-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="08ffa-107">此追蹤不代表整體系統失敗。</span><span class="sxs-lookup"><span data-stu-id="08ffa-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="08ffa-108">但是，它代表某個訊息的選定有害訊息處置作業失敗。</span><span class="sxs-lookup"><span data-stu-id="08ffa-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="08ffa-109">請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546)如需詳細資訊訊息何時變為有害，以及設定您的服務來適當處理這些。</span><span class="sxs-lookup"><span data-stu-id="08ffa-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ffa-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08ffa-110">See Also</span></span>  
 [<span data-ttu-id="08ffa-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="08ffa-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="08ffa-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="08ffa-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="08ffa-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="08ffa-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
