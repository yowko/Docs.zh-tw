---
title: Windows 驗證的傳輸安全性
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
caps.latest.revision: 17
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 5effb18435241b00c3036fd23e15ef5ce485b646
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="78f9b-102">Windows 驗證的傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="78f9b-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="78f9b-103">下列案例會顯示 Windows 安全性所保護的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="78f9b-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service secured by Windows security.</span></span> <span data-ttu-id="78f9b-104">如需程式設計的詳細資訊，請參閱[How to： 安全 Windows 認證的服務](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)。</span><span class="sxs-lookup"><span data-stu-id="78f9b-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="78f9b-105">內部網路 Web 服務顯示人力資源資訊。</span><span class="sxs-lookup"><span data-stu-id="78f9b-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="78f9b-106">用戶端為 Windows Form 應用程式。</span><span class="sxs-lookup"><span data-stu-id="78f9b-106">The client is a Windows Form application.</span></span> <span data-ttu-id="78f9b-107">應用程式部署於由 Kerberos 控制站負責網域安全的網域內。</span><span class="sxs-lookup"><span data-stu-id="78f9b-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 <span data-ttu-id="78f9b-108">![傳輸安全性使用 Windows 驗證](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span><span class="sxs-lookup"><span data-stu-id="78f9b-108">![Transport security with Windows authentication](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span></span>  
  
|<span data-ttu-id="78f9b-109">特性</span><span class="sxs-lookup"><span data-stu-id="78f9b-109">Characteristic</span></span>|<span data-ttu-id="78f9b-110">描述</span><span class="sxs-lookup"><span data-stu-id="78f9b-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="78f9b-111">安全性模式</span><span class="sxs-lookup"><span data-stu-id="78f9b-111">Security Mode</span></span>|<span data-ttu-id="78f9b-112">Transport</span><span class="sxs-lookup"><span data-stu-id="78f9b-112">Transport</span></span>|  
|<span data-ttu-id="78f9b-113">互通性</span><span class="sxs-lookup"><span data-stu-id="78f9b-113">Interoperability</span></span>|<span data-ttu-id="78f9b-114">僅限 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78f9b-114">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] only</span></span>|  
|<span data-ttu-id="78f9b-115">驗證 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="78f9b-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="78f9b-116">驗證 (用戶端)</span><span class="sxs-lookup"><span data-stu-id="78f9b-116">Authentication (Client)</span></span>|<span data-ttu-id="78f9b-117">是 (使用 Windows 整合式驗證)</span><span class="sxs-lookup"><span data-stu-id="78f9b-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="78f9b-118">是 (使用 Windows 整合式驗證)</span><span class="sxs-lookup"><span data-stu-id="78f9b-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="78f9b-119">完整性</span><span class="sxs-lookup"><span data-stu-id="78f9b-119">Integrity</span></span>|<span data-ttu-id="78f9b-120">是</span><span class="sxs-lookup"><span data-stu-id="78f9b-120">Yes</span></span>|  
|<span data-ttu-id="78f9b-121">機密性</span><span class="sxs-lookup"><span data-stu-id="78f9b-121">Confidentiality</span></span>|<span data-ttu-id="78f9b-122">是</span><span class="sxs-lookup"><span data-stu-id="78f9b-122">Yes</span></span>|  
|<span data-ttu-id="78f9b-123">Transport</span><span class="sxs-lookup"><span data-stu-id="78f9b-123">Transport</span></span>|<span data-ttu-id="78f9b-124">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="78f9b-124">NET.TCP</span></span>|  
|<span data-ttu-id="78f9b-125">繫結</span><span class="sxs-lookup"><span data-stu-id="78f9b-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="78f9b-126">服務</span><span class="sxs-lookup"><span data-stu-id="78f9b-126">Service</span></span>  
 <span data-ttu-id="78f9b-127">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="78f9b-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="78f9b-128">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="78f9b-128">Do one of the following:</span></span>  
  
-   <span data-ttu-id="78f9b-129">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="78f9b-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="78f9b-130">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="78f9b-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="78f9b-131">程式碼</span><span class="sxs-lookup"><span data-stu-id="78f9b-131">Code</span></span>  
 <span data-ttu-id="78f9b-132">下列程式碼顯示如何建立使用 Windows 安全性的服務端點。</span><span class="sxs-lookup"><span data-stu-id="78f9b-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="78f9b-133">組態</span><span class="sxs-lookup"><span data-stu-id="78f9b-133">Configuration</span></span>  
 <span data-ttu-id="78f9b-134">可使用以下組態來取代程式碼設定服務端點。</span><span class="sxs-lookup"><span data-stu-id="78f9b-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"   
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="78f9b-135">用戶端</span><span class="sxs-lookup"><span data-stu-id="78f9b-135">Client</span></span>  
 <span data-ttu-id="78f9b-136">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="78f9b-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="78f9b-137">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="78f9b-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="78f9b-138">使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。</span><span class="sxs-lookup"><span data-stu-id="78f9b-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="78f9b-139">建立未定義任何端點位址的用戶端，</span><span class="sxs-lookup"><span data-stu-id="78f9b-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="78f9b-140">然後改用可接受組態名稱當做引數的用戶端建構函式。</span><span class="sxs-lookup"><span data-stu-id="78f9b-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="78f9b-141">例如：</span><span class="sxs-lookup"><span data-stu-id="78f9b-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="78f9b-142">程式碼</span><span class="sxs-lookup"><span data-stu-id="78f9b-142">Code</span></span>  
 <span data-ttu-id="78f9b-143">下列程式碼會建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="78f9b-143">The following code creates the client.</span></span> <span data-ttu-id="78f9b-144">繫結會設定為使用傳輸模式安全性，採用 TCP 傳輸，並將用戶端認證類型設為 Windows。</span><span class="sxs-lookup"><span data-stu-id="78f9b-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="78f9b-145">組態</span><span class="sxs-lookup"><span data-stu-id="78f9b-145">Configuration</span></span>  
 <span data-ttu-id="78f9b-146">可使用以下組態來取代程式碼建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="78f9b-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"   
                binding="netTcpBinding"            
                bindingConfiguration="NetTcpBinding_ICalculator"   
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="78f9b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78f9b-147">See Also</span></span>  
 [<span data-ttu-id="78f9b-148">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="78f9b-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="78f9b-149">如何：利用 Windows 認證保護服務的安全</span><span class="sxs-lookup"><span data-stu-id="78f9b-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [<span data-ttu-id="78f9b-150">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="78f9b-150">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
