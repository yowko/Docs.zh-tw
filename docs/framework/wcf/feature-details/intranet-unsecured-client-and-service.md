---
title: "沒有安全保障的內部網路用戶端與服務"
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
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
caps.latest.revision: "20"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9a3faa27d54f2aa67cd974bc1827d71163e411b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="89d12-102">沒有安全保障的內部網路用戶端與服務</span><span class="sxs-lookup"><span data-stu-id="89d12-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="89d12-103">下圖說明為了在安全私人網路上提供資訊給 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式而開發的簡單 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="89d12-103">The following illustration depicts a simple [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service developed to provide information on a secure private network to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="89d12-104">因為資料重要性低、預期網路本質上是安全的，或者安全性已由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 基礎結構的下一層提供，所以不需要安全性。</span><span class="sxs-lookup"><span data-stu-id="89d12-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure.</span></span>  
  
 <span data-ttu-id="89d12-105">![內部網路不安全的用戶端和服務情節](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span><span class="sxs-lookup"><span data-stu-id="89d12-105">![Intranet unsecured client and service scenario](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span></span>  
  
|<span data-ttu-id="89d12-106">特性</span><span class="sxs-lookup"><span data-stu-id="89d12-106">Characteristic</span></span>|<span data-ttu-id="89d12-107">描述</span><span class="sxs-lookup"><span data-stu-id="89d12-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="89d12-108">安全性模式</span><span class="sxs-lookup"><span data-stu-id="89d12-108">Security Mode</span></span>|<span data-ttu-id="89d12-109">無</span><span class="sxs-lookup"><span data-stu-id="89d12-109">None</span></span>|  
|<span data-ttu-id="89d12-110">Transport</span><span class="sxs-lookup"><span data-stu-id="89d12-110">Transport</span></span>|<span data-ttu-id="89d12-111">TCP</span><span class="sxs-lookup"><span data-stu-id="89d12-111">TCP</span></span>|  
|<span data-ttu-id="89d12-112">繫結</span><span class="sxs-lookup"><span data-stu-id="89d12-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="89d12-113">互通性</span><span class="sxs-lookup"><span data-stu-id="89d12-113">Interoperability</span></span>|<span data-ttu-id="89d12-114">僅限 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89d12-114">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] only</span></span>|  
|<span data-ttu-id="89d12-115">驗證</span><span class="sxs-lookup"><span data-stu-id="89d12-115">Authentication</span></span>|<span data-ttu-id="89d12-116">無</span><span class="sxs-lookup"><span data-stu-id="89d12-116">None</span></span>|  
|<span data-ttu-id="89d12-117">完整性</span><span class="sxs-lookup"><span data-stu-id="89d12-117">Integrity</span></span>|<span data-ttu-id="89d12-118">無</span><span class="sxs-lookup"><span data-stu-id="89d12-118">None</span></span>|  
|<span data-ttu-id="89d12-119">機密性</span><span class="sxs-lookup"><span data-stu-id="89d12-119">Confidentiality</span></span>|<span data-ttu-id="89d12-120">無</span><span class="sxs-lookup"><span data-stu-id="89d12-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="89d12-121">服務</span><span class="sxs-lookup"><span data-stu-id="89d12-121">Service</span></span>  
 <span data-ttu-id="89d12-122">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="89d12-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="89d12-123">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="89d12-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="89d12-124">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="89d12-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="89d12-125">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="89d12-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="89d12-126">程式碼</span><span class="sxs-lookup"><span data-stu-id="89d12-126">Code</span></span>  
 <span data-ttu-id="89d12-127">下列程式碼會示範如何建立無安全性的端點：</span><span class="sxs-lookup"><span data-stu-id="89d12-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="89d12-128">組態</span><span class="sxs-lookup"><span data-stu-id="89d12-128">Configuration</span></span>  
 <span data-ttu-id="89d12-129">下列程式碼會設定使用組態的相同端點：</span><span class="sxs-lookup"><span data-stu-id="89d12-129">The following code sets up the same endpoint using configuration:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration=""   
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
                  bindingConfiguration="tcp_Unsecured"   
                  name="netTcp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="tcp_Unsecured">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="89d12-130">用戶端</span><span class="sxs-lookup"><span data-stu-id="89d12-130">Client</span></span>  
 <span data-ttu-id="89d12-131">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="89d12-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="89d12-132">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="89d12-132">Do one of the following:</span></span>  
  
-   <span data-ttu-id="89d12-133">使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。</span><span class="sxs-lookup"><span data-stu-id="89d12-133">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="89d12-134">建立未定義任何端點位址的用戶端，</span><span class="sxs-lookup"><span data-stu-id="89d12-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="89d12-135">然後改用可接受組態名稱當做引數的用戶端建構函式。</span><span class="sxs-lookup"><span data-stu-id="89d12-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="89d12-136">例如：</span><span class="sxs-lookup"><span data-stu-id="89d12-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="89d12-137">程式碼</span><span class="sxs-lookup"><span data-stu-id="89d12-137">Code</span></span>  
 <span data-ttu-id="89d12-138">下列程式碼示範使用 TCP 通訊協定來存取不安全端點的基本 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端。</span><span class="sxs-lookup"><span data-stu-id="89d12-138">The following code shows a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="89d12-139">組態</span><span class="sxs-lookup"><span data-stu-id="89d12-139">Configuration</span></span>  
 <span data-ttu-id="89d12-140">下列組態程式碼會套用至用戶端：</span><span class="sxs-lookup"><span data-stu-id="89d12-140">The following configuration code applies to the client:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator "  
                binding="netTcpBinding"   
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"   
                name="NetTcpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="89d12-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89d12-141">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 [<span data-ttu-id="89d12-142">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="89d12-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="89d12-143">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="89d12-143">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
