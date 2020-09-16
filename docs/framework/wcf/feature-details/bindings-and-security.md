---
title: 繫結和安全性
description: 瞭解如何為您的安全性需求選取正確的系結。 WCF 隨附的系統提供系結可提供快速的方法來程式設計 WCF 應用程式。
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
ms.openlocfilehash: 86b9a1d7b0c772a308b9f059bb31c1f489635300
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559398"
---
# <a name="bindings-and-security"></a><span data-ttu-id="3f579-104">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="3f579-104">Bindings and Security</span></span>

<span data-ttu-id="3f579-105">Windows Communication Foundation (WCF) 提供的系統提供系結，可讓您快速地為 WCF 應用程式進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="3f579-105">The system-provided bindings included with Windows Communication Foundation (WCF) offer a quick way to program WCF applications.</span></span> <span data-ttu-id="3f579-106">除了一個例外狀況以外，所有繫結預設都會啟用安全性配置。</span><span class="sxs-lookup"><span data-stu-id="3f579-106">With one exception, all the bindings have a default security scheme enabled.</span></span> <span data-ttu-id="3f579-107">本主題將根據您的安全性需求，協助您選取正確的繫結。</span><span class="sxs-lookup"><span data-stu-id="3f579-107">This topic helps you select the right binding for your security needs.</span></span>

