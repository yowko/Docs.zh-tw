---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 0ca3d198ce225221348ac7b405ea91ad215cd298
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61950640"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="aab37-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="aab37-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="aab37-103">訊息的傳入接收速率太高。</span><span class="sxs-lookup"><span data-stu-id="aab37-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="aab37-104">描述</span><span class="sxs-lookup"><span data-stu-id="aab37-104">Description</span></span>  
 <span data-ttu-id="aab37-105">這個追蹤會發生在嘗試處理傳入訊息時。</span><span class="sxs-lookup"><span data-stu-id="aab37-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="aab37-106">訊息無法轉送到特定的芳鄰，因為已超過該芳鄰的配額設定。</span><span class="sxs-lookup"><span data-stu-id="aab37-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="aab37-107">這發生在沒有回應的芳鄰無法清除該芳鄰之擱置訊息的待辦項目。</span><span class="sxs-lookup"><span data-stu-id="aab37-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="aab37-108">疑難排解</span><span class="sxs-lookup"><span data-stu-id="aab37-108">Troubleshooting</span></span>  
 <span data-ttu-id="aab37-109">降低訊息在 mesh 內傳送的速率。</span><span class="sxs-lookup"><span data-stu-id="aab37-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aab37-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aab37-110">See also</span></span>

- [<span data-ttu-id="aab37-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="aab37-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="aab37-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="aab37-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="aab37-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="aab37-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
