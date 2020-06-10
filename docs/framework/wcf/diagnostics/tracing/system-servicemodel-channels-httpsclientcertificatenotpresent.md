---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 3e3bedca7a46f147ee3d9e143cea7e57095c99d1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602035"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="393d4-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="393d4-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="393d4-103">用戶端憑證是必要的。</span><span class="sxs-lookup"><span data-stu-id="393d4-103">Client certificate is required.</span></span> <span data-ttu-id="393d4-104">在要求中找不到憑證。</span><span class="sxs-lookup"><span data-stu-id="393d4-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="393d4-105">描述</span><span class="sxs-lookup"><span data-stu-id="393d4-105">Description</span></span>  
 <span data-ttu-id="393d4-106">這個追蹤表示 HTTPS 接聽項收到了與用戶端憑證沒有關聯的 HTTPS 要求。</span><span class="sxs-lookup"><span data-stu-id="393d4-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="393d4-107">由於接聽項已設定為在所有的 HTTPS 要求上都需要用戶端憑證，因此接聽項無法驗證用戶端的真實性。</span><span class="sxs-lookup"><span data-stu-id="393d4-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="393d4-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="393d4-108">See also</span></span>

- [<span data-ttu-id="393d4-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="393d4-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="393d4-110">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="393d4-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="393d4-111">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="393d4-111">Administration and Diagnostics</span></span>](../index.md)
