---
title: "匿名用戶端的傳輸安全性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 97a3c9c618fc7d6c96deba0b72e25ef36c5785e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="e45c9-102">匿名用戶端的傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="e45c9-102">Transport Security with an Anonymous Client</span></span>
<span data-ttu-id="e45c9-103">這個 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 案例會使用傳輸安全性 (HTTPS) 來確保機密性和完整性。</span><span class="sxs-lookup"><span data-stu-id="e45c9-103">This [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="e45c9-104">伺服器必須使用安全通訊端層 (SSL) 憑證進行驗證，而且用戶端必須信任該伺服器的憑證。</span><span class="sxs-lookup"><span data-stu-id="e45c9-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="e45c9-105">此用戶端不會透過任何機制進行驗證，因此屬於匿名。</span><span class="sxs-lookup"><span data-stu-id="e45c9-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>  
  
 <span data-ttu-id="e45c9-106">範例應用程式，請參閱[WS 傳輸安全性](../../../../docs/framework/wcf/samples/ws-transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="e45c9-106">For a sample application, see [WS Transport Security](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e45c9-107">傳輸安全性，請參閱[傳輸安全性概觀](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e45c9-107"> transport security, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e45c9-108">使用憑證與服務，請參閱[使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)和[How to： 使用 SSL 憑證設定連接埠](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="e45c9-108"> using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 <span data-ttu-id="e45c9-109">![搭配匿名用戶端使用傳輸安全性](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span><span class="sxs-lookup"><span data-stu-id="e45c9-109">![Using transport security with an anonymous client](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span></span>  
  
|<span data-ttu-id="e45c9-110">特性</span><span class="sxs-lookup"><span data-stu-id="e45c9-110">Characteristic</span></span>|<span data-ttu-id="e45c9-111">描述</span><span class="sxs-lookup"><span data-stu-id="e45c9-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e45c9-112">安全性模式</span><span class="sxs-lookup"><span data-stu-id="e45c9-112">Security Mode</span></span>|<span data-ttu-id="e45c9-113">Transport</span><span class="sxs-lookup"><span data-stu-id="e45c9-113">Transport</span></span>|  
|<span data-ttu-id="e45c9-114">互通性</span><span class="sxs-lookup"><span data-stu-id="e45c9-114">Interoperability</span></span>|<span data-ttu-id="e45c9-115">與現有的 Web 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="e45c9-115">With existing Web services and clients</span></span>|  
|<span data-ttu-id="e45c9-116">驗證 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="e45c9-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="e45c9-117">驗證 (用戶端)</span><span class="sxs-lookup"><span data-stu-id="e45c9-117">Authentication (Client)</span></span>|<span data-ttu-id="e45c9-118">[是]</span><span class="sxs-lookup"><span data-stu-id="e45c9-118">Yes</span></span><br /><br /> <span data-ttu-id="e45c9-119">應用程式層 ([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不支援)</span><span class="sxs-lookup"><span data-stu-id="e45c9-119">Application level (no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] support)</span></span>|  
|<span data-ttu-id="e45c9-120">完整性</span><span class="sxs-lookup"><span data-stu-id="e45c9-120">Integrity</span></span>|<span data-ttu-id="e45c9-121">是</span><span class="sxs-lookup"><span data-stu-id="e45c9-121">Yes</span></span>|  
|<span data-ttu-id="e45c9-122">機密性</span><span class="sxs-lookup"><span data-stu-id="e45c9-122">Confidentiality</span></span>|<span data-ttu-id="e45c9-123">是</span><span class="sxs-lookup"><span data-stu-id="e45c9-123">Yes</span></span>|  
|<span data-ttu-id="e45c9-124">Transport</span><span class="sxs-lookup"><span data-stu-id="e45c9-124">Transport</span></span>|<span data-ttu-id="e45c9-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="e45c9-125">HTTPS</span></span>|  
|<span data-ttu-id="e45c9-126">繫結</span><span class="sxs-lookup"><span data-stu-id="e45c9-126">Binding</span></span>|<span data-ttu-id="e45c9-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="e45c9-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span></span>|  
  
## <a name="service"></a><span data-ttu-id="e45c9-128">服務</span><span class="sxs-lookup"><span data-stu-id="e45c9-128">Service</span></span>  
 <span data-ttu-id="e45c9-129">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="e45c9-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e45c9-130">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="e45c9-130">Do one of the following:</span></span>  
  
-   <span data-ttu-id="e45c9-131">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="e45c9-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="e45c9-132">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="e45c9-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e45c9-133">程式碼</span><span class="sxs-lookup"><span data-stu-id="e45c9-133">Code</span></span>  
 <span data-ttu-id="e45c9-134">下列程式碼會示範如何建立會使用傳輸安全性的端點：</span><span class="sxs-lookup"><span data-stu-id="e45c9-134">The following code shows how to create an endpoint using transport security:</span></span>  
  
 [!code-csharp[c_SecurityScenarios#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
 [!code-vb[c_SecurityScenarios#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]  
  
### <a name="configuration"></a><span data-ttu-id="e45c9-135">組態</span><span class="sxs-lookup"><span data-stu-id="e45c9-135">Configuration</span></span>  
 <span data-ttu-id="e45c9-136">下列程式碼會使用組態設定相同端點。</span><span class="sxs-lookup"><span data-stu-id="e45c9-136">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="e45c9-137">此用戶端不會透過任何機制進行驗證，因此屬於匿名。</span><span class="sxs-lookup"><span data-stu-id="e45c9-137">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="e45c9-138">用戶端</span><span class="sxs-lookup"><span data-stu-id="e45c9-138">Client</span></span>  
 <span data-ttu-id="e45c9-139">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="e45c9-139">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e45c9-140">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="e45c9-140">Do one of the following:</span></span>  
  
-   <span data-ttu-id="e45c9-141">使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。</span><span class="sxs-lookup"><span data-stu-id="e45c9-141">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="e45c9-142">建立未定義任何端點位址的用戶端，</span><span class="sxs-lookup"><span data-stu-id="e45c9-142">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="e45c9-143">然後改用可接受組態名稱當做引數的用戶端建構函式。</span><span class="sxs-lookup"><span data-stu-id="e45c9-143">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="e45c9-144">例如：</span><span class="sxs-lookup"><span data-stu-id="e45c9-144">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="e45c9-145">程式碼</span><span class="sxs-lookup"><span data-stu-id="e45c9-145">Code</span></span>  
 [!code-csharp[c_SecurityScenarios#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
 [!code-vb[c_SecurityScenarios#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]  
  
### <a name="configuration"></a><span data-ttu-id="e45c9-146">組態</span><span class="sxs-lookup"><span data-stu-id="e45c9-146">Configuration</span></span>  
 <span data-ttu-id="e45c9-147">可以使用下列組態來取代程式碼，進行設定服務。</span><span class="sxs-lookup"><span data-stu-id="e45c9-147">The following configuration can be used instead of the code to set up the service.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
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
  
## <a name="see-also"></a><span data-ttu-id="e45c9-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="e45c9-148">See Also</span></span>  
 [<span data-ttu-id="e45c9-149">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="e45c9-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="e45c9-150">WS 傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="e45c9-150">WS Transport Security</span></span>](../../../../docs/framework/wcf/samples/ws-transport-security.md)  
 [<span data-ttu-id="e45c9-151">傳輸安全性概觀</span><span class="sxs-lookup"><span data-stu-id="e45c9-151">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [<span data-ttu-id="e45c9-152">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="e45c9-152">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
