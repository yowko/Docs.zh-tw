---
title: "安全性通訊協定 1.0 版"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f40c79ad1a6eedc2b1de4dffa9de5b48aeb8e6f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="1acd5-102">安全性通訊協定 1.0 版</span><span class="sxs-lookup"><span data-stu-id="1acd5-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="1acd5-103">Web 服務安全性通訊協定提供 Web 服務安全性機制，涵蓋所有現有的企業訊息安全性需求。</span><span class="sxs-lookup"><span data-stu-id="1acd5-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="1acd5-104">本章節描述下列 Web 服務安全性通訊協定的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 1.0 版詳細資料 (在 <xref:System.ServiceModel.Channels.SecurityBindingElement> 中實作)。</span><span class="sxs-lookup"><span data-stu-id="1acd5-104">This section describes the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="1acd5-105">規格/文件</span><span class="sxs-lookup"><span data-stu-id="1acd5-105">Specification/Document</span></span>|<span data-ttu-id="1acd5-106">連結</span><span class="sxs-lookup"><span data-stu-id="1acd5-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="1acd5-107">WSS：SOAP 訊息安全性 1.0</span><span class="sxs-lookup"><span data-stu-id="1acd5-107">WSS: SOAP Message Security 1.0</span></span>|<span data-ttu-id="1acd5-108">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="1acd5-108">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf</span></span>|  
|<span data-ttu-id="1acd5-109">WSS：使用者名稱權杖設定檔 1.0</span><span class="sxs-lookup"><span data-stu-id="1acd5-109">WSS: Username Token Profile 1.0</span></span>|<span data-ttu-id="1acd5-110">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="1acd5-110">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="1acd5-111">WSS：X509 權杖設定檔 1.0</span><span class="sxs-lookup"><span data-stu-id="1acd5-111">WSS: X509 Token Profile 1.0</span></span>|<span data-ttu-id="1acd5-112">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="1acd5-112">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="1acd5-113">WSS：SAML 1.1 權杖設定檔 1.0</span><span class="sxs-lookup"><span data-stu-id="1acd5-113">WSS: SAML 1.1 Token Profile 1.0</span></span>|<span data-ttu-id="1acd5-114">http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="1acd5-114">http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="1acd5-115">WSS：SOAP 訊息安全性 1.1</span><span class="sxs-lookup"><span data-stu-id="1acd5-115">WSS: SOAP Message Security 1.1</span></span>|<span data-ttu-id="1acd5-116">http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf</span><span class="sxs-lookup"><span data-stu-id="1acd5-116">http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf</span></span>|  
|<span data-ttu-id="1acd5-117">WSS：使用者名稱權杖設定檔 1.1</span><span class="sxs-lookup"><span data-stu-id="1acd5-117">WSS Username Token Profile 1.1</span></span>|<span data-ttu-id="1acd5-118">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="1acd5-118">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="1acd5-119">WSS：X.509 權杖設定檔 1.1</span><span class="sxs-lookup"><span data-stu-id="1acd5-119">WSS: X.509 Token Profile 1.1</span></span>|<span data-ttu-id="1acd5-120">http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf</span><span class="sxs-lookup"><span data-stu-id="1acd5-120">http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf</span></span>|  
|<span data-ttu-id="1acd5-121">WSS：Kerberos 權杖設定檔 1.1</span><span class="sxs-lookup"><span data-stu-id="1acd5-121">WSS: Kerberos Token Profile 1.1</span></span>|<span data-ttu-id="1acd5-122">http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf</span><span class="sxs-lookup"><span data-stu-id="1acd5-122">http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf</span></span>|  
|<span data-ttu-id="1acd5-123">WSS：SAML 1.1 權杖設定檔 1.1</span><span class="sxs-lookup"><span data-stu-id="1acd5-123">WSS: SAML 1.1 Token Profile 1.1</span></span>|<span data-ttu-id="1acd5-124">http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf</span><span class="sxs-lookup"><span data-stu-id="1acd5-124">http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf</span></span>|  
|<span data-ttu-id="1acd5-125">WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="1acd5-125">WS-Secure Conversation</span></span>|<span data-ttu-id="1acd5-126">http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/</span><span class="sxs-lookup"><span data-stu-id="1acd5-126">http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/</span></span>|  
|<span data-ttu-id="1acd5-127">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="1acd5-127">WS-Trust</span></span>|<span data-ttu-id="1acd5-128">http://msdn.microsoft.com/ws/2005/02/ws-trust/</span><span class="sxs-lookup"><span data-stu-id="1acd5-128">http://msdn.microsoft.com/ws/2005/02/ws-trust/</span></span>|  
|<span data-ttu-id="1acd5-129">應用程式注意事項：</span><span class="sxs-lookup"><span data-stu-id="1acd5-129">Application Note:</span></span><br /><br /> <span data-ttu-id="1acd5-130">使用 WS-Trust 進行 TLS 信號交換</span><span class="sxs-lookup"><span data-stu-id="1acd5-130">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="1acd5-131">即將發行</span><span class="sxs-lookup"><span data-stu-id="1acd5-131">To be published</span></span>|  
|<span data-ttu-id="1acd5-132">應用程式注意事項：</span><span class="sxs-lookup"><span data-stu-id="1acd5-132">Application Note:</span></span><br /><br /> <span data-ttu-id="1acd5-133">使用 WS-Trust 進行 SPNEGO</span><span class="sxs-lookup"><span data-stu-id="1acd5-133">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="1acd5-134">即將發行</span><span class="sxs-lookup"><span data-stu-id="1acd5-134">To be published</span></span>|  
|<span data-ttu-id="1acd5-135">應用程式注意事項：</span><span class="sxs-lookup"><span data-stu-id="1acd5-135">Application Note:</span></span><br /><br /> <span data-ttu-id="1acd5-136">Web 服務定址端點參考和識別</span><span class="sxs-lookup"><span data-stu-id="1acd5-136">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="1acd5-137">即將發行</span><span class="sxs-lookup"><span data-stu-id="1acd5-137">To be published</span></span>|  
|<span data-ttu-id="1acd5-138">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="1acd5-138">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="1acd5-139">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="1acd5-139">(2005/07)</span></span>|<span data-ttu-id="1acd5-140">http://msdn.microsoft.com/ws/2005/07/ws-security-policy/</span><span class="sxs-lookup"><span data-stu-id="1acd5-140">http://msdn.microsoft.com/ws/2005/07/ws-security-policy/</span></span><br /><br /> <span data-ttu-id="1acd5-141">已使用提交至 OASIS WS-SX 技術委員會 (http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html) 的勘誤表修訂</span><span class="sxs-lookup"><span data-stu-id="1acd5-141">as amended by errata submitted to OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span></span>|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-142"> 第 1 版提供了 17 個可做為 Web 服務安全性組態基礎的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="1acd5-142">, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="1acd5-143">每個模式都已針對一組通用的部署需求最佳化，例如：</span><span class="sxs-lookup"><span data-stu-id="1acd5-143">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
-   <span data-ttu-id="1acd5-144">用來驗證用戶端和服務的認證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-144">Credentials used to authenticate client and service.</span></span>  
  
-   <span data-ttu-id="1acd5-145">訊息或傳輸安全性保護機制。</span><span class="sxs-lookup"><span data-stu-id="1acd5-145">Message or transport security protection mechanisms.</span></span>  
  
