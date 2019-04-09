---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 15ae13563cfcfb3765559cafb2d31bd6482df7b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201178"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="b4be3-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="b4be3-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="b4be3-103">用戶端憑證是必要的。</span><span class="sxs-lookup"><span data-stu-id="b4be3-103">Client certificate is required.</span></span> <span data-ttu-id="b4be3-104">在要求中找不到憑證。</span><span class="sxs-lookup"><span data-stu-id="b4be3-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b4be3-105">描述</span><span class="sxs-lookup"><span data-stu-id="b4be3-105">Description</span></span>  
 <span data-ttu-id="b4be3-106">這個追蹤表示 HTTPS 接聽項收到了與用戶端憑證沒有關聯的 HTTPS 要求。</span><span class="sxs-lookup"><span data-stu-id="b4be3-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="b4be3-107">由於接聽項已設定為在所有的 HTTPS 要求上都需要用戶端憑證，因此接聽項無法驗證用戶端的真實性。</span><span class="sxs-lookup"><span data-stu-id="b4be3-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4be3-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4be3-108">See also</span></span>

- [<span data-ttu-id="b4be3-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="b4be3-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="b4be3-110">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="b4be3-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b4be3-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="b4be3-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
