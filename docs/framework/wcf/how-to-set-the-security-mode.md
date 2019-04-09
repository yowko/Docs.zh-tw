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
ms.openlocfilehash: 652fcef75f8d5a8dee824bb89bf4695f1629fed8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116398"
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="d935c-102">HOW TO：設定安全性模式</span><span class="sxs-lookup"><span data-stu-id="d935c-102">How to: Set the Security Mode</span></span>
<span data-ttu-id="d935c-103">Windows Communication Foundation (WCF) 安全性有三種常見的安全性模式，最預先定義繫結上找到： 傳輸、 訊息和 「 傳輸與訊息認證 」。</span><span class="sxs-lookup"><span data-stu-id="d935c-103">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="d935c-104">另外有兩種額外的模式適用於下列兩種繫結：<xref:System.ServiceModel.BasicHttpBinding> 上的「僅限傳輸-認證」以及 <xref:System.ServiceModel.NetMsmqBinding> 上的「兩者並存」模式。</span><span class="sxs-lookup"><span data-stu-id="d935c-104">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="d935c-105">然而，此主題將著重在三種常見的安全性模式：<xref:System.ServiceModel.SecurityMode.Transport>、<xref:System.ServiceModel.SecurityMode.Message> 與 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。</span><span class="sxs-lookup"><span data-stu-id="d935c-105">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
 <span data-ttu-id="d935c-106">請注意，並非所有預先定義的繫結都支援這些模式。</span><span class="sxs-lookup"><span data-stu-id="d935c-106">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="d935c-107">本主題將使用 <xref:System.ServiceModel.WSHttpBinding> 和 <xref:System.ServiceModel.NetTcpBinding> 類別來設定模式，並示範如何以程式設計方式及透過組態來設定模式。</span><span class="sxs-lookup"><span data-stu-id="d935c-107">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>  
  
 <span data-ttu-id="d935c-108">如需詳細資訊，請參閱 WCF 安全性，請參閱[安全性概觀](../../../docs/framework/wcf/feature-details/security-overview.md)， [Securing Services](../../../docs/framework/wcf/securing-services.md)，並[Securing Services and Clients](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="d935c-108">For more information, see WCF security, see [Security Overview](../../../docs/framework/wcf/feature-details/security-overview.md), [Securing Services](../../../docs/framework/wcf/securing-services.md), and [Securing Services and Clients](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="d935c-109">如需有關傳輸模式與訊息的詳細資訊，請參閱[傳輸安全性](../../../docs/framework/wcf/feature-details/transport-security.md)並[訊息安全性](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="d935c-109">For more information about transport mode and message, see [Transport Security](../../../docs/framework/wcf/feature-details/transport-security.md) and [Message Security](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
### <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="d935c-110">若要在程式碼中設定安全性模式</span><span class="sxs-lookup"><span data-stu-id="d935c-110">To set the security mode in code</span></span>  
  
1.  <span data-ttu-id="d935c-111">針對您正在使用的繫結類別建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="d935c-111">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="d935c-112">如需預先定義繫結的清單，請參閱 < [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="d935c-112">For a list of predefined bindings, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="d935c-113">下列範例會建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d935c-113">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>  
  
2.  <span data-ttu-id="d935c-114">針對 `Mode` 屬性傳回的物件，設定其 `Security` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d935c-114">Set the `Mode` property of the object returned by the `Security` property.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     <span data-ttu-id="d935c-115">另外，如下列程式碼所示，設定訊息的模式。</span><span class="sxs-lookup"><span data-stu-id="d935c-115">Alternatively, set the mode to message, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     <span data-ttu-id="d935c-116">或者，如下列程式碼所示，使用訊息認證來設定傳輸的模式。</span><span class="sxs-lookup"><span data-stu-id="d935c-116">Or set the mode to transport with message credentials, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  <span data-ttu-id="d935c-117">您也可以如下列程式碼所示，在繫結的建構函式中設定模式。</span><span class="sxs-lookup"><span data-stu-id="d935c-117">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="d935c-118">設定 ClientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="d935c-118">Setting the ClientCredentialType Property</span></span>  
 <span data-ttu-id="d935c-119">將模式設為三個值中的其中一個值，可決定您設定 `ClientCredentialType` 屬性的方式。</span><span class="sxs-lookup"><span data-stu-id="d935c-119">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="d935c-120">例如，使用 <xref:System.ServiceModel.WSHttpBinding> 類別並將模式設為 `Transport` 時，代表您必須將 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> 類別的 <xref:System.ServiceModel.HttpTransportSecurity> 屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="d935c-120">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="d935c-121">若要設定傳輸模式的 ClientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="d935c-121">To set the ClientCredentialType property for Transport mode</span></span>  
  
1.  <span data-ttu-id="d935c-122">建立繫結的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d935c-122">Create an instance of the binding.</span></span>  
  
2.  <span data-ttu-id="d935c-123">將 `Mode` 屬性設定為 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="d935c-123">Set the `Mode` property to `Transport`.</span></span>  
  
3.  <span data-ttu-id="d935c-124">將 `ClientCredential` 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="d935c-124">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="d935c-125">下列程式碼會將屬性設為 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="d935c-125">The following code sets the property to `Windows`.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="d935c-126">若要設定訊息模式的 ClientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="d935c-126">To set the ClientCredentialType property for Message mode</span></span>  
  
1.  <span data-ttu-id="d935c-127">建立繫結的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d935c-127">Create an instance of the binding.</span></span>  
  
2.  <span data-ttu-id="d935c-128">將 `Mode` 屬性設定為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="d935c-128">Set the `Mode` property to `Message`.</span></span>  
  
3.  <span data-ttu-id="d935c-129">將 `ClientCredential` 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="d935c-129">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="d935c-130">下列程式碼會將屬性設為 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="d935c-130">The following code sets the property to `Certificate`.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="d935c-131">若要在組態中設定 Mode 與 ClientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="d935c-131">To set the Mode and ClientCredentialType property in configuration</span></span>  
  
1.  <span data-ttu-id="d935c-132">加入至適當的繫結項目[\<繫結 >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)組態檔的項目。</span><span class="sxs-lookup"><span data-stu-id="d935c-132">Add an appropriate binding element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="d935c-133">下列範例會將[ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="d935c-133">The following example adds a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
2.  <span data-ttu-id="d935c-134">新增`<binding>`項目並將其`name`屬性設為適當的值。</span><span class="sxs-lookup"><span data-stu-id="d935c-134">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="d935c-135">新增 `<security>` 項目，並將 `mode` 屬性設為 `Message`、`Transport` 或 `TransportWithMessageCredential`。</span><span class="sxs-lookup"><span data-stu-id="d935c-135">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>  
  
4.  <span data-ttu-id="d935c-136">如果模式已設為 `Transport`，則新增 `<transport>` 項目並將 `clientCredential` 屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="d935c-136">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>  
  
     <span data-ttu-id="d935c-137">下列範例會將模式設為 "`Transport"`，然後將 `clientCredentialType` 項目的 `<transport>` 屬性設為 "`Windows"`。</span><span class="sxs-lookup"><span data-stu-id="d935c-137">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" >  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     <span data-ttu-id="d935c-138">另外，將 `security mode` 設為 "`Message"`，並在它後面加上 `<"message">` 項目。</span><span class="sxs-lookup"><span data-stu-id="d935c-138">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="d935c-139">這個範例會將 `clientCredentialType` 設為 "`Certificate"`。</span><span class="sxs-lookup"><span data-stu-id="d935c-139">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" >  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     <span data-ttu-id="d935c-140">特殊情況下會使用 <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> 值 (請參見下列說明)。</span><span class="sxs-lookup"><span data-stu-id="d935c-140">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>  
  
### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="d935c-141">使用 TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d935c-141">Using TransportWithMessageCredential</span></span>  
 <span data-ttu-id="d935c-142">當您將安全性模式設為 `TransportWithMessageCredential` 時，傳輸會決定用來提供傳輸層安全性的實際機制。</span><span class="sxs-lookup"><span data-stu-id="d935c-142">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="d935c-143">例如，HTTP 通訊協定會使用 Secure Sockets Layer (SSL) over HTTP (HTTPS)。</span><span class="sxs-lookup"><span data-stu-id="d935c-143">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="d935c-144">因此，會忽略對任何傳輸安全性物件 (例如 `ClientCredentialType`) 的 <xref:System.ServiceModel.HttpTransportSecurity> 屬性設定。</span><span class="sxs-lookup"><span data-stu-id="d935c-144">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="d935c-145">換句話說，您只能設定訊息安全性物件的 `ClientCredentialType` (對 `WSHttpBinding` 繫結程序來說，指的是 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> 物件)。</span><span class="sxs-lookup"><span data-stu-id="d935c-145">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>  
  
 <span data-ttu-id="d935c-146">如需詳細資訊，請參閱[如何：使用傳輸安全性和訊息認證](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)。</span><span class="sxs-lookup"><span data-stu-id="d935c-146">For more information, see [How to: Use Transport Security and Message Credentials](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d935c-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d935c-147">See also</span></span>

- [<span data-ttu-id="d935c-148">HOW TO：使用 SSL 憑證設定連接埠</span><span class="sxs-lookup"><span data-stu-id="d935c-148">How to: Configure a Port with an SSL Certificate</span></span>](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="d935c-149">HOW TO：使用傳輸安全性和訊息認證</span><span class="sxs-lookup"><span data-stu-id="d935c-149">How to: Use Transport Security and Message Credentials</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [<span data-ttu-id="d935c-150">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="d935c-150">Transport Security</span></span>](../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="d935c-151">訊息安全性</span><span class="sxs-lookup"><span data-stu-id="d935c-151">Message Security</span></span>](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="d935c-152">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="d935c-152">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="d935c-153">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="d935c-153">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="d935c-154">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="d935c-154">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [<span data-ttu-id="d935c-155">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="d935c-155">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [<span data-ttu-id="d935c-156">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="d935c-156">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