-   <span data-ttu-id="1acd5-146">訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="1acd5-146">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="1acd5-147">驗證模式</span><span class="sxs-lookup"><span data-stu-id="1acd5-147">Authentication Mode</span></span>|<span data-ttu-id="1acd5-148">用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="1acd5-148">Client Authentication</span></span>|<span data-ttu-id="1acd5-149">伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="1acd5-149">Server Authentication</span></span>|<span data-ttu-id="1acd5-150">模式</span><span class="sxs-lookup"><span data-stu-id="1acd5-150">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="1acd5-151">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="1acd5-151">UserNameOverTransport</span></span>|<span data-ttu-id="1acd5-152">使用者名稱/密碼</span><span class="sxs-lookup"><span data-stu-id="1acd5-152">User name/password</span></span>|<span data-ttu-id="1acd5-153">X509</span><span class="sxs-lookup"><span data-stu-id="1acd5-153">X509</span></span>|<span data-ttu-id="1acd5-154">Transport</span><span class="sxs-lookup"><span data-stu-id="1acd5-154">Transport</span></span>|  
|<span data-ttu-id="1acd5-155">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="1acd5-155">CertificateOverTransport</span></span>|<span data-ttu-id="1acd5-156">X509</span><span class="sxs-lookup"><span data-stu-id="1acd5-156">X509</span></span>|<span data-ttu-id="1acd5-157">X509</span><span class="sxs-lookup"><span data-stu-id="1acd5-157">X509</span></span>|<span data-ttu-id="1acd5-158">Transport</span><span class="sxs-lookup"><span data-stu-id="1acd5-158">Transport</span></span>|  
|<span data-ttu-id="1acd5-159">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="1acd5-159">KerberosOverTransport</span></span>|<span data-ttu-id="1acd5-160">Windows</span><span class="sxs-lookup"><span data-stu-id="1acd5-160">Windows</span></span>|<span data-ttu-id="1acd5-161">X509</span><span class="sxs-lookup"><span data-stu-id="1acd5-161">X509</span></span>|<span data-ttu-id="1acd5-162">Transport</span><span class="sxs-lookup"><span data-stu-id="1acd5-162">Transport</span></span>|  
|<span data-ttu-id="1acd5-163">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="1acd5-163">IssuedTokenOverTransport</span></span>|<span data-ttu-id="1acd5-164">聯合</span><span class="sxs-lookup"><span data-stu-id="1acd5-164">Federated</span></span>|<span data-ttu-id="1acd5-165">X509</span><span class="sxs-lookup"><span data-stu-id="1acd5-165">X509</span></span>|<span data-ttu-id="1acd5-166">Transport</span><span class="sxs-lookup"><span data-stu-id="1acd5-166">Transport</span></span>|  
|<span data-ttu-id="1acd5-167">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="1acd5-167">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="1acd5-168">交涉的 Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="1acd5-168">Windows Sspi Negotiated</span></span>|<span data-ttu-id="1acd5-169">交涉的 Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="1acd5-169">Windows Sspi Negotiated</span></span>|<span data-ttu-id="1acd5-170">Transport</span><span class="sxs-lookup"><span data-stu-id="1acd5-170">Transport</span></span>|  
|<span data-ttu-id="1acd5-171">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="1acd5-171">AnonymousForCertificate</span></span>|<span data-ttu-id="1acd5-172">無</span><span class="sxs-lookup"><span data-stu-id="1acd5-172">None</span></span>|<span data-ttu-id="1acd5-173">X509</span><span class="sxs-lookup"><span data-stu-id="1acd5-173">X509</span></span>|<span data-ttu-id="1acd5-174">訊息</span><span class="sxs-lookup"><span data-stu-id="1acd5-174">Message</span></span>|  
|<span data-ttu-id="1acd5-175">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="1acd5-175">UserNameForCertificate</span></span>|<span data-ttu-id="1acd5-176">使用者名稱/密碼</span><span class="sxs-lookup"><span data-stu-id="1acd5-176">User name/password</span></span>|<span data-ttu-id="1acd5-177">X509</span><span class="sxs-lookup"><span data-stu-id="1acd5-177">X509</span></span>|<span data-ttu-id="1acd5-178">訊息</span><span class="sxs-lookup"><span data-stu-id="1acd5-178">Message</span></span>|  
|<span data-ttu-id="1acd5-179">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="1acd5-179">MutualCertificate</span></span>|<span data-ttu-id="1acd5-180">X509</span><span class="sxs-lookup"><span data-stu-id="1acd5-180">X509</span></span>|<span data-ttu-id="1acd5-181">X509</span><span class="sxs-lookup"><span data-stu-id="1acd5-181">X509</span></span>|<span data-ttu-id="1acd5-182">訊息</span><span class="sxs-lookup"><span data-stu-id="1acd5-182">Message</span></span>|  
|<span data-ttu-id="1acd5-183">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="1acd5-183">MutualCertificateDuplex</span></span>|<span data-ttu-id="1acd5-184">X509</span><span class="sxs-lookup"><span data-stu-id="1acd5-184">X509</span></span>|<span data-ttu-id="1acd5-185">X509</span><span class="sxs-lookup"><span data-stu-id="1acd5-185">X509</span></span>|<span data-ttu-id="1acd5-186">訊息</span><span class="sxs-lookup"><span data-stu-id="1acd5-186">Message</span></span>|  
|<span data-ttu-id="1acd5-187">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="1acd5-187">IssuedTokenForCertificate</span></span>|<span data-ttu-id="1acd5-188">聯合</span><span class="sxs-lookup"><span data-stu-id="1acd5-188">Federated</span></span>|<span data-ttu-id="1acd5-189">X509</span><span class="sxs-lookup"><span data-stu-id="1acd5-189">X509</span></span>|<span data-ttu-id="1acd5-190">訊息</span><span class="sxs-lookup"><span data-stu-id="1acd5-190">Message</span></span>|  
|<span data-ttu-id="1acd5-191">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1acd5-191">Kerberos</span></span>|<span data-ttu-id="1acd5-192">Windows</span><span class="sxs-lookup"><span data-stu-id="1acd5-192">Windows</span></span>|<span data-ttu-id="1acd5-193">Windows</span><span class="sxs-lookup"><span data-stu-id="1acd5-193">Windows</span></span>|<span data-ttu-id="1acd5-194">訊息</span><span class="sxs-lookup"><span data-stu-id="1acd5-194">Message</span></span>|  
|<span data-ttu-id="1acd5-195">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="1acd5-195">IssuedToken</span></span>|<span data-ttu-id="1acd5-196">聯合</span><span class="sxs-lookup"><span data-stu-id="1acd5-196">Federated</span></span>|<span data-ttu-id="1acd5-197">聯合</span><span class="sxs-lookup"><span data-stu-id="1acd5-197">Federated</span></span>|<span data-ttu-id="1acd5-198">訊息</span><span class="sxs-lookup"><span data-stu-id="1acd5-198">Message</span></span>|  
|<span data-ttu-id="1acd5-199">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="1acd5-199">SspiNegotiated</span></span>|<span data-ttu-id="1acd5-200">交涉的 Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="1acd5-200">Windows Sspi Negotiated</span></span>|<span data-ttu-id="1acd5-201">交涉的 Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="1acd5-201">Windows Sspi Negotiated</span></span>|<span data-ttu-id="1acd5-202">訊息</span><span class="sxs-lookup"><span data-stu-id="1acd5-202">Message</span></span>|  
|<span data-ttu-id="1acd5-203">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="1acd5-203">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="1acd5-204">無</span><span class="sxs-lookup"><span data-stu-id="1acd5-204">None</span></span>|<span data-ttu-id="1acd5-205">X509、TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="1acd5-205">X509, TLS-Nego</span></span>|<span data-ttu-id="1acd5-206">訊息</span><span class="sxs-lookup"><span data-stu-id="1acd5-206">Message</span></span>|  
|<span data-ttu-id="1acd5-207">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="1acd5-207">UserNameForSslNegotiated</span></span>|<span data-ttu-id="1acd5-208">使用者名稱/密碼</span><span class="sxs-lookup"><span data-stu-id="1acd5-208">User name/password</span></span>|<span data-ttu-id="1acd5-209">X509、TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="1acd5-209">X509, TLS-Nego</span></span>|<span data-ttu-id="1acd5-210">訊息</span><span class="sxs-lookup"><span data-stu-id="1acd5-210">Message</span></span>|  
|<span data-ttu-id="1acd5-211">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="1acd5-211">MutualSslNegotiated</span></span>|<span data-ttu-id="1acd5-212">X509</span><span class="sxs-lookup"><span data-stu-id="1acd5-212">X509</span></span>|<span data-ttu-id="1acd5-213">X509、TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="1acd5-213">X509, TLS-Nego</span></span>|<span data-ttu-id="1acd5-214">訊息</span><span class="sxs-lookup"><span data-stu-id="1acd5-214">Message</span></span>|  
|<span data-ttu-id="1acd5-215">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="1acd5-215">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="1acd5-216">聯合</span><span class="sxs-lookup"><span data-stu-id="1acd5-216">Federated</span></span>|<span data-ttu-id="1acd5-217">X509、TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="1acd5-217">X509, TLS-Nego</span></span>|<span data-ttu-id="1acd5-218">訊息</span><span class="sxs-lookup"><span data-stu-id="1acd5-218">Message</span></span>|  
  
 <span data-ttu-id="1acd5-219">使用這類驗證模式的端點可以使用 WS-SecurityPolicy (WS-SP) 來表示安全性需求。</span><span class="sxs-lookup"><span data-stu-id="1acd5-219">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="1acd5-220">本文件針對每個驗證模式描述安全性標頭和基礎結構訊息的結構，並提供原則和訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="1acd5-220">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-221"> 運用 WS-SecureConversation 提供安全工作階段支援，以保護應用程式間的多訊息交換。</span><span class="sxs-lookup"><span data-stu-id="1acd5-221"> leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="1acd5-222">如需實作的詳細資訊，請參閱下面的「安全工作階段」。</span><span class="sxs-lookup"><span data-stu-id="1acd5-222">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="1acd5-223">除了驗證模式之外，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 還提供設定來控制可套用至大部分訊息安全性驗證模式的通用保護機制，例如簽章和加密作業順序、演算法組合、金鑰衍生和簽章確認。</span><span class="sxs-lookup"><span data-stu-id="1acd5-223">In addition to authentication modes, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="1acd5-224">下列是本文件中使用的前置詞和命名空間。</span><span class="sxs-lookup"><span data-stu-id="1acd5-224">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="1acd5-225">前置詞</span><span class="sxs-lookup"><span data-stu-id="1acd5-225">Prefix</span></span>|<span data-ttu-id="1acd5-226">命名空間</span><span class="sxs-lookup"><span data-stu-id="1acd5-226">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="1acd5-227">s</span><span class="sxs-lookup"><span data-stu-id="1acd5-227">s</span></span>|<span data-ttu-id="1acd5-228">http://www.w3.org/2003/05/soap-envelope</span><span class="sxs-lookup"><span data-stu-id="1acd5-228">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="1acd5-229">sp</span><span class="sxs-lookup"><span data-stu-id="1acd5-229">sp</span></span>|<span data-ttu-id="1acd5-230">http://schemas.xmlsoap.org/ws/2005/07/securitypolicy</span><span class="sxs-lookup"><span data-stu-id="1acd5-230">http://schemas.xmlsoap.org/ws/2005/07/securitypolicy</span></span>|  
