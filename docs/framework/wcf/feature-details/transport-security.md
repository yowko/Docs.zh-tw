---
title: "傳輸安全性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86c94153-e48d-4539-b6cf-cd8060582e7f
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 364326e2ded11f7174adc891a5fd9bcdd3c98334
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="transport-security"></a><span data-ttu-id="08003-102">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="08003-102">Transport Security</span></span>
<span data-ttu-id="08003-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的傳輸安全性取決於選取的繫結。</span><span class="sxs-lookup"><span data-stu-id="08003-103">Transport security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] depends on the binding selected.</span></span> <span data-ttu-id="08003-104">繫結所實作的傳輸將決定實際的安全性機制。</span><span class="sxs-lookup"><span data-stu-id="08003-104">The transport that the binding implements determines the actual security mechanism.</span></span> <span data-ttu-id="08003-105">本章節中的主題說明所實作的機制及其選項。</span><span class="sxs-lookup"><span data-stu-id="08003-105">The topics in this section explain the mechanisms that are implemented and their options.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08003-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="08003-106">In This Section</span></span>  
 [<span data-ttu-id="08003-107">傳輸安全性概觀</span><span class="sxs-lookup"><span data-stu-id="08003-107">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="08003-108">說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的傳輸安全性基本概念。</span><span class="sxs-lookup"><span data-stu-id="08003-108">Explains the basics of transport security in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="08003-109">HTTP 傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="08003-109">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)  
 <span data-ttu-id="08003-110">說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 如何實作 Secure Sockets Layer (SSL，或 HTTPS)。</span><span class="sxs-lookup"><span data-stu-id="08003-110">Explains how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implements Secure Sockets Layer (SSL, or HTTPS).</span></span>  
  
 [<span data-ttu-id="08003-111">了解 HTTP 驗證</span><span class="sxs-lookup"><span data-stu-id="08003-111">Understanding HTTP Authentication</span></span>](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)  
 <span data-ttu-id="08003-112">說明 HTTP 驗證配置，例如基本、摘要、NT LAN Manager (NTLM) 以及其他等等。</span><span class="sxs-lookup"><span data-stu-id="08003-112">Describes HTTP authentication schemes, such as Basic, Digest, NT LAN Manager (NTLM), and others.</span></span>  
  
 [<span data-ttu-id="08003-113">使用模擬搭配傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="08003-113">Using Impersonation with Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 <span data-ttu-id="08003-114">說明傳輸安全性模式可能搭配的五種模擬層級。</span><span class="sxs-lookup"><span data-stu-id="08003-114">Explains the five levels of impersonation that are possible with transport security mode.</span></span>  
  
 [<span data-ttu-id="08003-115">如何：使用 SSL 憑證設定連接埠</span><span class="sxs-lookup"><span data-stu-id="08003-115">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 <span data-ttu-id="08003-116">逐步說明使用 X.509 憑證在電腦上設定連接埠以獲得 SSL (傳輸) 安全性的基本概念。</span><span class="sxs-lookup"><span data-stu-id="08003-116">Walks through the basics of configuring a port on a machine with an X.509 certificate for SSL (transport) security.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="08003-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="08003-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="08003-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="08003-118">Related Sections</span></span>  
 [<span data-ttu-id="08003-119">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="08003-119">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="08003-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="08003-120">See Also</span></span>  
 [<span data-ttu-id="08003-121">WCF 安全性程式設計</span><span class="sxs-lookup"><span data-stu-id="08003-121">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
