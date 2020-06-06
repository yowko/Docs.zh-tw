---
title: <message> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736754"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="50d96-102">\<message> 的 \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="50d96-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="50d96-103">定義此 `netMsmqBinding` 繫結上的 SOAP 訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="50d96-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  

## <a name="syntax"></a><span data-ttu-id="50d96-104">語法</span><span class="sxs-lookup"><span data-stu-id="50d96-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="50d96-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="50d96-105">Attributes and Elements</span></span>

<span data-ttu-id="50d96-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="50d96-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="50d96-107">屬性</span><span class="sxs-lookup"><span data-stu-id="50d96-107">Attributes</span></span>

|<span data-ttu-id="50d96-108">屬性</span><span class="sxs-lookup"><span data-stu-id="50d96-108">Attribute</span></span>|<span data-ttu-id="50d96-109">描述</span><span class="sxs-lookup"><span data-stu-id="50d96-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="50d96-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="50d96-110">algorithmSuite</span></span>|<span data-ttu-id="50d96-111">設定訊息加密和金鑰包裝演算法，用來針對 MSMQ 傳輸上傳送的訊息實現訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="50d96-111">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="50d96-112">預設值是 `Aes256`。</span><span class="sxs-lookup"><span data-stu-id="50d96-112">The default value is `Aes256`.</span></span> <span data-ttu-id="50d96-113">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。</span><span class="sxs-lookup"><span data-stu-id="50d96-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="50d96-114">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="50d96-114">clientCredentialType</span></span>|<span data-ttu-id="50d96-115">指定在為 MSMQ 傳輸上傳送的訊息執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="50d96-115">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="50d96-116">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="50d96-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="50d96-117">-None：這可讓服務與匿名用戶端互動。</span><span class="sxs-lookup"><span data-stu-id="50d96-117">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="50d96-118">服務和用戶端都不需要認證。</span><span class="sxs-lookup"><span data-stu-id="50d96-118">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="50d96-119">-Windows：這可讓 SOAP 交換在 Windows 認證的已驗證內容下。</span><span class="sxs-lookup"><span data-stu-id="50d96-119">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="50d96-120">如此一定會執行 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="50d96-120">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="50d96-121">-UserName：這可讓服務要求用戶端使用使用者名稱認證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="50d96-121">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="50d96-122">在此情況下，必須使用下列行為來指定 `clientCredentials` 認證 **：** Windows Communication Foundation （WCF）不支援傳送密碼摘要或使用密碼衍生金鑰，以及針對訊息安全性使用這類金鑰。</span><span class="sxs-lookup"><span data-stu-id="50d96-122">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="50d96-123">因此，在使用使用者名稱認證時，WCF 會強制保護交換。</span><span class="sxs-lookup"><span data-stu-id="50d96-123">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="50d96-124">這個模式需要使用 `clientCredential` 行為和 `serviceCertificate` 在用戶端上指定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="50d96-124">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="50d96-125">-Certificate：這可讓服務要求用戶端使用憑證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="50d96-125">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="50d96-126">此案例中的用戶端認證必須使用 `clientCredentials` 行為來指定。</span><span class="sxs-lookup"><span data-stu-id="50d96-126">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="50d96-127">此案例中的服務認證需要藉由指定 `clientCredentials`，以使用 `serviceCertificate` 行為來指定。</span><span class="sxs-lookup"><span data-stu-id="50d96-127">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="50d96-128">-CardSpace：這可讓服務要求用戶端使用 CardSpace 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="50d96-128">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="50d96-129">`serviceCertificate` 行為中必須提供 `clientCredential`。</span><span class="sxs-lookup"><span data-stu-id="50d96-129">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="50d96-130">預設值是 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="50d96-130">The default value is `Windows`.</span></span> <span data-ttu-id="50d96-131">此屬性的型別為 <xref:System.ServiceModel.MessageCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="50d96-131">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="50d96-132">子元素</span><span class="sxs-lookup"><span data-stu-id="50d96-132">Child Elements</span></span>

<span data-ttu-id="50d96-133">無</span><span class="sxs-lookup"><span data-stu-id="50d96-133">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="50d96-134">父項目</span><span class="sxs-lookup"><span data-stu-id="50d96-134">Parent Elements</span></span>

|<span data-ttu-id="50d96-135">元素</span><span class="sxs-lookup"><span data-stu-id="50d96-135">Element</span></span>|<span data-ttu-id="50d96-136">描述</span><span class="sxs-lookup"><span data-stu-id="50d96-136">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="50d96-137">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="50d96-137">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="50d96-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50d96-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="50d96-139">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="50d96-139">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="50d96-140">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="50d96-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="50d96-141">繫結</span><span class="sxs-lookup"><span data-stu-id="50d96-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="50d96-142">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="50d96-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="50d96-143">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="50d96-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
