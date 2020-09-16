---
title: 基本驗證的傳輸安全性
description: 請參閱此 WCF 案例，其中會顯示 WCF 服務和用戶端的基本驗證。 服務需要用戶端所信任的有效憑證。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 2add8c21ca8ade4b530e0e6b1b3c5bba66e100ab
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556781"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="d1e4b-104">基本驗證的傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="d1e4b-104">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="d1e4b-105">下圖顯示 WCF) 服務和用戶端 (Windows Communication Foundation。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-105">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="d1e4b-106">伺服器需要可用於 Secure Sockets Layer (SSL) 的有效 X.509 憑證，而用戶端必須信任伺服器的憑證。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-106">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="d1e4b-107">此外，Web 服務已經有可以使用的 SSL 實作。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-107">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="d1e4b-108">如需在 Internet Information Services 上啟用基本驗證 (IIS) 的詳細資訊，請參閱 <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> 。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-108">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![顯示使用基本驗證的傳輸安全性螢幕擷取畫面。](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="d1e4b-110">特性</span><span class="sxs-lookup"><span data-stu-id="d1e4b-110">Characteristic</span></span>|<span data-ttu-id="d1e4b-111">描述</span><span class="sxs-lookup"><span data-stu-id="d1e4b-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d1e4b-112">安全性模式</span><span class="sxs-lookup"><span data-stu-id="d1e4b-112">Security Mode</span></span>|<span data-ttu-id="d1e4b-113">傳輸</span><span class="sxs-lookup"><span data-stu-id="d1e4b-113">Transport</span></span>|  
|<span data-ttu-id="d1e4b-114">互通性</span><span class="sxs-lookup"><span data-stu-id="d1e4b-114">Interoperability</span></span>|<span data-ttu-id="d1e4b-115">使用現有的 Web 服務用戶端和服務</span><span class="sxs-lookup"><span data-stu-id="d1e4b-115">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="d1e4b-116">驗證 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="d1e4b-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="d1e4b-117">驗證 (用戶端)</span><span class="sxs-lookup"><span data-stu-id="d1e4b-117">Authentication (Client)</span></span>|<span data-ttu-id="d1e4b-118">是 (使用 HTTPS)</span><span class="sxs-lookup"><span data-stu-id="d1e4b-118">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="d1e4b-119">是 (透過使用者名稱/密碼)</span><span class="sxs-lookup"><span data-stu-id="d1e4b-119">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="d1e4b-120">完整性</span><span class="sxs-lookup"><span data-stu-id="d1e4b-120">Integrity</span></span>|<span data-ttu-id="d1e4b-121">是</span><span class="sxs-lookup"><span data-stu-id="d1e4b-121">Yes</span></span>|  
|<span data-ttu-id="d1e4b-122">機密性</span><span class="sxs-lookup"><span data-stu-id="d1e4b-122">Confidentiality</span></span>|<span data-ttu-id="d1e4b-123">是</span><span class="sxs-lookup"><span data-stu-id="d1e4b-123">Yes</span></span>|  
|<span data-ttu-id="d1e4b-124">傳輸</span><span class="sxs-lookup"><span data-stu-id="d1e4b-124">Transport</span></span>|<span data-ttu-id="d1e4b-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="d1e4b-125">HTTPS</span></span>|  
|<span data-ttu-id="d1e4b-126">繫結</span><span class="sxs-lookup"><span data-stu-id="d1e4b-126">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="d1e4b-127">服務</span><span class="sxs-lookup"><span data-stu-id="d1e4b-127">Service</span></span>  
 <span data-ttu-id="d1e4b-128">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-128">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d1e4b-129">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="d1e4b-129">Do one of the following:</span></span>  
  
- <span data-ttu-id="d1e4b-130">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-130">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="d1e4b-131">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-131">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d1e4b-132">程式碼</span><span class="sxs-lookup"><span data-stu-id="d1e4b-132">Code</span></span>  
 <span data-ttu-id="d1e4b-133">下列程式碼顯示如何為傳輸安全性建立使用 Windows 網域使用者名稱和密碼的服務端點。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-133">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="d1e4b-134">請注意，服務需要 X.509 憑證來驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-134">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="d1e4b-135">如需詳細資訊，請參閱 [使用憑證](working-with-certificates.md) 和 [如何：使用 SSL 憑證設定埠](how-to-configure-a-port-with-an-ssl-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-135">For more information, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="d1e4b-136">組態</span><span class="sxs-lookup"><span data-stu-id="d1e4b-136">Configuration</span></span>  
 <span data-ttu-id="d1e4b-137">下列會設定服務以使用具有傳輸層級安全性的基本驗證：</span><span class="sxs-lookup"><span data-stu-id="d1e4b-137">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="d1e4b-138">用戶端</span><span class="sxs-lookup"><span data-stu-id="d1e4b-138">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="d1e4b-139">程式碼</span><span class="sxs-lookup"><span data-stu-id="d1e4b-139">Code</span></span>  
 <span data-ttu-id="d1e4b-140">下列程式碼顯示包含使用者名稱和密碼的用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-140">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="d1e4b-141">請注意，使用者必須提供有效的 Windows 使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-141">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="d1e4b-142">此處未顯示傳回使用者名稱和密碼的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-142">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="d1e4b-143">請使用對話方塊或其他介面向使用者查詢資訊。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-143">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1e4b-144">使用者名稱和密碼只能使用程式碼來設定。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-144">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="d1e4b-145">組態</span><span class="sxs-lookup"><span data-stu-id="d1e4b-145">Configuration</span></span>  
 <span data-ttu-id="d1e4b-146">下列程式碼顯示用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-146">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1e4b-147">您不能使用組態來設定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-147">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="d1e4b-148">此處所示的組態必須使用程式碼來增強，以設定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="d1e4b-148">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d1e4b-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1e4b-149">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="d1e4b-150">使用憑證</span><span class="sxs-lookup"><span data-stu-id="d1e4b-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="d1e4b-151">作法：使用 SSL 憑證設定連接埠</span><span class="sxs-lookup"><span data-stu-id="d1e4b-151">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="d1e4b-152">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="d1e4b-152">Security Overview</span></span>](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="d1e4b-153">[Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d1e4b-153">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
