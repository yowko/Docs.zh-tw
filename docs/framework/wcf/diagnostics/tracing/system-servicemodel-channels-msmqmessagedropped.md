---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 07bef8b391a03f2c011e1d1a7c7fb4fad908e022
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44067801"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="a5b72-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="a5b72-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="a5b72-103">MSMQ 已捨棄訊息。</span><span class="sxs-lookup"><span data-stu-id="a5b72-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a5b72-104">描述</span><span class="sxs-lookup"><span data-stu-id="a5b72-104">Description</span></span>  
 <span data-ttu-id="a5b72-105">此追蹤表示已捨棄 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="a5b72-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="a5b72-106">Windows Communication Foundation (WCF) （使用與 NetMsmqBinding 或 MsmqIntegrationBinding） 無法處理它們時，可以卸除 MSMQ 訊息。</span><span class="sxs-lookup"><span data-stu-id="a5b72-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="a5b72-107">這類訊息稱為有害訊息。</span><span class="sxs-lookup"><span data-stu-id="a5b72-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="a5b72-108">當 NetMsmqBinding 或 MsmqIntegrationBinding 上的 `ReceiveErrorHandling` 屬性設定為 `Drop` 時，就會捨棄有害訊息。</span><span class="sxs-lookup"><span data-stu-id="a5b72-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="a5b72-109">捨棄的訊息會從佇列中移除，無法再復原。</span><span class="sxs-lookup"><span data-stu-id="a5b72-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="a5b72-110">請參閱[有害訊息處理](https://go.microsoft.com/fwlink/?LinkID=99546)如需詳細資訊訊息何時變為有害，以及如何將服務設定為適當地處理它們。</span><span class="sxs-lookup"><span data-stu-id="a5b72-110">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b72-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5b72-111">See Also</span></span>  
 [<span data-ttu-id="a5b72-112">追蹤</span><span class="sxs-lookup"><span data-stu-id="a5b72-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a5b72-113">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="a5b72-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="a5b72-114">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="a5b72-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="a5b72-115">有害訊息處理</span><span class="sxs-lookup"><span data-stu-id="a5b72-115">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkID=99546)
