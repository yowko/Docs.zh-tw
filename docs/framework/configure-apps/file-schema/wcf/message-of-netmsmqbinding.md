---
title: <message> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 306bc56820cdbcba17cce9fc50d426260eb0e0d4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360663"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="7d637-102">\<message> of \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="7d637-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="7d637-103">定義此 `netMsmqBinding` 繫結上的 SOAP 訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="7d637-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

<span data-ttu-id="7d637-104">\<system.ServiceModel>\\</span><span class="sxs-lookup"><span data-stu-id="7d637-104">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="7d637-105">\<bindings>\\</span><span class="sxs-lookup"><span data-stu-id="7d637-105">\<bindings>\\</span></span>
<span data-ttu-id="7d637-106">\<netMsmqBinding>\\</span><span class="sxs-lookup"><span data-stu-id="7d637-106">\<netMsmqBinding>\\</span></span>
<span data-ttu-id="7d637-107">\<binding>\\</span><span class="sxs-lookup"><span data-stu-id="7d637-107">\<binding>\\</span></span>
<span data-ttu-id="7d637-108">\<安全性 > \\</span><span class="sxs-lookup"><span data-stu-id="7d637-108">\<security>\\</span></span>
<span data-ttu-id="7d637-109">\<message></span><span class="sxs-lookup"><span data-stu-id="7d637-109">\<message></span></span>

## <a name="syntax"></a><span data-ttu-id="7d637-110">語法</span><span class="sxs-lookup"><span data-stu-id="7d637-110">Syntax</span></span>

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d637-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7d637-111">Attributes and Elements</span></span>

<span data-ttu-id="7d637-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7d637-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d637-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7d637-113">Attributes</span></span>

|<span data-ttu-id="7d637-114">屬性</span><span class="sxs-lookup"><span data-stu-id="7d637-114">Attribute</span></span>|<span data-ttu-id="7d637-115">描述</span><span class="sxs-lookup"><span data-stu-id="7d637-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="7d637-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="7d637-116">algorithmSuite</span></span>|<span data-ttu-id="7d637-117">設定訊息加密和金鑰包裝演算法，用來針對 MSMQ 傳輸上傳送的訊息實現訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="7d637-117">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="7d637-118">預設值是 `Aes256`。</span><span class="sxs-lookup"><span data-stu-id="7d637-118">The default value is `Aes256`.</span></span> <span data-ttu-id="7d637-119">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。</span><span class="sxs-lookup"><span data-stu-id="7d637-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="7d637-120">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="7d637-120">clientCredentialType</span></span>|<span data-ttu-id="7d637-121">指定在為 MSMQ 傳輸上傳送的訊息執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="7d637-121">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="7d637-122">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="7d637-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7d637-123">-None:這會允許服務與匿名用戶端互動。</span><span class="sxs-lookup"><span data-stu-id="7d637-123">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="7d637-124">服務和用戶端都不需要認證。</span><span class="sxs-lookup"><span data-stu-id="7d637-124">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="7d637-125">-Windows:這可讓 SOAP 交換加入 Windows 認證的已驗證的內容。</span><span class="sxs-lookup"><span data-stu-id="7d637-125">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="7d637-126">如此一定會執行 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="7d637-126">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="7d637-127">-使用者名稱：這可讓服務要求使用 UserName 認證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="7d637-127">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="7d637-128">認證在此情況下必須使用來指定`clientCredentials`行為**注意：** Windows Communication Foundation (WCF) 不支援傳送密碼摘要或衍生金鑰使用的密碼，並使用訊息安全性這類金鑰。</span><span class="sxs-lookup"><span data-stu-id="7d637-128">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="7d637-129">因此，WCF 會強制使用 UserName 認證時，保護交換。</span><span class="sxs-lookup"><span data-stu-id="7d637-129">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="7d637-130">這個模式需要使用 `clientCredential` 行為和 `serviceCertificate` 在用戶端上指定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="7d637-130">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="7d637-131">憑證：這可讓服務要求使用憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="7d637-131">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="7d637-132">此案例中的用戶端認證必須使用 `clientCredentials` 行為來指定。</span><span class="sxs-lookup"><span data-stu-id="7d637-132">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="7d637-133">此案例中的服務認證需要藉由指定 `clientCredentials`，以使用 `serviceCertificate` 行為來指定。</span><span class="sxs-lookup"><span data-stu-id="7d637-133">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="7d637-134">-CardSpace:這可讓服務要求用戶端使用 CardSpace 來驗證。</span><span class="sxs-lookup"><span data-stu-id="7d637-134">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="7d637-135">
  `serviceCertificate\` 行為中必須提供 `clientCredential`。</span><span class="sxs-lookup"><span data-stu-id="7d637-135">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="7d637-136">預設值是 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="7d637-136">The default value is `Windows`.</span></span> <span data-ttu-id="7d637-137">此屬性的型別為 <xref:System.ServiceModel.MessageCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="7d637-137">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="7d637-138">子元素</span><span class="sxs-lookup"><span data-stu-id="7d637-138">Child Elements</span></span>

<span data-ttu-id="7d637-139">無</span><span class="sxs-lookup"><span data-stu-id="7d637-139">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7d637-140">父項目</span><span class="sxs-lookup"><span data-stu-id="7d637-140">Parent Elements</span></span>

|<span data-ttu-id="7d637-141">項目</span><span class="sxs-lookup"><span data-stu-id="7d637-141">Element</span></span>|<span data-ttu-id="7d637-142">描述</span><span class="sxs-lookup"><span data-stu-id="7d637-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d637-143">\<security></span><span class="sxs-lookup"><span data-stu-id="7d637-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="7d637-144">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="7d637-144">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="7d637-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d637-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="7d637-146">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="7d637-146">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="7d637-147">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="7d637-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7d637-148">繫結</span><span class="sxs-lookup"><span data-stu-id="7d637-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="7d637-149">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="7d637-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7d637-150">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="7d637-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7d637-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="7d637-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
