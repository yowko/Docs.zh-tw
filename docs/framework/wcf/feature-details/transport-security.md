---
title: 傳輸安全性
description: 使用這些參考來瞭解 WFC 中的傳輸安全性機制、它們的實執行方式，以及它們的選項。
ms.date: 03/30/2017
ms.assetid: 86c94153-e48d-4539-b6cf-cd8060582e7f
ms.openlocfilehash: d39aa49906b79b9e12eecf04629080863719f986
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244747"
---
# <a name="transport-security"></a><span data-ttu-id="caf12-103">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="caf12-103">Transport Security</span></span>
<span data-ttu-id="caf12-104">Windows Communication Foundation （WCF）中的傳輸安全性取決於選取的系結。</span><span class="sxs-lookup"><span data-stu-id="caf12-104">Transport security in Windows Communication Foundation (WCF) depends on the binding selected.</span></span> <span data-ttu-id="caf12-105">繫結所實作的傳輸將決定實際的安全性機制。</span><span class="sxs-lookup"><span data-stu-id="caf12-105">The transport that the binding implements determines the actual security mechanism.</span></span> <span data-ttu-id="caf12-106">本章節中的主題說明所實作的機制及其選項。</span><span class="sxs-lookup"><span data-stu-id="caf12-106">The topics in this section explain the mechanisms that are implemented and their options.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="caf12-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="caf12-107">In This Section</span></span>  
 [<span data-ttu-id="caf12-108">傳輸安全性概觀</span><span class="sxs-lookup"><span data-stu-id="caf12-108">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="caf12-109">說明 WCF 中傳輸安全性的基本概念。</span><span class="sxs-lookup"><span data-stu-id="caf12-109">Explains the basics of transport security in WCF.</span></span>  
  
 [<span data-ttu-id="caf12-110">HTTP 傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="caf12-110">HTTP Transport Security</span></span>](http-transport-security.md)  
 <span data-ttu-id="caf12-111">說明 WCF 如何實行安全通訊端層（SSL 或 HTTPS）。</span><span class="sxs-lookup"><span data-stu-id="caf12-111">Explains how WCF implements Secure Sockets Layer (SSL, or HTTPS).</span></span>  
  
 [<span data-ttu-id="caf12-112">了解 HTTP 驗證</span><span class="sxs-lookup"><span data-stu-id="caf12-112">Understanding HTTP Authentication</span></span>](understanding-http-authentication.md)  
 <span data-ttu-id="caf12-113">說明 HTTP 驗證配置，例如基本、摘要、NT LAN Manager (NTLM) 以及其他等等。</span><span class="sxs-lookup"><span data-stu-id="caf12-113">Describes HTTP authentication schemes, such as Basic, Digest, NT LAN Manager (NTLM), and others.</span></span>  
  
 [<span data-ttu-id="caf12-114">使用模擬搭配傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="caf12-114">Using Impersonation with Transport Security</span></span>](using-impersonation-with-transport-security.md)  
 <span data-ttu-id="caf12-115">說明傳輸安全性模式可能搭配的五種模擬層級。</span><span class="sxs-lookup"><span data-stu-id="caf12-115">Explains the five levels of impersonation that are possible with transport security mode.</span></span>  
  
 [<span data-ttu-id="caf12-116">如何：使用 SSL 憑證設定連接埠</span><span class="sxs-lookup"><span data-stu-id="caf12-116">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)  
 <span data-ttu-id="caf12-117">逐步說明使用 X.509 憑證在電腦上設定連接埠以獲得 SSL (傳輸) 安全性的基本概念。</span><span class="sxs-lookup"><span data-stu-id="caf12-117">Walks through the basics of configuring a port on a machine with an X.509 certificate for SSL (transport) security.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="caf12-118">參考</span><span class="sxs-lookup"><span data-stu-id="caf12-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="caf12-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="caf12-119">Related Sections</span></span>  
 [<span data-ttu-id="caf12-120">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="caf12-120">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="caf12-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caf12-121">See also</span></span>

- [<span data-ttu-id="caf12-122">WCF 安全性程式設計</span><span class="sxs-lookup"><span data-stu-id="caf12-122">Programming WCF Security</span></span>](programming-wcf-security.md)
