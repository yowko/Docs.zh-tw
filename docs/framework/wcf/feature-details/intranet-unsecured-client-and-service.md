---
title: 沒有安全保障的內部網路用戶端與服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: 1edbfe2d0d25ea9f2145f879673fc9f0a6ee7f96
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547189"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="d6bcb-102">沒有安全保障的內部網路用戶端與服務</span><span class="sxs-lookup"><span data-stu-id="d6bcb-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="d6bcb-103">下圖說明一個簡單 Windows Communication Foundation (WCF) 服務，其開發目的是要將安全私人網路的資訊提供給 WCF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6bcb-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="d6bcb-104">不需要安全性，因為資料的重要性很低、網路預期會是安全的，或是由 WCF 基礎結構底下的層級提供安全性。</span><span class="sxs-lookup"><span data-stu-id="d6bcb-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 ![內部網路不安全的用戶端和服務案例。](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|<span data-ttu-id="d6bcb-106">特性</span><span class="sxs-lookup"><span data-stu-id="d6bcb-106">Characteristic</span></span>|<span data-ttu-id="d6bcb-107">描述</span><span class="sxs-lookup"><span data-stu-id="d6bcb-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d6bcb-108">安全性模式</span><span class="sxs-lookup"><span data-stu-id="d6bcb-108">Security Mode</span></span>|<span data-ttu-id="d6bcb-109">None</span><span class="sxs-lookup"><span data-stu-id="d6bcb-109">None</span></span>|  
|<span data-ttu-id="d6bcb-110">傳輸</span><span class="sxs-lookup"><span data-stu-id="d6bcb-110">Transport</span></span>|<span data-ttu-id="d6bcb-111">TCP</span><span class="sxs-lookup"><span data-stu-id="d6bcb-111">TCP</span></span>|  
|<span data-ttu-id="d6bcb-112">繫結</span><span class="sxs-lookup"><span data-stu-id="d6bcb-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="d6bcb-113">互通性</span><span class="sxs-lookup"><span data-stu-id="d6bcb-113">Interoperability</span></span>|<span data-ttu-id="d6bcb-114">僅限 WCF</span><span class="sxs-lookup"><span data-stu-id="d6bcb-114">WCF only</span></span>|  
|<span data-ttu-id="d6bcb-115">驗證</span><span class="sxs-lookup"><span data-stu-id="d6bcb-115">Authentication</span></span>|<span data-ttu-id="d6bcb-116">None</span><span class="sxs-lookup"><span data-stu-id="d6bcb-116">None</span></span>|  
|<span data-ttu-id="d6bcb-117">完整性</span><span class="sxs-lookup"><span data-stu-id="d6bcb-117">Integrity</span></span>|<span data-ttu-id="d6bcb-118">None</span><span class="sxs-lookup"><span data-stu-id="d6bcb-118">None</span></span>|  
|<span data-ttu-id="d6bcb-119">機密性</span><span class="sxs-lookup"><span data-stu-id="d6bcb-119">Confidentiality</span></span>|<span data-ttu-id="d6bcb-120">None</span><span class="sxs-lookup"><span data-stu-id="d6bcb-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="d6bcb-121">服務</span><span class="sxs-lookup"><span data-stu-id="d6bcb-121">Service</span></span>  
 <span data-ttu-id="d6bcb-122">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="d6bcb-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d6bcb-123">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="d6bcb-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="d6bcb-124">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="d6bcb-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="d6bcb-125">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="d6bcb-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d6bcb-126">程式碼</span><span class="sxs-lookup"><span data-stu-id="d6bcb-126">Code</span></span>  
 <span data-ttu-id="d6bcb-127">下列程式碼會示範如何建立無安全性的端點：</span><span class="sxs-lookup"><span data-stu-id="d6bcb-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="d6bcb-128">組態</span><span class="sxs-lookup"><span data-stu-id="d6bcb-128">Configuration</span></span>  
 <span data-ttu-id="d6bcb-129">下列程式碼會設定使用組態的相同端點：</span><span class="sxs-lookup"><span data-stu-id="d6bcb-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="d6bcb-130">用戶端</span><span class="sxs-lookup"><span data-stu-id="d6bcb-130">Client</span></span>  
 <span data-ttu-id="d6bcb-131">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="d6bcb-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d6bcb-132">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="d6bcb-132">Do one of the following:</span></span>  
  
- <span data-ttu-id="d6bcb-133">使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。</span><span class="sxs-lookup"><span data-stu-id="d6bcb-133">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="d6bcb-134">建立未定義任何端點位址的用戶端，</span><span class="sxs-lookup"><span data-stu-id="d6bcb-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="d6bcb-135">然後改用可接受組態名稱當做引數的用戶端建構函式。</span><span class="sxs-lookup"><span data-stu-id="d6bcb-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="d6bcb-136">例如：</span><span class="sxs-lookup"><span data-stu-id="d6bcb-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="d6bcb-137">程式碼</span><span class="sxs-lookup"><span data-stu-id="d6bcb-137">Code</span></span>  
 <span data-ttu-id="d6bcb-138">下列程式碼顯示使用 TCP 通訊協定來存取不安全端點的基本 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="d6bcb-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="d6bcb-139">組態</span><span class="sxs-lookup"><span data-stu-id="d6bcb-139">Configuration</span></span>  
 <span data-ttu-id="d6bcb-140">下列組態程式碼會套用至用戶端：</span><span class="sxs-lookup"><span data-stu-id="d6bcb-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6bcb-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6bcb-141">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- [<span data-ttu-id="d6bcb-142">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="d6bcb-142">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="d6bcb-143">[Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d6bcb-143">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
