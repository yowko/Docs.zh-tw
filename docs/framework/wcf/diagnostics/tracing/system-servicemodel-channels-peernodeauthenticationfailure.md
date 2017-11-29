---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b09d7fc476d5eed7f7c534fdde46cb18eeac30d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="7aab9-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="7aab9-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="7aab9-103">與未來芳鄰的安全性交換失敗。</span><span class="sxs-lookup"><span data-stu-id="7aab9-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7aab9-104">描述</span><span class="sxs-lookup"><span data-stu-id="7aab9-104">Description</span></span>  
 <span data-ttu-id="7aab9-105">在嘗試建立安全的芳鄰連線時，發生這個追蹤。</span><span class="sxs-lookup"><span data-stu-id="7aab9-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="7aab9-106">這可能是因為認證不足或不正確而導致。</span><span class="sxs-lookup"><span data-stu-id="7aab9-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="7aab9-107">PeerChannel 會辨認嚴密識別 (X.509 憑證) 的單一權杖類型，它會根據能夠實作的驗證與授權類型，提供嚴密的識別模型。</span><span class="sxs-lookup"><span data-stu-id="7aab9-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="7aab9-108">PeerChannel 也會透過使用密碼的方式提供簡單應用程式的支援。</span><span class="sxs-lookup"><span data-stu-id="7aab9-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="7aab9-109">密碼只能用來允許進入工作階段；而不能用來執行訊息驗證。</span><span class="sxs-lookup"><span data-stu-id="7aab9-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="7aab9-110">這是因為對等群組共享的對稱式權杖，如果使用在來源驗證方面會發生困難而且不適當。</span><span class="sxs-lookup"><span data-stu-id="7aab9-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="7aab9-111">疑難排解</span><span class="sxs-lookup"><span data-stu-id="7aab9-111">Troubleshooting</span></span>  
 <span data-ttu-id="7aab9-112">請確認所有芳鄰都有適當的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="7aab9-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aab9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7aab9-113">See Also</span></span>  
 [<span data-ttu-id="7aab9-114">對等通道安全性</span><span class="sxs-lookup"><span data-stu-id="7aab9-114">Peer Channel Security</span></span>](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [<span data-ttu-id="7aab9-115">追蹤</span><span class="sxs-lookup"><span data-stu-id="7aab9-115">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="7aab9-116">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="7aab9-116">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="7aab9-117">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="7aab9-117">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
