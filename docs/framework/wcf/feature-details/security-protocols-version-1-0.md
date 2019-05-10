---
title: 安全性通訊協定 1.0 版
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: 8114183109befcb77c3bf2b35fe246118da5afde
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586879"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="42f49-102">安全性通訊協定 1.0 版</span><span class="sxs-lookup"><span data-stu-id="42f49-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="42f49-103">Web 服務安全性通訊協定提供 Web 服務安全性機制，涵蓋所有現有的企業訊息安全性需求。</span><span class="sxs-lookup"><span data-stu-id="42f49-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="42f49-104">本節描述 Windows Communication Foundation (WCF) 1.0 版詳細資料 (在中實作<xref:System.ServiceModel.Channels.SecurityBindingElement>) 下列 Web 服務安全性通訊協定。</span><span class="sxs-lookup"><span data-stu-id="42f49-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="42f49-105">規格/文件</span><span class="sxs-lookup"><span data-stu-id="42f49-105">Specification/Document</span></span>|<span data-ttu-id="42f49-106">連結</span><span class="sxs-lookup"><span data-stu-id="42f49-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="42f49-107">WSS:SOAP 訊息安全性 1.0</span><span class="sxs-lookup"><span data-stu-id="42f49-107">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="42f49-108">WSS:使用者名稱權杖設定檔 1.0</span><span class="sxs-lookup"><span data-stu-id="42f49-108">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="42f49-109">WSS:X509 權杖設定檔 1.0</span><span class="sxs-lookup"><span data-stu-id="42f49-109">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="42f49-110">WSS:SAML 1.1 權杖設定檔 1.0</span><span class="sxs-lookup"><span data-stu-id="42f49-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="42f49-111">WSS:SOAP 訊息安全性 1.1</span><span class="sxs-lookup"><span data-stu-id="42f49-111">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="42f49-112">WSS：使用者名稱權杖設定檔 1.1</span><span class="sxs-lookup"><span data-stu-id="42f49-112">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="42f49-113">WSS:X.509 權杖設定檔 1.1</span><span class="sxs-lookup"><span data-stu-id="42f49-113">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="42f49-114">WSS:Kerberos 權杖設定檔 1.1</span><span class="sxs-lookup"><span data-stu-id="42f49-114">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="42f49-115">WSS:SAML 1.1 權杖設定檔 1.1</span><span class="sxs-lookup"><span data-stu-id="42f49-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="42f49-116">WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="42f49-116">WS-Secure Conversation</span></span>|<http://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="42f49-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="42f49-117">WS-Trust</span></span>|<http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="42f49-118">應用程式注意事項：</span><span class="sxs-lookup"><span data-stu-id="42f49-118">Application Note:</span></span><br /><br /> <span data-ttu-id="42f49-119">使用 WS-Trust 進行 TLS 信號交換</span><span class="sxs-lookup"><span data-stu-id="42f49-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="42f49-120">即將發行</span><span class="sxs-lookup"><span data-stu-id="42f49-120">To be published</span></span>|  
|<span data-ttu-id="42f49-121">應用程式注意事項：</span><span class="sxs-lookup"><span data-stu-id="42f49-121">Application Note:</span></span><br /><br /> <span data-ttu-id="42f49-122">使用 WS-Trust 進行 SPNEGO</span><span class="sxs-lookup"><span data-stu-id="42f49-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="42f49-123">即將發行</span><span class="sxs-lookup"><span data-stu-id="42f49-123">To be published</span></span>|  
|<span data-ttu-id="42f49-124">應用程式注意事項：</span><span class="sxs-lookup"><span data-stu-id="42f49-124">Application Note:</span></span><br /><br /> <span data-ttu-id="42f49-125">Web 服務定址端點參考和識別</span><span class="sxs-lookup"><span data-stu-id="42f49-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="42f49-126">即將發行</span><span class="sxs-lookup"><span data-stu-id="42f49-126">To be published</span></span>|  
|<span data-ttu-id="42f49-127">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="42f49-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="42f49-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="42f49-128">(2005/07)</span></span>|<http://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="42f49-129">已由[errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html)提交至 OASIS WS-SX 技術委員會</span><span class="sxs-lookup"><span data-stu-id="42f49-129">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="42f49-130">WCF，第 1 版提供 17 可用來當做基礎 Web 服務安全性設定的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="42f49-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="42f49-131">每個模式都已針對一組通用的部署需求最佳化，例如：</span><span class="sxs-lookup"><span data-stu-id="42f49-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="42f49-132">用來驗證用戶端和服務的認證。</span><span class="sxs-lookup"><span data-stu-id="42f49-132">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="42f49-133">訊息或傳輸安全性保護機制。</span><span class="sxs-lookup"><span data-stu-id="42f49-133">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="42f49-134">訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="42f49-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="42f49-135">驗證模式</span><span class="sxs-lookup"><span data-stu-id="42f49-135">Authentication Mode</span></span>|<span data-ttu-id="42f49-136">用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="42f49-136">Client Authentication</span></span>|<span data-ttu-id="42f49-137">伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="42f49-137">Server Authentication</span></span>|<span data-ttu-id="42f49-138">模式</span><span class="sxs-lookup"><span data-stu-id="42f49-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="42f49-139">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="42f49-139">UserNameOverTransport</span></span>|<span data-ttu-id="42f49-140">使用者名稱/密碼</span><span class="sxs-lookup"><span data-stu-id="42f49-140">User name/password</span></span>|<span data-ttu-id="42f49-141">X509</span><span class="sxs-lookup"><span data-stu-id="42f49-141">X509</span></span>|<span data-ttu-id="42f49-142">Transport</span><span class="sxs-lookup"><span data-stu-id="42f49-142">Transport</span></span>|  
|<span data-ttu-id="42f49-143">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="42f49-143">CertificateOverTransport</span></span>|<span data-ttu-id="42f49-144">X509</span><span class="sxs-lookup"><span data-stu-id="42f49-144">X509</span></span>|<span data-ttu-id="42f49-145">X509</span><span class="sxs-lookup"><span data-stu-id="42f49-145">X509</span></span>|<span data-ttu-id="42f49-146">Transport</span><span class="sxs-lookup"><span data-stu-id="42f49-146">Transport</span></span>|  
|<span data-ttu-id="42f49-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="42f49-147">KerberosOverTransport</span></span>|<span data-ttu-id="42f49-148">Windows</span><span class="sxs-lookup"><span data-stu-id="42f49-148">Windows</span></span>|<span data-ttu-id="42f49-149">X509</span><span class="sxs-lookup"><span data-stu-id="42f49-149">X509</span></span>|<span data-ttu-id="42f49-150">Transport</span><span class="sxs-lookup"><span data-stu-id="42f49-150">Transport</span></span>|  
|<span data-ttu-id="42f49-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="42f49-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="42f49-152">聯合</span><span class="sxs-lookup"><span data-stu-id="42f49-152">Federated</span></span>|<span data-ttu-id="42f49-153">X509</span><span class="sxs-lookup"><span data-stu-id="42f49-153">X509</span></span>|<span data-ttu-id="42f49-154">Transport</span><span class="sxs-lookup"><span data-stu-id="42f49-154">Transport</span></span>|  
|<span data-ttu-id="42f49-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="42f49-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="42f49-156">交涉的 Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="42f49-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="42f49-157">交涉的 Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="42f49-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="42f49-158">Transport</span><span class="sxs-lookup"><span data-stu-id="42f49-158">Transport</span></span>|  
|<span data-ttu-id="42f49-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="42f49-159">AnonymousForCertificate</span></span>|<span data-ttu-id="42f49-160">None</span><span class="sxs-lookup"><span data-stu-id="42f49-160">None</span></span>|<span data-ttu-id="42f49-161">X509</span><span class="sxs-lookup"><span data-stu-id="42f49-161">X509</span></span>|<span data-ttu-id="42f49-162">訊息</span><span class="sxs-lookup"><span data-stu-id="42f49-162">Message</span></span>|  
|<span data-ttu-id="42f49-163">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="42f49-163">UserNameForCertificate</span></span>|<span data-ttu-id="42f49-164">使用者名稱/密碼</span><span class="sxs-lookup"><span data-stu-id="42f49-164">User name/password</span></span>|<span data-ttu-id="42f49-165">X509</span><span class="sxs-lookup"><span data-stu-id="42f49-165">X509</span></span>|<span data-ttu-id="42f49-166">訊息</span><span class="sxs-lookup"><span data-stu-id="42f49-166">Message</span></span>|  
|<span data-ttu-id="42f49-167">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="42f49-167">MutualCertificate</span></span>|<span data-ttu-id="42f49-168">X509</span><span class="sxs-lookup"><span data-stu-id="42f49-168">X509</span></span>|<span data-ttu-id="42f49-169">X509</span><span class="sxs-lookup"><span data-stu-id="42f49-169">X509</span></span>|<span data-ttu-id="42f49-170">訊息</span><span class="sxs-lookup"><span data-stu-id="42f49-170">Message</span></span>|  
|<span data-ttu-id="42f49-171">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="42f49-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="42f49-172">X509</span><span class="sxs-lookup"><span data-stu-id="42f49-172">X509</span></span>|<span data-ttu-id="42f49-173">X509</span><span class="sxs-lookup"><span data-stu-id="42f49-173">X509</span></span>|<span data-ttu-id="42f49-174">訊息</span><span class="sxs-lookup"><span data-stu-id="42f49-174">Message</span></span>|  
|<span data-ttu-id="42f49-175">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="42f49-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="42f49-176">聯合</span><span class="sxs-lookup"><span data-stu-id="42f49-176">Federated</span></span>|<span data-ttu-id="42f49-177">X509</span><span class="sxs-lookup"><span data-stu-id="42f49-177">X509</span></span>|<span data-ttu-id="42f49-178">訊息</span><span class="sxs-lookup"><span data-stu-id="42f49-178">Message</span></span>|  
|<span data-ttu-id="42f49-179">Kerberos</span><span class="sxs-lookup"><span data-stu-id="42f49-179">Kerberos</span></span>|<span data-ttu-id="42f49-180">Windows</span><span class="sxs-lookup"><span data-stu-id="42f49-180">Windows</span></span>|<span data-ttu-id="42f49-181">Windows</span><span class="sxs-lookup"><span data-stu-id="42f49-181">Windows</span></span>|<span data-ttu-id="42f49-182">訊息</span><span class="sxs-lookup"><span data-stu-id="42f49-182">Message</span></span>|  
|<span data-ttu-id="42f49-183">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="42f49-183">IssuedToken</span></span>|<span data-ttu-id="42f49-184">聯合</span><span class="sxs-lookup"><span data-stu-id="42f49-184">Federated</span></span>|<span data-ttu-id="42f49-185">聯合</span><span class="sxs-lookup"><span data-stu-id="42f49-185">Federated</span></span>|<span data-ttu-id="42f49-186">訊息</span><span class="sxs-lookup"><span data-stu-id="42f49-186">Message</span></span>|  
|<span data-ttu-id="42f49-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="42f49-187">SspiNegotiated</span></span>|<span data-ttu-id="42f49-188">交涉的 Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="42f49-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="42f49-189">交涉的 Windows Sspi</span><span class="sxs-lookup"><span data-stu-id="42f49-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="42f49-190">訊息</span><span class="sxs-lookup"><span data-stu-id="42f49-190">Message</span></span>|  
|<span data-ttu-id="42f49-191">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="42f49-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="42f49-192">None</span><span class="sxs-lookup"><span data-stu-id="42f49-192">None</span></span>|<span data-ttu-id="42f49-193">X509、TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="42f49-193">X509, TLS-Nego</span></span>|<span data-ttu-id="42f49-194">訊息</span><span class="sxs-lookup"><span data-stu-id="42f49-194">Message</span></span>|  
|<span data-ttu-id="42f49-195">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="42f49-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="42f49-196">使用者名稱/密碼</span><span class="sxs-lookup"><span data-stu-id="42f49-196">User name/password</span></span>|<span data-ttu-id="42f49-197">X509、TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="42f49-197">X509, TLS-Nego</span></span>|<span data-ttu-id="42f49-198">訊息</span><span class="sxs-lookup"><span data-stu-id="42f49-198">Message</span></span>|  
|<span data-ttu-id="42f49-199">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="42f49-199">MutualSslNegotiated</span></span>|<span data-ttu-id="42f49-200">X509</span><span class="sxs-lookup"><span data-stu-id="42f49-200">X509</span></span>|<span data-ttu-id="42f49-201">X509、TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="42f49-201">X509, TLS-Nego</span></span>|<span data-ttu-id="42f49-202">訊息</span><span class="sxs-lookup"><span data-stu-id="42f49-202">Message</span></span>|  
|<span data-ttu-id="42f49-203">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="42f49-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="42f49-204">聯合</span><span class="sxs-lookup"><span data-stu-id="42f49-204">Federated</span></span>|<span data-ttu-id="42f49-205">X509、TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="42f49-205">X509, TLS-Nego</span></span>|<span data-ttu-id="42f49-206">訊息</span><span class="sxs-lookup"><span data-stu-id="42f49-206">Message</span></span>|  
  
 <span data-ttu-id="42f49-207">使用這類驗證模式的端點可以使用 WS-SecurityPolicy (WS-SP) 來表示安全性需求。</span><span class="sxs-lookup"><span data-stu-id="42f49-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="42f49-208">本文件針對每個驗證模式描述安全性標頭和基礎結構訊息的結構，並提供原則和訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="42f49-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="42f49-209">WCF 會運用 Ws-secureconversation 提供安全工作階段支援來保護應用程式之間的多訊息交換。</span><span class="sxs-lookup"><span data-stu-id="42f49-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="42f49-210">如需實作的詳細資訊，請參閱下面的「安全工作階段」。</span><span class="sxs-lookup"><span data-stu-id="42f49-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="42f49-211">除了驗證模式中，WCF 會提供設定來控制適用於大部分的訊息安全性驗證模式，如的通用保護機制： 簽章和加密作業、 演算法組合、 金鑰衍生的順序與簽章確認。</span><span class="sxs-lookup"><span data-stu-id="42f49-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="42f49-212">下列是本文件中使用的前置詞和命名空間。</span><span class="sxs-lookup"><span data-stu-id="42f49-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="42f49-213">前置詞</span><span class="sxs-lookup"><span data-stu-id="42f49-213">Prefix</span></span>|<span data-ttu-id="42f49-214">命名空間</span><span class="sxs-lookup"><span data-stu-id="42f49-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="42f49-215">秒</span><span class="sxs-lookup"><span data-stu-id="42f49-215">s</span></span>|<https://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="42f49-216">sp</span><span class="sxs-lookup"><span data-stu-id="42f49-216">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="42f49-217">一個</span><span class="sxs-lookup"><span data-stu-id="42f49-217">a</span></span>|<https://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="42f49-218">wsse</span><span class="sxs-lookup"><span data-stu-id="42f49-218">wsse</span></span>|<span data-ttu-id="42f49-219">TBD – OASIS WSS 1.0 URI</span><span class="sxs-lookup"><span data-stu-id="42f49-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="42f49-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="42f49-220">wsse11</span></span>|<span data-ttu-id="42f49-221">TBD – OASIS WSS 1.1 URI</span><span class="sxs-lookup"><span data-stu-id="42f49-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="42f49-222">wsu</span><span class="sxs-lookup"><span data-stu-id="42f49-222">wsu</span></span>|<span data-ttu-id="42f49-223">TBD – OASIS WSS 1.0 Utility URI</span><span class="sxs-lookup"><span data-stu-id="42f49-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="42f49-224">ds</span><span class="sxs-lookup"><span data-stu-id="42f49-224">ds</span></span>|<span data-ttu-id="42f49-225">TBD – W3C XMLDSig URI</span><span class="sxs-lookup"><span data-stu-id="42f49-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="42f49-226">wst</span><span class="sxs-lookup"><span data-stu-id="42f49-226">wst</span></span>|<span data-ttu-id="42f49-227">TBD – WS-Trust 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="42f49-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="42f49-228">wssc</span><span class="sxs-lookup"><span data-stu-id="42f49-228">wssc</span></span>|<span data-ttu-id="42f49-229">TBD – WS-SecureConversation 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="42f49-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="42f49-230">wsaw</span><span class="sxs-lookup"><span data-stu-id="42f49-230">wsaw</span></span>|<span data-ttu-id="42f49-231">TBD - WS-Addressing policy namespace</span><span class="sxs-lookup"><span data-stu-id="42f49-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="42f49-232">wsp</span><span class="sxs-lookup"><span data-stu-id="42f49-232">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="42f49-233">mssp</span><span class="sxs-lookup"><span data-stu-id="42f49-233">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="42f49-234">1.權杖設定檔</span><span class="sxs-lookup"><span data-stu-id="42f49-234">1. Token Profiles</span></span>  
 <span data-ttu-id="42f49-235">Web 服務安全性規格會以安全性權杖來表示認證。</span><span class="sxs-lookup"><span data-stu-id="42f49-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="42f49-236">WCF 支援下列權杖類型：</span><span class="sxs-lookup"><span data-stu-id="42f49-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="42f49-237">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="42f49-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="42f49-238">WCF 會遵循 UsernameToken10 和 UsernameToken11 設定檔，具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="42f49-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="42f49-239">R1101 UsernameToken\Password 項目上的 PasswordType 屬性必須被省略，或者必須具有值 #PasswordText (預設)。</span><span class="sxs-lookup"><span data-stu-id="42f49-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="42f49-240">使用擴充性，便可以實作 #PasswordDigest。</span><span class="sxs-lookup"><span data-stu-id="42f49-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="42f49-241">據觀察，#PasswordDigest 通常會被誤認是具備足夠安全性的密碼保護機制。</span><span class="sxs-lookup"><span data-stu-id="42f49-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="42f49-242">但是 #PasswordDigest 無法取代 UsernameToken 加密。</span><span class="sxs-lookup"><span data-stu-id="42f49-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="42f49-243">#PasswordDigest 的主要目標是防禦重新執行攻擊。</span><span class="sxs-lookup"><span data-stu-id="42f49-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="42f49-244">在 WCF 驗證模式中，使用訊息簽章來降低重新執行攻擊威脅。</span><span class="sxs-lookup"><span data-stu-id="42f49-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="42f49-245">B1102 WCF 永遠不會發出 UsernameToken 的 Nonce 和 Created 子項目。</span><span class="sxs-lookup"><span data-stu-id="42f49-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="42f49-246">這些子元素是為了協助進行重新執行偵測。</span><span class="sxs-lookup"><span data-stu-id="42f49-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="42f49-247">WCF 會改用訊息簽章。</span><span class="sxs-lookup"><span data-stu-id="42f49-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="42f49-248">OASIS WSS SOAP 訊息安全性 UsernameToken 設定檔 1.1 (UsernameToken11) 從密碼功能引入金鑰衍生。</span><span class="sxs-lookup"><span data-stu-id="42f49-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="42f49-249">B1103 UsernameToken 密碼不能做為金鑰衍生，也不能用於密碼編譯作業。</span><span class="sxs-lookup"><span data-stu-id="42f49-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="42f49-250">基本原理：密碼通常被視為太弱，無法用於密碼編譯作業。</span><span class="sxs-lookup"><span data-stu-id="42f49-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="42f49-251">1.2 X509 權杖</span><span class="sxs-lookup"><span data-stu-id="42f49-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="42f49-252">WCF 支援 X509v3 憑證做為認證類型，並遵循 X509TokenProfile1.0 和 X509TokenProfile1.1，具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="42f49-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="42f49-253">R1201 當包含 X509v3 憑證時，BinarySecurityToken 項目上的 ValueType 屬性必須具有值 #X509v3。</span><span class="sxs-lookup"><span data-stu-id="42f49-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="42f49-254">WSS X509 權杖設定檔 1.0 和 1.1 也會將 #X509PKIPathv1 和 #PKCS7 定義為實值型別。</span><span class="sxs-lookup"><span data-stu-id="42f49-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="42f49-255">WCF 不支援這些型別。</span><span class="sxs-lookup"><span data-stu-id="42f49-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="42f49-256">R1202 如果 SubjectKeyIdentifier (SKI) 延伸出現在 X509 憑證中，則 wsse:KeyIdentifier 應該當做權杖的外部參考，並且使用 ValueType 屬性做為 #X509SubjectKeyIdentifier，而它的內容做為憑證 SKI 延伸 base64 編碼值。</span><span class="sxs-lookup"><span data-stu-id="42f49-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="42f49-257">SKI 參考已廣泛實作，且已證實為高度互通的外部參考型別。</span><span class="sxs-lookup"><span data-stu-id="42f49-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="42f49-258">R1203 X509 安全性權杖的外部參考不可使用 ds:X509IssuerSerial。</span><span class="sxs-lookup"><span data-stu-id="42f49-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="42f49-259">R1204 如果 X509TokenProfile1.1 正在使用中，則 X509 安全性權杖的外部參考應使用 WS-Security 1.1 所引入的指紋。</span><span class="sxs-lookup"><span data-stu-id="42f49-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="42f49-260">WCF 支援 X509IssuerSerial。</span><span class="sxs-lookup"><span data-stu-id="42f49-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="42f49-261">不過有 x509issuerserial 的互通性問題：WCF 會使用字串來比較 X509IssuerSerial 的兩個值。</span><span class="sxs-lookup"><span data-stu-id="42f49-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="42f49-262">因此如果其中一個的主體名稱的元件重新排序，而且會將傳送至 WCF 服務參考的憑證，它可能會找到。</span><span class="sxs-lookup"><span data-stu-id="42f49-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="42f49-263">1.3 Kerberos 權杖</span><span class="sxs-lookup"><span data-stu-id="42f49-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="42f49-264">WCF 支援 kerberostokenprofile1.1，但受以進行 Windows 驗證，具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="42f49-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="42f49-265">R1301 依照 GSS_API 和 Kerberos 規格定義，Kerberos 權杖必須具有 GSS 包裝的 Kerberos v4 AP_REQ 值，而且必須具有值為 #GSS_Kerberosv5_AP_REQ 的 ValueType 屬性。</span><span class="sxs-lookup"><span data-stu-id="42f49-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="42f49-266">WCF 使用 GSS 包裝的 Kerberos AP-REQ，不 AP-REQ</span><span class="sxs-lookup"><span data-stu-id="42f49-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="42f49-267">這是安全性的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="42f49-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="42f49-268">1.4 SAML v1.1 權杖</span><span class="sxs-lookup"><span data-stu-id="42f49-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="42f49-269">WCF 支援 SAML v1.1 權杖 WSS SAML 權杖設定檔 1.0 和 1.1 版。</span><span class="sxs-lookup"><span data-stu-id="42f49-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="42f49-270">它也可以實作其他版本的 SAML 權杖格式。</span><span class="sxs-lookup"><span data-stu-id="42f49-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="42f49-271">1.5 安全性內容權杖</span><span class="sxs-lookup"><span data-stu-id="42f49-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="42f49-272">WCF 支援的安全性內容權杖 (SCT) Ws-securecoversation 中引入。</span><span class="sxs-lookup"><span data-stu-id="42f49-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="42f49-273">SCT 是用來表示 SecureConversation 和二進位交涉通訊協定 TLS 和 SSPI 中所建立的安全性內容，說明如下。</span><span class="sxs-lookup"><span data-stu-id="42f49-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="42f49-274">2.通用訊息安全性參數</span><span class="sxs-lookup"><span data-stu-id="42f49-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="42f49-275">2.1 TimeStamp</span><span class="sxs-lookup"><span data-stu-id="42f49-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="42f49-276">時間戳記存在是使用 <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> 類別的 <xref:System.ServiceModel.Channels.SecurityBindingElement> 屬性加以控制。</span><span class="sxs-lookup"><span data-stu-id="42f49-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="42f49-277">WCF 一律會序列化 wsse: timestamp 使用 wsse： 建立和 wsse: Expires 欄位。</span><span class="sxs-lookup"><span data-stu-id="42f49-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="42f49-278">使用簽章時，一定會簽署 wsse:TimeStamp。</span><span class="sxs-lookup"><span data-stu-id="42f49-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="42f49-279">2.2 保護順序</span><span class="sxs-lookup"><span data-stu-id="42f49-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="42f49-280">WCF 支援訊息保護順序 「 簽署後加密 」 和 「 加密後簽署 」 (安全性原則 1.1)。</span><span class="sxs-lookup"><span data-stu-id="42f49-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="42f49-281">基於下列理由，建議使用「簽署後加密」：除非使用 WS-Security 1.1 SignatureConfirmation 機制，否則使用「加密後簽署」保護的訊息容易遭受簽章替換攻擊，而且加密內容上的簽章會造成稽核困難。</span><span class="sxs-lookup"><span data-stu-id="42f49-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="42f49-282">2.3 簽章保護</span><span class="sxs-lookup"><span data-stu-id="42f49-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="42f49-283">使用「加密後簽署」時，建議保護簽章，以防止暴力密碼破解攻擊猜測加密內容或簽署金鑰 (特別是在自訂權杖與弱式金鑰內容搭配使用時)。</span><span class="sxs-lookup"><span data-stu-id="42f49-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="42f49-284">2.4 演算法組合</span><span class="sxs-lookup"><span data-stu-id="42f49-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="42f49-285">WCF 支援安全性原則 1.1 中列出的所有演算法組合。</span><span class="sxs-lookup"><span data-stu-id="42f49-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="42f49-286">2.5 金鑰衍生</span><span class="sxs-lookup"><span data-stu-id="42f49-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="42f49-287">WCF 會使用"的對稱金鑰的金鑰衍生 」，如 Ws-secureconversation 中所述。</span><span class="sxs-lookup"><span data-stu-id="42f49-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="42f49-288">2.6 簽章確認</span><span class="sxs-lookup"><span data-stu-id="42f49-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="42f49-289">簽章確認可以防禦攔截式攻擊，以保護簽章組。</span><span class="sxs-lookup"><span data-stu-id="42f49-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="42f49-290">2.7 安全性標頭配置</span><span class="sxs-lookup"><span data-stu-id="42f49-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="42f49-291">每個驗證模式都會描述安全性標頭的某種配置。</span><span class="sxs-lookup"><span data-stu-id="42f49-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="42f49-292">安全性標頭中的項目是半排序的。</span><span class="sxs-lookup"><span data-stu-id="42f49-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="42f49-293">為了定義安全性標頭子項目的順序，WS-Security 原則會定義下列安全性標頭配置模式：</span><span class="sxs-lookup"><span data-stu-id="42f49-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="42f49-294">Strict</span><span class="sxs-lookup"><span data-stu-id="42f49-294">Strict</span></span>|<span data-ttu-id="42f49-295">根據「使用前宣告」的一般原則，遵循安全性原則 7.7.1 一節中所述的編號配置規則，將項目加入至安全性標頭中。</span><span class="sxs-lookup"><span data-stu-id="42f49-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="42f49-296">Lax</span><span class="sxs-lookup"><span data-stu-id="42f49-296">Lax</span></span>|<span data-ttu-id="42f49-297">項目會加入至安全性標頭，以任何順序符合 WSS:SOAP 訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="42f49-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="42f49-298">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="42f49-298">LaxTimestampFirst</span></span>|<span data-ttu-id="42f49-299">與 Lax 相同，除了安全性標頭中的第一個項目必須是 wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="42f49-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="42f49-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="42f49-300">LaxTimestampLast</span></span>|<span data-ttu-id="42f49-301">與 Lax 相同，除了安全性標頭中的最後一個項目必須是 wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="42f49-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="42f49-302">WCF 安全性標頭配置支援所有的四種模式。</span><span class="sxs-lookup"><span data-stu-id="42f49-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="42f49-303">下列驗證模式的安全性標頭結構和訊息範例都遵循 "Strict" 模式。</span><span class="sxs-lookup"><span data-stu-id="42f49-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="42f49-304">2.通用訊息安全性參數</span><span class="sxs-lookup"><span data-stu-id="42f49-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="42f49-305">本章節提供每個驗證模式的範例原則，並提供範例來示範用戶端和服務交換訊息中的安全性標頭結構。</span><span class="sxs-lookup"><span data-stu-id="42f49-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="42f49-306">6.1 傳輸保護</span><span class="sxs-lookup"><span data-stu-id="42f49-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="42f49-307">WCF 會提供五個使用安全傳輸來保護訊息的驗證模式: UserNameOverTransport、 CertificateOverTransport、 KerberosOverTransport、 IssuedTokenOverTransport 和 SspiNegotiatedOverTransport。</span><span class="sxs-lookup"><span data-stu-id="42f49-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="42f49-308">這些驗證模式使用 SecurityPolicy 中所述的傳輸繫結加以建構。</span><span class="sxs-lookup"><span data-stu-id="42f49-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="42f49-309">對於 UserNameOverTransport 驗證模式，UsernameToken 是已簽署的支援權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="42f49-310">對於其他驗證模式，此權杖會顯示為已簽署 (Signed) 的簽署 (Endorsing) 權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="42f49-311">SecurityPolicy 的附錄 C.1.2 和 C.1.3 詳細描述了安全性標頭配置。</span><span class="sxs-lookup"><span data-stu-id="42f49-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="42f49-312">下列範例安全性標頭示範指定之驗證模式的 Strict 配置。</span><span class="sxs-lookup"><span data-stu-id="42f49-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="42f49-313">權杖的 "Derived Keys" 屬性值一定是 "false"。</span><span class="sxs-lookup"><span data-stu-id="42f49-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="42f49-314">傳輸繫結的各種屬性值如下：</span><span class="sxs-lookup"><span data-stu-id="42f49-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="42f49-315">時間戳記：true</span><span class="sxs-lookup"><span data-stu-id="42f49-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="42f49-316">安全性標頭配置：Strict</span><span class="sxs-lookup"><span data-stu-id="42f49-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="42f49-317">演算法套件：Basic256</span><span class="sxs-lookup"><span data-stu-id="42f49-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="42f49-318">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="42f49-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="42f49-319">在這個驗證模式中，用戶端會使用使用者名稱權杖來進行驗證，這個權杖出現在 SOAP 層中做為已簽署的支援權杖，且一定會從啟動器傳送至收件者。</span><span class="sxs-lookup"><span data-stu-id="42f49-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="42f49-320">服務會在傳輸層上使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="42f49-321">使用的繫結為傳輸繫結。</span><span class="sxs-lookup"><span data-stu-id="42f49-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="42f49-322">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-322">Policy</span></span>  
  
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
  
 <span data-ttu-id="42f49-323">安全性標頭配置</span><span class="sxs-lookup"><span data-stu-id="42f49-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="42f49-324">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-324">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-325">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="42f49-326">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="42f49-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="42f49-327">在這個驗證模式中，用戶端會使用 X.509 憑證來進行驗證，這個憑證出現在 SOAP 層中做為簽署支援權杖，且一定會從啟動器傳送至收件者。</span><span class="sxs-lookup"><span data-stu-id="42f49-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="42f49-328">服務會在傳輸層上使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="42f49-329">使用的繫結為傳輸繫結。</span><span class="sxs-lookup"><span data-stu-id="42f49-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="42f49-330">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-330">Policy</span></span>  
  
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
  
 <span data-ttu-id="42f49-331">安全性標頭配置</span><span class="sxs-lookup"><span data-stu-id="42f49-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="42f49-332">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-332">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-333">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="42f49-334">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="42f49-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="42f49-335">在這個驗證模式中，用戶端本身不會向服務驗證，但會出示安全性權杖服務 (STS) 所發出的權杖，並證明得知共用金鑰。</span><span class="sxs-lookup"><span data-stu-id="42f49-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="42f49-336">發出的權杖出現在 SOAP 層中做為簽署支援權杖，且一定會從啟動器傳送至收件者。</span><span class="sxs-lookup"><span data-stu-id="42f49-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="42f49-337">服務會在傳輸層上使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="42f49-338">繫結為傳輸繫結。</span><span class="sxs-lookup"><span data-stu-id="42f49-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="42f49-339">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="42f49-340">安全性標頭配置</span><span class="sxs-lookup"><span data-stu-id="42f49-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="42f49-341">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-341">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-342">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="42f49-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="42f49-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="42f49-344">在這個驗證模式中，用戶端會使用 Kerberos 票證，向服務進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="42f49-345">Kerberos 權杖出現在 SOAP 層中做為簽署支援權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="42f49-346">服務會在傳輸層上使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="42f49-347">繫結為傳輸繫結。</span><span class="sxs-lookup"><span data-stu-id="42f49-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="42f49-348">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-348">Policy</span></span>  
  
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
  
 <span data-ttu-id="42f49-349">安全性標頭配置</span><span class="sxs-lookup"><span data-stu-id="42f49-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="42f49-350">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-350">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-351">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="42f49-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="42f49-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="42f49-353">在這個模式中，交涉通訊協定是用來執行用戶端和伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="42f49-354">如果可能則會使用 Kerberos，否則會使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="42f49-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="42f49-355">產生的 SCT 出現在 SOAP 層中做為簽署支援權杖，且一定會從啟動器傳送至收件者。</span><span class="sxs-lookup"><span data-stu-id="42f49-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="42f49-356">此外，服務也會在傳輸層上使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="42f49-357">使用的繫結為傳輸繫結。</span><span class="sxs-lookup"><span data-stu-id="42f49-357">The binding used is a transport binding.</span></span> <span data-ttu-id="42f49-358">"SPNEGO"（交涉） 描述 WCF 如何使用 SSPI 二進位交涉通訊協定與 Ws-trust 搭配。</span><span class="sxs-lookup"><span data-stu-id="42f49-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="42f49-359">本章節中的安全性標頭範例是在透過 SPNEGO 信號交換建立了 SCT 之後。</span><span class="sxs-lookup"><span data-stu-id="42f49-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="42f49-360">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-360">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="42f49-361">安全性標頭範例</span><span class="sxs-lookup"><span data-stu-id="42f49-361">Security Header Examples</span></span>  
 <span data-ttu-id="42f49-362">一旦使用 WS-Trust 二進位交涉透過 SPNEGO 信號交換來建立安全性內容權杖，應用程式訊息就會有下列結構的安全性標頭。</span><span class="sxs-lookup"><span data-stu-id="42f49-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="42f49-363">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-363">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-364">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="42f49-365">6.2 使用 X.509 憑證來驗證服務</span><span class="sxs-lookup"><span data-stu-id="42f49-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="42f49-366">本章節描述下列驗證模式：MutualCertificate WSS1.0、MUTUAL CertificateDuplex、 MutualCertificate WSS1.1、ANONYMOUSFORCERTIFICATE、USERNAMEFORCERTIFICATE、 AnonymousForCertificate、 和 issuedtokenforcertificate 全部。</span><span class="sxs-lookup"><span data-stu-id="42f49-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="42f49-367">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="42f49-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="42f49-368">在這個驗證模式中，用戶端會使用 X.509 憑證來進行驗證，這個憑證出現在 SOAP 層中做為啟動器權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="42f49-369">服務也會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="42f49-370">使用的繫結為具有下列屬性值的非對稱式繫結：</span><span class="sxs-lookup"><span data-stu-id="42f49-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="42f49-371">啟動器權杖：用戶端的 X.509 憑證，其內含模式設定為 …/IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="42f49-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="42f49-372">收件者權杖：伺服器的 X.509 憑證，其內含模式設定.../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="42f49-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="42f49-373">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="42f49-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="42f49-374">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="42f49-375">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="42f49-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="42f49-376">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="42f49-377">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-378">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-379">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-379">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-380">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-380">Response</span></span>  
  
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
  
 <span data-ttu-id="42f49-381">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="42f49-382">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-382">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-383">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-383">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="42f49-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="42f49-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="42f49-385">在這個驗證模式中，用戶端會使用 X.509 憑證來進行驗證，這個憑證出現在 SOAP 層中做為啟動器權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="42f49-386">服務也會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="42f49-387">使用的繫結為具有下列屬性值的非對稱式繫結：</span><span class="sxs-lookup"><span data-stu-id="42f49-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="42f49-388">啟動器權杖：用戶端的 X509 憑證，內含模式設定為.../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="42f49-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="42f49-389">收件者權杖：伺服器的 X509 憑證，內含模式設定為.../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="42f49-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="42f49-390">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="42f49-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="42f49-391">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="42f49-392">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="42f49-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="42f49-393">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="42f49-394">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-395">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-396">要求和回應</span><span class="sxs-lookup"><span data-stu-id="42f49-396">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="42f49-397">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="42f49-398">要求和回應</span><span class="sxs-lookup"><span data-stu-id="42f49-398">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="42f49-399">6.2.3 搭配使用 SymmetricBinding 與 X.509 服務驗證</span><span class="sxs-lookup"><span data-stu-id="42f49-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="42f49-400">"WSS10" 會為使用 X509 權杖的案例提供有限支援。</span><span class="sxs-lookup"><span data-stu-id="42f49-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="42f49-401">例如，對於只使用服務 X509 權杖的訊息，則無法提供簽章和加密保護。</span><span class="sxs-lookup"><span data-stu-id="42f49-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="42f49-402">"WSS11" 引入 EncryptedKey 做為對稱式權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="42f49-403">現在，服務 X.509 憑證的暫時加密金鑰可以做為要求和回應訊息保護。</span><span class="sxs-lookup"><span data-stu-id="42f49-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="42f49-404">下面 6.4 節中描述的驗證模式 (Mode) 會使用這個模式 (Pattern)。</span><span class="sxs-lookup"><span data-stu-id="42f49-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="42f49-405">WS-SecurityPolicy 使用 SymmetricBinding 搭配服務 X509 權杖做為保護權杖，描述這個模式。</span><span class="sxs-lookup"><span data-stu-id="42f49-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="42f49-406">驗證模式 AnonymousForCertificate、UsernameForCertificate、MutualCertificate WSS11 和 IssuedTokenForCertificate 全部都會使用類似具有下列屬性值的 sp:SymmetricBinding 執行個體：</span><span class="sxs-lookup"><span data-stu-id="42f49-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="42f49-407">保護權杖：伺服器的 X509 憑證，內含模式設定為.../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="42f49-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="42f49-408">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="42f49-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="42f49-409">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="42f49-410">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="42f49-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="42f49-411">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="42f49-412">以上的驗證模式只有一個地方不同，那就是支援的權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="42f49-413">AnonymousForCertificate 沒有任何支援權杖，MutualCertificate WSS 1.1 會將用戶端的 X509 憑證當做簽署 (Endorsing) 支援權杖，UserNameForCertificate 會將 UserName 權杖當做已簽署 (Signed) 的支援權杖、IssuedTokenForCertificate 會將發出的權杖當做簽署 (Endorsing) 支援權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="42f49-414">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-414">Policy</span></span>  
  
 <span data-ttu-id="42f49-415">對稱式繫結</span><span class="sxs-lookup"><span data-stu-id="42f49-415">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="42f49-416">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="42f49-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="42f49-417">在這個驗證模式中，用戶端為匿名，而服務會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="42f49-418">使用的繫結為對稱式繫結的執行個體，如 6.4.2 中所述。</span><span class="sxs-lookup"><span data-stu-id="42f49-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="42f49-419">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-419">Policy</span></span>  
  
 <span data-ttu-id="42f49-420">如需繫結的詳細資訊，請參閱上面 6.2.3 中的「原則」。</span><span class="sxs-lookup"><span data-stu-id="42f49-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-421">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-422">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-422">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-423">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-423">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="42f49-424">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="42f49-425">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-425">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-426">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-426">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="42f49-427">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="42f49-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="42f49-428">在這個驗證模式中，用戶端會使用使用者名稱權杖，向服務進行驗證，這個權杖出現在 SOAP 層中做為已簽署的支援權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="42f49-429">服務會使用 X.509 憑證對用戶端進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="42f49-430">使用的繫結是對稱式繫結，其中的保護權杖是用戶端產生的金鑰，且以服務的公開金鑰來加密。</span><span class="sxs-lookup"><span data-stu-id="42f49-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="42f49-431">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-431">Policy</span></span>  
  
 <span data-ttu-id="42f49-432">如需繫結的詳細資訊，請參閱上面 6.2.3 中的「原則」。</span><span class="sxs-lookup"><span data-stu-id="42f49-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="42f49-433">已簽署的支援權杖</span><span class="sxs-lookup"><span data-stu-id="42f49-433">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-434">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-435">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-435">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-436">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-436">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="42f49-437">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="42f49-438">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-438">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-439">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-439">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="42f49-440">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="42f49-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="42f49-441">在這個驗證模式中，用戶端會使用 X.509 憑證來進行驗證，這個憑證出現在 SOAP 層中做為簽署支援權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="42f49-442">服務也會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="42f49-443">使用的繫結是對稱式繫結，其中的保護權杖是用戶端產生的金鑰，且以服務的公開金鑰來加密。</span><span class="sxs-lookup"><span data-stu-id="42f49-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="42f49-444">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-444">Policy</span></span>  
  
 <span data-ttu-id="42f49-445">如需繫結的詳細資訊，請參閱上面 6.2.3 中的「原則」。</span><span class="sxs-lookup"><span data-stu-id="42f49-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="42f49-446">簽署支援權杖</span><span class="sxs-lookup"><span data-stu-id="42f49-446">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-447">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-448">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-448">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-449">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-449">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="42f49-450">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="42f49-451">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-451">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-452">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-452">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="42f49-453">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="42f49-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="42f49-454">在這個驗證模式中，用戶端本身不會向服務驗證，但會出示 STS 所發出的權杖，並證明得知共用金鑰。</span><span class="sxs-lookup"><span data-stu-id="42f49-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="42f49-455">發出的權杖出現在 SOAP 層中做為簽署支援權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="42f49-456">服務會使用 X.509 憑證對用戶端進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="42f49-457">使用的繫結是對稱式繫結，其中的保護權杖是用戶端產生的金鑰，且以服務的公開金鑰來加密。</span><span class="sxs-lookup"><span data-stu-id="42f49-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="42f49-458">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-458">Policy</span></span>  
  
 <span data-ttu-id="42f49-459">如需繫結的詳細資訊，請參閱上面 6.2.3 中的「原則」。</span><span class="sxs-lookup"><span data-stu-id="42f49-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="42f49-460">簽署支援權杖</span><span class="sxs-lookup"><span data-stu-id="42f49-460">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-461">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-462">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-462">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-463">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-463">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="42f49-464">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="42f49-465">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-465">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-466">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-466">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="42f49-467">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="42f49-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="42f49-468">在這個驗證模式中，用戶端會使用 Kerberos 票證，向服務進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="42f49-469">相同的票證也會提供伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="42f49-470">使用的繫結為具有下列屬性的對稱式繫結：</span><span class="sxs-lookup"><span data-stu-id="42f49-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="42f49-471">保護權杖：Kerberos 票證，其內含模式設定來.../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="42f49-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="42f49-472">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="42f49-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="42f49-473">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="42f49-474">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="42f49-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="42f49-475">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="42f49-476">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-476">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-477">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-478">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-478">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-479">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-479">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="42f49-480">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="42f49-481">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="42f49-482">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="42f49-483">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="42f49-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="42f49-484">在這個驗證模式中，用戶端本身不會向服務驗證，但用戶端會出示 STS 所發出的權杖，並證明得知共用金鑰。</span><span class="sxs-lookup"><span data-stu-id="42f49-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="42f49-485">服務本身也不會向用戶端驗證，但 STS 會加密共用金鑰做為已發出權杖的一部分，只有服務才能解密金鑰。</span><span class="sxs-lookup"><span data-stu-id="42f49-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="42f49-486">使用的繫結為具有下列屬性的對稱式繫結：</span><span class="sxs-lookup"><span data-stu-id="42f49-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="42f49-487">保護權杖：發出的權杖，內含模式設定為.../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="42f49-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="42f49-488">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="42f49-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="42f49-489">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="42f49-490">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="42f49-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="42f49-491">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="42f49-492">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-492">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-493">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-494">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-494">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-495">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-495">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="42f49-496">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="42f49-497">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-497">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-498">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-498">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="42f49-499">6.5 使用 SslNegotiated 來驗證服務</span><span class="sxs-lookup"><span data-stu-id="42f49-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="42f49-500">本章節描述一組驗證模式，這些驗證模式使用對稱式繫結，並將基於 WS-SecureConversation (WS-SC) 的安全性內容權杖做為保護權杖，權杖的金鑰值是藉由在 WS-Trust (WS-T) RST/RSTR 訊息上執行 TLS 通訊協定交涉而來。</span><span class="sxs-lookup"><span data-stu-id="42f49-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="42f49-501">TLSNEGO 中會詳細描述使用 WS-Trust 的 TLS 信號交換實作。</span><span class="sxs-lookup"><span data-stu-id="42f49-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="42f49-502">在這裡的訊息範例中，假設具有相關安全性內容的 SCT 已透過信號交換而建立。</span><span class="sxs-lookup"><span data-stu-id="42f49-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="42f49-503">使用的繫結為具有下列屬性的對稱式繫結：</span><span class="sxs-lookup"><span data-stu-id="42f49-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="42f49-504">保護權杖：Sslcontexttoken，其內含模式設定為.../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="42f49-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="42f49-505">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="42f49-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="42f49-506">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="42f49-507">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="42f49-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="42f49-508">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="42f49-509">6.5.1 SslNegotiated 服務驗證的原則</span><span class="sxs-lookup"><span data-stu-id="42f49-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="42f49-510">本章節中所有驗證模式的原則都相似，只有一個不同之處，就是使用特定已簽署 (Signed) 的支援權杖或簽署 (Endorsing) 權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="42f49-511">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="42f49-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="42f49-512">在這個驗證模式中，用戶端為匿名，而服務會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="42f49-513">使用的繫結為對稱式繫結的執行個體，如上面 6.5.1 中所述。</span><span class="sxs-lookup"><span data-stu-id="42f49-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="42f49-514">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-514">Policy</span></span>  
  
 <span data-ttu-id="42f49-515">如需繫結的詳細資訊，請參閱上面 6.5.1 中的「原則」。</span><span class="sxs-lookup"><span data-stu-id="42f49-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-516">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-517">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-517">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-518">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-518">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="42f49-519">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="42f49-520">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-520">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-521">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-521">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="42f49-522">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="42f49-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="42f49-523">在這個驗證模式中，用戶端會使用使用者名稱權杖來進行驗證，這個權杖出現在 SOAP 層中做為已簽署的支援權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="42f49-524">服務會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="42f49-525">使用的繫結為對稱式繫結的執行個體，如 6.5.1 中所述。</span><span class="sxs-lookup"><span data-stu-id="42f49-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="42f49-526">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-526">Policy</span></span>  
  
 <span data-ttu-id="42f49-527">如需繫結的詳細資訊，請參閱上面的 6.5.1 一節。</span><span class="sxs-lookup"><span data-stu-id="42f49-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="42f49-528">已簽署的支援權杖</span><span class="sxs-lookup"><span data-stu-id="42f49-528">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-529">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-530">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-530">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-531">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-531">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="42f49-532">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="42f49-533">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-533">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-534">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-534">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="42f49-535">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="42f49-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="42f49-536">在這個驗證模式中，用戶端本身不會向服務驗證，但會出示 STS 所發出的權杖，並證明得知共用金鑰。</span><span class="sxs-lookup"><span data-stu-id="42f49-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="42f49-537">發出的權杖出現在 SOAP 層中做為簽署支援權杖。</span><span class="sxs-lookup"><span data-stu-id="42f49-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="42f49-538">服務會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="42f49-539">使用的繫結為對稱式繫結的執行個體，如上面 6.5.1 中所述。</span><span class="sxs-lookup"><span data-stu-id="42f49-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="42f49-540">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-540">Policy</span></span>  
  
 <span data-ttu-id="42f49-541">如需繫結的詳細資訊，請參閱上面的 6.5.1 一節。</span><span class="sxs-lookup"><span data-stu-id="42f49-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="42f49-542">簽署支援權杖</span><span class="sxs-lookup"><span data-stu-id="42f49-542">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-543">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-544">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-544">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-545">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-545">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="42f49-546">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="42f49-547">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-547">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-548">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-548">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="42f49-549">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="42f49-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="42f49-550">在這個驗證模式中，用戶端和服務會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="42f49-551">使用的繫結為對稱式繫結的執行個體，如上面 6.5.1 中所述。</span><span class="sxs-lookup"><span data-stu-id="42f49-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="42f49-552">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-552">Policy</span></span>  
  
 <span data-ttu-id="42f49-553">如需繫結的詳細資訊，請參閱上面的 6.5.1 一節。</span><span class="sxs-lookup"><span data-stu-id="42f49-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="42f49-554">簽署支援權杖</span><span class="sxs-lookup"><span data-stu-id="42f49-554">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-555">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-556">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-556">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-557">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-557">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="42f49-558">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="42f49-559">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-559">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-560">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-560">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="42f49-561">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="42f49-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="42f49-562">在這個驗證模式中，交涉通訊協定是用來執行用戶端和伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="42f49-563">如果可能則會使用 Kerberos，否則會使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="42f49-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="42f49-564">使用的繫結為具有下列屬性的對稱式繫結：</span><span class="sxs-lookup"><span data-stu-id="42f49-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="42f49-565">保護權杖：Spnegocontexttoken，其內含模式設定為.../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="42f49-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="42f49-566">權杖保護：False</span><span class="sxs-lookup"><span data-stu-id="42f49-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="42f49-567">整個標頭和本文簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="42f49-568">保護順序：SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="42f49-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="42f49-569">加密簽章：True</span><span class="sxs-lookup"><span data-stu-id="42f49-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="42f49-570">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-570">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-571">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-572">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-572">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-573">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-573">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="42f49-574">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="42f49-575">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-575">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-576">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-576">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="42f49-577">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="42f49-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="42f49-578">使用的繫結為對稱式繫結，其中的保護權杖是依據 WS-SecureConversation (WS-SC) 的 SCT。</span><span class="sxs-lookup"><span data-stu-id="42f49-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="42f49-579">SCT 是根據巢狀繫結使用 WS-Trust (WS-Trust) 或 WS-SecureConversation (WS-SC) 交涉而來，而巢狀繫結本身則是使用交涉通訊協定的對稱式繫結。</span><span class="sxs-lookup"><span data-stu-id="42f49-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="42f49-580">如果可能，交涉通訊協定會使用 Kerberos 來執行用戶端和伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="42f49-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="42f49-581">如果無法使用 Kerberos，則會退而使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="42f49-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="42f49-582">原則</span><span class="sxs-lookup"><span data-stu-id="42f49-582">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="42f49-583">安全性標頭範例：SignBeforeEncrypt、 EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="42f49-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="42f49-584">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-584">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-585">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-585">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="42f49-586">安全性標頭範例：EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="42f49-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="42f49-587">要求</span><span class="sxs-lookup"><span data-stu-id="42f49-587">Request</span></span>  
  
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
  
 <span data-ttu-id="42f49-588">回應</span><span class="sxs-lookup"><span data-stu-id="42f49-588">Response</span></span>  
  
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
