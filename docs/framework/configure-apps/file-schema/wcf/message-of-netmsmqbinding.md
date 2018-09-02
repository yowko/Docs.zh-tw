---
title: '&lt;netMsmqBinding&gt; 的 &lt;message&gt;'
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 65a8b0fa120d23931ad218ac67846c066b050af8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402240"
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="d0a17-102">&lt;netMsmqBinding&gt; 的 &lt;message&gt;</span><span class="sxs-lookup"><span data-stu-id="d0a17-102">&lt;message&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="d0a17-103">定義此 `netMsmqBinding` 繫結上的 SOAP 訊息安全性設定。</span><span class="sxs-lookup"><span data-stu-id="d0a17-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>  
  
 <span data-ttu-id="d0a17-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d0a17-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0a17-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="d0a17-105">\<bindings></span></span>  
<span data-ttu-id="d0a17-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="d0a17-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="d0a17-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="d0a17-107">\<binding></span></span>  
<span data-ttu-id="d0a17-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="d0a17-108">\<security></span></span>  
<span data-ttu-id="d0a17-109">\<message></span><span class="sxs-lookup"><span data-stu-id="d0a17-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0a17-110">語法</span><span class="sxs-lookup"><span data-stu-id="d0a17-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0a17-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d0a17-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d0a17-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d0a17-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0a17-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d0a17-113">Attributes</span></span>  
  
|<span data-ttu-id="d0a17-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d0a17-114">Attribute</span></span>|<span data-ttu-id="d0a17-115">描述</span><span class="sxs-lookup"><span data-stu-id="d0a17-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0a17-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="d0a17-116">algorithmSuite</span></span>|<span data-ttu-id="d0a17-117">設定訊息加密和金鑰包裝演算法，用來針對 MSMQ 傳輸上傳送的訊息實現訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="d0a17-117">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="d0a17-118">預設值是 `Aes256`。</span><span class="sxs-lookup"><span data-stu-id="d0a17-118">The default value is `Aes256`.</span></span> <span data-ttu-id="d0a17-119">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。</span><span class="sxs-lookup"><span data-stu-id="d0a17-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|  
|<span data-ttu-id="d0a17-120">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="d0a17-120">clientCredentialType</span></span>|<span data-ttu-id="d0a17-121">指定在為 MSMQ 傳輸上傳送的訊息執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="d0a17-121">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="d0a17-122">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="d0a17-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d0a17-123">-None： 這會讓服務與匿名用戶端互動。</span><span class="sxs-lookup"><span data-stu-id="d0a17-123">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="d0a17-124">服務和用戶端都不需要認證。</span><span class="sxs-lookup"><span data-stu-id="d0a17-124">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="d0a17-125">-Windows： 這可讓 SOAP 交換加入 Windows 認證的已驗證的內容。</span><span class="sxs-lookup"><span data-stu-id="d0a17-125">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="d0a17-126">如此一定會執行 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="d0a17-126">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="d0a17-127">-UserName： 這可讓服務要求使用 UserName 認證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="d0a17-127">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="d0a17-128">認證在此情況下必須使用來指定`clientCredentials`行為**注意：** Windows Communication Foundation (WCF) 不支援傳送密碼摘要或衍生的金鑰使用的密碼，並使用這類金鑰訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="d0a17-128">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="d0a17-129">因此，WCF 會強制使用 UserName 認證時，保護交換。</span><span class="sxs-lookup"><span data-stu-id="d0a17-129">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="d0a17-130">這個模式需要使用 `clientCredential` 行為和 `serviceCertificate` 在用戶端上指定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="d0a17-130">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="d0a17-131">這可讓服務要求憑證： 使用憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="d0a17-131">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="d0a17-132">此案例中的用戶端認證必須使用 `clientCredentials` 行為來指定。</span><span class="sxs-lookup"><span data-stu-id="d0a17-132">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="d0a17-133">此案例中的服務認證需要藉由指定 `clientCredentials`，以使用 `serviceCertificate` 行為來指定。</span><span class="sxs-lookup"><span data-stu-id="d0a17-133">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="d0a17-134">-CardSpace： 這可讓服務要求用戶端使用 CardSpace 來驗證。</span><span class="sxs-lookup"><span data-stu-id="d0a17-134">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="d0a17-135">`serviceCertiifcate` 行為中必須提供 `clientCredential`。</span><span class="sxs-lookup"><span data-stu-id="d0a17-135">The `serviceCertiifcate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="d0a17-136">預設值是 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="d0a17-136">The default value is `Windows`.</span></span> <span data-ttu-id="d0a17-137">此屬性的型別為 <xref:System.ServiceModel.MessageCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="d0a17-137">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0a17-138">子元素</span><span class="sxs-lookup"><span data-stu-id="d0a17-138">Child Elements</span></span>  
 <span data-ttu-id="d0a17-139">無</span><span class="sxs-lookup"><span data-stu-id="d0a17-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0a17-140">父項目</span><span class="sxs-lookup"><span data-stu-id="d0a17-140">Parent Elements</span></span>  
  
|<span data-ttu-id="d0a17-141">項目</span><span class="sxs-lookup"><span data-stu-id="d0a17-141">Element</span></span>|<span data-ttu-id="d0a17-142">描述</span><span class="sxs-lookup"><span data-stu-id="d0a17-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0a17-143">\<security></span><span class="sxs-lookup"><span data-stu-id="d0a17-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="d0a17-144">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="d0a17-144">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0a17-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0a17-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [<span data-ttu-id="d0a17-146">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="d0a17-146">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="d0a17-147">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="d0a17-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d0a17-148">繫結</span><span class="sxs-lookup"><span data-stu-id="d0a17-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d0a17-149">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="d0a17-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d0a17-150">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="d0a17-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d0a17-151">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="d0a17-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
