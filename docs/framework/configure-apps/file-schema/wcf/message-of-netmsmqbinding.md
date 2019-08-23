---
title: <message> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: b163dcb08e9656e3bde9c7fbb71fa1c92c9957ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931522"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="33673-102">\<netMsmqBinding > 的\<訊息 ></span><span class="sxs-lookup"><span data-stu-id="33673-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="33673-103">定義此 `netMsmqBinding` 繫結上的 SOAP 訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="33673-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <netMsmqBinding>
      <binding>
        <security>
          <message>
```

## <a name="syntax"></a><span data-ttu-id="33673-104">語法</span><span class="sxs-lookup"><span data-stu-id="33673-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="33673-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="33673-105">Attributes and Elements</span></span>

<span data-ttu-id="33673-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="33673-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="33673-107">屬性</span><span class="sxs-lookup"><span data-stu-id="33673-107">Attributes</span></span>

|<span data-ttu-id="33673-108">屬性</span><span class="sxs-lookup"><span data-stu-id="33673-108">Attribute</span></span>|<span data-ttu-id="33673-109">描述</span><span class="sxs-lookup"><span data-stu-id="33673-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="33673-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="33673-110">algorithmSuite</span></span>|<span data-ttu-id="33673-111">設定訊息加密和金鑰包裝演算法，用來針對 MSMQ 傳輸上傳送的訊息實現訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="33673-111">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="33673-112">預設值為 `Aes256`。</span><span class="sxs-lookup"><span data-stu-id="33673-112">The default value is `Aes256`.</span></span> <span data-ttu-id="33673-113">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。</span><span class="sxs-lookup"><span data-stu-id="33673-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="33673-114">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="33673-114">clientCredentialType</span></span>|<span data-ttu-id="33673-115">指定在為 MSMQ 傳輸上傳送的訊息執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="33673-115">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="33673-116">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="33673-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="33673-117">無這會允許服務與匿名用戶端互動。</span><span class="sxs-lookup"><span data-stu-id="33673-117">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="33673-118">服務和用戶端都不需要認證。</span><span class="sxs-lookup"><span data-stu-id="33673-118">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="33673-119">時段這可讓 SOAP 交換在 Windows 認證的已驗證內容下進行。</span><span class="sxs-lookup"><span data-stu-id="33673-119">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="33673-120">如此一定會執行 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="33673-120">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="33673-121">UserName這可讓服務要求用戶端必須使用 UserName 認證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="33673-121">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="33673-122">在此情況下, 必須使用`clientCredentials`下列行為來指定認證 **:** Windows Communication Foundation (WCF) 不支援傳送密碼摘要或使用密碼衍生金鑰, 以及使用這類金鑰來取得訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="33673-122">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="33673-123">因此, 在使用使用者名稱認證時, WCF 會強制保護交換。</span><span class="sxs-lookup"><span data-stu-id="33673-123">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="33673-124">這個模式需要使用 `clientCredential` 行為和 `serviceCertificate` 在用戶端上指定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="33673-124">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="33673-125">證書這可讓服務要求用戶端使用憑證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="33673-125">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="33673-126">此案例中的用戶端認證必須使用 `clientCredentials` 行為來指定。</span><span class="sxs-lookup"><span data-stu-id="33673-126">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="33673-127">此案例中的服務認證需要藉由指定 `clientCredentials`，以使用 `serviceCertificate` 行為來指定。</span><span class="sxs-lookup"><span data-stu-id="33673-127">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="33673-128">CardSpace這可讓服務要求用戶端使用 CardSpace 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="33673-128">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="33673-129">`serviceCertificate` 行為中必須提供 `clientCredential`。</span><span class="sxs-lookup"><span data-stu-id="33673-129">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="33673-130">預設值為 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="33673-130">The default value is `Windows`.</span></span> <span data-ttu-id="33673-131">此屬性的型別為 <xref:System.ServiceModel.MessageCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="33673-131">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="33673-132">子元素</span><span class="sxs-lookup"><span data-stu-id="33673-132">Child Elements</span></span>

<span data-ttu-id="33673-133">無</span><span class="sxs-lookup"><span data-stu-id="33673-133">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="33673-134">父項目</span><span class="sxs-lookup"><span data-stu-id="33673-134">Parent Elements</span></span>

|<span data-ttu-id="33673-135">項目</span><span class="sxs-lookup"><span data-stu-id="33673-135">Element</span></span>|<span data-ttu-id="33673-136">說明</span><span class="sxs-lookup"><span data-stu-id="33673-136">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33673-137">\<security></span><span class="sxs-lookup"><span data-stu-id="33673-137">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="33673-138">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="33673-138">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="33673-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33673-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="33673-140">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="33673-140">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="33673-141">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="33673-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="33673-142">繫結</span><span class="sxs-lookup"><span data-stu-id="33673-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="33673-143">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="33673-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="33673-144">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="33673-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="33673-145">\<binding></span><span class="sxs-lookup"><span data-stu-id="33673-145">\<binding></span></span>](../../../misc/binding.md)
