---
title: 沒有安全保障的內部網路用戶端與服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: eb165b69e1312363a8cc7c1a3ceea66a422d54f7
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50048459"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="b0e53-102">沒有安全保障的內部網路用戶端與服務</span><span class="sxs-lookup"><span data-stu-id="b0e53-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="b0e53-103">下圖說明簡單的 Windows Communication Foundation (WCF) 服務，開發 WCF 應用程式的安全私人網路上提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="b0e53-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="b0e53-104">因為資料重要性低、 預期是原本就是安全的網路，或安全性由 WCF 基礎結構下一層提供，則不需要安全性。</span><span class="sxs-lookup"><span data-stu-id="b0e53-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 <span data-ttu-id="b0e53-105">![內部網路不安全的用戶端和服務情節](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span><span class="sxs-lookup"><span data-stu-id="b0e53-105">![Intranet unsecured client and service scenario](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span></span>  
  
|<span data-ttu-id="b0e53-106">特性</span><span class="sxs-lookup"><span data-stu-id="b0e53-106">Characteristic</span></span>|<span data-ttu-id="b0e53-107">描述</span><span class="sxs-lookup"><span data-stu-id="b0e53-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b0e53-108">安全性模式</span><span class="sxs-lookup"><span data-stu-id="b0e53-108">Security Mode</span></span>|<span data-ttu-id="b0e53-109">無</span><span class="sxs-lookup"><span data-stu-id="b0e53-109">None</span></span>|  
|<span data-ttu-id="b0e53-110">Transport</span><span class="sxs-lookup"><span data-stu-id="b0e53-110">Transport</span></span>|<span data-ttu-id="b0e53-111">TCP</span><span class="sxs-lookup"><span data-stu-id="b0e53-111">TCP</span></span>|  
|<span data-ttu-id="b0e53-112">繫結</span><span class="sxs-lookup"><span data-stu-id="b0e53-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="b0e53-113">互通性</span><span class="sxs-lookup"><span data-stu-id="b0e53-113">Interoperability</span></span>|<span data-ttu-id="b0e53-114">WCF 只</span><span class="sxs-lookup"><span data-stu-id="b0e53-114">WCF only</span></span>|  
|<span data-ttu-id="b0e53-115">驗證</span><span class="sxs-lookup"><span data-stu-id="b0e53-115">Authentication</span></span>|<span data-ttu-id="b0e53-116">無</span><span class="sxs-lookup"><span data-stu-id="b0e53-116">None</span></span>|  
|<span data-ttu-id="b0e53-117">完整性</span><span class="sxs-lookup"><span data-stu-id="b0e53-117">Integrity</span></span>|<span data-ttu-id="b0e53-118">無</span><span class="sxs-lookup"><span data-stu-id="b0e53-118">None</span></span>|  
|<span data-ttu-id="b0e53-119">機密性</span><span class="sxs-lookup"><span data-stu-id="b0e53-119">Confidentiality</span></span>|<span data-ttu-id="b0e53-120">無</span><span class="sxs-lookup"><span data-stu-id="b0e53-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="b0e53-121">服務</span><span class="sxs-lookup"><span data-stu-id="b0e53-121">Service</span></span>  
 <span data-ttu-id="b0e53-122">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="b0e53-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b0e53-123">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="b0e53-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="b0e53-124">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="b0e53-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="b0e53-125">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="b0e53-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b0e53-126">程式碼</span><span class="sxs-lookup"><span data-stu-id="b0e53-126">Code</span></span>  
 <span data-ttu-id="b0e53-127">下列程式碼會示範如何建立無安全性的端點：</span><span class="sxs-lookup"><span data-stu-id="b0e53-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="b0e53-128">組態</span><span class="sxs-lookup"><span data-stu-id="b0e53-128">Configuration</span></span>  
 <span data-ttu-id="b0e53-129">下列程式碼會設定使用組態的相同端點：</span><span class="sxs-lookup"><span data-stu-id="b0e53-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="b0e53-130">用戶端</span><span class="sxs-lookup"><span data-stu-id="b0e53-130">Client</span></span>  
 <span data-ttu-id="b0e53-131">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="b0e53-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b0e53-132">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="b0e53-132">Do one of the following:</span></span>  
  
-   <span data-ttu-id="b0e53-133">使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。</span><span class="sxs-lookup"><span data-stu-id="b0e53-133">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="b0e53-134">建立未定義任何端點位址的用戶端，</span><span class="sxs-lookup"><span data-stu-id="b0e53-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="b0e53-135">然後改用可接受組態名稱當做引數的用戶端建構函式。</span><span class="sxs-lookup"><span data-stu-id="b0e53-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="b0e53-136">例如：</span><span class="sxs-lookup"><span data-stu-id="b0e53-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="b0e53-137">程式碼</span><span class="sxs-lookup"><span data-stu-id="b0e53-137">Code</span></span>  
 <span data-ttu-id="b0e53-138">下列程式碼會顯示基本的 WCF 用戶端存取使用 TCP 通訊協定的不安全的端點。</span><span class="sxs-lookup"><span data-stu-id="b0e53-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="b0e53-139">組態</span><span class="sxs-lookup"><span data-stu-id="b0e53-139">Configuration</span></span>  
 <span data-ttu-id="b0e53-140">下列組態程式碼會套用至用戶端：</span><span class="sxs-lookup"><span data-stu-id="b0e53-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0e53-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0e53-141">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 [<span data-ttu-id="b0e53-142">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="b0e53-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="b0e53-143">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="b0e53-143">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
