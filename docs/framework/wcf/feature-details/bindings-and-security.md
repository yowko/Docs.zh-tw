---
title: 繫結和安全性
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
ms.openlocfilehash: 63d3888df364d033b17972a5fd3ba3b851e00c42
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964430"
---
# <a name="bindings-and-security"></a><span data-ttu-id="c890b-102">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="c890b-102">Bindings and Security</span></span>

<span data-ttu-id="c890b-103">Windows Communication Foundation （WCF）隨附的系統提供系結，提供了一種程式設計 WCF 應用程式的快速方式。</span><span class="sxs-lookup"><span data-stu-id="c890b-103">The system-provided bindings included with Windows Communication Foundation (WCF) offer a quick way to program WCF applications.</span></span> <span data-ttu-id="c890b-104">除了一個例外狀況以外，所有繫結預設都會啟用安全性配置。</span><span class="sxs-lookup"><span data-stu-id="c890b-104">With one exception, all the bindings have a default security scheme enabled.</span></span> <span data-ttu-id="c890b-105">本主題將根據您的安全性需求，協助您選取正確的繫結。</span><span class="sxs-lookup"><span data-stu-id="c890b-105">This topic helps you select the right binding for your security needs.</span></span>

<span data-ttu-id="c890b-106">如需 WCF 安全性的總覽，請參閱[安全性總覽](../../../../docs/framework/wcf/feature-details/security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c890b-106">For an overview of WCF security, see [Security Overview](../../../../docs/framework/wcf/feature-details/security-overview.md).</span></span> <span data-ttu-id="c890b-107">如需使用系結進行 WCF 程式設計的詳細資訊，請參閱[Wcf 安全性程式設計](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)。</span><span class="sxs-lookup"><span data-stu-id="c890b-107">For more information about programming WCF using bindings, see [Programming WCF Security](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md).</span></span>

<span data-ttu-id="c890b-108">如果您已經選取系結，您可以在[安全性行為](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)中深入瞭解與安全性相關聯的執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="c890b-108">If you have already selected a binding, you can find out more about the run-time behaviors that are associated with security in [Security Behaviors](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).</span></span>

<span data-ttu-id="c890b-109">某些安全性功能無法使用系統提供的繫結進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="c890b-109">Some security functions are not programmable using the system-provided bindings.</span></span> <span data-ttu-id="c890b-110">如需使用自訂系結的更多控制，請參閱[使用自訂](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)系結的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="c890b-110">For more control using a custom binding, see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).</span></span>

## <a name="security-functions-of-bindings"></a><span data-ttu-id="c890b-111">繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="c890b-111">Security Functions of Bindings</span></span>

<span data-ttu-id="c890b-112">WCF 包含許多系統提供的系結，可滿足大部分的需求。</span><span class="sxs-lookup"><span data-stu-id="c890b-112">WCF includes a number of system-provided bindings that meet most needs.</span></span> <span data-ttu-id="c890b-113">如果特定繫結不敷使用，您也可以建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="c890b-113">If a particular binding does not suffice, you can also create a custom binding.</span></span> <span data-ttu-id="c890b-114">如需系統提供之系結的清單，請參閱[系統提供](../../../../docs/framework/wcf/system-provided-bindings.md)的系結。</span><span class="sxs-lookup"><span data-stu-id="c890b-114">For a list of system-provided bindings, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="c890b-115">如需自訂系結的詳細資訊，請參閱[自訂](../../../../docs/framework/wcf/extending/custom-bindings.md)系結。</span><span class="sxs-lookup"><span data-stu-id="c890b-115">For more information about custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>

<span data-ttu-id="c890b-116">WCF 中的每個系結都有兩種形式：作為 API，以及做為設定檔中所使用的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="c890b-116">Every binding in WCF has two forms: as an API and as an XML element used in a configuration file.</span></span> <span data-ttu-id="c890b-117">例如，`WSHttpBinding` （API）在[\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)中有一個對應的。</span><span class="sxs-lookup"><span data-stu-id="c890b-117">For example, the `WSHttpBinding` (API) has a counterpart in the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>

<span data-ttu-id="c890b-118">下列章節將列出每個繫結的兩種型式，並摘要說明其安全功能。</span><span class="sxs-lookup"><span data-stu-id="c890b-118">The following section lists both forms for each binding and summarizes the security features.</span></span>

### <a name="basichttp"></a><span data-ttu-id="c890b-119">BasicHttp</span><span class="sxs-lookup"><span data-stu-id="c890b-119">BasicHttp</span></span>

