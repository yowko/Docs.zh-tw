---
title: 設定 Windows Communication Foundation 服務的繫結
description: 瞭解如何藉由編輯系統下的專案，在部署階段為 WCF 應用程式設定系結。System.servicemodel 元素。
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 60ab04764851ef82a43d5c2050d3bac7b56ce551
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266723"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="2f866-103">設定 Windows Communication Foundation 服務的繫結</span><span class="sxs-lookup"><span data-stu-id="2f866-103">Configuring Bindings for Windows Communication Foundation Services</span></span>

<span data-ttu-id="2f866-104">建立應用程式時，您經常會需要在應用程式部署後，延後系統管理員的決定。</span><span class="sxs-lookup"><span data-stu-id="2f866-104">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="2f866-105">例如，我們很多時都無法預知服務位址，或統一資源識別元 (URI)。</span><span class="sxs-lookup"><span data-stu-id="2f866-105">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="2f866-106">這時候，為位址進行硬式編碼並不是理想的作法，較好的作法是讓系統管理員在建立服務後再處理。</span><span class="sxs-lookup"><span data-stu-id="2f866-106">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="2f866-107">這樣的靈活性是透過組態達成。</span><span class="sxs-lookup"><span data-stu-id="2f866-107">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f866-108">使用「配置 [中繼資料公用程式工具」 ( # A0) ](servicemodel-metadata-utility-tool-svcutil-exe.md) 搭配 `/config` 參數來快速建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="2f866-108">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="2f866-109">主要區段</span><span class="sxs-lookup"><span data-stu-id="2f866-109">Major Sections</span></span>  

 <span data-ttu-id="2f866-110">Windows Communication Foundation (WCF) 設定配置包含下列三個主要區段 (`serviceModel` 、 `bindings` 和 `services`) ：</span><span class="sxs-lookup"><span data-stu-id="2f866-110">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a><span data-ttu-id="2f866-111">ServiceModel 項目</span><span class="sxs-lookup"><span data-stu-id="2f866-111">ServiceModel Elements</span></span>  

 <span data-ttu-id="2f866-112">您可以使用專案所系結的區段 `system.ServiceModel` ，以一或多個端點來設定服務類型，以及服務的設定。</span><span class="sxs-lookup"><span data-stu-id="2f866-112">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="2f866-113">然後可以使用位址、合約與繫結來設定每個端點。</span><span class="sxs-lookup"><span data-stu-id="2f866-113">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="2f866-114">如需端點的詳細資訊，請參閱 [端點建立總覽](endpoint-creation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="2f866-114">For more information about endpoints, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="2f866-115">如果沒有指定任何端點，則執行階段會加入預設端點。</span><span class="sxs-lookup"><span data-stu-id="2f866-115">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="2f866-116">如需預設端點、繫結和行為的詳細資訊，請參閱[簡化的組態](simplified-configuration.md)和 [WCF 服務的簡化組態](./samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2f866-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="2f866-117">繫結程序指定傳輸 (HTTP、TCP、管道、訊息佇列) 與通訊協定 (安全性、可靠性、異動流) 並且包含繫結程序項目，每個皆指定端點如何與外界通訊。</span><span class="sxs-lookup"><span data-stu-id="2f866-117">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="2f866-118">例如，指定 [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) 元素表示使用 HTTP 做為端點的傳輸。</span><span class="sxs-lookup"><span data-stu-id="2f866-118">For example, specifying the [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="2f866-119">這是在執行階段，當使用此端點的服務開啟時，用來連接端點。</span><span class="sxs-lookup"><span data-stu-id="2f866-119">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="2f866-120">有兩類的繫結：預先定義和自訂。</span><span class="sxs-lookup"><span data-stu-id="2f866-120">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="2f866-121">預先定義的繫結包含有用的項目組合，在一般狀況下使用。</span><span class="sxs-lookup"><span data-stu-id="2f866-121">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="2f866-122">如需 WCF 提供之預先定義系結類型的清單，請參閱 [系統提供](system-provided-bindings.md)的系結。</span><span class="sxs-lookup"><span data-stu-id="2f866-122">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="2f866-123">若無預先定義的繫結程序集合擁有服務應用程式所需的正確功能組合，您可以建構自訂繫結程序來滿足應用程式的要求。</span><span class="sxs-lookup"><span data-stu-id="2f866-123">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="2f866-124">如需自訂系結的詳細資訊，請參閱 [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2f866-124">For more information about custom bindings, see [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="2f866-125">下列四個範例說明用來設定 WCF 服務的最常見系結設定。</span><span class="sxs-lookup"><span data-stu-id="2f866-125">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="2f866-126">指定使用繫結型別的端點</span><span class="sxs-lookup"><span data-stu-id="2f866-126">Specifying an Endpoint to Use a Binding Type</span></span>  

 <span data-ttu-id="2f866-127">第一個範例說明如何指定以位址、合約及繫結組態的端點。</span><span class="sxs-lookup"><span data-stu-id="2f866-127">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!-- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 <span data-ttu-id="2f866-128">在此範例中，`name` 屬性表示組態是針對哪種服務類型。</span><span class="sxs-lookup"><span data-stu-id="2f866-128">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="2f866-129">當您在編碼中以 `HelloWorld` 合約建立服務，它將以範例組態定義的所有端點進行初始化。</span><span class="sxs-lookup"><span data-stu-id="2f866-129">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="2f866-130">如果元件只實作為一個服務合約， `name` 就可以省略屬性，因為服務會使用唯一可用的型別。</span><span class="sxs-lookup"><span data-stu-id="2f866-130">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="2f866-131">該屬性取用一個字串，格式必須為 `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="2f866-131">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="2f866-132">`address` 屬性指定其他端點用來和服務通訊的 URI。</span><span class="sxs-lookup"><span data-stu-id="2f866-132">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="2f866-133">URI 可能是絕對或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="2f866-133">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="2f866-134">如果提供相對位址，主機必須為繫結中使用的傳輸配置提供適當的基底位址。</span><span class="sxs-lookup"><span data-stu-id="2f866-134">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="2f866-135">如果沒有設定位址，會將基底位址假設為該端點的位址。</span><span class="sxs-lookup"><span data-stu-id="2f866-135">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="2f866-136">`contract` 屬性指定此端點所公開的合約。</span><span class="sxs-lookup"><span data-stu-id="2f866-136">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="2f866-137">服務實作型別必須實作合約類型。</span><span class="sxs-lookup"><span data-stu-id="2f866-137">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="2f866-138">如果服務實作實作單一合約類型，便可省略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="2f866-138">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="2f866-139">`binding` 屬性選擇此特定端點使用之預先定義或自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="2f866-139">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="2f866-140">未明確選擇繫結的端點會使用預設的繫結選擇，也就是 `BasicHttpBinding`。</span><span class="sxs-lookup"><span data-stu-id="2f866-140">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="2f866-141">修改預先定義繫結</span><span class="sxs-lookup"><span data-stu-id="2f866-141">Modifying a Predefined Binding</span></span>  

 <span data-ttu-id="2f866-142">下列範例會修改預先定義的繫結，</span><span class="sxs-lookup"><span data-stu-id="2f866-142">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="2f866-143">然後可用作設定服務中的所有端點。</span><span class="sxs-lookup"><span data-stu-id="2f866-143">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="2f866-144">設定 <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> 值為 1 秒以修改繫結。</span><span class="sxs-lookup"><span data-stu-id="2f866-144">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="2f866-145">請注意，屬性傳回 <xref:System.TimeSpan> 物件。</span><span class="sxs-lookup"><span data-stu-id="2f866-145">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="2f866-146">更動後的繫結會在繫結區段內。</span><span class="sxs-lookup"><span data-stu-id="2f866-146">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="2f866-147">如今當您設定 `binding` 項目的 `endpoint` 屬性建立任何端點時，都可以使用此已更動的繫結。</span><span class="sxs-lookup"><span data-stu-id="2f866-147">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f866-148">如果您賦予此繫結一個特定名稱，則服務端點所指定的 `bindingConfiguration` 必須與其相一致。</span><span class="sxs-lookup"><span data-stu-id="2f866-148">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="2f866-149">設定行為以套用至服務</span><span class="sxs-lookup"><span data-stu-id="2f866-149">Configuring a Behavior to Apply to a Service</span></span>  

 <span data-ttu-id="2f866-150">下列範例會針對服務類型來設定特定行為。</span><span class="sxs-lookup"><span data-stu-id="2f866-150">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="2f866-151">`ServiceMetadataBehavior`元素可用來啟用 [ [System.servicemodel 中繼資料公用程式] 工具 ( # A0) ](servicemodel-metadata-utility-tool-svcutil-exe.md)來查詢服務，並從中繼資料產生 Web 服務描述語言 (WSDL) 檔。</span><span class="sxs-lookup"><span data-stu-id="2f866-151">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f866-152">如果您賦予此行為一個特定名稱，則服務或端點區段內所指定的 `behaviorConfiguration` 必須與其相一致。</span><span class="sxs-lookup"><span data-stu-id="2f866-152">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />
    </behavior>  
</behaviors>  
<services>  
    <service
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 <span data-ttu-id="2f866-153">前述組態讓用戶端得以呼叫 "HelloWorld" 類型的服務並取得中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2f866-153">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="2f866-154">指定具有使用不同繫結值之兩端點的服務</span><span class="sxs-lookup"><span data-stu-id="2f866-154">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  

 <span data-ttu-id="2f866-155">在此最後的範例，兩個端點設定為 `HelloWorld` 服務類型。</span><span class="sxs-lookup"><span data-stu-id="2f866-155">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="2f866-156">每個端點都會使用相同系結類型的不同自訂  `bindingConfiguration` 屬性 (每個端點都會修改 `basicHttpBinding`) 。</span><span class="sxs-lookup"><span data-stu-id="2f866-156">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding
        name="shortTimeout"  
        timeout="00:00:00:01"
     />  
     <basicHttpBinding
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="2f866-157">您可以使用預設組態再加入 `protocolMapping` 區段並設定繫結，而得到同樣的行為，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2f866-157">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding
        name="shortTimeout"  
        timeout="00:00:00:01"
     />  
     <basicHttpBinding
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f866-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f866-158">See also</span></span>

- [<span data-ttu-id="2f866-159">簡化的組態</span><span class="sxs-lookup"><span data-stu-id="2f866-159">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="2f866-160">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="2f866-160">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="2f866-161">端點建立概觀</span><span class="sxs-lookup"><span data-stu-id="2f866-161">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)
- [<span data-ttu-id="2f866-162">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="2f866-162">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
