---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46bc39237f0a6f0b9b25b9616782ec3e97fa22ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="216a7-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="216a7-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>
<span data-ttu-id="216a7-103">無法透過 HTTP 通道接收訊息。</span><span class="sxs-lookup"><span data-stu-id="216a7-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="216a7-104">描述</span><span class="sxs-lookup"><span data-stu-id="216a7-104">Description</span></span>  
 <span data-ttu-id="216a7-105">這個追蹤可以發出做為警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="216a7-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="216a7-106">在這兩種情況下，當找不到與傳入 HTTP 要求相容的接聽項，並且 HTTP 要求已捨棄時，就會發出追蹤。</span><span class="sxs-lookup"><span data-stu-id="216a7-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="216a7-107">之所以發生，是因為沒有任何 HTTP 接聽項辨識出要求的 HTTP 動詞，或者在要求的目標位址上沒有任何接聽項在接聽。</span><span class="sxs-lookup"><span data-stu-id="216a7-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="216a7-108">在自我裝載的案例中，會發出追蹤做為警告，而當服務裝載在 IIS 時，則會發出追蹤做為錯誤。</span><span class="sxs-lookup"><span data-stu-id="216a7-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="216a7-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="216a7-109">See Also</span></span>  
 [<span data-ttu-id="216a7-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="216a7-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="216a7-111">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="216a7-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="216a7-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="216a7-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
