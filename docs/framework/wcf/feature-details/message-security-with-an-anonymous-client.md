---
title: 匿名用戶端的訊息安全性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: aed56be359f094db483ab1d012bd77a1096433b6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553762"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="91d28-102">匿名用戶端的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="91d28-102">Message Security with an Anonymous Client</span></span>

<span data-ttu-id="91d28-103">下列案例顯示 Windows Communication Foundation (WCF) 訊息安全性所保護的用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="91d28-103">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="91d28-104">這樣的設計目的是使用訊息安全性而非傳輸安全性，如此未來可以支援更豐富的宣告型模型。</span><span class="sxs-lookup"><span data-stu-id="91d28-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="91d28-105">如需有關使用豐富宣告進行授權的詳細資訊，請參閱使用身分 [識別模型來管理宣告與授權](managing-claims-and-authorization-with-the-identity-model.md)。</span><span class="sxs-lookup"><span data-stu-id="91d28-105">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="91d28-106">如需範例應用程式，請參閱 [訊息安全性匿名](../samples/message-security-anonymous.md)。</span><span class="sxs-lookup"><span data-stu-id="91d28-106">For a sample application, see [Message Security Anonymous](../samples/message-security-anonymous.md).</span></span>

<span data-ttu-id="91d28-107">![匿名用戶端的訊息安全性](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="91d28-107">![Message security with an anonymous client](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>

|<span data-ttu-id="91d28-108">特性</span><span class="sxs-lookup"><span data-stu-id="91d28-108">Characteristic</span></span>|<span data-ttu-id="91d28-109">描述</span><span class="sxs-lookup"><span data-stu-id="91d28-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="91d28-110">安全性模式</span><span class="sxs-lookup"><span data-stu-id="91d28-110">Security Mode</span></span>|<span data-ttu-id="91d28-111">訊息</span><span class="sxs-lookup"><span data-stu-id="91d28-111">Message</span></span>|
|<span data-ttu-id="91d28-112">互通性</span><span class="sxs-lookup"><span data-stu-id="91d28-112">Interoperability</span></span>|<span data-ttu-id="91d28-113">僅限 WCF</span><span class="sxs-lookup"><span data-stu-id="91d28-113">WCF only</span></span>|
|<span data-ttu-id="91d28-114">驗證 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="91d28-114">Authentication (Server)</span></span>|<span data-ttu-id="91d28-115">初始交涉需要伺服器驗證，而不需要用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="91d28-115">Initial negotiation requires server authentication, but not client authentication</span></span>|
|<span data-ttu-id="91d28-116">驗證 (用戶端)</span><span class="sxs-lookup"><span data-stu-id="91d28-116">Authentication (Client)</span></span>|<span data-ttu-id="91d28-117">None</span><span class="sxs-lookup"><span data-stu-id="91d28-117">None</span></span>|
|<span data-ttu-id="91d28-118">完整性</span><span class="sxs-lookup"><span data-stu-id="91d28-118">Integrity</span></span>|<span data-ttu-id="91d28-119">是，使用共用安全性內容</span><span class="sxs-lookup"><span data-stu-id="91d28-119">Yes, using shared security context</span></span>|
|<span data-ttu-id="91d28-120">機密性</span><span class="sxs-lookup"><span data-stu-id="91d28-120">Confidentiality</span></span>|<span data-ttu-id="91d28-121">是，使用共用安全性內容</span><span class="sxs-lookup"><span data-stu-id="91d28-121">Yes, using shared security context</span></span>|
|<span data-ttu-id="91d28-122">傳輸</span><span class="sxs-lookup"><span data-stu-id="91d28-122">Transport</span></span>|<span data-ttu-id="91d28-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="91d28-123">HTTP</span></span>|

## <a name="service"></a><span data-ttu-id="91d28-124">服務</span><span class="sxs-lookup"><span data-stu-id="91d28-124">Service</span></span>

<span data-ttu-id="91d28-125">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="91d28-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="91d28-126">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="91d28-126">Do one of the following:</span></span>

- <span data-ttu-id="91d28-127">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="91d28-127">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="91d28-128">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="91d28-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="91d28-129">程式碼</span><span class="sxs-lookup"><span data-stu-id="91d28-129">Code</span></span>

<span data-ttu-id="91d28-130">下列程式碼會顯示如何建立會使用訊息安全性的服務端點。</span><span class="sxs-lookup"><span data-stu-id="91d28-130">The following code shows how to create a service endpoint that uses message security.</span></span>

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a><span data-ttu-id="91d28-131">組態</span><span class="sxs-lookup"><span data-stu-id="91d28-131">Configuration</span></span>

<span data-ttu-id="91d28-132">可以使用以下組態來取代程式碼。</span><span class="sxs-lookup"><span data-stu-id="91d28-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="91d28-133">使用服務行為項目來指定用來驗證用戶端服務的憑證。</span><span class="sxs-lookup"><span data-stu-id="91d28-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="91d28-134">服務項目必須使用 `behaviorConfiguration` 屬性來指定行為。</span><span class="sxs-lookup"><span data-stu-id="91d28-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="91d28-135">繫結項目會指定用戶端認證類型為 `None`，因此可讓匿名用戶端使用服務。</span><span class="sxs-lookup"><span data-stu-id="91d28-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="91d28-136">用戶端</span><span class="sxs-lookup"><span data-stu-id="91d28-136">Client</span></span>

<span data-ttu-id="91d28-137">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="91d28-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="91d28-138">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="91d28-138">Do one of the following:</span></span>

- <span data-ttu-id="91d28-139">使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。</span><span class="sxs-lookup"><span data-stu-id="91d28-139">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="91d28-140">建立未定義任何端點位址的用戶端，</span><span class="sxs-lookup"><span data-stu-id="91d28-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="91d28-141">然後改用可接受組態名稱當做引數的用戶端建構函式。</span><span class="sxs-lookup"><span data-stu-id="91d28-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="91d28-142">例如：</span><span class="sxs-lookup"><span data-stu-id="91d28-142">For example:</span></span>

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="91d28-143">程式碼</span><span class="sxs-lookup"><span data-stu-id="91d28-143">Code</span></span>

<span data-ttu-id="91d28-144">下列程式碼會建立用戶端的執行個體。</span><span class="sxs-lookup"><span data-stu-id="91d28-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="91d28-145">繫結會使用訊息模式安全性，而且用戶端認證類型設為 none。</span><span class="sxs-lookup"><span data-stu-id="91d28-145">The binding uses message mode security, and the client credential type is set to none.</span></span>

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a><span data-ttu-id="91d28-146">組態</span><span class="sxs-lookup"><span data-stu-id="91d28-146">Configuration</span></span>

<span data-ttu-id="91d28-147">下列程式碼會設定用戶端。</span><span class="sxs-lookup"><span data-stu-id="91d28-147">The following code configures the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://machineName/Calculator"
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_ICalculator"
        contract="ICalculator"
        name="WSHttpBinding_ICalculator">
        <identity>
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="91d28-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91d28-148">See also</span></span>

- [<span data-ttu-id="91d28-149">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="91d28-149">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="91d28-150">分散式應用程式安全性</span><span class="sxs-lookup"><span data-stu-id="91d28-150">Distributed Application Security</span></span>](distributed-application-security.md)
- [<span data-ttu-id="91d28-151">訊息安全性匿名</span><span class="sxs-lookup"><span data-stu-id="91d28-151">Message Security Anonymous</span></span>](../samples/message-security-anonymous.md)
- [<span data-ttu-id="91d28-152">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="91d28-152">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- <span data-ttu-id="91d28-153">[Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="91d28-153">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
