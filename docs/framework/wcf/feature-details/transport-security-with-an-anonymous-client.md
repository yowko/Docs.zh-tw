---
title: 使用匿名用戶端的傳輸安全性
description: 請參閱此 WCF 案例，此案例會使用傳輸安全性，利用用戶端所信任的憑證來驗證服務器。 用戶端未通過驗證。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 5e8bcab4cdd8f27e9ea27e66fe4c848ccd35e99c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556807"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="27896-104">使用匿名用戶端的傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="27896-104">Transport security with an anonymous client</span></span>

<span data-ttu-id="27896-105">這 Windows Communication Foundation (WCF) 案例會使用傳輸安全性 (HTTPS) ，以確保機密性和完整性。</span><span class="sxs-lookup"><span data-stu-id="27896-105">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="27896-106">伺服器必須使用安全通訊端層 (SSL) 憑證進行驗證，而且用戶端必須信任該伺服器的憑證。</span><span class="sxs-lookup"><span data-stu-id="27896-106">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="27896-107">此用戶端不會透過任何機制進行驗證，因此屬於匿名。</span><span class="sxs-lookup"><span data-stu-id="27896-107">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>

<span data-ttu-id="27896-108">如需範例應用程式，請參閱 [WS 傳輸安全性](../samples/ws-transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="27896-108">For a sample application, see [WS Transport Security](../samples/ws-transport-security.md).</span></span> <span data-ttu-id="27896-109">如需傳輸安全性的詳細資訊，請參閱 [傳輸安全性概觀](transport-security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="27896-109">For more information about transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>

<span data-ttu-id="27896-110">如需有關使用憑證搭配服務的詳細資訊，請參閱使用 [憑證](working-with-certificates.md) 和 [如何：使用 SSL 憑證設定埠](how-to-configure-a-port-with-an-ssl-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="27896-110">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

![搭配匿名用戶端使用傳輸安全性](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|<span data-ttu-id="27896-112">特性</span><span class="sxs-lookup"><span data-stu-id="27896-112">Characteristic</span></span>|<span data-ttu-id="27896-113">描述</span><span class="sxs-lookup"><span data-stu-id="27896-113">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="27896-114">安全性模式</span><span class="sxs-lookup"><span data-stu-id="27896-114">Security Mode</span></span>|<span data-ttu-id="27896-115">傳輸</span><span class="sxs-lookup"><span data-stu-id="27896-115">Transport</span></span>|
|<span data-ttu-id="27896-116">互通性</span><span class="sxs-lookup"><span data-stu-id="27896-116">Interoperability</span></span>|<span data-ttu-id="27896-117">與現有的 Web 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="27896-117">With existing Web services and clients</span></span>|
|<span data-ttu-id="27896-118">驗證 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="27896-118">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="27896-119">驗證 (用戶端)</span><span class="sxs-lookup"><span data-stu-id="27896-119">Authentication (Client)</span></span>|<span data-ttu-id="27896-120">是</span><span class="sxs-lookup"><span data-stu-id="27896-120">Yes</span></span><br /><br /> <span data-ttu-id="27896-121">應用層級 (沒有 WCF 支援) </span><span class="sxs-lookup"><span data-stu-id="27896-121">Application level (no WCF support)</span></span>|
|<span data-ttu-id="27896-122">完整性</span><span class="sxs-lookup"><span data-stu-id="27896-122">Integrity</span></span>|<span data-ttu-id="27896-123">是</span><span class="sxs-lookup"><span data-stu-id="27896-123">Yes</span></span>|
|<span data-ttu-id="27896-124">機密性</span><span class="sxs-lookup"><span data-stu-id="27896-124">Confidentiality</span></span>|<span data-ttu-id="27896-125">是</span><span class="sxs-lookup"><span data-stu-id="27896-125">Yes</span></span>|
|<span data-ttu-id="27896-126">傳輸</span><span class="sxs-lookup"><span data-stu-id="27896-126">Transport</span></span>|<span data-ttu-id="27896-127">HTTPS</span><span class="sxs-lookup"><span data-stu-id="27896-127">HTTPS</span></span>|
|<span data-ttu-id="27896-128">繫結</span><span class="sxs-lookup"><span data-stu-id="27896-128">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="27896-129">服務</span><span class="sxs-lookup"><span data-stu-id="27896-129">Service</span></span>

<span data-ttu-id="27896-130">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="27896-130">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="27896-131">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="27896-131">Do one of the following:</span></span>

- <span data-ttu-id="27896-132">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="27896-132">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="27896-133">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="27896-133">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="27896-134">程式碼</span><span class="sxs-lookup"><span data-stu-id="27896-134">Code</span></span>

<span data-ttu-id="27896-135">下列程式碼會示範如何建立會使用傳輸安全性的端點：</span><span class="sxs-lookup"><span data-stu-id="27896-135">The following code shows how to create an endpoint using transport security:</span></span>

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a><span data-ttu-id="27896-136">組態</span><span class="sxs-lookup"><span data-stu-id="27896-136">Configuration</span></span>

<span data-ttu-id="27896-137">下列程式碼會使用組態設定相同端點。</span><span class="sxs-lookup"><span data-stu-id="27896-137">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="27896-138">此用戶端不會透過任何機制進行驗證，因此屬於匿名。</span><span class="sxs-lookup"><span data-stu-id="27896-138">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="ServiceModel.Calculator">
        <endpoint address="https://localhost/Calculator"
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

## <a name="client"></a><span data-ttu-id="27896-139">用戶端</span><span class="sxs-lookup"><span data-stu-id="27896-139">Client</span></span>

<span data-ttu-id="27896-140">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="27896-140">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="27896-141">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="27896-141">Do one of the following:</span></span>

- <span data-ttu-id="27896-142">使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。</span><span class="sxs-lookup"><span data-stu-id="27896-142">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="27896-143">建立未定義任何端點位址的用戶端，</span><span class="sxs-lookup"><span data-stu-id="27896-143">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="27896-144">然後改用可接受組態名稱當做引數的用戶端建構函式。</span><span class="sxs-lookup"><span data-stu-id="27896-144">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="27896-145">例如：</span><span class="sxs-lookup"><span data-stu-id="27896-145">For example:</span></span>

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="27896-146">程式碼</span><span class="sxs-lookup"><span data-stu-id="27896-146">Code</span></span>

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a><span data-ttu-id="27896-147">組態</span><span class="sxs-lookup"><span data-stu-id="27896-147">Configuration</span></span>

<span data-ttu-id="27896-148">可以使用下列組態來取代程式碼，進行設定服務。</span><span class="sxs-lookup"><span data-stu-id="27896-148">The following configuration can be used instead of the code to set up the service.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="27896-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27896-149">See also</span></span>

- [<span data-ttu-id="27896-150">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="27896-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="27896-151">WS 傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="27896-151">WS Transport Security</span></span>](../samples/ws-transport-security.md)
- [<span data-ttu-id="27896-152">傳輸安全性概觀</span><span class="sxs-lookup"><span data-stu-id="27896-152">Transport Security Overview</span></span>](transport-security-overview.md)
- <span data-ttu-id="27896-153">[Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="27896-153">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
