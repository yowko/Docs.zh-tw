---
title: 常見的安全性案例
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: f36ebdb5ea248ec8134c688f89eb5d0be38dfe38
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579732"
---
# <a name="common-security-scenarios"></a><span data-ttu-id="ef6cd-102">常見的安全性案例</span><span class="sxs-lookup"><span data-stu-id="ef6cd-102">Common Security Scenarios</span></span>
<span data-ttu-id="ef6cd-103">本章節中的主題列出一些可能的用戶端和服務安全性組態。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-103">The topics in this section catalog a number of possible client and service security configurations.</span></span> <span data-ttu-id="ef6cd-104">組態會視一些因素而改變。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-104">Configurations vary according to a number of factors.</span></span> <span data-ttu-id="ef6cd-105">例如，服務或用戶端是否在內部網路，或安全性是由 Windows 或傳輸 (例如 HTTPS) 所提供。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-105">For example, whether a service or client is on an intranet, or whether the security is provided by Windows or transport (such as HTTPS).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef6cd-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="ef6cd-106">In This Section</span></span>  
 [<span data-ttu-id="ef6cd-107">沒有安全保障的網際網路用戶端與服務</span><span class="sxs-lookup"><span data-stu-id="ef6cd-107">Internet Unsecured Client and Service</span></span>](internet-unsecured-client-and-service.md)  
 <span data-ttu-id="ef6cd-108">公開、不安全的用戶端與服務範例。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-108">An example of a public, unsecured client and service.</span></span>  
  
 [<span data-ttu-id="ef6cd-109">沒有安全保障的內部網路用戶端與服務</span><span class="sxs-lookup"><span data-stu-id="ef6cd-109">Intranet Unsecured Client and Service</span></span>](intranet-unsecured-client-and-service.md)  
 <span data-ttu-id="ef6cd-110">已開發的基本 Windows Communication Foundation （WCF）服務，可提供安全的私人網路資訊給 WCF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-110">A basic Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span>  
  
 [<span data-ttu-id="ef6cd-111">使用基本驗證的傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="ef6cd-111">Transport Security with Basic Authentication</span></span>](transport-security-with-basic-authentication.md)  
 <span data-ttu-id="ef6cd-112">應用程式允許用戶端使用自訂驗證登入。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-112">The application allows clients to log on using custom authentication.</span></span>  
  
 [<span data-ttu-id="ef6cd-113">Windows 驗證的傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="ef6cd-113">Transport Security with Windows Authentication</span></span>](transport-security-with-windows-authentication.md)  
 <span data-ttu-id="ef6cd-114">顯示由 Windows 安全性保護的用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-114">Shows a client and service secured by Windows security.</span></span>  
  
 [<span data-ttu-id="ef6cd-115">匿名用戶端的傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="ef6cd-115">Transport Security with an Anonymous Client</span></span>](transport-security-with-an-anonymous-client.md)  
 <span data-ttu-id="ef6cd-116">這個案例會使用傳輸安全性 (例如 HTTPS) 來確保機密性和完整性。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-116">This scenario uses transport security (such as HTTPS) to ensure confidentiality and integrity.</span></span>  
  
 [<span data-ttu-id="ef6cd-117">使用憑證驗證的傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="ef6cd-117">Transport Security with Certificate Authentication</span></span>](transport-security-with-certificate-authentication.md)  
 <span data-ttu-id="ef6cd-118">顯示由憑證保護的用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-118">Shows a client and service secured by a certificate.</span></span>  
  
 [<span data-ttu-id="ef6cd-119">匿名用戶端的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="ef6cd-119">Message Security with an Anonymous Client</span></span>](message-security-with-an-anonymous-client.md)  
 <span data-ttu-id="ef6cd-120">顯示受 WCF 訊息安全性保護的用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-120">Shows a client and service secured by WCF message security.</span></span>  
  
 [<span data-ttu-id="ef6cd-121">使用者名稱用戶端的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="ef6cd-121">Message Security with a User Name Client</span></span>](message-security-with-a-user-name-client.md)  
 <span data-ttu-id="ef6cd-122">用戶端是 Windows Forms 應用程式，允許用戶端使用網域使用者名稱和密碼登入。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-122">The client is a Windows Forms application that allows clients to log on using a domain user name and password.</span></span>  
  
 [<span data-ttu-id="ef6cd-123">憑證用戶端的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="ef6cd-123">Message Security with a Certificate Client</span></span>](message-security-with-a-certificate-client.md)  
 <span data-ttu-id="ef6cd-124">伺服器有憑證，每一個用戶端也都有憑證。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-124">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="ef6cd-125">安全性內容是透過傳輸層安全性 (TLS) 交涉所建立。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-125">A security context is established through Transport Layer Security (TLS) negotiation.</span></span>  
  
 [<span data-ttu-id="ef6cd-126">Windows 用戶端的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="ef6cd-126">Message Security with a Windows Client</span></span>](message-security-with-a-windows-client.md)  
 <span data-ttu-id="ef6cd-127">憑證用戶端的驗證。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-127">A variation of the certificate client.</span></span> <span data-ttu-id="ef6cd-128">伺服器有憑證，每一個用戶端也都有憑證。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-128">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="ef6cd-129">安全性內容是透過 TLS 交涉所建立。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-129">A security context is established through TLS negotiation.</span></span>  
  
 [<span data-ttu-id="ef6cd-130">未使用認證交涉的 Windows 用戶端訊息安全性</span><span class="sxs-lookup"><span data-stu-id="ef6cd-130">Message Security with a Windows Client without Credential Negotiation</span></span>](message-security-with-a-windows-client-without-credential-negotiation.md)  
 <span data-ttu-id="ef6cd-131">顯示由 Kerberos 網域保護的用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-131">Shows a client and service secured by a Kerberos domain.</span></span>  
  
 [<span data-ttu-id="ef6cd-132">具有彼此憑證的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="ef6cd-132">Message Security with Mutual Certificates</span></span>](message-security-with-mutual-certificates.md)  
 <span data-ttu-id="ef6cd-133">伺服器有憑證，每一個用戶端也都有憑證。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-133">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="ef6cd-134">伺服器憑證隨應用程式散發，並可超出範圍提供。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-134">The server certificate is distributed with the application and is available out of band.</span></span>  
  
 [<span data-ttu-id="ef6cd-135">發行之權杖的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="ef6cd-135">Message Security with Issued Tokens</span></span>](message-security-with-issued-tokens.md)  
 <span data-ttu-id="ef6cd-136">聯合安全性，可在獨立網域之間建立信任關係。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-136">Federated security that enables the establishment of trust between independent domains.</span></span>  
  
 [<span data-ttu-id="ef6cd-137">受信任的子系統</span><span class="sxs-lookup"><span data-stu-id="ef6cd-137">Trusted Subsystem</span></span>](trusted-subsystem.md)  
 <span data-ttu-id="ef6cd-138">用戶端會存取分散在網路上的一或多個 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-138">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="ef6cd-139">Web 服務會存取必須受到保護的其他資源 (例如，資料庫或其他 Web 服務)。</span><span class="sxs-lookup"><span data-stu-id="ef6cd-139">The Web services access additional resources (such as databases or other Web services) that must be secured.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ef6cd-140">參考</span><span class="sxs-lookup"><span data-stu-id="ef6cd-140">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="ef6cd-141">相關章節</span><span class="sxs-lookup"><span data-stu-id="ef6cd-141">Related Sections</span></span>  
 [<span data-ttu-id="ef6cd-142">授權</span><span class="sxs-lookup"><span data-stu-id="ef6cd-142">Authorization</span></span>](authorization-in-wcf.md)  
  
 [<span data-ttu-id="ef6cd-143">安全性總覽</span><span class="sxs-lookup"><span data-stu-id="ef6cd-143">Security Overview</span></span>](security-overview.md)  
  
 [<span data-ttu-id="ef6cd-144">安全性</span><span class="sxs-lookup"><span data-stu-id="ef6cd-144">Security</span></span>](security.md)  
  
 [<span data-ttu-id="ef6cd-145">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="ef6cd-145">Bindings and Security</span></span>](bindings-and-security.md)  
  
 [<span data-ttu-id="ef6cd-146">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="ef6cd-146">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
 [<span data-ttu-id="ef6cd-147">驗證</span><span class="sxs-lookup"><span data-stu-id="ef6cd-147">Authentication</span></span>](authentication-in-wcf.md)  
  
 [<span data-ttu-id="ef6cd-148">授權</span><span class="sxs-lookup"><span data-stu-id="ef6cd-148">Authorization</span></span>](authorization-in-wcf.md)  
  
 [<span data-ttu-id="ef6cd-149">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="ef6cd-149">Federation and Issued Tokens</span></span>](federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="ef6cd-150">稽核</span><span class="sxs-lookup"><span data-stu-id="ef6cd-150">Auditing</span></span>](auditing-security-events.md)  
  
## <a name="see-also"></a><span data-ttu-id="ef6cd-151">請參閱</span><span class="sxs-lookup"><span data-stu-id="ef6cd-151">See also</span></span>

- [<span data-ttu-id="ef6cd-152">安全性指引與最佳做法</span><span class="sxs-lookup"><span data-stu-id="ef6cd-152">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)
- <span data-ttu-id="ef6cd-153">[Windows Server AppFabric 的資訊安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ef6cd-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
