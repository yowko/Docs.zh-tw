---
title: <message> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: c623b7daf1e91c9c1800b9653525cd51b1087506
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58890562"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="706d0-102">\<message> of \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="706d0-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="706d0-103">定義此 `netMsmqBinding` 繫結上的 SOAP 訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="706d0-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <netMsmqBinding>
      <binding>
        <security>
          <message>
```

## <a name="syntax"></a><span data-ttu-id="706d0-104">語法</span><span class="sxs-lookup"><span data-stu-id="706d0-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="706d0-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="706d0-105">Attributes and Elements</span></span>

<span data-ttu-id="706d0-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="706d0-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="706d0-107">屬性</span><span class="sxs-lookup"><span data-stu-id="706d0-107">Attributes</span></span>

|<span data-ttu-id="706d0-108">屬性</span><span class="sxs-lookup"><span data-stu-id="706d0-108">Attribute</span></span>|<span data-ttu-id="706d0-109">描述</span><span class="sxs-lookup"><span data-stu-id="706d0-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="706d0-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="706d0-110">algorithmSuite</span></span>|<span data-ttu-id="706d0-111">設定訊息加密和金鑰包裝演算法，用來針對 MSMQ 傳輸上傳送的訊息實現訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="706d0-111">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="706d0-112">預設值為 `Aes256`。</span><span class="sxs-lookup"><span data-stu-id="706d0-112">The default value is `Aes256`.</span></span> <span data-ttu-id="706d0-113">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。</span><span class="sxs-lookup"><span data-stu-id="706d0-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="706d0-114">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="706d0-114">clientCredentialType</span></span>|<span data-ttu-id="706d0-115">指定在為 MSMQ 傳輸上傳送的訊息執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="706d0-115">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="706d0-116">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="706d0-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="706d0-117">-None:這會允許服務與匿名用戶端互動。</span><span class="sxs-lookup"><span data-stu-id="706d0-117">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="706d0-118">服務和用戶端都不需要認證。</span><span class="sxs-lookup"><span data-stu-id="706d0-118">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="706d0-119">-Windows:這可讓 SOAP 交換加入 Windows 認證的已驗證的內容。</span><span class="sxs-lookup"><span data-stu-id="706d0-119">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="706d0-120">如此一定會執行 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="706d0-120">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="706d0-121">-使用者名稱：這可讓服務要求使用 UserName 認證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="706d0-121">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="706d0-122">認證在此情況下必須使用來指定`clientCredentials`行為**注意：** Windows Communication Foundation (WCF) 不支援傳送密碼摘要或衍生金鑰使用的密碼，並使用訊息安全性這類金鑰。</span><span class="sxs-lookup"><span data-stu-id="706d0-122">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="706d0-123">因此，WCF 會強制使用 UserName 認證時，保護交換。</span><span class="sxs-lookup"><span data-stu-id="706d0-123">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="706d0-124">這個模式需要使用 `clientCredential` 行為和 `serviceCertificate` 在用戶端上指定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="706d0-124">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="706d0-125">憑證：這可讓服務要求使用憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="706d0-125">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="706d0-126">此案例中的用戶端認證必須使用 `clientCredentials` 行為來指定。</span><span class="sxs-lookup"><span data-stu-id="706d0-126">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="706d0-127">此案例中的服務認證需要藉由指定 `clientCredentials`，以使用 `serviceCertificate` 行為來指定。</span><span class="sxs-lookup"><span data-stu-id="706d0-127">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="706d0-128">-CardSpace:這可讓服務要求用戶端使用 CardSpace 來驗證。</span><span class="sxs-lookup"><span data-stu-id="706d0-128">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="706d0-129">`serviceCertificate` 行為中必須提供 `clientCredential`。</span><span class="sxs-lookup"><span data-stu-id="706d0-129">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="706d0-130">預設值為 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="706d0-130">The default value is `Windows`.</span></span> <span data-ttu-id="706d0-131">此屬性的型別為 <xref:System.ServiceModel.MessageCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="706d0-131">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="706d0-132">子元素</span><span class="sxs-lookup"><span data-stu-id="706d0-132">Child Elements</span></span>

<span data-ttu-id="706d0-133">None</span><span class="sxs-lookup"><span data-stu-id="706d0-133">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="706d0-134">父項目</span><span class="sxs-lookup"><span data-stu-id="706d0-134">Parent Elements</span></span>

|<span data-ttu-id="706d0-135">項目</span><span class="sxs-lookup"><span data-stu-id="706d0-135">Element</span></span>|<span data-ttu-id="706d0-136">描述</span><span class="sxs-lookup"><span data-stu-id="706d0-136">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="706d0-137">\<security></span><span class="sxs-lookup"><span data-stu-id="706d0-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="706d0-138">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="706d0-138">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="706d0-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="706d0-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="706d0-140">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="706d0-140">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="706d0-141">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="706d0-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="706d0-142">繫結</span><span class="sxs-lookup"><span data-stu-id="706d0-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="706d0-143">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="706d0-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="706d0-144">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="706d0-144">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="706d0-145">\<binding></span><span class="sxs-lookup"><span data-stu-id="706d0-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