|<span data-ttu-id="1acd5-231">a</span><span class="sxs-lookup"><span data-stu-id="1acd5-231">a</span></span>|<span data-ttu-id="1acd5-232">http://www.w3.org/2005/08/addressing</span><span class="sxs-lookup"><span data-stu-id="1acd5-232">http://www.w3.org/2005/08/addressing</span></span>|  
|<span data-ttu-id="1acd5-233">wsse</span><span class="sxs-lookup"><span data-stu-id="1acd5-233">wsse</span></span>|<span data-ttu-id="1acd5-234">TBD – OASIS WSS 1.0 URI</span><span class="sxs-lookup"><span data-stu-id="1acd5-234">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="1acd5-235">wsse11</span><span class="sxs-lookup"><span data-stu-id="1acd5-235">wsse11</span></span>|<span data-ttu-id="1acd5-236">TBD – OASIS WSS 1.1 URI</span><span class="sxs-lookup"><span data-stu-id="1acd5-236">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="1acd5-237">wsu</span><span class="sxs-lookup"><span data-stu-id="1acd5-237">wsu</span></span>|<span data-ttu-id="1acd5-238">TBD – OASIS WSS 1.0 Utility URI</span><span class="sxs-lookup"><span data-stu-id="1acd5-238">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="1acd5-239">ds</span><span class="sxs-lookup"><span data-stu-id="1acd5-239">ds</span></span>|<span data-ttu-id="1acd5-240">TBD – W3C XMLDSig URI</span><span class="sxs-lookup"><span data-stu-id="1acd5-240">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="1acd5-241">wst</span><span class="sxs-lookup"><span data-stu-id="1acd5-241">wst</span></span>|<span data-ttu-id="1acd5-242">TBD – WS-Trust 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="1acd5-242">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="1acd5-243">wssc</span><span class="sxs-lookup"><span data-stu-id="1acd5-243">wssc</span></span>|<span data-ttu-id="1acd5-244">TBD – WS-SecureConversation 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="1acd5-244">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="1acd5-245">wsaw</span><span class="sxs-lookup"><span data-stu-id="1acd5-245">wsaw</span></span>|<span data-ttu-id="1acd5-246">TBD - WS-Addressing policy namespace</span><span class="sxs-lookup"><span data-stu-id="1acd5-246">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="1acd5-247">wsp</span><span class="sxs-lookup"><span data-stu-id="1acd5-247">wsp</span></span>|<span data-ttu-id="1acd5-248">http://schemas.xmlsoap.org/ws/2004/09/policy</span><span class="sxs-lookup"><span data-stu-id="1acd5-248">http://schemas.xmlsoap.org/ws/2004/09/policy</span></span>|  
|<span data-ttu-id="1acd5-249">mssp</span><span class="sxs-lookup"><span data-stu-id="1acd5-249">mssp</span></span>|<span data-ttu-id="1acd5-250">http://schemas.microsoft.com/ws/2005/07/securitypolicy</span><span class="sxs-lookup"><span data-stu-id="1acd5-250">http://schemas.microsoft.com/ws/2005/07/securitypolicy</span></span>|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="1acd5-251">1.權杖設定檔</span><span class="sxs-lookup"><span data-stu-id="1acd5-251">1. Token Profiles</span></span>  
 <span data-ttu-id="1acd5-252">Web 服務安全性規格會以安全性權杖來表示認證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-252">Web Services Security specifications represent credential as security tokens.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-253"> 支援下列權杖型別：</span><span class="sxs-lookup"><span data-stu-id="1acd5-253"> supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="1acd5-254">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="1acd5-254">1.1 UsernameToken</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-255"> 遵循 UsernameToken10 和 UsernameToken11 設定檔，但受下列條件約束：</span><span class="sxs-lookup"><span data-stu-id="1acd5-255"> follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="1acd5-256">R1101 UsernameToken\Password 項目上的 PasswordType 屬性必須被省略，或者必須具有值 #PasswordText (預設)。</span><span class="sxs-lookup"><span data-stu-id="1acd5-256">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="1acd5-257">使用擴充性，便可以實作 #PasswordDigest。</span><span class="sxs-lookup"><span data-stu-id="1acd5-257">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="1acd5-258">據觀察，#PasswordDigest 通常會被誤認是具備足夠安全性的密碼保護機制。</span><span class="sxs-lookup"><span data-stu-id="1acd5-258">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="1acd5-259">但是 #PasswordDigest 無法取代 UsernameToken 加密。</span><span class="sxs-lookup"><span data-stu-id="1acd5-259">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="1acd5-260">#PasswordDigest 的主要目標是防禦重新執行攻擊。</span><span class="sxs-lookup"><span data-stu-id="1acd5-260">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="1acd5-261">在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 驗證模式中，重新執行攻擊威脅會透過使用訊息簽章來降低風險。</span><span class="sxs-lookup"><span data-stu-id="1acd5-261">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="1acd5-262">B1102 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 絕不會發出 UsernameToken 的 Nonce 和 Created 子項目。</span><span class="sxs-lookup"><span data-stu-id="1acd5-262">B1102 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="1acd5-263">這些子元素是為了協助進行重新執行偵測。</span><span class="sxs-lookup"><span data-stu-id="1acd5-263">These sub-elements are intended to help replay detection.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-264"> 會改用訊息簽章。</span><span class="sxs-lookup"><span data-stu-id="1acd5-264"> uses message signatures instead.</span></span>  
  
 <span data-ttu-id="1acd5-265">OASIS WSS SOAP 訊息安全性 UsernameToken 設定檔 1.1 (UsernameToken11) 從密碼功能引入金鑰衍生。</span><span class="sxs-lookup"><span data-stu-id="1acd5-265">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="1acd5-266">B1103 UsernameToken 密碼不能做為金鑰衍生，也不能用於密碼編譯作業。</span><span class="sxs-lookup"><span data-stu-id="1acd5-266">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="1acd5-267">基本原理：密碼通常被視為太弱，無法用於密碼編譯作業。</span><span class="sxs-lookup"><span data-stu-id="1acd5-267">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="1acd5-268">1.2 X509 權杖</span><span class="sxs-lookup"><span data-stu-id="1acd5-268">1.2 X509 Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-269"> 支援 X509v3 憑證做為認證類型，且遵循 X509TokenProfile1.0 和 X509TokenProfile1.1，但受下列條件約束：</span><span class="sxs-lookup"><span data-stu-id="1acd5-269"> supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="1acd5-270">R1201 當包含 X509v3 憑證時，BinarySecurityToken 項目上的 ValueType 屬性必須具有值 #X509v3。</span><span class="sxs-lookup"><span data-stu-id="1acd5-270">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="1acd5-271">WSS X509 權杖設定檔 1.0 和 1.1 也會將 #X509PKIPathv1 和 #PKCS7 定義為實值型別。</span><span class="sxs-lookup"><span data-stu-id="1acd5-271">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-272"> 不支援這些型別。</span><span class="sxs-lookup"><span data-stu-id="1acd5-272"> does not support these types.</span></span>  
  
 <span data-ttu-id="1acd5-273">R1202 如果 SubjectKeyIdentifier (SKI) 延伸出現在 X509 憑證中，則 wsse:KeyIdentifier 應該當做權杖的外部參考，並且使用 ValueType 屬性做為 #X509SubjectKeyIdentifier，而它的內容做為憑證 SKI 延伸 base64 編碼值。</span><span class="sxs-lookup"><span data-stu-id="1acd5-273">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="1acd5-274">SKI 參考已廣泛實作，且已證實為高度互通的外部參考型別。</span><span class="sxs-lookup"><span data-stu-id="1acd5-274">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="1acd5-275">R1203 X509 安全性權杖的外部參考不可使用 ds:X509IssuerSerial。</span><span class="sxs-lookup"><span data-stu-id="1acd5-275">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="1acd5-276">R1204 如果 X509TokenProfile1.1 正在使用中，則 X509 安全性權杖的外部參考應使用 WS-Security 1.1 所引入的指紋。</span><span class="sxs-lookup"><span data-stu-id="1acd5-276">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-277"> 支援 X509IssuerSerial。</span><span class="sxs-lookup"><span data-stu-id="1acd5-277"> supports X509IssuerSerial.</span></span> <span data-ttu-id="1acd5-278">不過，X509IssuerSerial 會有互通性問題：[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用字串來比較 X509IssuerSerial 的兩個值。</span><span class="sxs-lookup"><span data-stu-id="1acd5-278">However There are interoperability issues with X509IssuerSerial: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="1acd5-279">因此，如果將主體名稱的元件重新排序，並將憑證的參考傳送至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，可能會找不到此憑證參考。</span><span class="sxs-lookup"><span data-stu-id="1acd5-279">Therefore if one reorders components of the Subject Name and sends to an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="1acd5-280">1.3 Kerberos 權杖</span><span class="sxs-lookup"><span data-stu-id="1acd5-280">1.3 Kerberos Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-281"> 為了 Windows 驗證而支援 KerberosTokenProfile1.1，但受下列條件約束：</span><span class="sxs-lookup"><span data-stu-id="1acd5-281"> supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="1acd5-282">R1301 依照 GSS_API 和 Kerberos 規格定義，Kerberos 權杖必須具有 GSS 包裝的 Kerberos v4 AP_REQ 值，而且必須具有值為 #GSS_Kerberosv5_AP_REQ 的 ValueType 屬性。</span><span class="sxs-lookup"><span data-stu-id="1acd5-282">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-283"> 使用 GSS 包裝的 Kerberos AP-REQ，而非不包裝的 AP-REQ。</span><span class="sxs-lookup"><span data-stu-id="1acd5-283"> uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="1acd5-284">這是安全性的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="1acd5-284">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="1acd5-285">1.4 SAML v1.1 權杖</span><span class="sxs-lookup"><span data-stu-id="1acd5-285">1.4 SAML v1.1 Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-286"> 支援 SAML v1.1 權杖使用 WSS SAML 權杖設定檔 1.0 和 1.1。</span><span class="sxs-lookup"><span data-stu-id="1acd5-286"> supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="1acd5-287">它也可以實作其他版本的 SAML 權杖格式。</span><span class="sxs-lookup"><span data-stu-id="1acd5-287">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="1acd5-288">1.5 安全性內容權杖</span><span class="sxs-lookup"><span data-stu-id="1acd5-288">1.5 Security Context Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-289"> 支援 WS-SecureCoversation 中引入的安全性內容權杖 (SCT)。</span><span class="sxs-lookup"><span data-stu-id="1acd5-289"> supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="1acd5-290">SCT 是用來表示 SecureConversation 和二進位交涉通訊協定 TLS 和 SSPI 中所建立的安全性內容，說明如下。</span><span class="sxs-lookup"><span data-stu-id="1acd5-290">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="1acd5-291">2.通用訊息安全性參數</span><span class="sxs-lookup"><span data-stu-id="1acd5-291">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="1acd5-292">2.1 TimeStamp</span><span class="sxs-lookup"><span data-stu-id="1acd5-292">2.1 TimeStamp</span></span>  
 <span data-ttu-id="1acd5-293">時間戳記存在是使用 <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> 類別的 <xref:System.ServiceModel.Channels.SecurityBindingElement> 屬性加以控制。</span><span class="sxs-lookup"><span data-stu-id="1acd5-293">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-294"> 永遠使用 wsse:Created 和 wsse:Expires 欄位以序列化 wsse:TimeStamp。</span><span class="sxs-lookup"><span data-stu-id="1acd5-294"> always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="1acd5-295">使用簽章時，一定會簽署 wsse:TimeStamp。</span><span class="sxs-lookup"><span data-stu-id="1acd5-295">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="1acd5-296">2.2 保護順序</span><span class="sxs-lookup"><span data-stu-id="1acd5-296">2.2 Protection Order</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-297"> 支援訊息保護順序「加密後簽署」和「簽署後加密」(安全性原則 1.1)。</span><span class="sxs-lookup"><span data-stu-id="1acd5-297"> supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="1acd5-298">基於下列理由，建議使用「簽署後加密」：除非使用 WS-Security 1.1 SignatureConfirmation 機制，否則使用「加密後簽署」保護的訊息容易遭受簽章替換攻擊，而且加密內容上的簽章會造成稽核困難。</span><span class="sxs-lookup"><span data-stu-id="1acd5-298">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="1acd5-299">2.3 簽章保護</span><span class="sxs-lookup"><span data-stu-id="1acd5-299">2.3 Signature Protection</span></span>  
 <span data-ttu-id="1acd5-300">使用「加密後簽署」時，建議保護簽章，以防止暴力密碼破解攻擊猜測加密內容或簽署金鑰 (特別是在自訂權杖與弱式金鑰內容搭配使用時)。</span><span class="sxs-lookup"><span data-stu-id="1acd5-300">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="1acd5-301">2.4 演算法組合</span><span class="sxs-lookup"><span data-stu-id="1acd5-301">2.4 Algorithm Suite</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-302"> 支援安全性原則 1.1 中列出的所有演算法組合。</span><span class="sxs-lookup"><span data-stu-id="1acd5-302"> supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="1acd5-303">2.5 金鑰衍生</span><span class="sxs-lookup"><span data-stu-id="1acd5-303">2.5 Key Derivation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-304"> 使用「對稱式金鑰的金鑰衍生」，如 WS-SecureConversation 中所述。</span><span class="sxs-lookup"><span data-stu-id="1acd5-304"> uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="1acd5-305">2.6 簽章確認</span><span class="sxs-lookup"><span data-stu-id="1acd5-305">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="1acd5-306">簽章確認可以防禦攔截式攻擊，以保護簽章組。</span><span class="sxs-lookup"><span data-stu-id="1acd5-306">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="1acd5-307">2.7 安全性標頭配置</span><span class="sxs-lookup"><span data-stu-id="1acd5-307">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="1acd5-308">每個驗證模式都會描述安全性標頭的某種配置。</span><span class="sxs-lookup"><span data-stu-id="1acd5-308">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="1acd5-309">安全性標頭中的項目是半排序的。</span><span class="sxs-lookup"><span data-stu-id="1acd5-309">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="1acd5-310">為了定義安全性標頭子項目的順序，WS-Security 原則會定義下列安全性標頭配置模式：</span><span class="sxs-lookup"><span data-stu-id="1acd5-310">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1acd5-311">Strict</span><span class="sxs-lookup"><span data-stu-id="1acd5-311">Strict</span></span>|<span data-ttu-id="1acd5-312">根據「使用前宣告」的一般原則，遵循安全性原則 7.7.1 一節中所述的編號配置規則，將項目加入至安全性標頭中。</span><span class="sxs-lookup"><span data-stu-id="1acd5-312">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="1acd5-313">Lax</span><span class="sxs-lookup"><span data-stu-id="1acd5-313">Lax</span></span>|<span data-ttu-id="1acd5-314">依據符合 WSS: SOAP 訊息安全性的任何順序，將項目新增至安全性標頭中。</span><span class="sxs-lookup"><span data-stu-id="1acd5-314">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="1acd5-315">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="1acd5-315">LaxTimestampFirst</span></span>|<span data-ttu-id="1acd5-316">與 Lax 相同，除了安全性標頭中的第一個項目必須是 wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="1acd5-316">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="1acd5-317">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="1acd5-317">LaxTimestampLast</span></span>|<span data-ttu-id="1acd5-318">與 Lax 相同，除了安全性標頭中的最後一個項目必須是 wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="1acd5-318">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-319"> 支援安全性標頭配置的所有四個模式。</span><span class="sxs-lookup"><span data-stu-id="1acd5-319"> supports all four modes for security header layout.</span></span> <span data-ttu-id="1acd5-320">下列驗證模式的安全性標頭結構和訊息範例都遵循 "Strict" 模式。</span><span class="sxs-lookup"><span data-stu-id="1acd5-320">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="1acd5-321">2.通用訊息安全性參數</span><span class="sxs-lookup"><span data-stu-id="1acd5-321">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="1acd5-322">本章節提供每個驗證模式的範例原則，並提供範例來示範用戶端和服務交換訊息中的安全性標頭結構。</span><span class="sxs-lookup"><span data-stu-id="1acd5-322">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="1acd5-323">6.1 傳輸保護</span><span class="sxs-lookup"><span data-stu-id="1acd5-323">6.1 Transport Protection</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1acd5-324"> 提供五個使用安全傳輸來保護訊息的驗證模式：UserNameOverTransport、CertificateOverTransport、KerberosOverTransport、IssuedTokenOverTransport 和 SspiNegotiatedOverTransport。</span><span class="sxs-lookup"><span data-stu-id="1acd5-324"> provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="1acd5-325">這些驗證模式使用 SecurityPolicy 中所述的傳輸繫結加以建構。</span><span class="sxs-lookup"><span data-stu-id="1acd5-325">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="1acd5-326">對於 UserNameOverTransport 驗證模式，UsernameToken 是已簽署的支援權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-326">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="1acd5-327">對於其他驗證模式，此權杖會顯示為已簽署 (Signed) 的簽署 (Endorsing) 權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-327">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="1acd5-328">SecurityPolicy 的附錄 C.1.2 和 C.1.3 詳細描述了安全性標頭配置。</span><span class="sxs-lookup"><span data-stu-id="1acd5-328">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="1acd5-329">下列範例安全性標頭示範指定之驗證模式的 Strict 配置。</span><span class="sxs-lookup"><span data-stu-id="1acd5-329">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="1acd5-330">權杖的 "Derived Keys" 屬性值一定是 "false"。</span><span class="sxs-lookup"><span data-stu-id="1acd5-330">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="1acd5-331">傳輸繫結的各種屬性值如下：</span><span class="sxs-lookup"><span data-stu-id="1acd5-331">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="1acd5-332">時間戳記：true</span><span class="sxs-lookup"><span data-stu-id="1acd5-332">Timestamp: true</span></span>  
  
 <span data-ttu-id="1acd5-333">安全性標頭配置：Strict</span><span class="sxs-lookup"><span data-stu-id="1acd5-333">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="1acd5-334">演算法組合：Basic256</span><span class="sxs-lookup"><span data-stu-id="1acd5-334">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="1acd5-335">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="1acd5-335">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="1acd5-336">在這個驗證模式中，用戶端會使用使用者名稱權杖來進行驗證，這個權杖出現在 SOAP 層中做為已簽署的支援權杖，且一定會從啟動器傳送至收件者。</span><span class="sxs-lookup"><span data-stu-id="1acd5-336">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="1acd5-337">服務會在傳輸層上使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="1acd5-338">使用的繫結為傳輸繫結。</span><span class="sxs-lookup"><span data-stu-id="1acd5-338">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="1acd5-339">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-339">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='UsernameOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:SignedSupportingTokens >  
        <wsp:Policy>  
          <sp:UsernameToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:WssUsernameToken10 />   
            </wsp:Policy>  
          </sp:UsernameToken>  
        </wsp:Policy>  
      </sp:SignedSupportingTokens>  
      <sp:Wss11 >  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10 >  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="1acd5-340">安全性標頭配置</span><span class="sxs-lookup"><span data-stu-id="1acd5-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="1acd5-341">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-341">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken ... >  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-342">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="1acd5-343">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="1acd5-343">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="1acd5-344">在這個驗證模式中，用戶端會使用 X.509 憑證來進行驗證，這個憑證出現在 SOAP 層中做為簽署支援權杖，且一定會從啟動器傳送至收件者。</span><span class="sxs-lookup"><span data-stu-id="1acd5-344">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="1acd5-345">服務會在傳輸層上使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-345">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="1acd5-346">使用的繫結為傳輸繫結。</span><span class="sxs-lookup"><span data-stu-id="1acd5-346">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="1acd5-347">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-347">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CertificateOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding xmlns:sp='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy' >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
             <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:RequireThumbprintReference />   
              <sp:WssX509V3Token10 />   
            </wsp:Policy>  
          </sp:X509Token>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="1acd5-348">安全性標頭配置</span><span class="sxs-lookup"><span data-stu-id="1acd5-348">Security Header Layout</span></span>  
  
 <span data-ttu-id="1acd5-349">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-349">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wse:Timestamp u:Id="_0">  
  ...  
  </wse:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-350">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-350">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="1acd5-351">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="1acd5-351">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="1acd5-352">在這個驗證模式中，用戶端本身不會向服務驗證，但會出示安全性權杖服務 (STS) 所發出的權杖，並證明得知共用金鑰。</span><span class="sxs-lookup"><span data-stu-id="1acd5-352">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="1acd5-353">發出的權杖出現在 SOAP 層中做為簽署支援權杖，且一定會從啟動器傳送至收件者。</span><span class="sxs-lookup"><span data-stu-id="1acd5-353">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="1acd5-354">服務會在傳輸層上使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-354">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="1acd5-355">繫結為傳輸繫結。</span><span class="sxs-lookup"><span data-stu-id="1acd5-355">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="1acd5-356">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-356">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='IssuedTokenOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:IssuedToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <sp:RequestSecurityTokenTemplate>  
              <wst:KeyType>  
              http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
              </wst:KeyType>   
            </sp:RequestSecurityTokenTemplate>  
            <wsp:Policy>  
              <sp:RequireInternalReference />   
            </wsp:Policy>  
          </sp:IssuedToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="1acd5-357">安全性標頭配置</span><span class="sxs-lookup"><span data-stu-id="1acd5-357">Security Header Layout</span></span>  
  
 <span data-ttu-id="1acd5-358">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-358">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion ...>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-359">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-359">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="1acd5-360">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="1acd5-360">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="1acd5-361">在這個驗證模式中，用戶端會使用 Kerberos 票證，向服務進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-361">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="1acd5-362">Kerberos 權杖出現在 SOAP 層中做為簽署支援權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-362">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="1acd5-363">服務會在傳輸層上使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-363">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="1acd5-364">繫結為傳輸繫結。</span><span class="sxs-lookup"><span data-stu-id="1acd5-364">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="1acd5-365">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-365">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='KerberosOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:KerberosToken  
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
            <wsp:Policy>  
              <sp:WssGssKerberosV5ApReqToken11 />   
            </wsp:Policy>  
          </sp:KerberosToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="1acd5-366">安全性標頭配置</span><span class="sxs-lookup"><span data-stu-id="1acd5-366">Security Header Layout</span></span>  
  
 <span data-ttu-id="1acd5-367">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-367">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken ValueType="...#GSS_Kerberosv5_AP_REQ">  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-368">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-368">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="1acd5-369">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="1acd5-369">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="1acd5-370">在這個模式中，交涉通訊協定是用來執行用戶端和伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-370">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="1acd5-371">如果可能則會使用 Kerberos，否則會使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="1acd5-371">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="1acd5-372">產生的 SCT 出現在 SOAP 層中做為簽署支援權杖，且一定會從啟動器傳送至收件者。</span><span class="sxs-lookup"><span data-stu-id="1acd5-372">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="1acd5-373">此外，服務也會在傳輸層上使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-373">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="1acd5-374">使用的繫結為傳輸繫結。</span><span class="sxs-lookup"><span data-stu-id="1acd5-374">The binding used is a transport binding.</span></span> <span data-ttu-id="1acd5-375">"SPNEGO" (交涉) 描述 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 如何將 SSPI 二進位交涉通訊協定與 WS-Trust 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="1acd5-375">"SPNEGO" (negotiation) describes how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="1acd5-376">本章節中的安全性標頭範例是在透過 SPNEGO 信號交換建立了 SCT 之後。</span><span class="sxs-lookup"><span data-stu-id="1acd5-376">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="1acd5-377">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-377">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SspiNegotiatedOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:SpnegoContextToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy />   
          </sp:SpnegoContextToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples"></a><span data-ttu-id="1acd5-378">安全性標頭範例</span><span class="sxs-lookup"><span data-stu-id="1acd5-378">Security Header Examples</span></span>  
 <span data-ttu-id="1acd5-379">一旦使用 WS-Trust 二進位交涉透過 SPNEGO 信號交換來建立安全性內容權杖，應用程式訊息就會有下列結構的安全性標頭。</span><span class="sxs-lookup"><span data-stu-id="1acd5-379">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="1acd5-380">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-380">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:SecurityContextToken u:Id="uuid-2202746a-7725-453d-8747-809cb718dab0-29" >  
  ...  
  </wssc:SecurityContextToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-381">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-381">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="1acd5-382">6.2 使用 X.509 憑證來驗證服務</span><span class="sxs-lookup"><span data-stu-id="1acd5-382">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="1acd5-383">本章節描述下列驗證模式：MutualCertificate WSS1.0、Mutual CertificateDuplex、MutualCertificate WSS1.1、AnonymousForCertificate、UserNameForCertificate 和 IssuedTokenForCertificate。</span><span class="sxs-lookup"><span data-stu-id="1acd5-383">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="1acd5-384">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="1acd5-384">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="1acd5-385">在這個驗證模式中，用戶端會使用 X.509 憑證來進行驗證，這個憑證出現在 SOAP 層中做為啟動器權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="1acd5-386">服務也會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="1acd5-387">使用的繫結為具有下列屬性值的非對稱式繫結：</span><span class="sxs-lookup"><span data-stu-id="1acd5-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="1acd5-388">啟動器權杖：用戶端的 X.509 憑證，其內含模式設定為 …/IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="1acd5-388">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="1acd5-389">收件者權杖：伺服器的 X.509 憑證，其內含模式設定為 …/IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="1acd5-389">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="1acd5-390">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="1acd5-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="1acd5-391">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="1acd5-392">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="1acd5-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="1acd5-393">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="1acd5-394">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-394">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificate_WSS10_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-395">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-396">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-396">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-397">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-397">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-398">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-398">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="1acd5-399">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-399">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-400">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-400">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="1acd5-401">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="1acd5-401">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="1acd5-402">在這個驗證模式中，用戶端會使用 X.509 憑證來進行驗證，這個憑證出現在 SOAP 層中做為啟動器權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-402">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="1acd5-403">服務也會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-403">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="1acd5-404">使用的繫結為具有下列屬性值的非對稱式繫結：</span><span class="sxs-lookup"><span data-stu-id="1acd5-404">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="1acd5-405">啟動器權杖：用戶端的 X509 憑證，其內含模式設定為 …/IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="1acd5-405">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="1acd5-406">收件者權杖：伺服器的 X509 憑證，其內含模式設定為 …/IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="1acd5-406">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="1acd5-407">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="1acd5-407">Token Protection: False</span></span>  
  
 <span data-ttu-id="1acd5-408">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-408">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="1acd5-409">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="1acd5-409">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="1acd5-410">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-410">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="1acd5-411">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-411">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificateDuplex_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToInitiator' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-412">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-412">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-413">要求和回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-413">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="1acd5-414">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-414">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="1acd5-415">要求和回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-415">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="1acd5-416">6.2.3 搭配使用 SymmetricBinding 與 X.509 服務驗證</span><span class="sxs-lookup"><span data-stu-id="1acd5-416">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="1acd5-417">"WSS10" 會為使用 X509 權杖的案例提供有限支援。</span><span class="sxs-lookup"><span data-stu-id="1acd5-417">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="1acd5-418">例如，對於只使用服務 X509 權杖的訊息，則無法提供簽章和加密保護。</span><span class="sxs-lookup"><span data-stu-id="1acd5-418">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="1acd5-419">"WSS11" 引入 EncryptedKey 做為對稱式權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-419">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="1acd5-420">現在，服務 X.509 憑證的暫時加密金鑰可以做為要求和回應訊息保護。</span><span class="sxs-lookup"><span data-stu-id="1acd5-420">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="1acd5-421">下面 6.4 節中描述的驗證模式 (Mode) 會使用這個模式 (Pattern)。</span><span class="sxs-lookup"><span data-stu-id="1acd5-421">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="1acd5-422">WS-SecurityPolicy 使用 SymmetricBinding 搭配服務 X509 權杖做為保護權杖，描述這個模式。</span><span class="sxs-lookup"><span data-stu-id="1acd5-422">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="1acd5-423">驗證模式 AnonymousForCertificate、UsernameForCertificate、MutualCertificate WSS11 和 IssuedTokenForCertificate 全部都會使用類似具有下列屬性值的 sp:SymmetricBinding 執行個體：</span><span class="sxs-lookup"><span data-stu-id="1acd5-423">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="1acd5-424">保護權杖：伺服器的 X509 憑證，其內含模式設定為 .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="1acd5-424">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="1acd5-425">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="1acd5-425">Token Protection: False</span></span>  
  
 <span data-ttu-id="1acd5-426">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-426">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="1acd5-427">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="1acd5-427">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="1acd5-428">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-428">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="1acd5-429">以上的驗證模式只有一個地方不同，那就是支援的權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-429">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="1acd5-430">AnonymousForCertificate 沒有任何支援權杖，MutualCertificate WSS 1.1 會將用戶端的 X509 憑證當做簽署 (Endorsing) 支援權杖，UserNameForCertificate 會將 UserName 權杖當做已簽署 (Signed) 的支援權杖、IssuedTokenForCertificate 會將發出的權杖當做簽署 (Endorsing) 支援權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-430">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="1acd5-431">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-431">Policy</span></span>  
  
 <span data-ttu-id="1acd5-432">對稱式繫結</span><span class="sxs-lookup"><span data-stu-id="1acd5-432">Symmetric Binding</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SymmetricCert_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireThumbprintReference />   
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />  
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting Token Assertions appear here -->  
      ...  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
          <sp:RequireSignatureConfirmation />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="1acd5-433">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="1acd5-433">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="1acd5-434">在這個驗證模式中，用戶端為匿名，而服務會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-434">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="1acd5-435">使用的繫結為對稱式繫結的執行個體，如 6.4.2 中所述。</span><span class="sxs-lookup"><span data-stu-id="1acd5-435">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="1acd5-436">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-436">Policy</span></span>  
  
 <span data-ttu-id="1acd5-437">如需繫結的詳細資訊，請參閱上面 6.2.3 中的「原則」。</span><span class="sxs-lookup"><span data-stu-id="1acd5-437">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-438">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-438">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-439">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-439">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-440">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-440">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="1acd5-441">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-441">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="1acd5-442">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-442">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-443">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-443">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="1acd5-444">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="1acd5-444">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="1acd5-445">在這個驗證模式中，用戶端會使用使用者名稱權杖，向服務進行驗證，這個權杖出現在 SOAP 層中做為已簽署的支援權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-445">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="1acd5-446">服務會使用 X.509 憑證對用戶端進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-446">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="1acd5-447">使用的繫結是對稱式繫結，其中的保護權杖是用戶端產生的金鑰，且以服務的公開金鑰來加密。</span><span class="sxs-lookup"><span data-stu-id="1acd5-447">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="1acd5-448">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-448">Policy</span></span>  
  
 <span data-ttu-id="1acd5-449">如需繫結的詳細資訊，請參閱上面 6.2.3 中的「原則」。</span><span class="sxs-lookup"><span data-stu-id="1acd5-449">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="1acd5-450">已簽署的支援權杖</span><span class="sxs-lookup"><span data-stu-id="1acd5-450">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-451">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-451">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-452">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-452">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-453">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-453">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="1acd5-454">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-454">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="1acd5-455">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-455">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-456">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-456">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="1acd5-457">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="1acd5-457">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="1acd5-458">在這個驗證模式中，用戶端會使用 X.509 憑證來進行驗證，這個憑證出現在 SOAP 層中做為簽署支援權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-458">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="1acd5-459">服務也會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-459">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="1acd5-460">使用的繫結是對稱式繫結，其中的保護權杖是用戶端產生的金鑰，且以服務的公開金鑰來加密。</span><span class="sxs-lookup"><span data-stu-id="1acd5-460">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="1acd5-461">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-461">Policy</span></span>  
  
 <span data-ttu-id="1acd5-462">如需繫結的詳細資訊，請參閱上面 6.2.3 中的「原則」。</span><span class="sxs-lookup"><span data-stu-id="1acd5-462">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="1acd5-463">簽署支援權杖</span><span class="sxs-lookup"><span data-stu-id="1acd5-463">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-464">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-464">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-465">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-465">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-466">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-466">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="1acd5-467">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-467">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="1acd5-468">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-468">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-469">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-469">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="1acd5-470">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="1acd5-470">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="1acd5-471">在這個驗證模式中，用戶端本身不會向服務驗證，但會出示 STS 所發出的權杖，並證明得知共用金鑰。</span><span class="sxs-lookup"><span data-stu-id="1acd5-471">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="1acd5-472">發出的權杖出現在 SOAP 層中做為簽署支援權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-472">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="1acd5-473">服務會使用 X.509 憑證對用戶端進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-473">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="1acd5-474">使用的繫結是對稱式繫結，其中的保護權杖是用戶端產生的金鑰，且以服務的公開金鑰來加密。</span><span class="sxs-lookup"><span data-stu-id="1acd5-474">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="1acd5-475">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-475">Policy</span></span>  
  
 <span data-ttu-id="1acd5-476">如需繫結的詳細資訊，請參閱上面 6.2.3 中的「原則」。</span><span class="sxs-lookup"><span data-stu-id="1acd5-476">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="1acd5-477">簽署支援權杖</span><span class="sxs-lookup"><span data-stu-id="1acd5-477">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
       </wst:KeyType>  
     </sp:RequestSecurityTokenTemplate>  
     <wsp:Policy>  
       <sp:RequireDerivedKeys />   
       <sp:RequireInternalReference />   
     </wsp:Policy>  
   </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-478">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-478">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-479">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-479">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-480">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-480">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="1acd5-481">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-481">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="1acd5-482">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-482">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-483">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-483">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
