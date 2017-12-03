---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a9eb867826fbf1e4028f57e5118ff18d4329b23
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="1ad96-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="1ad96-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="1ad96-103">用戶端憑證是必要的。</span><span class="sxs-lookup"><span data-stu-id="1ad96-103">Client certificate is required.</span></span> <span data-ttu-id="1ad96-104">在要求中找不到憑證。</span><span class="sxs-lookup"><span data-stu-id="1ad96-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1ad96-105">描述</span><span class="sxs-lookup"><span data-stu-id="1ad96-105">Description</span></span>  
 <span data-ttu-id="1ad96-106">這個追蹤表示 HTTPS 接聽項收到了與用戶端憑證沒有關聯的 HTTPS 要求。</span><span class="sxs-lookup"><span data-stu-id="1ad96-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="1ad96-107">由於接聽項已設定為在所有的 HTTPS 要求上都需要用戶端憑證，因此接聽項無法驗證用戶端的真實性。</span><span class="sxs-lookup"><span data-stu-id="1ad96-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad96-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ad96-108">See Also</span></span>  
 [<span data-ttu-id="1ad96-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="1ad96-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1ad96-110">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="1ad96-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1ad96-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="1ad96-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
