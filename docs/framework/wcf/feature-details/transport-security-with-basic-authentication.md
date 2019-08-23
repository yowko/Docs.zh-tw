---
title: 基本驗證的傳輸安全性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 3340a0f455646357035b0999a12e78acb08c2572
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962635"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="b6b29-102">基本驗證的傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="b6b29-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="b6b29-103">下圖顯示 Windows Communication Foundation (WCF) 服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="b6b29-103">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="b6b29-104">伺服器需要可用於 Secure Sockets Layer (SSL) 的有效 X.509 憑證，而用戶端必須信任伺服器的憑證。</span><span class="sxs-lookup"><span data-stu-id="b6b29-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="b6b29-105">此外，Web 服務已經有可以使用的 SSL 實作。</span><span class="sxs-lookup"><span data-stu-id="b6b29-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="b6b29-106">如需在 Internet Information Services (IIS) 上啟用基本驗證的詳細<https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>資訊, 請參閱。</span><span class="sxs-lookup"><span data-stu-id="b6b29-106">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![顯示使用基本驗證之傳輸安全性的螢幕擷取畫面。](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="b6b29-108">特性</span><span class="sxs-lookup"><span data-stu-id="b6b29-108">Characteristic</span></span>|<span data-ttu-id="b6b29-109">說明</span><span class="sxs-lookup"><span data-stu-id="b6b29-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b6b29-110">安全性模式</span><span class="sxs-lookup"><span data-stu-id="b6b29-110">Security Mode</span></span>|<span data-ttu-id="b6b29-111">Transport</span><span class="sxs-lookup"><span data-stu-id="b6b29-111">Transport</span></span>|  
|<span data-ttu-id="b6b29-112">互通性</span><span class="sxs-lookup"><span data-stu-id="b6b29-112">Interoperability</span></span>|<span data-ttu-id="b6b29-113">使用現有的 Web 服務用戶端和服務</span><span class="sxs-lookup"><span data-stu-id="b6b29-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="b6b29-114">驗證 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="b6b29-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="b6b29-115">驗證 (用戶端)</span><span class="sxs-lookup"><span data-stu-id="b6b29-115">Authentication (Client)</span></span>|<span data-ttu-id="b6b29-116">是 (使用 HTTPS)</span><span class="sxs-lookup"><span data-stu-id="b6b29-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="b6b29-117">是 (透過使用者名稱/密碼)</span><span class="sxs-lookup"><span data-stu-id="b6b29-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="b6b29-118">完整性</span><span class="sxs-lookup"><span data-stu-id="b6b29-118">Integrity</span></span>|<span data-ttu-id="b6b29-119">是</span><span class="sxs-lookup"><span data-stu-id="b6b29-119">Yes</span></span>|  
|<span data-ttu-id="b6b29-120">機密性</span><span class="sxs-lookup"><span data-stu-id="b6b29-120">Confidentiality</span></span>|<span data-ttu-id="b6b29-121">是</span><span class="sxs-lookup"><span data-stu-id="b6b29-121">Yes</span></span>|  
|<span data-ttu-id="b6b29-122">Transport</span><span class="sxs-lookup"><span data-stu-id="b6b29-122">Transport</span></span>|<span data-ttu-id="b6b29-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="b6b29-123">HTTPS</span></span>|  
|<span data-ttu-id="b6b29-124">繫結</span><span class="sxs-lookup"><span data-stu-id="b6b29-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="b6b29-125">服務</span><span class="sxs-lookup"><span data-stu-id="b6b29-125">Service</span></span>  
 <span data-ttu-id="b6b29-126">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="b6b29-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b6b29-127">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="b6b29-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="b6b29-128">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="b6b29-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="b6b29-129">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="b6b29-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b6b29-130">程式碼</span><span class="sxs-lookup"><span data-stu-id="b6b29-130">Code</span></span>  
 <span data-ttu-id="b6b29-131">下列程式碼顯示如何為傳輸安全性建立使用 Windows 網域使用者名稱和密碼的服務端點。</span><span class="sxs-lookup"><span data-stu-id="b6b29-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="b6b29-132">請注意，服務需要 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="b6b29-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="b6b29-133">如需詳細資訊, 請參閱[使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)和[如何:使用 SSL 憑證](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)設定埠。</span><span class="sxs-lookup"><span data-stu-id="b6b29-133">For more information, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="b6b29-134">組態</span><span class="sxs-lookup"><span data-stu-id="b6b29-134">Configuration</span></span>  
 <span data-ttu-id="b6b29-135">下列會設定服務以使用具有傳輸層級安全性的基本驗證：</span><span class="sxs-lookup"><span data-stu-id="b6b29-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"   
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"   
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="b6b29-136">用戶端</span><span class="sxs-lookup"><span data-stu-id="b6b29-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="b6b29-137">程式碼</span><span class="sxs-lookup"><span data-stu-id="b6b29-137">Code</span></span>  
 <span data-ttu-id="b6b29-138">下列程式碼顯示包含使用者名稱和密碼的用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6b29-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="b6b29-139">請注意，使用者必須提供有效的 Windows 使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="b6b29-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="b6b29-140">此處未顯示傳回使用者名稱和密碼的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6b29-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="b6b29-141">請使用對話方塊或其他介面向使用者查詢資訊。</span><span class="sxs-lookup"><span data-stu-id="b6b29-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6b29-142">使用者名稱和密碼只能使用程式碼來設定。</span><span class="sxs-lookup"><span data-stu-id="b6b29-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="b6b29-143">組態</span><span class="sxs-lookup"><span data-stu-id="b6b29-143">Configuration</span></span>  
 <span data-ttu-id="b6b29-144">下列程式碼顯示用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="b6b29-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6b29-145">您不能使用組態來設定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="b6b29-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="b6b29-146">此處所示的組態必須使用程式碼來增強，以設定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="b6b29-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6b29-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6b29-147">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="b6b29-148">使用憑證</span><span class="sxs-lookup"><span data-stu-id="b6b29-148">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="b6b29-149">如何：使用 SSL 憑證設定埠</span><span class="sxs-lookup"><span data-stu-id="b6b29-149">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="b6b29-150">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="b6b29-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="b6b29-151">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="b6b29-151">\<clientCredentials></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
- [<span data-ttu-id="b6b29-152">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="b6b29-152">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
