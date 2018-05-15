---
title: HOW TO：設定安全性模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e8c08fba0e4a74eafab00e75977a9f756c1b1cfa
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="d2546-102">HOW TO：設定安全性模式</span><span class="sxs-lookup"><span data-stu-id="d2546-102">How to: Set the Security Mode</span></span>
<span data-ttu-id="d2546-103">Windows Communication Foundation (WCF) 安全性有三種常見的安全性模式最預先定義繫結上找到： 傳輸、 訊息與 「 使用訊息認證進行傳輸。 」</span><span class="sxs-lookup"><span data-stu-id="d2546-103">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="d2546-104">另外有兩種額外的模式適用於下列兩種繫結：<xref:System.ServiceModel.BasicHttpBinding> 上的「僅限傳輸-認證」以及 <xref:System.ServiceModel.NetMsmqBinding> 上的「兩者並存」模式。</span><span class="sxs-lookup"><span data-stu-id="d2546-104">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="d2546-105">然而，此主題將著重在三種常見的安全性模式：<xref:System.ServiceModel.SecurityMode.Transport>、<xref:System.ServiceModel.SecurityMode.Message> 與 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。</span><span class="sxs-lookup"><span data-stu-id="d2546-105">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
 <span data-ttu-id="d2546-106">請注意，並非所有預先定義的繫結都支援這些模式。</span><span class="sxs-lookup"><span data-stu-id="d2546-106">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="d2546-107">本主題將使用 <xref:System.ServiceModel.WSHttpBinding> 和 <xref:System.ServiceModel.NetTcpBinding> 類別來設定模式，並示範如何以程式設計方式及透過組態來設定模式。</span><span class="sxs-lookup"><span data-stu-id="d2546-107">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>  
  
 <span data-ttu-id="d2546-108">如需詳細資訊，請參閱 WCF 安全性，請參閱[安全性概觀](../../../docs/framework/wcf/feature-details/security-overview.md)，[保護 Services](../../../docs/framework/wcf/securing-services.md)，和[保護服務和用戶端](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="d2546-108">For more information, see WCF security, see [Security Overview](../../../docs/framework/wcf/feature-details/security-overview.md), [Securing Services](../../../docs/framework/wcf/securing-services.md), and [Securing Services and Clients](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="d2546-109">如需傳輸的模式與訊息的詳細資訊，請參閱[傳輸安全性](../../../docs/framework/wcf/feature-details/transport-security.md)和[訊息安全性](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="d2546-109">For more information about transport mode and message, see [Transport Security](../../../docs/framework/wcf/feature-details/transport-security.md) and [Message Security](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
### <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="d2546-110">若要在程式碼中設定安全性模式</span><span class="sxs-lookup"><span data-stu-id="d2546-110">To set the security mode in code</span></span>  
  
1.  <span data-ttu-id="d2546-111">針對您正在使用的繫結類別建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="d2546-111">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="d2546-112">如需預先定義繫結的清單，請參閱[之繫結](../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="d2546-112">For a list of predefined bindings, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="d2546-113">下列範例會建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d2546-113">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>  
  
2.  <span data-ttu-id="d2546-114">針對 `Mode` 屬性傳回的物件，設定其 `Security` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d2546-114">Set the `Mode` property of the object returned by the `Security` property.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     <span data-ttu-id="d2546-115">另外，如下列程式碼所示，設定訊息的模式。</span><span class="sxs-lookup"><span data-stu-id="d2546-115">Alternatively, set the mode to message, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     <span data-ttu-id="d2546-116">或者，如下列程式碼所示，使用訊息認證來設定傳輸的模式。</span><span class="sxs-lookup"><span data-stu-id="d2546-116">Or set the mode to transport with message credentials, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  <span data-ttu-id="d2546-117">您也可以如下列程式碼所示，在繫結的建構函式中設定模式。</span><span class="sxs-lookup"><span data-stu-id="d2546-117">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="d2546-118">設定 ClientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="d2546-118">Setting the ClientCredentialType Property</span></span>  
 <span data-ttu-id="d2546-119">將模式設為三個值中的其中一個值，可決定您設定 `ClientCredentialType` 屬性的方式。</span><span class="sxs-lookup"><span data-stu-id="d2546-119">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="d2546-120">例如，使用 <xref:System.ServiceModel.WSHttpBinding> 類別並將模式設為 `Transport` 時，代表您必須將 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> 類別的 <xref:System.ServiceModel.HttpTransportSecurity> 屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="d2546-120">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="d2546-121">若要設定傳輸模式的 ClientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="d2546-121">To set the ClientCredentialType property for Transport mode</span></span>  
  
1.  <span data-ttu-id="d2546-122">建立繫結的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d2546-122">Create an instance of the binding.</span></span>  
  
2.  <span data-ttu-id="d2546-123">將 `Mode` 屬性設定為 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="d2546-123">Set the `Mode` property to `Transport`.</span></span>  
  
3.  <span data-ttu-id="d2546-124">將 `ClientCredential` 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="d2546-124">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="d2546-125">下列程式碼會將屬性設為 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="d2546-125">The following code sets the property to `Windows`.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="d2546-126">若要設定訊息模式的 ClientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="d2546-126">To set the ClientCredentialType property for Message mode</span></span>  
  
1.  <span data-ttu-id="d2546-127">建立繫結的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d2546-127">Create an instance of the binding.</span></span>  
  
2.  <span data-ttu-id="d2546-128">將 `Mode` 屬性設定為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="d2546-128">Set the `Mode` property to `Message`.</span></span>  
  
3.  <span data-ttu-id="d2546-129">將 `ClientCredential` 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="d2546-129">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="d2546-130">下列程式碼會將屬性設為 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="d2546-130">The following code sets the property to `Certificate`.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="d2546-131">若要在組態中設定 Mode 與 ClientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="d2546-131">To set the Mode and ClientCredentialType property in configuration</span></span>  
  
1.  <span data-ttu-id="d2546-132">新增適當的繫結項目的[\<繫結 >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)組態檔元素。</span><span class="sxs-lookup"><span data-stu-id="d2546-132">Add an appropriate binding element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="d2546-133">下列範例會將[ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="d2546-133">The following example adds a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
2.  <span data-ttu-id="d2546-134">新增`<binding>`項目並設定其`name`屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="d2546-134">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="d2546-135">新增 `<security>` 項目，並將 `mode` 屬性設為 `Message`、`Transport` 或 `TransportWithMessageCredential`。</span><span class="sxs-lookup"><span data-stu-id="d2546-135">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>  
  
4.  <span data-ttu-id="d2546-136">如果模式已設為 `Transport`，則新增 `<transport>` 項目並將 `clientCredential` 屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="d2546-136">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>  
  
     <span data-ttu-id="d2546-137">下列範例會將模式設為 "`Transport"`，然後將 `clientCredentialType` 項目的 `<transport>` 屬性設為 "`Windows"`。</span><span class="sxs-lookup"><span data-stu-id="d2546-137">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" />  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     <span data-ttu-id="d2546-138">另外，將 `security mode` 設為 "`Message"`，並在它後面加上 `<"message">` 項目。</span><span class="sxs-lookup"><span data-stu-id="d2546-138">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="d2546-139">這個範例會將 `clientCredentialType` 設為 "`Certificate"`。</span><span class="sxs-lookup"><span data-stu-id="d2546-139">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" />  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     <span data-ttu-id="d2546-140">特殊情況下會使用 <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> 值 (請參見下列說明)。</span><span class="sxs-lookup"><span data-stu-id="d2546-140">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>  
  
### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="d2546-141">使用 TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d2546-141">Using TransportWithMessageCredential</span></span>  
 <span data-ttu-id="d2546-142">當您將安全性模式設為 `TransportWithMessageCredential` 時，傳輸會決定用來提供傳輸層安全性的實際機制。</span><span class="sxs-lookup"><span data-stu-id="d2546-142">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="d2546-143">例如，HTTP 通訊協定會使用 Secure Sockets Layer (SSL) over HTTP (HTTPS)。</span><span class="sxs-lookup"><span data-stu-id="d2546-143">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="d2546-144">因此，會忽略對任何傳輸安全性物件 (例如 `ClientCredentialType`) 的 <xref:System.ServiceModel.HttpTransportSecurity> 屬性設定。</span><span class="sxs-lookup"><span data-stu-id="d2546-144">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="d2546-145">換句話說，您只能設定訊息安全性物件的 `ClientCredentialType` (對 `WSHttpBinding` 繫結來說，指的是 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> 物件)。</span><span class="sxs-lookup"><span data-stu-id="d2546-145">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>  
  
 <span data-ttu-id="d2546-146">如需詳細資訊，請參閱[How to： 使用傳輸安全性和訊息認證](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)。</span><span class="sxs-lookup"><span data-stu-id="d2546-146">For more information, see [How to: Use Transport Security and Message Credentials](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2546-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2546-147">See Also</span></span>  
 [<span data-ttu-id="d2546-148">如何：使用 SSL 憑證設定連接埠</span><span class="sxs-lookup"><span data-stu-id="d2546-148">How to: Configure a Port with an SSL Certificate</span></span>](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="d2546-149">如何：使用傳輸安全性和訊息認證</span><span class="sxs-lookup"><span data-stu-id="d2546-149">How to: Use Transport Security and Message Credentials</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [<span data-ttu-id="d2546-150">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="d2546-150">Transport Security</span></span>](../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="d2546-151">訊息安全性</span><span class="sxs-lookup"><span data-stu-id="d2546-151">Message Security</span></span>](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [<span data-ttu-id="d2546-152">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="d2546-152">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="d2546-153">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="d2546-153">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="d2546-154">\<security></span><span class="sxs-lookup"><span data-stu-id="d2546-154">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)  
 [<span data-ttu-id="d2546-155">\<security></span><span class="sxs-lookup"><span data-stu-id="d2546-155">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)  
 [<span data-ttu-id="d2546-156">\<security></span><span class="sxs-lookup"><span data-stu-id="d2546-156">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