<span data-ttu-id="c890b-120">在程式碼中，使用 <xref:System.ServiceModel.BasicHttpBinding> 類別;在 [設定] 中，使用[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="c890b-120">In code, use the <xref:System.ServiceModel.BasicHttpBinding> class; in configuration, use the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>

<span data-ttu-id="c890b-121">這個繫結是設計用來與一系列現有技術搭配使用的，包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="c890b-121">This binding is designed for use with a range of existing technologies, including the following:</span></span>

- <span data-ttu-id="c890b-122">ASP.NET Web 服務 (ASMX) 第 1 版。</span><span class="sxs-lookup"><span data-stu-id="c890b-122">ASP.NET Web services (ASMX), version 1.</span></span>

- <span data-ttu-id="c890b-123">Web Service Enhancements (WSE) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c890b-123">Web Service Enhancements (WSE) applications.</span></span>

- <span data-ttu-id="c890b-124">基本設定檔，如 Web 服務互通性（WS-I）規格（<https://go.microsoft.com/fwlink/?LinkId=38955>）中所定義。</span><span class="sxs-lookup"><span data-stu-id="c890b-124">Basic Profile as defined in the Web Services Interoperability (WS-I) specification (<https://go.microsoft.com/fwlink/?LinkId=38955>).</span></span>

- <span data-ttu-id="c890b-125">如 WS-I 中定義的 Basic Security Profile。</span><span class="sxs-lookup"><span data-stu-id="c890b-125">Basic security profile as defined in WS-I.</span></span>

<span data-ttu-id="c890b-126">根據預設，這個繫結是不安全的。</span><span class="sxs-lookup"><span data-stu-id="c890b-126">By default, this binding is not secure.</span></span> <span data-ttu-id="c890b-127">它是針對與 ASMX 服務相互操作所設計的。</span><span class="sxs-lookup"><span data-stu-id="c890b-127">It is designed to interoperate with ASMX services.</span></span> <span data-ttu-id="c890b-128">啟用安全性時，繫結是設計成可用來與 Internet Information Services (IIS) 安全性機制進行順暢互通的，例如：基本的驗證、摘要和整合式 Windows 安全性。</span><span class="sxs-lookup"><span data-stu-id="c890b-128">When security is enabled, the binding is designed for seamless interoperation with Internet Information Services (IIS) security mechanisms, such as basic authentication, digest, and integrated Windows security.</span></span> <span data-ttu-id="c890b-129">如需詳細資訊，請參閱[傳輸安全性總覽](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c890b-129">For more information, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span> <span data-ttu-id="c890b-130">這個繫結支援下列各項：</span><span class="sxs-lookup"><span data-stu-id="c890b-130">This binding supports the following:</span></span>

- <span data-ttu-id="c890b-131">HTTPS 傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="c890b-131">HTTPS transport security.</span></span>

- <span data-ttu-id="c890b-132">HTTP 基本驗證。</span><span class="sxs-lookup"><span data-stu-id="c890b-132">HTTP basic authentication.</span></span>

- <span data-ttu-id="c890b-133">WS-Security。</span><span class="sxs-lookup"><span data-stu-id="c890b-133">WS-Security.</span></span>

<span data-ttu-id="c890b-134">如需詳細資訊，請參閱<xref:System.ServiceModel.BasicHttpSecurity>、<xref:System.ServiceModel.BasicHttpMessageSecurity>、<xref:System.ServiceModel.BasicHttpMessageCredentialType>，以及<xref:System.ServiceModel.BasicHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="c890b-134">For more information, see <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType>, and <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>

### <a name="wshttpbinding"></a><span data-ttu-id="c890b-135">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c890b-135">WSHttpBinding</span></span>

<span data-ttu-id="c890b-136">在程式碼中，使用 <xref:System.ServiceModel.WSHttpBinding> 類別;在 [設定] 中，使用[\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="c890b-136">In code, use the <xref:System.ServiceModel.WSHttpBinding> class; in configuration, use the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>

<span data-ttu-id="c890b-137">根據預設，這個繫結會實作 WS-Security 規格，並提供與實作 WS-\* 規格之服務的互通性。</span><span class="sxs-lookup"><span data-stu-id="c890b-137">By default, this binding implements the WS-Security specification and provides interoperability with services that implement the WS-\* specifications.</span></span> <span data-ttu-id="c890b-138">它支援下列各項：</span><span class="sxs-lookup"><span data-stu-id="c890b-138">It supports the following:</span></span>

- <span data-ttu-id="c890b-139">HTTPS 傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="c890b-139">HTTPS transport security.</span></span>

- <span data-ttu-id="c890b-140">WS-Security。</span><span class="sxs-lookup"><span data-stu-id="c890b-140">WS-Security.</span></span>

- <span data-ttu-id="c890b-141">用於驗證呼叫者的 HTTPS 傳輸保護 (具 SOAP 訊息認證安全性)。</span><span class="sxs-lookup"><span data-stu-id="c890b-141">HTTPS transport protection with SOAP message credential security for authenticating the caller.</span></span>

<span data-ttu-id="c890b-142">如需詳細資訊，請參閱 <xref:System.ServiceModel.WSHttpSecurity>、<xref:System.ServiceModel.MessageSecurityOverHttp>、<xref:System.ServiceModel.MessageCredentialType>、<xref:System.ServiceModel.SecurityMode>、<xref:System.ServiceModel.HttpTransportSecurity>、<xref:System.ServiceModel.HttpClientCredentialType>和 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="c890b-142">For more information, see <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>, and <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>

### <a name="wsdualhttpbinding"></a><span data-ttu-id="c890b-143">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c890b-143">WSDualHttpBinding</span></span>

<span data-ttu-id="c890b-144">在程式碼中，使用 <xref:System.ServiceModel.WSDualHttpBinding> 類別;在 [設定] 中，使用[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="c890b-144">In code, use the <xref:System.ServiceModel.WSDualHttpBinding> class; in configuration, use the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>

<span data-ttu-id="c890b-145">這個繫結設計的目的，是為了要提供雙工服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="c890b-145">This binding is designed to enable duplex service applications.</span></span> <span data-ttu-id="c890b-146">這個繫結實作了 WS-Security 規格，以提供訊息傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="c890b-146">This binding implements the WS-Security specification for message-based transfer security.</span></span> <span data-ttu-id="c890b-147">傳輸安全性在此無法使用。</span><span class="sxs-lookup"><span data-stu-id="c890b-147">Transport security is not available.</span></span> <span data-ttu-id="c890b-148">根據預設，這個繫結提供了下列功能：</span><span class="sxs-lookup"><span data-stu-id="c890b-148">By default, it provides the following features:</span></span>

- <span data-ttu-id="c890b-149">實作 WS-Reliable 訊息以提供可靠性。</span><span class="sxs-lookup"><span data-stu-id="c890b-149">Implements WS-Reliable Messaging for reliability.</span></span>

- <span data-ttu-id="c890b-150">實作 WS-Security 以提供傳輸安全性和驗證。</span><span class="sxs-lookup"><span data-stu-id="c890b-150">Implements WS-Security for transfer security and authentication.</span></span>

- <span data-ttu-id="c890b-151">使用 HTTP 傳遞訊息。</span><span class="sxs-lookup"><span data-stu-id="c890b-151">Uses HTTP for message delivery.</span></span>

- <span data-ttu-id="c890b-152">使用 text/XML 訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="c890b-152">Uses text/XML message encoding.</span></span>

 <span data-ttu-id="c890b-153">使用 WS-Security (訊息層安全性) 時，繫結可讓您設定下列參數：</span><span class="sxs-lookup"><span data-stu-id="c890b-153">Using WS-Security (message-layer security), the binding allows you to configure the following parameters:</span></span>

- <span data-ttu-id="c890b-154">安全性演算法組合，用於判斷密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="c890b-154">The security algorithm suite to determine the cryptographic algorithm.</span></span>

- <span data-ttu-id="c890b-155">可供下列項目運用的繫結選項：</span><span class="sxs-lookup"><span data-stu-id="c890b-155">Binding options for the following:</span></span>

  - <span data-ttu-id="c890b-156">經由超出範圍的方式，提供可在用戶端使用的服務認證。</span><span class="sxs-lookup"><span data-stu-id="c890b-156">Providing service credentials available out-of-band at the client.</span></span>

  - <span data-ttu-id="c890b-157">提供通道設定期間之服務交涉的服務認證。</span><span class="sxs-lookup"><span data-stu-id="c890b-157">Providing service credentials negotiated from the service as part of channel setup.</span></span>

<span data-ttu-id="c890b-158">如需詳細資訊，請參閱<xref:System.ServiceModel.WSDualHttpSecurity>和<xref:System.ServiceModel.WSDualHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="c890b-158">For more information, see <xref:System.ServiceModel.WSDualHttpSecurity> and <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>

### <a name="nettcpbinding"></a><span data-ttu-id="c890b-159">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="c890b-159">NetTcpBinding</span></span>

<span data-ttu-id="c890b-160">在程式碼中，使用 <xref:System.ServiceModel.NetTcpBinding> 類別;在 [設定] 中，使用[\<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="c890b-160">In code, use the <xref:System.ServiceModel.NetTcpBinding> class; in configuration, use the [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>

<span data-ttu-id="c890b-161">這個繫結已針對跨電腦通訊進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="c890b-161">This binding is optimized for cross-machine communication.</span></span> <span data-ttu-id="c890b-162">根據預設，這個繫結具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="c890b-162">By default, it has the following characteristics:</span></span>

- <span data-ttu-id="c890b-163">實作傳輸層安全性。</span><span class="sxs-lookup"><span data-stu-id="c890b-163">Implements transport-layer security.</span></span>

- <span data-ttu-id="c890b-164">以 Windows 安全性提供傳輸安全性和驗證。</span><span class="sxs-lookup"><span data-stu-id="c890b-164">Leverages Windows security for transfer security and authentication.</span></span>

- <span data-ttu-id="c890b-165">使用 TCP 進行傳輸。</span><span class="sxs-lookup"><span data-stu-id="c890b-165">Uses TCP for transport.</span></span>

- <span data-ttu-id="c890b-166">實作二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="c890b-166">Implements binary message encoding.</span></span>

- <span data-ttu-id="c890b-167">實作 WS-Reliable 訊息。</span><span class="sxs-lookup"><span data-stu-id="c890b-167">Implements WS-Reliable Messaging.</span></span>

<span data-ttu-id="c890b-168">這些選項包括：</span><span class="sxs-lookup"><span data-stu-id="c890b-168">Options include the following:</span></span>

- <span data-ttu-id="c890b-169">訊息層安全性 (使用 WS-Security)。</span><span class="sxs-lookup"><span data-stu-id="c890b-169">Message-layer security (using WS-Security).</span></span>

- <span data-ttu-id="c890b-170">使用訊息認證的傳輸安全性，其機密性和完整性是由透過 TCP 之上的傳輸層安全性 (TLS) 所提供，而授權的認證則是由 WS-Security 提供。</span><span class="sxs-lookup"><span data-stu-id="c890b-170">Transport security with message credential—confidentiality and integrity provided by Transport Layer Security (TLS) over TCP, and credentials for authorization provided by WS-Security.</span></span>

<span data-ttu-id="c890b-171">如需詳細資訊，請參閱 <xref:System.ServiceModel.NetTcpSecurity>、<xref:System.ServiceModel.TcpTransportSecurity>、<xref:System.ServiceModel.TcpClientCredentialType>、<xref:System.ServiceModel.MessageSecurityOverTcp>和 <xref:System.ServiceModel.MessageCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="c890b-171">For more information, see <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp>, and <xref:System.ServiceModel.MessageCredentialType>.</span></span>

### <a name="netnamedpipebinding"></a><span data-ttu-id="c890b-172">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="c890b-172">NetNamedPipeBinding</span></span>

<span data-ttu-id="c890b-173">在程式碼中，使用 <xref:System.ServiceModel.NetNamedPipeBinding> 類別;在 [設定] 中，使用[\<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)。</span><span class="sxs-lookup"><span data-stu-id="c890b-173">In code, use the <xref:System.ServiceModel.NetNamedPipeBinding> class; in configuration, use the [\<netNamedPipeBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>

<span data-ttu-id="c890b-174">這個繫結已針對跨處理序通訊進行最佳化 (通常是在同一部電腦上)。</span><span class="sxs-lookup"><span data-stu-id="c890b-174">This binding is optimized for cross-process communication (usually on the same machine).</span></span> <span data-ttu-id="c890b-175">根據預設，這個繫結具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="c890b-175">By default, this binding has the following characteristics:</span></span>

- <span data-ttu-id="c890b-176">使用傳輸安全性進行訊息傳輸和驗證。</span><span class="sxs-lookup"><span data-stu-id="c890b-176">Uses transport security for message transfer and authentication.</span></span>

- <span data-ttu-id="c890b-177">使用具名管道 (Named Pipe) 傳遞訊息。</span><span class="sxs-lookup"><span data-stu-id="c890b-177">Uses named pipes for message delivery.</span></span>

- <span data-ttu-id="c890b-178">實作二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="c890b-178">Implements binary message encoding.</span></span>

- <span data-ttu-id="c890b-179">加密和訊息簽署。</span><span class="sxs-lookup"><span data-stu-id="c890b-179">Encryption and message signing.</span></span>

<span data-ttu-id="c890b-180">這些選項包括：</span><span class="sxs-lookup"><span data-stu-id="c890b-180">Options include the following:</span></span>

- <span data-ttu-id="c890b-181">使用 Windows 安全性進行驗證。</span><span class="sxs-lookup"><span data-stu-id="c890b-181">Authentication using Windows security.</span></span>

<span data-ttu-id="c890b-182">如需詳細資訊，請參閱 <xref:System.ServiceModel.NetNamedPipeSecurity>、<xref:System.ServiceModel.NetNamedPipeSecurityMode> 和 <xref:System.ServiceModel.NamedPipeTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="c890b-182">For more information, see <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode>, and <xref:System.ServiceModel.NamedPipeTransportSecurity>.</span></span>

### <a name="msmqintegrationbinding"></a><span data-ttu-id="c890b-183">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="c890b-183">MsmqIntegrationBinding</span></span>

<span data-ttu-id="c890b-184">在程式碼中，使用 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 類別;在 [設定] 中，使用[\<msmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="c890b-184">In code, use the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> class; in configuration, use the [\<msmqIntegrationBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>

<span data-ttu-id="c890b-185">這個系結已針對建立與非 WCF Microsoft Message Queuing （MSMQ）端點互通的 WCF 用戶端和服務進行優化。</span><span class="sxs-lookup"><span data-stu-id="c890b-185">This binding is optimized for creating WCF clients and services that interoperate with non-WCF Microsoft Message Queuing (MSMQ) endpoints.</span></span>

<span data-ttu-id="c890b-186">根據預設，這個繫結會使用傳輸安全性，並提供下列安全性特性：</span><span class="sxs-lookup"><span data-stu-id="c890b-186">By default, this binding uses transport security and provides the following security characteristics:</span></span>

- <span data-ttu-id="c890b-187">可以停用安全性 (無)。</span><span class="sxs-lookup"><span data-stu-id="c890b-187">Security can be disabled (None).</span></span>

- <span data-ttu-id="c890b-188">MSMQ 傳輸安全性 (傳輸)。</span><span class="sxs-lookup"><span data-stu-id="c890b-188">MSMQ transport security (Transport).</span></span>

<span data-ttu-id="c890b-189">如需詳細資訊，請參閱<xref:System.ServiceModel.NetMsmqSecurity>和<xref:System.ServiceModel.NetMsmqSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="c890b-189">For more information, see <xref:System.ServiceModel.NetMsmqSecurity> and <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>

### <a name="netmsmqbinding"></a><span data-ttu-id="c890b-190">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="c890b-190">NetMsmqBinding</span></span>

<span data-ttu-id="c890b-191">在程式碼中，使用 <xref:System.ServiceModel.NetMsmqBinding> 類別;在 [設定] 中，使用[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="c890b-191">In code, use the <xref:System.ServiceModel.NetMsmqBinding> class; in configuration, use the [\<netMsmqBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md).</span></span>

<span data-ttu-id="c890b-192">此系結的目的是要在建立需要 MSMQ 佇列訊息支援的 WCF 服務時使用。</span><span class="sxs-lookup"><span data-stu-id="c890b-192">This binding is intended for use when creating WCF services that require MSMQ queued message support.</span></span>

<span data-ttu-id="c890b-193">根據預設，這個繫結會使用傳輸安全性，並提供下列安全性特性：</span><span class="sxs-lookup"><span data-stu-id="c890b-193">By default, this binding uses transport security and provides the following security characteristics:</span></span>

- <span data-ttu-id="c890b-194">可以停用安全性 (無)。</span><span class="sxs-lookup"><span data-stu-id="c890b-194">Security can be disabled (None).</span></span>

- <span data-ttu-id="c890b-195">MSMQ 傳輸安全性 (傳輸)。</span><span class="sxs-lookup"><span data-stu-id="c890b-195">MSMQ transport security (Transport).</span></span>

- <span data-ttu-id="c890b-196">SOAP 訊息安全性 (訊息)。</span><span class="sxs-lookup"><span data-stu-id="c890b-196">SOAP-based message security (Message).</span></span>

- <span data-ttu-id="c890b-197">同時具有傳輸和訊息安全性 (兩者並存)。</span><span class="sxs-lookup"><span data-stu-id="c890b-197">Simultaneous Transport and Message security (Both).</span></span>

- <span data-ttu-id="c890b-198">支援的用戶端認證類型：無、Windows、UserName、憑證、IssuedToken。</span><span class="sxs-lookup"><span data-stu-id="c890b-198">Client Credential Types supported: None, Windows, UserName, Certificate, IssuedToken.</span></span>

<span data-ttu-id="c890b-199">只有在將安全性模式設定為 <xref:System.ServiceModel.MessageCredentialType.Certificate> 或 <xref:System.ServiceModel.NetMsmqSecurityMode.Both> 時，才會支援 <xref:System.ServiceModel.NetMsmqSecurityMode.Message> 認證。</span><span class="sxs-lookup"><span data-stu-id="c890b-199">The <xref:System.ServiceModel.MessageCredentialType.Certificate> credential is supported only when the security mode is set to either <xref:System.ServiceModel.NetMsmqSecurityMode.Both> or <xref:System.ServiceModel.NetMsmqSecurityMode.Message>.</span></span>

<span data-ttu-id="c890b-200">如需詳細資訊，請參閱<xref:System.ServiceModel.MessageSecurityOverMsmq>和<xref:System.ServiceModel.MsmqTransportSecurity>。</span><span class="sxs-lookup"><span data-stu-id="c890b-200">For more information, see <xref:System.ServiceModel.MessageSecurityOverMsmq> and <xref:System.ServiceModel.MsmqTransportSecurity>.</span></span>

### <a name="wsfederationhttpbinding"></a><span data-ttu-id="c890b-201">WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c890b-201">WSFederationHttpBinding</span></span>

<span data-ttu-id="c890b-202">在程式碼中，使用 <xref:System.ServiceModel.WSFederationHttpBinding> 類別;在 [設定] 中，使用[\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="c890b-202">In code, use the <xref:System.ServiceModel.WSFederationHttpBinding> class; in configuration, use the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>

<span data-ttu-id="c890b-203">根據預設，這個繫結會使用 WS-Security (訊息層安全性)。</span><span class="sxs-lookup"><span data-stu-id="c890b-203">By default, this binding uses WS-Security (message-layer security).</span></span>

<span data-ttu-id="c890b-204">如需詳細資訊，請參閱[同盟](../../../../docs/framework/wcf/feature-details/federation.md)、<xref:System.ServiceModel.WSFederationHttpSecurity>和 <xref:System.ServiceModel.WSFederationHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="c890b-204">For more information, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>, and <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>

## <a name="custom-bindings"></a><span data-ttu-id="c890b-205">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="c890b-205">Custom Bindings</span></span>

<span data-ttu-id="c890b-206">如果系統提供的繫結程序都不符合您的需求，您可以以自訂的安全性繫結程序項目建立自訂繫結程序。</span><span class="sxs-lookup"><span data-stu-id="c890b-206">If none of the system-provided bindings meets you requirements, you can create a custom binding with a custom security binding element.</span></span> <span data-ttu-id="c890b-207">如需詳細資訊，請參閱[使用自訂系結的安全性功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="c890b-207">For more information, see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).</span></span>

## <a name="binding-choices"></a><span data-ttu-id="c890b-208">繫結選擇</span><span class="sxs-lookup"><span data-stu-id="c890b-208">Binding Choices</span></span>

<span data-ttu-id="c890b-209">下表摘要說明了安全性模式設定中提供的功能，也就是說，列出了當安全性模式設定為 `Transport`、`Message` 或 `TransportWithMessageCredential` 時可以使用的功能。</span><span class="sxs-lookup"><span data-stu-id="c890b-209">The following table summarizes the features offered in the security mode setting, that is, it lists the features available when the security mode is set to `Transport`, `Message`, or `TransportWithMessageCredential`.</span></span> <span data-ttu-id="c890b-210">此表可協助您找出應用程式所需的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="c890b-210">Use this table to help you find the security features your application requires.</span></span>

|<span data-ttu-id="c890b-211">設定</span><span class="sxs-lookup"><span data-stu-id="c890b-211">Setting</span></span>|<span data-ttu-id="c890b-212">功能</span><span class="sxs-lookup"><span data-stu-id="c890b-212">Features</span></span>|
|-------------|--------------|
|<span data-ttu-id="c890b-213">Transport</span><span class="sxs-lookup"><span data-stu-id="c890b-213">Transport</span></span>|<span data-ttu-id="c890b-214">伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="c890b-214">Server authentication</span></span><br /><br /> <span data-ttu-id="c890b-215">用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="c890b-215">Client authentication</span></span><br /><br /> <span data-ttu-id="c890b-216">點對點安全性</span><span class="sxs-lookup"><span data-stu-id="c890b-216">Point-to-point security</span></span><br /><br /> <span data-ttu-id="c890b-217">互通性</span><span class="sxs-lookup"><span data-stu-id="c890b-217">Interoperability</span></span><br /><br /> <span data-ttu-id="c890b-218">硬體加速</span><span class="sxs-lookup"><span data-stu-id="c890b-218">Hardware acceleration</span></span><br /><br /> <span data-ttu-id="c890b-219">高度輸送量</span><span class="sxs-lookup"><span data-stu-id="c890b-219">High throughput</span></span><br /><br /> <span data-ttu-id="c890b-220">安全的防火牆</span><span class="sxs-lookup"><span data-stu-id="c890b-220">Secure firewall</span></span><br /><br /> <span data-ttu-id="c890b-221">高延遲的應用程式</span><span class="sxs-lookup"><span data-stu-id="c890b-221">High-latency applications</span></span><br /><br /> <span data-ttu-id="c890b-222">多個躍點間重新加密</span><span class="sxs-lookup"><span data-stu-id="c890b-222">Re-encryption across multiple hops</span></span>|
|<span data-ttu-id="c890b-223">訊息</span><span class="sxs-lookup"><span data-stu-id="c890b-223">Message</span></span>|<span data-ttu-id="c890b-224">伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="c890b-224">Server authentication</span></span><br /><br /> <span data-ttu-id="c890b-225">用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="c890b-225">Client authentication</span></span><br /><br /> <span data-ttu-id="c890b-226">端對端安全性</span><span class="sxs-lookup"><span data-stu-id="c890b-226">End-to-end security</span></span><br /><br /> <span data-ttu-id="c890b-227">互通性</span><span class="sxs-lookup"><span data-stu-id="c890b-227">Interoperability</span></span><br /><br /> <span data-ttu-id="c890b-228">豐富的宣告</span><span class="sxs-lookup"><span data-stu-id="c890b-228">Rich claims</span></span><br /><br /> <span data-ttu-id="c890b-229">聯合</span><span class="sxs-lookup"><span data-stu-id="c890b-229">Federation</span></span><br /><br /> <span data-ttu-id="c890b-230">多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="c890b-230">Multifactor authentication</span></span><br /><br /> <span data-ttu-id="c890b-231">自訂權杖</span><span class="sxs-lookup"><span data-stu-id="c890b-231">Custom tokens</span></span><br /><br /> <span data-ttu-id="c890b-232">公證/時間戳記服務</span><span class="sxs-lookup"><span data-stu-id="c890b-232">Notary/timestamp service</span></span><br /><br /> <span data-ttu-id="c890b-233">高延遲的應用程式</span><span class="sxs-lookup"><span data-stu-id="c890b-233">High-latency applications</span></span><br /><br /> <span data-ttu-id="c890b-234">訊息簽章的持續性</span><span class="sxs-lookup"><span data-stu-id="c890b-234">Persistence of message signatures</span></span>|
|<span data-ttu-id="c890b-235">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="c890b-235">TransportWithMessageCredential</span></span>|<span data-ttu-id="c890b-236">伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="c890b-236">Server authentication</span></span><br /><br /> <span data-ttu-id="c890b-237">用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="c890b-237">Client authentication</span></span><br /><br /> <span data-ttu-id="c890b-238">點對點安全性</span><span class="sxs-lookup"><span data-stu-id="c890b-238">Point-to-point security</span></span><br /><br /> <span data-ttu-id="c890b-239">互通性</span><span class="sxs-lookup"><span data-stu-id="c890b-239">Interoperability</span></span><br /><br /> <span data-ttu-id="c890b-240">硬體加速</span><span class="sxs-lookup"><span data-stu-id="c890b-240">Hardware acceleration</span></span><br /><br /> <span data-ttu-id="c890b-241">高度輸送量</span><span class="sxs-lookup"><span data-stu-id="c890b-241">High throughput</span></span><br /><br /> <span data-ttu-id="c890b-242">豐富的用戶端宣告</span><span class="sxs-lookup"><span data-stu-id="c890b-242">Rich client claims</span></span><br /><br /> <span data-ttu-id="c890b-243">聯合</span><span class="sxs-lookup"><span data-stu-id="c890b-243">Federation</span></span><br /><br /> <span data-ttu-id="c890b-244">多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="c890b-244">Multifactor authentication</span></span><br /><br /> <span data-ttu-id="c890b-245">自訂權杖</span><span class="sxs-lookup"><span data-stu-id="c890b-245">Custom tokens</span></span><br /><br /> <span data-ttu-id="c890b-246">安全的防火牆</span><span class="sxs-lookup"><span data-stu-id="c890b-246">Secure firewall</span></span><br /><br /> <span data-ttu-id="c890b-247">高延遲的應用程式</span><span class="sxs-lookup"><span data-stu-id="c890b-247">High-latency applications</span></span><br /><br /> <span data-ttu-id="c890b-248">多個躍點間重新加密</span><span class="sxs-lookup"><span data-stu-id="c890b-248">Re-encryption across multiple hops</span></span>|

<span data-ttu-id="c890b-249">下表列出支援各種模式設定的繫結。</span><span class="sxs-lookup"><span data-stu-id="c890b-249">The following table lists the bindings that support the various mode settings.</span></span> <span data-ttu-id="c890b-250">您可以從表格中選取一種繫結，以便用來建立您的服務端點。</span><span class="sxs-lookup"><span data-stu-id="c890b-250">Select a binding from the table to use to create your service endpoint.</span></span>

|<span data-ttu-id="c890b-251">繫結</span><span class="sxs-lookup"><span data-stu-id="c890b-251">Binding</span></span>|<span data-ttu-id="c890b-252">傳輸模式支援</span><span class="sxs-lookup"><span data-stu-id="c890b-252">Transport mode support</span></span>|<span data-ttu-id="c890b-253">訊息模式支援</span><span class="sxs-lookup"><span data-stu-id="c890b-253">Message mode support</span></span>|<span data-ttu-id="c890b-254">TransportWithMessageCredential 支援</span><span class="sxs-lookup"><span data-stu-id="c890b-254">TransportWithMessageCredential support</span></span>|
|-------------|----------------------------|--------------------------|--------------------------------------------|
|`BasicHttpBinding`|<span data-ttu-id="c890b-255">是</span><span class="sxs-lookup"><span data-stu-id="c890b-255">Yes</span></span>|<span data-ttu-id="c890b-256">是</span><span class="sxs-lookup"><span data-stu-id="c890b-256">Yes</span></span>|<span data-ttu-id="c890b-257">是</span><span class="sxs-lookup"><span data-stu-id="c890b-257">Yes</span></span>|
|`WSHttpBinding`|<span data-ttu-id="c890b-258">是</span><span class="sxs-lookup"><span data-stu-id="c890b-258">Yes</span></span>|<span data-ttu-id="c890b-259">是</span><span class="sxs-lookup"><span data-stu-id="c890b-259">Yes</span></span>|<span data-ttu-id="c890b-260">是</span><span class="sxs-lookup"><span data-stu-id="c890b-260">Yes</span></span>|
|`WSDualHttpBinding`|<span data-ttu-id="c890b-261">否</span><span class="sxs-lookup"><span data-stu-id="c890b-261">No</span></span>|<span data-ttu-id="c890b-262">是</span><span class="sxs-lookup"><span data-stu-id="c890b-262">Yes</span></span>|<span data-ttu-id="c890b-263">否</span><span class="sxs-lookup"><span data-stu-id="c890b-263">No</span></span>|
|`NetTcpBinding`|<span data-ttu-id="c890b-264">是</span><span class="sxs-lookup"><span data-stu-id="c890b-264">Yes</span></span>|<span data-ttu-id="c890b-265">是</span><span class="sxs-lookup"><span data-stu-id="c890b-265">Yes</span></span>|<span data-ttu-id="c890b-266">是</span><span class="sxs-lookup"><span data-stu-id="c890b-266">Yes</span></span>|
|`NetNamedPipeBinding`|<span data-ttu-id="c890b-267">是</span><span class="sxs-lookup"><span data-stu-id="c890b-267">Yes</span></span>|<span data-ttu-id="c890b-268">否</span><span class="sxs-lookup"><span data-stu-id="c890b-268">No</span></span>|<span data-ttu-id="c890b-269">否</span><span class="sxs-lookup"><span data-stu-id="c890b-269">No</span></span>|
|`NetMsmqBinding`|<span data-ttu-id="c890b-270">是</span><span class="sxs-lookup"><span data-stu-id="c890b-270">Yes</span></span>|<span data-ttu-id="c890b-271">是</span><span class="sxs-lookup"><span data-stu-id="c890b-271">Yes</span></span>|<span data-ttu-id="c890b-272">否</span><span class="sxs-lookup"><span data-stu-id="c890b-272">No</span></span>|
|`MsmqIntegrationBinding`|<span data-ttu-id="c890b-273">是</span><span class="sxs-lookup"><span data-stu-id="c890b-273">Yes</span></span>|<span data-ttu-id="c890b-274">否</span><span class="sxs-lookup"><span data-stu-id="c890b-274">No</span></span>|<span data-ttu-id="c890b-275">否</span><span class="sxs-lookup"><span data-stu-id="c890b-275">No</span></span>|
|`wsFederationHttpBinding`|<span data-ttu-id="c890b-276">否</span><span class="sxs-lookup"><span data-stu-id="c890b-276">No</span></span>|<span data-ttu-id="c890b-277">是</span><span class="sxs-lookup"><span data-stu-id="c890b-277">Yes</span></span>|<span data-ttu-id="c890b-278">是</span><span class="sxs-lookup"><span data-stu-id="c890b-278">Yes</span></span>|

## <a name="transport-credentials-in-bindings"></a><span data-ttu-id="c890b-279">繫結中的傳輸認證</span><span class="sxs-lookup"><span data-stu-id="c890b-279">Transport Credentials in Bindings</span></span>

<span data-ttu-id="c890b-280">下表列出在傳輸安全性模式中使用 `BasicHttpBinding` 或 `WSHttpBinding` 時，可以使用的用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="c890b-280">The following table lists the client credential types available when using either `BasicHttpBinding` or `WSHttpBinding` in transport security mode.</span></span>

|<span data-ttu-id="c890b-281">類型</span><span class="sxs-lookup"><span data-stu-id="c890b-281">Type</span></span>|<span data-ttu-id="c890b-282">描述</span><span class="sxs-lookup"><span data-stu-id="c890b-282">Description</span></span>|
|----------|-----------------|
|<span data-ttu-id="c890b-283">None</span><span class="sxs-lookup"><span data-stu-id="c890b-283">None</span></span>|<span data-ttu-id="c890b-284">指定用戶端不需要提出任何認證。</span><span class="sxs-lookup"><span data-stu-id="c890b-284">Specifies that the client does not need to present any credential.</span></span> <span data-ttu-id="c890b-285">這會轉譯成匿名用戶端。</span><span class="sxs-lookup"><span data-stu-id="c890b-285">This translates to an anonymous client.</span></span>|
|<span data-ttu-id="c890b-286">Basic</span><span class="sxs-lookup"><span data-stu-id="c890b-286">Basic</span></span>|<span data-ttu-id="c890b-287">基本驗證。</span><span class="sxs-lookup"><span data-stu-id="c890b-287">Basic authentication.</span></span> <span data-ttu-id="c890b-288">如需詳細資訊，請參閱 RFC 2617-HTTP 驗證：基本和摘要式驗證（可在 <https://go.microsoft.com/fwlink/?LinkId=84023>取得）。</span><span class="sxs-lookup"><span data-stu-id="c890b-288">For more information, see RFC 2617 – HTTP Authentication: Basic and Digest Authentication, available at <https://go.microsoft.com/fwlink/?LinkId=84023>.</span></span>|
|<span data-ttu-id="c890b-289">Digest</span><span class="sxs-lookup"><span data-stu-id="c890b-289">Digest</span></span>|<span data-ttu-id="c890b-290">摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="c890b-290">Digest authentication.</span></span> <span data-ttu-id="c890b-291">如需詳細資訊，請參閱 RFC 2617-HTTP 驗證：基本和摘要式驗證（可在 <https://go.microsoft.com/fwlink/?LinkId=84023>取得）。</span><span class="sxs-lookup"><span data-stu-id="c890b-291">For more information, see RFC 2617 – HTTP Authentication: Basic and Digest Authentication, available at <https://go.microsoft.com/fwlink/?LinkId=84023>.</span></span>|
|<span data-ttu-id="c890b-292">NTLM</span><span class="sxs-lookup"><span data-stu-id="c890b-292">NTLM</span></span>|<span data-ttu-id="c890b-293">NT LAN Manager (NTLM) 驗證。</span><span class="sxs-lookup"><span data-stu-id="c890b-293">NT LAN Manager (NTLM) authentication.</span></span>|
|<span data-ttu-id="c890b-294">Windows</span><span class="sxs-lookup"><span data-stu-id="c890b-294">Windows</span></span>|<span data-ttu-id="c890b-295">Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c890b-295">Windows authentication.</span></span>|
|<span data-ttu-id="c890b-296">憑證</span><span class="sxs-lookup"><span data-stu-id="c890b-296">Certificate</span></span>|<span data-ttu-id="c890b-297">使用憑證執行的驗證。</span><span class="sxs-lookup"><span data-stu-id="c890b-297">Authentication performed using a certificate.</span></span>|
|<span data-ttu-id="c890b-298">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="c890b-298">IssuedToken</span></span>|<span data-ttu-id="c890b-299">允許服務要求用戶端使用由 Security Token Service 或 CardSpace 所發行的權杖進行驗證。</span><span class="sxs-lookup"><span data-stu-id="c890b-299">Allows the service to require that the client be authenticated using a token issued by a security token service or by CardSpace.</span></span> <span data-ttu-id="c890b-300">如需詳細資訊，請參閱[同盟和發行的權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="c890b-300">For more information, see [Federation and Issued Tokens](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>|

### <a name="message-client-credentials-in-bindings"></a><span data-ttu-id="c890b-301">繫結中的訊息用戶端認證</span><span class="sxs-lookup"><span data-stu-id="c890b-301">Message Client Credentials in Bindings</span></span>

<span data-ttu-id="c890b-302">下表列出在訊息安全性模式中使用繫結時，可以使用的用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="c890b-302">The following table lists the client credential types available when using a binding in Message security mode.</span></span>

|<span data-ttu-id="c890b-303">類型</span><span class="sxs-lookup"><span data-stu-id="c890b-303">Type</span></span>|<span data-ttu-id="c890b-304">描述</span><span class="sxs-lookup"><span data-stu-id="c890b-304">Description</span></span>|
|----------|-----------------|
|<span data-ttu-id="c890b-305">None</span><span class="sxs-lookup"><span data-stu-id="c890b-305">None</span></span>|<span data-ttu-id="c890b-306">允許服務與匿名用戶端互動。</span><span class="sxs-lookup"><span data-stu-id="c890b-306">Allows the service to interact with anonymous clients.</span></span>|
|<span data-ttu-id="c890b-307">Windows</span><span class="sxs-lookup"><span data-stu-id="c890b-307">Windows</span></span>|<span data-ttu-id="c890b-308">允許在 Windows 認證的已驗證內容中進行 SOAP 訊息交換。</span><span class="sxs-lookup"><span data-stu-id="c890b-308">Allows SOAP message exchanges to be made under the authenticated context of a Windows credential.</span></span>|
|<span data-ttu-id="c890b-309">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="c890b-309">UserName</span></span>|<span data-ttu-id="c890b-310">允許服務要求用戶端必須以使用者名稱認證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="c890b-310">Allows the service to require that the client be authenticated using a user name credential.</span></span> <span data-ttu-id="c890b-311">請注意，當安全性模式設定為 `TransportWithMessageCredential`時，WCF 不支援傳送密碼摘要或使用密碼衍生金鑰，以及使用這類金鑰來進行訊息模式安全性。</span><span class="sxs-lookup"><span data-stu-id="c890b-311">Note that when the security mode is set to `TransportWithMessageCredential`, WCF does not support sending a password digest or deriving keys using password and using such keys for Message mode security.</span></span> <span data-ttu-id="c890b-312">因此，在使用使用者名稱認證時，WCF 會強制保護傳輸。</span><span class="sxs-lookup"><span data-stu-id="c890b-312">As such, WCF enforces that the transport is secured when using user name credentials.</span></span>|
|<span data-ttu-id="c890b-313">憑證</span><span class="sxs-lookup"><span data-stu-id="c890b-313">Certificate</span></span>|<span data-ttu-id="c890b-314">允許服務要求用戶端使用憑證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="c890b-314">Allows the service to require that the client be authenticated using a certificate.</span></span>|
|<span data-ttu-id="c890b-315">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="c890b-315">IssuedToken</span></span>|<span data-ttu-id="c890b-316">允許服務使用安全性權杖服務提供自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="c890b-316">Allows the service to use a security token service to supply a custom token.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c890b-317">請參閱</span><span class="sxs-lookup"><span data-stu-id="c890b-317">See also</span></span>

- [<span data-ttu-id="c890b-318">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="c890b-318">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="c890b-319">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="c890b-319">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c890b-320">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="c890b-320">Selecting a Credential Type</span></span>](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="c890b-321">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="c890b-321">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c890b-322">安全性行為</span><span class="sxs-lookup"><span data-stu-id="c890b-322">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- <span data-ttu-id="c890b-323">[Windows Server App Fabric 的安全性模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c890b-323">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