## <a name="63-kerberos"></a><span data-ttu-id="1acd5-484">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="1acd5-484">6.3 Kerberos</span></span>  
 <span data-ttu-id="1acd5-485">在這個驗證模式中，用戶端會使用 Kerberos 票證，向服務進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-485">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="1acd5-486">相同的票證也會提供伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-486">That same ticket also provides server authentication.</span></span> <span data-ttu-id="1acd5-487">使用的繫結為具有下列屬性的對稱式繫結：</span><span class="sxs-lookup"><span data-stu-id="1acd5-487">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="1acd5-488">保護權杖：Kerberos 票證，其內含模式設定為 .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="1acd5-488">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="1acd5-489">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="1acd5-489">Token Protection: False</span></span>  
  
 <span data-ttu-id="1acd5-490">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-490">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="1acd5-491">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="1acd5-491">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="1acd5-492">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-492">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="1acd5-493">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-493">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='Kerberos_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:KerberosToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:WssGssKerberosV5ApReqToken11 />   
                </wsp:Policy>  
              </sp:KerberosToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-494">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-494">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-495">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-495">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-496">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-496">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="1acd5-497">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-497">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="1acd5-498">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-498">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-499">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-499">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="1acd5-500">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="1acd5-500">6.4 IssuedToken</span></span>  
 <span data-ttu-id="1acd5-501">在這個驗證模式中，用戶端本身不會向服務驗證，但用戶端會出示 STS 所發出的權杖，並證明得知共用金鑰。</span><span class="sxs-lookup"><span data-stu-id="1acd5-501">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="1acd5-502">服務本身也不會向用戶端驗證，但 STS 會加密共用金鑰做為已發出權杖的一部分，只有服務才能解密金鑰。</span><span class="sxs-lookup"><span data-stu-id="1acd5-502">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="1acd5-503">使用的繫結為具有下列屬性的對稱式繫結：</span><span class="sxs-lookup"><span data-stu-id="1acd5-503">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="1acd5-504">保護權杖：發出的權杖，其內含模式設定為 .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="1acd5-504">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="1acd5-505">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="1acd5-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="1acd5-506">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="1acd5-507">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="1acd5-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="1acd5-508">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-508">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="1acd5-509">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-509">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple3_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <sp:RequestSecurityTokenTemplate>  
                  <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
                  </wst:KeyType>   
                </sp:RequestSecurityTokenTemplate>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireInternalReference />   
                </wsp:Policy>  
              </sp:IssuedToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-510">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-510">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-511">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-511">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-512">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-512">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="1acd5-513">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-513">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="1acd5-514">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-514">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-515">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-515">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="1acd5-516">6.5 使用 SslNegotiated 來驗證服務</span><span class="sxs-lookup"><span data-stu-id="1acd5-516">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="1acd5-517">本章節描述一組驗證模式，這些驗證模式使用對稱式繫結，並將基於 WS-SecureConversation (WS-SC) 的安全性內容權杖做為保護權杖，權杖的金鑰值是藉由在 WS-Trust (WS-T) RST/RSTR 訊息上執行 TLS 通訊協定交涉而來。</span><span class="sxs-lookup"><span data-stu-id="1acd5-517">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="1acd5-518">TLSNEGO 中會詳細描述使用 WS-Trust 的 TLS 信號交換實作。</span><span class="sxs-lookup"><span data-stu-id="1acd5-518">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="1acd5-519">在這裡的訊息範例中，假設具有相關安全性內容的 SCT 已透過信號交換而建立。</span><span class="sxs-lookup"><span data-stu-id="1acd5-519">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="1acd5-520">使用的繫結為具有下列屬性的對稱式繫結：</span><span class="sxs-lookup"><span data-stu-id="1acd5-520">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="1acd5-521">保護權杖：SslContextToken，其內含模式設定為 .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="1acd5-521">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="1acd5-522">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="1acd5-522">Token Protection: False</span></span>  
  
 <span data-ttu-id="1acd5-523">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-523">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="1acd5-524">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="1acd5-524">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="1acd5-525">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-525">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="1acd5-526">6.5.1 SslNegotiated 服務驗證的原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-526">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="1acd5-527">本章節中所有驗證模式的原則都相似，只有一個不同之處，就是使用特定已簽署 (Signed) 的支援權杖或簽署 (Endorsing) 權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-527">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' />  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </mssp:SslContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting token assertions go here -->  
      ..  
      <sp:Wss11>   
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="1acd5-528">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="1acd5-528">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="1acd5-529">在這個驗證模式中，用戶端為匿名，而服務會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-529">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="1acd5-530">使用的繫結為對稱式繫結的執行個體，如上面 6.5.1 中所述。</span><span class="sxs-lookup"><span data-stu-id="1acd5-530">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="1acd5-531">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-531">Policy</span></span>  
  
 <span data-ttu-id="1acd5-532">如需繫結的詳細資訊，請參閱上面 6.5.1 中的「原則」。</span><span class="sxs-lookup"><span data-stu-id="1acd5-532">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-533">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-533">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-534">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-534">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-535">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-535">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="1acd5-536">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-536">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="1acd5-537">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-537">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-538">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-538">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="1acd5-539">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="1acd5-539">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="1acd5-540">在這個驗證模式中，用戶端會使用使用者名稱權杖來進行驗證，這個權杖出現在 SOAP 層中做為已簽署的支援權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-540">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="1acd5-541">服務會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-541">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="1acd5-542">使用的繫結為對稱式繫結的執行個體，如 6.5.1 中所述。</span><span class="sxs-lookup"><span data-stu-id="1acd5-542">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="1acd5-543">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-543">Policy</span></span>  
  
 <span data-ttu-id="1acd5-544">如需繫結的詳細資訊，請參閱上面的 6.5.1 一節。</span><span class="sxs-lookup"><span data-stu-id="1acd5-544">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="1acd5-545">已簽署的支援權杖</span><span class="sxs-lookup"><span data-stu-id="1acd5-545">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-546">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-546">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-547">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-547">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-548">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-548">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="1acd5-549">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-549">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="1acd5-550">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-550">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-551">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-551">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="1acd5-552">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="1acd5-552">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="1acd5-553">在這個驗證模式中，用戶端本身不會向服務驗證，但會出示 STS 所發出的權杖，並證明得知共用金鑰。</span><span class="sxs-lookup"><span data-stu-id="1acd5-553">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="1acd5-554">發出的權杖出現在 SOAP 層中做為簽署支援權杖。</span><span class="sxs-lookup"><span data-stu-id="1acd5-554">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="1acd5-555">服務會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-555">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="1acd5-556">使用的繫結為對稱式繫結的執行個體，如上面 6.5.1 中所述。</span><span class="sxs-lookup"><span data-stu-id="1acd5-556">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="1acd5-557">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-557">Policy</span></span>  
  
 <span data-ttu-id="1acd5-558">如需繫結的詳細資訊，請參閱上面的 6.5.1 一節。</span><span class="sxs-lookup"><span data-stu-id="1acd5-558">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="1acd5-559">簽署支援權杖</span><span class="sxs-lookup"><span data-stu-id="1acd5-559">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
        </wst:KeyType>   
      </sp:RequestSecurityTokenTemplate>  
      <wsp:Policy>  
        <sp:RequireDerivedKeys />   
        <sp:RequireInternalReference />   
      </wsp:Policy>  
    </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-560">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-560">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-561">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-561">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-562">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-562">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="1acd5-563">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-563">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="1acd5-564">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-564">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-565">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-565">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="1acd5-566">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="1acd5-566">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="1acd5-567">在這個驗證模式中，用戶端和服務會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-567">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="1acd5-568">使用的繫結為對稱式繫結的執行個體，如上面 6.5.1 中所述。</span><span class="sxs-lookup"><span data-stu-id="1acd5-568">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="1acd5-569">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-569">Policy</span></span>  
  
 <span data-ttu-id="1acd5-570">如需繫結的詳細資訊，請參閱上面的 6.5.1 一節。</span><span class="sxs-lookup"><span data-stu-id="1acd5-570">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="1acd5-571">簽署支援權杖</span><span class="sxs-lookup"><span data-stu-id="1acd5-571">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-572">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-572">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-573">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-573">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-574">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-574">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="1acd5-575">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-575">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="1acd5-576">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-576">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-577">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-577">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="1acd5-578">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="1acd5-578">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="1acd5-579">在這個驗證模式中，交涉通訊協定是用來執行用戶端和伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-579">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="1acd5-580">如果可能則會使用 Kerberos，否則會使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="1acd5-580">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="1acd5-581">使用的繫結為具有下列屬性的對稱式繫結：</span><span class="sxs-lookup"><span data-stu-id="1acd5-581">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="1acd5-582">保護權杖：SpnegoContextToken，其內含模式設定為 .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="1acd5-582">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="1acd5-583">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="1acd5-583">Token Protection: False</span></span>  
  
 <span data-ttu-id="1acd5-584">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-584">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="1acd5-585">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="1acd5-585">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="1acd5-586">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="1acd5-586">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="1acd5-587">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-587">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple13_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </sp:SpnegoContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-588">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-588">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-589">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-589">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-590">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-590">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="1acd5-591">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-591">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="1acd5-592">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-592">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-593">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-593">Response</span></span>  
  