<span data-ttu-id="3f579-108">如需 WCF 安全性的總覽，請參閱 [安全性概觀](security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3f579-108">For an overview of WCF security, see [Security Overview](security-overview.md).</span></span> <span data-ttu-id="3f579-109">如需使用系結程式設計 WCF 的詳細資訊，請參閱程式 [設計 Wcf 安全性](programming-wcf-security.md)。</span><span class="sxs-lookup"><span data-stu-id="3f579-109">For more information about programming WCF using bindings, see [Programming WCF Security](programming-wcf-security.md).</span></span>

<span data-ttu-id="3f579-110">如果您已經選取系結，您可以深入瞭解與安全性 [行為](security-behaviors-in-wcf.md)安全性相關聯的執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="3f579-110">If you have already selected a binding, you can find out more about the run-time behaviors that are associated with security in [Security Behaviors](security-behaviors-in-wcf.md).</span></span>

<span data-ttu-id="3f579-111">某些安全性功能無法使用系統提供的繫結進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="3f579-111">Some security functions are not programmable using the system-provided bindings.</span></span> <span data-ttu-id="3f579-112">如需使用自訂系結的更多控制，請參閱 [使用自訂](security-capabilities-with-custom-bindings.md)系結的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="3f579-112">For more control using a custom binding, see [Security Capabilities with Custom Bindings](security-capabilities-with-custom-bindings.md).</span></span>

## <a name="security-functions-of-bindings"></a><span data-ttu-id="3f579-113">繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="3f579-113">Security Functions of Bindings</span></span>

<span data-ttu-id="3f579-114">WCF 包含一些符合大部分需求的系統提供系結。</span><span class="sxs-lookup"><span data-stu-id="3f579-114">WCF includes a number of system-provided bindings that meet most needs.</span></span> <span data-ttu-id="3f579-115">如果特定繫結不敷使用，您也可以建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="3f579-115">If a particular binding does not suffice, you can also create a custom binding.</span></span> <span data-ttu-id="3f579-116">如需系統提供之系結的清單，請參閱 [系統提供](../system-provided-bindings.md)的系結。</span><span class="sxs-lookup"><span data-stu-id="3f579-116">For a list of system-provided bindings, see [System-Provided Bindings](../system-provided-bindings.md).</span></span> <span data-ttu-id="3f579-117">如需自訂系結的詳細資訊，請參閱 [自訂](../extending/custom-bindings.md)系結。</span><span class="sxs-lookup"><span data-stu-id="3f579-117">For more information about custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>

<span data-ttu-id="3f579-118">WCF 中的每個系結都有兩種形式：作為 API，以及做為設定檔中所使用的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="3f579-118">Every binding in WCF has two forms: as an API and as an XML element used in a configuration file.</span></span> <span data-ttu-id="3f579-119">例如， `WSHttpBinding` (API) 在中具有對應的 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="3f579-119">For example, the `WSHttpBinding` (API) has a counterpart in the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>

<span data-ttu-id="3f579-120">下列章節將列出每個繫結的兩種型式，並摘要說明其安全功能。</span><span class="sxs-lookup"><span data-stu-id="3f579-120">The following section lists both forms for each binding and summarizes the security features.</span></span>

### <a name="basichttp"></a><span data-ttu-id="3f579-121">BasicHttp</span><span class="sxs-lookup"><span data-stu-id="3f579-121">BasicHttp</span></span>

<span data-ttu-id="3f579-122">在程式碼中，使用 <xref:System.ServiceModel.BasicHttpBinding> 類別，在設定中使用 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="3f579-122">In code, use the <xref:System.ServiceModel.BasicHttpBinding> class; in configuration, use the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>

<span data-ttu-id="3f579-123">這個繫結是設計用來與一系列現有技術搭配使用的，包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="3f579-123">This binding is designed for use with a range of existing technologies, including the following:</span></span>

- <span data-ttu-id="3f579-124">ASP.NET Web 服務 (ASMX) 第 1 版。</span><span class="sxs-lookup"><span data-stu-id="3f579-124">ASP.NET Web services (ASMX), version 1.</span></span>

- <span data-ttu-id="3f579-125">Web Service Enhancements (WSE) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f579-125">Web Service Enhancements (WSE) applications.</span></span>

- <span data-ttu-id="3f579-126">Web 服務互通性中定義的基本設定檔 (WS-I) 規格 (<https://go.microsoft.com/fwlink/?LinkId=38955>) 。</span><span class="sxs-lookup"><span data-stu-id="3f579-126">Basic Profile as defined in the Web Services Interoperability (WS-I) specification (<https://go.microsoft.com/fwlink/?LinkId=38955>).</span></span>

- <span data-ttu-id="3f579-127">如 WS-I 中定義的 Basic Security Profile。</span><span class="sxs-lookup"><span data-stu-id="3f579-127">Basic security profile as defined in WS-I.</span></span>

<span data-ttu-id="3f579-128">根據預設，這個繫結是不安全的。</span><span class="sxs-lookup"><span data-stu-id="3f579-128">By default, this binding is not secure.</span></span> <span data-ttu-id="3f579-129">它是針對與 ASMX 服務相互操作所設計的。</span><span class="sxs-lookup"><span data-stu-id="3f579-129">It is designed to interoperate with ASMX services.</span></span> <span data-ttu-id="3f579-130">啟用安全性時，繫結是設計成可用來與 Internet Information Services (IIS) 安全性機制進行順暢互通的，例如：基本的驗證、摘要和整合式 Windows 安全性。</span><span class="sxs-lookup"><span data-stu-id="3f579-130">When security is enabled, the binding is designed for seamless interoperation with Internet Information Services (IIS) security mechanisms, such as basic authentication, digest, and integrated Windows security.</span></span> <span data-ttu-id="3f579-131">如需詳細資訊，請參閱 [傳輸安全性概觀](transport-security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3f579-131">For more information, see [Transport Security Overview](transport-security-overview.md).</span></span> <span data-ttu-id="3f579-132">這個繫結支援下列各項：</span><span class="sxs-lookup"><span data-stu-id="3f579-132">This binding supports the following:</span></span>

- <span data-ttu-id="3f579-133">HTTPS 傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="3f579-133">HTTPS transport security.</span></span>

- <span data-ttu-id="3f579-134">HTTP 基本驗證。</span><span class="sxs-lookup"><span data-stu-id="3f579-134">HTTP basic authentication.</span></span>

- <span data-ttu-id="3f579-135">WS-Security。</span><span class="sxs-lookup"><span data-stu-id="3f579-135">WS-Security.</span></span>

<span data-ttu-id="3f579-136">如需詳細資訊，請參閱<xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType>和<xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3f579-136">For more information, see <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType>, and <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>

### <a name="wshttpbinding"></a><span data-ttu-id="3f579-137">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3f579-137">WSHttpBinding</span></span>

<span data-ttu-id="3f579-138">在程式碼中，使用 <xref:System.ServiceModel.WSHttpBinding> 類別，在設定中使用 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="3f579-138">In code, use the <xref:System.ServiceModel.WSHttpBinding> class; in configuration, use the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>

<span data-ttu-id="3f579-139">根據預設，這個繫結會實作 WS-Security 規格，並提供與實作 WS-\* 規格之服務的互通性。</span><span class="sxs-lookup"><span data-stu-id="3f579-139">By default, this binding implements the WS-Security specification and provides interoperability with services that implement the WS-\* specifications.</span></span> <span data-ttu-id="3f579-140">它支援下列各項：</span><span class="sxs-lookup"><span data-stu-id="3f579-140">It supports the following:</span></span>

- <span data-ttu-id="3f579-141">HTTPS 傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="3f579-141">HTTPS transport security.</span></span>

- <span data-ttu-id="3f579-142">WS-Security。</span><span class="sxs-lookup"><span data-stu-id="3f579-142">WS-Security.</span></span>

- <span data-ttu-id="3f579-143">用於驗證呼叫者的 HTTPS 傳輸保護 (具 SOAP 訊息認證安全性)。</span><span class="sxs-lookup"><span data-stu-id="3f579-143">HTTPS transport protection with SOAP message credential security for authenticating the caller.</span></span>

<span data-ttu-id="3f579-144">如需詳細資訊，請參閱、、、、、 <xref:System.ServiceModel.WSHttpSecurity> <xref:System.ServiceModel.MessageSecurityOverHttp> <xref:System.ServiceModel.MessageCredentialType> <xref:System.ServiceModel.SecurityMode> <xref:System.ServiceModel.HttpTransportSecurity> <xref:System.ServiceModel.HttpClientCredentialType> 和 <xref:System.ServiceModel.HttpProxyCredentialType> 。</span><span class="sxs-lookup"><span data-stu-id="3f579-144">For more information, see <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>, and <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>

### <a name="wsdualhttpbinding"></a><span data-ttu-id="3f579-145">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3f579-145">WSDualHttpBinding</span></span>

<span data-ttu-id="3f579-146">在程式碼中，使用 <xref:System.ServiceModel.WSDualHttpBinding> 類別，在設定中使用 [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="3f579-146">In code, use the <xref:System.ServiceModel.WSDualHttpBinding> class; in configuration, use the [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>

<span data-ttu-id="3f579-147">這個繫結設計的目的，是為了要提供雙工服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f579-147">This binding is designed to enable duplex service applications.</span></span> <span data-ttu-id="3f579-148">這個繫結實作了 WS-Security 規格，以提供訊息傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="3f579-148">This binding implements the WS-Security specification for message-based transfer security.</span></span> <span data-ttu-id="3f579-149">傳輸安全性在此無法使用。</span><span class="sxs-lookup"><span data-stu-id="3f579-149">Transport security is not available.</span></span> <span data-ttu-id="3f579-150">根據預設，這個繫結提供了下列功能：</span><span class="sxs-lookup"><span data-stu-id="3f579-150">By default, it provides the following features:</span></span>

- <span data-ttu-id="3f579-151">實作 WS-Reliable 訊息以提供可靠性。</span><span class="sxs-lookup"><span data-stu-id="3f579-151">Implements WS-Reliable Messaging for reliability.</span></span>

- <span data-ttu-id="3f579-152">實作 WS-Security 以提供傳輸安全性和驗證。</span><span class="sxs-lookup"><span data-stu-id="3f579-152">Implements WS-Security for transfer security and authentication.</span></span>

- <span data-ttu-id="3f579-153">使用 HTTP 傳遞訊息。</span><span class="sxs-lookup"><span data-stu-id="3f579-153">Uses HTTP for message delivery.</span></span>

- <span data-ttu-id="3f579-154">使用 text/XML 訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="3f579-154">Uses text/XML message encoding.</span></span>

 <span data-ttu-id="3f579-155">使用 WS-Security (訊息層安全性) 時，繫結可讓您設定下列參數：</span><span class="sxs-lookup"><span data-stu-id="3f579-155">Using WS-Security (message-layer security), the binding allows you to configure the following parameters:</span></span>

- <span data-ttu-id="3f579-156">安全性演算法組合，用於判斷密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="3f579-156">The security algorithm suite to determine the cryptographic algorithm.</span></span>

- <span data-ttu-id="3f579-157">可供下列項目運用的繫結選項：</span><span class="sxs-lookup"><span data-stu-id="3f579-157">Binding options for the following:</span></span>

  - <span data-ttu-id="3f579-158">經由超出範圍的方式，提供可在用戶端使用的服務認證。</span><span class="sxs-lookup"><span data-stu-id="3f579-158">Providing service credentials available out-of-band at the client.</span></span>

  - <span data-ttu-id="3f579-159">提供通道設定期間之服務交涉的服務認證。</span><span class="sxs-lookup"><span data-stu-id="3f579-159">Providing service credentials negotiated from the service as part of channel setup.</span></span>

<span data-ttu-id="3f579-160">如需詳細資訊，請參閱 <xref:System.ServiceModel.WSDualHttpSecurity> 和 <xref:System.ServiceModel.WSDualHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="3f579-160">For more information, see <xref:System.ServiceModel.WSDualHttpSecurity> and <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>

### <a name="nettcpbinding"></a><span data-ttu-id="3f579-161">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="3f579-161">NetTcpBinding</span></span>

<span data-ttu-id="3f579-162">在程式碼中，使用 <xref:System.ServiceModel.NetTcpBinding> 類別，在設定中使用 [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="3f579-162">In code, use the <xref:System.ServiceModel.NetTcpBinding> class; in configuration, use the [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>

<span data-ttu-id="3f579-163">這個繫結已針對跨電腦通訊進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="3f579-163">This binding is optimized for cross-machine communication.</span></span> <span data-ttu-id="3f579-164">根據預設，這個繫結具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="3f579-164">By default, it has the following characteristics:</span></span>

- <span data-ttu-id="3f579-165">實作傳輸層安全性。</span><span class="sxs-lookup"><span data-stu-id="3f579-165">Implements transport-layer security.</span></span>

- <span data-ttu-id="3f579-166">以 Windows 安全性提供傳輸安全性和驗證。</span><span class="sxs-lookup"><span data-stu-id="3f579-166">Leverages Windows security for transfer security and authentication.</span></span>

- <span data-ttu-id="3f579-167">使用 TCP 進行傳輸。</span><span class="sxs-lookup"><span data-stu-id="3f579-167">Uses TCP for transport.</span></span>

- <span data-ttu-id="3f579-168">實作二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="3f579-168">Implements binary message encoding.</span></span>

- <span data-ttu-id="3f579-169">實作 WS-Reliable 訊息。</span><span class="sxs-lookup"><span data-stu-id="3f579-169">Implements WS-Reliable Messaging.</span></span>

<span data-ttu-id="3f579-170">包括下列選項：</span><span class="sxs-lookup"><span data-stu-id="3f579-170">Options include the following:</span></span>

- <span data-ttu-id="3f579-171">訊息層安全性 (使用 WS-Security)。</span><span class="sxs-lookup"><span data-stu-id="3f579-171">Message-layer security (using WS-Security).</span></span>

- <span data-ttu-id="3f579-172">使用訊息認證的傳輸安全性，其機密性和完整性是由透過 TCP 之上的傳輸層安全性 (TLS) 所提供，而授權的認證則是由 WS-Security 提供。</span><span class="sxs-lookup"><span data-stu-id="3f579-172">Transport security with message credential—confidentiality and integrity provided by Transport Layer Security (TLS) over TCP, and credentials for authorization provided by WS-Security.</span></span>

<span data-ttu-id="3f579-173">如需詳細資訊，請參閱、、、 <xref:System.ServiceModel.NetTcpSecurity> <xref:System.ServiceModel.TcpTransportSecurity> <xref:System.ServiceModel.TcpClientCredentialType> <xref:System.ServiceModel.MessageSecurityOverTcp> 和 <xref:System.ServiceModel.MessageCredentialType> 。</span><span class="sxs-lookup"><span data-stu-id="3f579-173">For more information, see <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp>, and <xref:System.ServiceModel.MessageCredentialType>.</span></span>

### <a name="netnamedpipebinding"></a><span data-ttu-id="3f579-174">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="3f579-174">NetNamedPipeBinding</span></span>

<span data-ttu-id="3f579-175">在程式碼中，使用 <xref:System.ServiceModel.NetNamedPipeBinding> 類別，在設定中使用 [\<netNamedPipeBinding>](../../configure-apps/file-schema/wcf/netnamedpipebinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="3f579-175">In code, use the <xref:System.ServiceModel.NetNamedPipeBinding> class; in configuration, use the [\<netNamedPipeBinding>](../../configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>

<span data-ttu-id="3f579-176">這個繫結已針對跨處理序通訊進行最佳化 (通常是在同一部電腦上)。</span><span class="sxs-lookup"><span data-stu-id="3f579-176">This binding is optimized for cross-process communication (usually on the same machine).</span></span> <span data-ttu-id="3f579-177">根據預設，這個繫結具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="3f579-177">By default, this binding has the following characteristics:</span></span>

- <span data-ttu-id="3f579-178">使用傳輸安全性進行訊息傳輸和驗證。</span><span class="sxs-lookup"><span data-stu-id="3f579-178">Uses transport security for message transfer and authentication.</span></span>

- <span data-ttu-id="3f579-179">使用具名管道 (Named Pipe) 傳遞訊息。</span><span class="sxs-lookup"><span data-stu-id="3f579-179">Uses named pipes for message delivery.</span></span>

- <span data-ttu-id="3f579-180">實作二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="3f579-180">Implements binary message encoding.</span></span>

- <span data-ttu-id="3f579-181">加密和訊息簽署。</span><span class="sxs-lookup"><span data-stu-id="3f579-181">Encryption and message signing.</span></span>

<span data-ttu-id="3f579-182">包括下列選項：</span><span class="sxs-lookup"><span data-stu-id="3f579-182">Options include the following:</span></span>

- <span data-ttu-id="3f579-183">使用 Windows 安全性進行驗證。</span><span class="sxs-lookup"><span data-stu-id="3f579-183">Authentication using Windows security.</span></span>

<span data-ttu-id="3f579-184">如需詳細資訊，請參閱<xref:System.ServiceModel.NetNamedPipeSecurity>、<xref:System.ServiceModel.NetNamedPipeSecurityMode>和<xref:System.ServiceModel.NamedPipeTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="3f579-184">For more information, see <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode>, and <xref:System.ServiceModel.NamedPipeTransportSecurity>.</span></span>

### <a name="msmqintegrationbinding"></a><span data-ttu-id="3f579-185">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="3f579-185">MsmqIntegrationBinding</span></span>

<span data-ttu-id="3f579-186">在程式碼中，使用 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 類別，在設定中使用 [\<msmqIntegrationBinding>](../../configure-apps/file-schema/wcf/msmqintegrationbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="3f579-186">In code, use the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> class; in configuration, use the [\<msmqIntegrationBinding>](../../configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>

<span data-ttu-id="3f579-187">這個系結已針對建立 WCF 用戶端和服務進行優化，這些用戶端與服務會與非 WCF Microsoft Message Queuing (MSMQ) 端點相交互操作。</span><span class="sxs-lookup"><span data-stu-id="3f579-187">This binding is optimized for creating WCF clients and services that interoperate with non-WCF Microsoft Message Queuing (MSMQ) endpoints.</span></span>

<span data-ttu-id="3f579-188">根據預設，這個繫結會使用傳輸安全性，並提供下列安全性特性：</span><span class="sxs-lookup"><span data-stu-id="3f579-188">By default, this binding uses transport security and provides the following security characteristics:</span></span>

- <span data-ttu-id="3f579-189">可以停用安全性 (無)。</span><span class="sxs-lookup"><span data-stu-id="3f579-189">Security can be disabled (None).</span></span>

- <span data-ttu-id="3f579-190">MSMQ 傳輸安全性 (傳輸)。</span><span class="sxs-lookup"><span data-stu-id="3f579-190">MSMQ transport security (Transport).</span></span>

<span data-ttu-id="3f579-191">如需詳細資訊，請參閱 <xref:System.ServiceModel.NetMsmqSecurity> 和 <xref:System.ServiceModel.NetMsmqSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="3f579-191">For more information, see <xref:System.ServiceModel.NetMsmqSecurity> and <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>

### <a name="netmsmqbinding"></a><span data-ttu-id="3f579-192">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="3f579-192">NetMsmqBinding</span></span>

<span data-ttu-id="3f579-193">在程式碼中，使用 <xref:System.ServiceModel.NetMsmqBinding> 類別，在設定中使用 [\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="3f579-193">In code, use the <xref:System.ServiceModel.NetMsmqBinding> class; in configuration, use the [\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md).</span></span>

<span data-ttu-id="3f579-194">這個系結的目的是要在建立需要 MSMQ 佇列訊息支援的 WCF 服務時使用。</span><span class="sxs-lookup"><span data-stu-id="3f579-194">This binding is intended for use when creating WCF services that require MSMQ queued message support.</span></span>

<span data-ttu-id="3f579-195">根據預設，這個繫結會使用傳輸安全性，並提供下列安全性特性：</span><span class="sxs-lookup"><span data-stu-id="3f579-195">By default, this binding uses transport security and provides the following security characteristics:</span></span>

- <span data-ttu-id="3f579-196">可以停用安全性 (無)。</span><span class="sxs-lookup"><span data-stu-id="3f579-196">Security can be disabled (None).</span></span>

- <span data-ttu-id="3f579-197">MSMQ 傳輸安全性 (傳輸)。</span><span class="sxs-lookup"><span data-stu-id="3f579-197">MSMQ transport security (Transport).</span></span>

- <span data-ttu-id="3f579-198">SOAP 訊息安全性 (訊息)。</span><span class="sxs-lookup"><span data-stu-id="3f579-198">SOAP-based message security (Message).</span></span>

- <span data-ttu-id="3f579-199">同時具有傳輸和訊息安全性 (兩者並存)。</span><span class="sxs-lookup"><span data-stu-id="3f579-199">Simultaneous Transport and Message security (Both).</span></span>

- <span data-ttu-id="3f579-200">支援的用戶端認證類型：無、Windows、UserName、憑證、IssuedToken。</span><span class="sxs-lookup"><span data-stu-id="3f579-200">Client Credential Types supported: None, Windows, UserName, Certificate, IssuedToken.</span></span>

<span data-ttu-id="3f579-201">只有在將安全性模式設定為 <xref:System.ServiceModel.MessageCredentialType.Certificate> 或 <xref:System.ServiceModel.NetMsmqSecurityMode.Both> 時，才會支援 <xref:System.ServiceModel.NetMsmqSecurityMode.Message> 認證。</span><span class="sxs-lookup"><span data-stu-id="3f579-201">The <xref:System.ServiceModel.MessageCredentialType.Certificate> credential is supported only when the security mode is set to either <xref:System.ServiceModel.NetMsmqSecurityMode.Both> or <xref:System.ServiceModel.NetMsmqSecurityMode.Message>.</span></span>

<span data-ttu-id="3f579-202">如需詳細資訊，請參閱 <xref:System.ServiceModel.MessageSecurityOverMsmq> 和 <xref:System.ServiceModel.MsmqTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="3f579-202">For more information, see <xref:System.ServiceModel.MessageSecurityOverMsmq> and <xref:System.ServiceModel.MsmqTransportSecurity>.</span></span>

### <a name="wsfederationhttpbinding"></a><span data-ttu-id="3f579-203">WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3f579-203">WSFederationHttpBinding</span></span>

<span data-ttu-id="3f579-204">在程式碼中，使用 <xref:System.ServiceModel.WSFederationHttpBinding> 類別，在設定中使用 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="3f579-204">In code, use the <xref:System.ServiceModel.WSFederationHttpBinding> class; in configuration, use the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>

<span data-ttu-id="3f579-205">根據預設，這個繫結會使用 WS-Security (訊息層安全性)。</span><span class="sxs-lookup"><span data-stu-id="3f579-205">By default, this binding uses WS-Security (message-layer security).</span></span>

<span data-ttu-id="3f579-206">如需詳細資訊，請參閱 [同盟](federation.md)、 <xref:System.ServiceModel.WSFederationHttpSecurity> 和 <xref:System.ServiceModel.WSFederationHttpSecurityMode> 。</span><span class="sxs-lookup"><span data-stu-id="3f579-206">For more information, see [Federation](federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>, and <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>

## <a name="custom-bindings"></a><span data-ttu-id="3f579-207">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="3f579-207">Custom Bindings</span></span>

<span data-ttu-id="3f579-208">如果系統提供的繫結程序都不符合您的需求，您可以以自訂的安全性繫結程序項目建立自訂繫結程序。</span><span class="sxs-lookup"><span data-stu-id="3f579-208">If none of the system-provided bindings meets you requirements, you can create a custom binding with a custom security binding element.</span></span> <span data-ttu-id="3f579-209">如需詳細資訊，請參閱 [使用自訂系結的安全性功能](security-capabilities-with-custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="3f579-209">For more information, see [Security Capabilities with Custom Bindings](security-capabilities-with-custom-bindings.md).</span></span>

## <a name="binding-choices"></a><span data-ttu-id="3f579-210">繫結選擇</span><span class="sxs-lookup"><span data-stu-id="3f579-210">Binding Choices</span></span>

<span data-ttu-id="3f579-211">下表摘要說明了安全性模式設定中提供的功能，也就是說，列出了當安全性模式設定為 `Transport`、`Message` 或 `TransportWithMessageCredential` 時可以使用的功能。</span><span class="sxs-lookup"><span data-stu-id="3f579-211">The following table summarizes the features offered in the security mode setting, that is, it lists the features available when the security mode is set to `Transport`, `Message`, or `TransportWithMessageCredential`.</span></span> <span data-ttu-id="3f579-212">此表可協助您找出應用程式所需的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="3f579-212">Use this table to help you find the security features your application requires.</span></span>

|<span data-ttu-id="3f579-213">設定</span><span class="sxs-lookup"><span data-stu-id="3f579-213">Setting</span></span>|<span data-ttu-id="3f579-214">特性</span><span class="sxs-lookup"><span data-stu-id="3f579-214">Features</span></span>|
|-------------|--------------|
|<span data-ttu-id="3f579-215">傳輸</span><span class="sxs-lookup"><span data-stu-id="3f579-215">Transport</span></span>|<span data-ttu-id="3f579-216">伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="3f579-216">Server authentication</span></span><br /><br /> <span data-ttu-id="3f579-217">用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="3f579-217">Client authentication</span></span><br /><br /> <span data-ttu-id="3f579-218">點對點安全性</span><span class="sxs-lookup"><span data-stu-id="3f579-218">Point-to-point security</span></span><br /><br /> <span data-ttu-id="3f579-219">互通性</span><span class="sxs-lookup"><span data-stu-id="3f579-219">Interoperability</span></span><br /><br /> <span data-ttu-id="3f579-220">硬體加速</span><span class="sxs-lookup"><span data-stu-id="3f579-220">Hardware acceleration</span></span><br /><br /> <span data-ttu-id="3f579-221">高輸送量</span><span class="sxs-lookup"><span data-stu-id="3f579-221">High throughput</span></span><br /><br /> <span data-ttu-id="3f579-222">安全的防火牆</span><span class="sxs-lookup"><span data-stu-id="3f579-222">Secure firewall</span></span><br /><br /> <span data-ttu-id="3f579-223">高延遲的應用程式</span><span class="sxs-lookup"><span data-stu-id="3f579-223">High-latency applications</span></span><br /><br /> <span data-ttu-id="3f579-224">多個躍點間重新加密</span><span class="sxs-lookup"><span data-stu-id="3f579-224">Re-encryption across multiple hops</span></span>|
|<span data-ttu-id="3f579-225">訊息</span><span class="sxs-lookup"><span data-stu-id="3f579-225">Message</span></span>|<span data-ttu-id="3f579-226">伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="3f579-226">Server authentication</span></span><br /><br /> <span data-ttu-id="3f579-227">用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="3f579-227">Client authentication</span></span><br /><br /> <span data-ttu-id="3f579-228">端對端安全性</span><span class="sxs-lookup"><span data-stu-id="3f579-228">End-to-end security</span></span><br /><br /> <span data-ttu-id="3f579-229">互通性</span><span class="sxs-lookup"><span data-stu-id="3f579-229">Interoperability</span></span><br /><br /> <span data-ttu-id="3f579-230">豐富的宣告</span><span class="sxs-lookup"><span data-stu-id="3f579-230">Rich claims</span></span><br /><br /> <span data-ttu-id="3f579-231">同盟</span><span class="sxs-lookup"><span data-stu-id="3f579-231">Federation</span></span><br /><br /> <span data-ttu-id="3f579-232">多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="3f579-232">Multifactor authentication</span></span><br /><br /> <span data-ttu-id="3f579-233">自訂權杖</span><span class="sxs-lookup"><span data-stu-id="3f579-233">Custom tokens</span></span><br /><br /> <span data-ttu-id="3f579-234">公證/時間戳記服務</span><span class="sxs-lookup"><span data-stu-id="3f579-234">Notary/timestamp service</span></span><br /><br /> <span data-ttu-id="3f579-235">高延遲的應用程式</span><span class="sxs-lookup"><span data-stu-id="3f579-235">High-latency applications</span></span><br /><br /> <span data-ttu-id="3f579-236">訊息簽章的持續性</span><span class="sxs-lookup"><span data-stu-id="3f579-236">Persistence of message signatures</span></span>|
|<span data-ttu-id="3f579-237">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="3f579-237">TransportWithMessageCredential</span></span>|<span data-ttu-id="3f579-238">伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="3f579-238">Server authentication</span></span><br /><br /> <span data-ttu-id="3f579-239">用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="3f579-239">Client authentication</span></span><br /><br /> <span data-ttu-id="3f579-240">點對點安全性</span><span class="sxs-lookup"><span data-stu-id="3f579-240">Point-to-point security</span></span><br /><br /> <span data-ttu-id="3f579-241">互通性</span><span class="sxs-lookup"><span data-stu-id="3f579-241">Interoperability</span></span><br /><br /> <span data-ttu-id="3f579-242">硬體加速</span><span class="sxs-lookup"><span data-stu-id="3f579-242">Hardware acceleration</span></span><br /><br /> <span data-ttu-id="3f579-243">高輸送量</span><span class="sxs-lookup"><span data-stu-id="3f579-243">High throughput</span></span><br /><br /> <span data-ttu-id="3f579-244">豐富的用戶端宣告</span><span class="sxs-lookup"><span data-stu-id="3f579-244">Rich client claims</span></span><br /><br /> <span data-ttu-id="3f579-245">同盟</span><span class="sxs-lookup"><span data-stu-id="3f579-245">Federation</span></span><br /><br /> <span data-ttu-id="3f579-246">多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="3f579-246">Multifactor authentication</span></span><br /><br /> <span data-ttu-id="3f579-247">自訂權杖</span><span class="sxs-lookup"><span data-stu-id="3f579-247">Custom tokens</span></span><br /><br /> <span data-ttu-id="3f579-248">安全的防火牆</span><span class="sxs-lookup"><span data-stu-id="3f579-248">Secure firewall</span></span><br /><br /> <span data-ttu-id="3f579-249">高延遲的應用程式</span><span class="sxs-lookup"><span data-stu-id="3f579-249">High-latency applications</span></span><br /><br /> <span data-ttu-id="3f579-250">多個躍點間重新加密</span><span class="sxs-lookup"><span data-stu-id="3f579-250">Re-encryption across multiple hops</span></span>|

<span data-ttu-id="3f579-251">下表列出支援各種模式設定的繫結。</span><span class="sxs-lookup"><span data-stu-id="3f579-251">The following table lists the bindings that support the various mode settings.</span></span> <span data-ttu-id="3f579-252">您可以從表格中選取一種繫結，以便用來建立您的服務端點。</span><span class="sxs-lookup"><span data-stu-id="3f579-252">Select a binding from the table to use to create your service endpoint.</span></span>

|<span data-ttu-id="3f579-253">繫結</span><span class="sxs-lookup"><span data-stu-id="3f579-253">Binding</span></span>|<span data-ttu-id="3f579-254">傳輸模式支援</span><span class="sxs-lookup"><span data-stu-id="3f579-254">Transport mode support</span></span>|<span data-ttu-id="3f579-255">訊息模式支援</span><span class="sxs-lookup"><span data-stu-id="3f579-255">Message mode support</span></span>|<span data-ttu-id="3f579-256">TransportWithMessageCredential 支援</span><span class="sxs-lookup"><span data-stu-id="3f579-256">TransportWithMessageCredential support</span></span>|
|-------------|----------------------------|--------------------------|--------------------------------------------|
|`BasicHttpBinding`|<span data-ttu-id="3f579-257">是</span><span class="sxs-lookup"><span data-stu-id="3f579-257">Yes</span></span>|<span data-ttu-id="3f579-258">是</span><span class="sxs-lookup"><span data-stu-id="3f579-258">Yes</span></span>|<span data-ttu-id="3f579-259">是</span><span class="sxs-lookup"><span data-stu-id="3f579-259">Yes</span></span>|
|`WSHttpBinding`|<span data-ttu-id="3f579-260">是</span><span class="sxs-lookup"><span data-stu-id="3f579-260">Yes</span></span>|<span data-ttu-id="3f579-261">是</span><span class="sxs-lookup"><span data-stu-id="3f579-261">Yes</span></span>|<span data-ttu-id="3f579-262">是</span><span class="sxs-lookup"><span data-stu-id="3f579-262">Yes</span></span>|
|`WSDualHttpBinding`|<span data-ttu-id="3f579-263">否</span><span class="sxs-lookup"><span data-stu-id="3f579-263">No</span></span>|<span data-ttu-id="3f579-264">是</span><span class="sxs-lookup"><span data-stu-id="3f579-264">Yes</span></span>|<span data-ttu-id="3f579-265">否</span><span class="sxs-lookup"><span data-stu-id="3f579-265">No</span></span>|
|`NetTcpBinding`|<span data-ttu-id="3f579-266">是</span><span class="sxs-lookup"><span data-stu-id="3f579-266">Yes</span></span>|<span data-ttu-id="3f579-267">是</span><span class="sxs-lookup"><span data-stu-id="3f579-267">Yes</span></span>|<span data-ttu-id="3f579-268">是</span><span class="sxs-lookup"><span data-stu-id="3f579-268">Yes</span></span>|
|`NetNamedPipeBinding`|<span data-ttu-id="3f579-269">是</span><span class="sxs-lookup"><span data-stu-id="3f579-269">Yes</span></span>|<span data-ttu-id="3f579-270">否</span><span class="sxs-lookup"><span data-stu-id="3f579-270">No</span></span>|<span data-ttu-id="3f579-271">否</span><span class="sxs-lookup"><span data-stu-id="3f579-271">No</span></span>|
|`NetMsmqBinding`|<span data-ttu-id="3f579-272">是</span><span class="sxs-lookup"><span data-stu-id="3f579-272">Yes</span></span>|<span data-ttu-id="3f579-273">是</span><span class="sxs-lookup"><span data-stu-id="3f579-273">Yes</span></span>|<span data-ttu-id="3f579-274">否</span><span class="sxs-lookup"><span data-stu-id="3f579-274">No</span></span>|
|`MsmqIntegrationBinding`|<span data-ttu-id="3f579-275">是</span><span class="sxs-lookup"><span data-stu-id="3f579-275">Yes</span></span>|<span data-ttu-id="3f579-276">否</span><span class="sxs-lookup"><span data-stu-id="3f579-276">No</span></span>|<span data-ttu-id="3f579-277">否</span><span class="sxs-lookup"><span data-stu-id="3f579-277">No</span></span>|
|`wsFederationHttpBinding`|<span data-ttu-id="3f579-278">否</span><span class="sxs-lookup"><span data-stu-id="3f579-278">No</span></span>|<span data-ttu-id="3f579-279">是</span><span class="sxs-lookup"><span data-stu-id="3f579-279">Yes</span></span>|<span data-ttu-id="3f579-280">是</span><span class="sxs-lookup"><span data-stu-id="3f579-280">Yes</span></span>|

## <a name="transport-credentials-in-bindings"></a><span data-ttu-id="3f579-281">繫結中的傳輸認證</span><span class="sxs-lookup"><span data-stu-id="3f579-281">Transport Credentials in Bindings</span></span>

<span data-ttu-id="3f579-282">下表列出在傳輸安全性模式中使用 `BasicHttpBinding` 或 `WSHttpBinding` 時，可以使用的用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="3f579-282">The following table lists the client credential types available when using either `BasicHttpBinding` or `WSHttpBinding` in transport security mode.</span></span>

|<span data-ttu-id="3f579-283">類型</span><span class="sxs-lookup"><span data-stu-id="3f579-283">Type</span></span>|<span data-ttu-id="3f579-284">描述</span><span class="sxs-lookup"><span data-stu-id="3f579-284">Description</span></span>|
|----------|-----------------|
|<span data-ttu-id="3f579-285">None</span><span class="sxs-lookup"><span data-stu-id="3f579-285">None</span></span>|<span data-ttu-id="3f579-286">指定用戶端不需要提出任何認證。</span><span class="sxs-lookup"><span data-stu-id="3f579-286">Specifies that the client does not need to present any credential.</span></span> <span data-ttu-id="3f579-287">這會轉譯成匿名用戶端。</span><span class="sxs-lookup"><span data-stu-id="3f579-287">This translates to an anonymous client.</span></span>|
|<span data-ttu-id="3f579-288">基本</span><span class="sxs-lookup"><span data-stu-id="3f579-288">Basic</span></span>|<span data-ttu-id="3f579-289">基本驗證。</span><span class="sxs-lookup"><span data-stu-id="3f579-289">Basic authentication.</span></span> <span data-ttu-id="3f579-290">如需詳細資訊，請參閱 RFC 2617 – HTTP 驗證：基本與摘要式驗證（可從取得） <https://go.microsoft.com/fwlink/?LinkId=84023> 。</span><span class="sxs-lookup"><span data-stu-id="3f579-290">For more information, see RFC 2617 – HTTP Authentication: Basic and Digest Authentication, available at <https://go.microsoft.com/fwlink/?LinkId=84023>.</span></span>|
|<span data-ttu-id="3f579-291">Digest</span><span class="sxs-lookup"><span data-stu-id="3f579-291">Digest</span></span>|<span data-ttu-id="3f579-292">摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="3f579-292">Digest authentication.</span></span> <span data-ttu-id="3f579-293">如需詳細資訊，請參閱 RFC 2617 – HTTP 驗證：基本與摘要式驗證（可從取得） <https://go.microsoft.com/fwlink/?LinkId=84023> 。</span><span class="sxs-lookup"><span data-stu-id="3f579-293">For more information, see RFC 2617 – HTTP Authentication: Basic and Digest Authentication, available at <https://go.microsoft.com/fwlink/?LinkId=84023>.</span></span>|
|<span data-ttu-id="3f579-294">NTLM</span><span class="sxs-lookup"><span data-stu-id="3f579-294">NTLM</span></span>|<span data-ttu-id="3f579-295">NT LAN Manager (NTLM) 驗證。</span><span class="sxs-lookup"><span data-stu-id="3f579-295">NT LAN Manager (NTLM) authentication.</span></span>|
|<span data-ttu-id="3f579-296">Windows</span><span class="sxs-lookup"><span data-stu-id="3f579-296">Windows</span></span>|<span data-ttu-id="3f579-297">Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="3f579-297">Windows authentication.</span></span>|
|<span data-ttu-id="3f579-298">憑證</span><span class="sxs-lookup"><span data-stu-id="3f579-298">Certificate</span></span>|<span data-ttu-id="3f579-299">使用憑證執行的驗證。</span><span class="sxs-lookup"><span data-stu-id="3f579-299">Authentication performed using a certificate.</span></span>|
|<span data-ttu-id="3f579-300">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="3f579-300">IssuedToken</span></span>|<span data-ttu-id="3f579-301">允許服務要求用戶端使用安全性權杖服務或 CardSpace 發出的權杖進行驗證。</span><span class="sxs-lookup"><span data-stu-id="3f579-301">Allows the service to require that the client be authenticated using a token issued by a security token service or by CardSpace.</span></span> <span data-ttu-id="3f579-302">如需詳細資訊，請參閱 [同盟和已發行的權杖](federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="3f579-302">For more information, see [Federation and Issued Tokens](federation-and-issued-tokens.md).</span></span>|

### <a name="message-client-credentials-in-bindings"></a><span data-ttu-id="3f579-303">繫結中的訊息用戶端認證</span><span class="sxs-lookup"><span data-stu-id="3f579-303">Message Client Credentials in Bindings</span></span>

<span data-ttu-id="3f579-304">下表列出在訊息安全性模式中使用繫結時，可以使用的用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="3f579-304">The following table lists the client credential types available when using a binding in Message security mode.</span></span>

|<span data-ttu-id="3f579-305">類型</span><span class="sxs-lookup"><span data-stu-id="3f579-305">Type</span></span>|<span data-ttu-id="3f579-306">描述</span><span class="sxs-lookup"><span data-stu-id="3f579-306">Description</span></span>|
|----------|-----------------|
|<span data-ttu-id="3f579-307">None</span><span class="sxs-lookup"><span data-stu-id="3f579-307">None</span></span>|<span data-ttu-id="3f579-308">允許服務與匿名用戶端互動。</span><span class="sxs-lookup"><span data-stu-id="3f579-308">Allows the service to interact with anonymous clients.</span></span>|
|<span data-ttu-id="3f579-309">Windows</span><span class="sxs-lookup"><span data-stu-id="3f579-309">Windows</span></span>|<span data-ttu-id="3f579-310">允許在 Windows 認證的已驗證內容中進行 SOAP 訊息交換。</span><span class="sxs-lookup"><span data-stu-id="3f579-310">Allows SOAP message exchanges to be made under the authenticated context of a Windows credential.</span></span>|
|<span data-ttu-id="3f579-311">UserName</span><span class="sxs-lookup"><span data-stu-id="3f579-311">UserName</span></span>|<span data-ttu-id="3f579-312">允許服務要求用戶端必須以使用者名稱認證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="3f579-312">Allows the service to require that the client be authenticated using a user name credential.</span></span> <span data-ttu-id="3f579-313">請注意，當安全性模式設定為時 `TransportWithMessageCredential` ，WCF 不支援傳送密碼摘要或使用密碼衍生金鑰，並針對訊息模式安全性使用這類金鑰。</span><span class="sxs-lookup"><span data-stu-id="3f579-313">Note that when the security mode is set to `TransportWithMessageCredential`, WCF does not support sending a password digest or deriving keys using password and using such keys for Message mode security.</span></span> <span data-ttu-id="3f579-314">因此，WCF 會在使用使用者名稱認證時強制保護傳輸。</span><span class="sxs-lookup"><span data-stu-id="3f579-314">As such, WCF enforces that the transport is secured when using user name credentials.</span></span>|
|<span data-ttu-id="3f579-315">憑證</span><span class="sxs-lookup"><span data-stu-id="3f579-315">Certificate</span></span>|<span data-ttu-id="3f579-316">允許服務要求用戶端使用憑證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="3f579-316">Allows the service to require that the client be authenticated using a certificate.</span></span>|
|<span data-ttu-id="3f579-317">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="3f579-317">IssuedToken</span></span>|<span data-ttu-id="3f579-318">允許服務使用安全性權杖服務提供自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="3f579-318">Allows the service to use a security token service to supply a custom token.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3f579-319">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f579-319">See also</span></span>

- [<span data-ttu-id="3f579-320">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="3f579-320">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="3f579-321">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="3f579-321">Securing Services and Clients</span></span>](securing-services-and-clients.md)
- [<span data-ttu-id="3f579-322">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="3f579-322">Selecting a Credential Type</span></span>](selecting-a-credential-type.md)
- [<span data-ttu-id="3f579-323">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="3f579-323">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="3f579-324">安全性行為</span><span class="sxs-lookup"><span data-stu-id="3f579-324">Security Behaviors</span></span>](security-behaviors-in-wcf.md)
- <span data-ttu-id="3f579-325">[Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3f579-325">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