```xml  
<wsse:Security>  
<wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="67-secureconversation"></a><span data-ttu-id="1acd5-594">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="1acd5-594">6.7 SecureConversation</span></span>  
 <span data-ttu-id="1acd5-595">使用的繫結為對稱式繫結，其中的保護權杖是依據 WS-SecureConversation (WS-SC) 的 SCT。</span><span class="sxs-lookup"><span data-stu-id="1acd5-595">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="1acd5-596">SCT 是根據巢狀繫結使用 WS-Trust (WS-Trust) 或 WS-SecureConversation (WS-SC) 交涉而來，而巢狀繫結本身則是使用交涉通訊協定的對稱式繫結。</span><span class="sxs-lookup"><span data-stu-id="1acd5-596">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="1acd5-597">如果可能，交涉通訊協定會使用 Kerberos 來執行用戶端和伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="1acd5-597">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="1acd5-598">如果無法使用 Kerberos，則會退而使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="1acd5-598">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="1acd5-599">原則</span><span class="sxs-lookup"><span data-stu-id="1acd5-599">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SecureConversation_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SecureConversationToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:BootstrapPolicy>  
                    <wsp:Policy>  
                      <sp:SignedParts>  
                        <sp:Body />   
                        <sp:Header Name='To' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='From' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='FaultTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='ReplyTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='MessageID' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='RelatesTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='Action' Namespace='http://www.w3.org/2005/08/addressing' />   
                      </sp:SignedParts>  
                      <sp:EncryptedParts>  
                        <sp:Body />   
                      </sp:EncryptedParts>  
                      <sp:SymmetricBinding>  
                        <wsp:Policy>  
                          <sp:ProtectionToken>  
                            <wsp:Policy>  
                              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                                <wsp:Policy>  
                                  <sp:RequireDerivedKeys />   
                                </wsp:Policy>  
                              </sp:SpnegoContextToken>  
                            </wsp:Policy>  
                          </sp:ProtectionToken>  
                          <sp:AlgorithmSuite>  
                            <wsp:Policy>  
                              <sp:Basic256 />   
                            </wsp:Policy>  
                          </sp:AlgorithmSuite>  
                          <sp:Layout>  
                            <wsp:Policy>  
                              <sp:Strict />   
                            </wsp:Policy>  
                          </sp:Layout>  
                          <sp:IncludeTimestamp />   
                          <sp:EncryptSignature />   
                          <sp:OnlySignEntireHeadersAndBody />   
                        </wsp:Policy>  
                      </sp:SymmetricBinding>  
                      <sp:Wss11>  
                        <wsp:Policy>  
                          <sp:MustSupportRefKeyIdentifier />   
                          <sp:MustSupportRefIssuerSerial />   
                          <sp:MustSupportRefThumbprint />   
                          <sp:MustSupportRefEncryptedKey />   
                        </wsp:Policy>  
                      </sp:Wss11>  
                      <sp:Trust10>  
                        <wsp:Policy>  
                          <sp:MustSupportIssuedTokens />   
                          <sp:RequireClientEntropy />   
                          <sp:RequireServerEntropy />   
                        </wsp:Policy>  
                      </sp:Trust10>  
                    </wsp:Policy>  
                  </sp:BootstrapPolicy>  
                </wsp:Policy>  
              </sp:SecureConversationToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="1acd5-600">安全性標頭範例：SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="1acd5-600">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="1acd5-601">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-601">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-602">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-602">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="1acd5-603">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="1acd5-603">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="1acd5-604">要求</span><span class="sxs-lookup"><span data-stu-id="1acd5-604">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="1acd5-605">回應</span><span class="sxs-lookup"><span data-stu-id="1acd5-605">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```
