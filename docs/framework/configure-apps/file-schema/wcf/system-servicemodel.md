---
title: <system.serviceModel>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 2125ce00b0e23f2e93ff251549f9c1276892b16b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399447"
---
# <a name="systemservicemodel"></a><span data-ttu-id="c1f53-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c1f53-102">\<system.serviceModel></span></span>
<span data-ttu-id="c1f53-103">此設定區段包含所有的 Windows Communication Foundation （WCF） System.servicemodel configuration 元素。</span><span class="sxs-lookup"><span data-stu-id="c1f53-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

<span data-ttu-id="c1f53-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1f53-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c1f53-105">&nbsp;&nbsp; **\<System.servicemodel >**</span><span class="sxs-lookup"><span data-stu-id="c1f53-105">&nbsp;&nbsp;**\<system.serviceModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f53-106">語法</span><span class="sxs-lookup"><span data-stu-id="c1f53-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
  </behaviors>
  <bindings>
  </bindings>
  <client>
  </client>
  <comContracts>
  </comContracts>
  <commonBehaviors>
  </commonBehaviors>
  <diagnostics>
  </diagnostics>
  <extensions>
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>
  <serviceHostingEnvironment>
  </serviceHostingEnvironment>
  <services>
  </services>
  <standardEndpoints>
  </standardEndpoints>
  <tracking>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1f53-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c1f53-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c1f53-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c1f53-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1f53-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c1f53-109">Attributes</span></span>  
 <span data-ttu-id="c1f53-110">無</span><span class="sxs-lookup"><span data-stu-id="c1f53-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c1f53-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c1f53-111">Child Elements</span></span>  
  
|<span data-ttu-id="c1f53-112">項目</span><span class="sxs-lookup"><span data-stu-id="c1f53-112">Element</span></span>|<span data-ttu-id="c1f53-113">描述</span><span class="sxs-lookup"><span data-stu-id="c1f53-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1f53-114">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="c1f53-114">\<behaviors></span></span>](behaviors.md)|<span data-ttu-id="c1f53-115">這個區段會定義兩個名稱為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="c1f53-115">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="c1f53-116">每個集合會定義分別由端點和服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="c1f53-116">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="c1f53-117">每個行為項目都由其唯一的 `name` 屬性所識別。</span><span class="sxs-lookup"><span data-stu-id="c1f53-117">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="c1f53-118">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c1f53-118">\<bindings></span></span>](bindings.md)|<span data-ttu-id="c1f53-119">這個區段保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="c1f53-119">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="c1f53-120">每一個項目都是由它的唯一 `name` 所識別。</span><span class="sxs-lookup"><span data-stu-id="c1f53-120">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="c1f53-121">服務會使用 `name` 來連結繫結，以便利用繫結。</span><span class="sxs-lookup"><span data-stu-id="c1f53-121">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="c1f53-122">\<client></span><span class="sxs-lookup"><span data-stu-id="c1f53-122">\<client></span></span>](client.md)|<span data-ttu-id="c1f53-123">這個區段包含用戶端用於連接服務之端點的清單。</span><span class="sxs-lookup"><span data-stu-id="c1f53-123">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="c1f53-124">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="c1f53-124">\<comContracts></span></span>](comcontracts.md)|<span data-ttu-id="c1f53-125">這個區段會定義為 WCF 與 COM interop 啟用的 COM 合約。</span><span class="sxs-lookup"><span data-stu-id="c1f53-125">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="c1f53-126">\<commonBehaviors></span><span class="sxs-lookup"><span data-stu-id="c1f53-126">\<commonBehaviors></span></span>](commonbehaviors.md)|<span data-ttu-id="c1f53-127">這個區段只能定義在 machine.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="c1f53-127">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="c1f53-128">它會定義兩個名為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="c1f53-128">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="c1f53-129">每個集合會分別定義機器上所有 WCF 端點和服務所使用的行為專案。</span><span class="sxs-lookup"><span data-stu-id="c1f53-129">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="c1f53-130">如果在`<commonBehaviors>`和`<behaviors>`區段中都定義了行為，則 [ \<行為 >] 區段中的行為會獲得喜好設定。</span><span class="sxs-lookup"><span data-stu-id="c1f53-130">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="c1f53-131">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="c1f53-131">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="c1f53-132">這個區段包含 WCF 之診斷功能的設定。</span><span class="sxs-lookup"><span data-stu-id="c1f53-132">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="c1f53-133">使用者可以啟用/停用追蹤、效能計數器和 WMI 提供者，並且可以新增自訂訊息篩選條件。</span><span class="sxs-lookup"><span data-stu-id="c1f53-133">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="c1f53-134">\<延伸模組 ></span><span class="sxs-lookup"><span data-stu-id="c1f53-134">\<extensions></span></span>](extensions-section.md)|<span data-ttu-id="c1f53-135">這個區段包含延伸的集合，可讓使用者建立使用者定義的繫結程序、行為和其他方面的延伸。</span><span class="sxs-lookup"><span data-stu-id="c1f53-135">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="c1f53-136">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="c1f53-136">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="c1f53-137">這個區段會定義傳輸通訊協定配置（例如 HTTP、net.tcp、net.pipe 等）和 WCF 系結之間的一組預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="c1f53-137">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="c1f53-138">\<routing></span><span class="sxs-lookup"><span data-stu-id="c1f53-138">\<routing></span></span>](routing.md)|<span data-ttu-id="c1f53-139">這個區段會定義一組路由篩選準則，以決定在評估傳入訊息時所<xref:System.ServiceModel.Dispatcher.MessageFilter>使用的 Windows Communication Foundation （WCF）類型，以及定義在下列情況下要傳送訊息的目標端點的路由表：篩選符合專案。</span><span class="sxs-lookup"><span data-stu-id="c1f53-139">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="c1f53-140">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="c1f53-140">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="c1f53-141">這個區段會定義服務裝載環境為特定傳輸具現化的型別。</span><span class="sxs-lookup"><span data-stu-id="c1f53-141">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="c1f53-142">如果這個區段是空白的，便會使用預設的型別。</span><span class="sxs-lookup"><span data-stu-id="c1f53-142">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="c1f53-143">\<services></span><span class="sxs-lookup"><span data-stu-id="c1f53-143">\<services></span></span>](services.md)|<span data-ttu-id="c1f53-144">這個區段包含服務的集合。</span><span class="sxs-lookup"><span data-stu-id="c1f53-144">The section contains a collection of services.</span></span> <span data-ttu-id="c1f53-145">對於在組件中定義的各個服務，此項目包含指定服務設定的 `service` 項目。</span><span class="sxs-lookup"><span data-stu-id="c1f53-145">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="c1f53-146">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="c1f53-146">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="c1f53-147">這個區段會定義標準端點的集合，這些端點是可重複使用的預先設定端點。</span><span class="sxs-lookup"><span data-stu-id="c1f53-147">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="c1f53-148">標準端點會有一個或多個位址、繫結，以及設為固定值的合約屬性。</span><span class="sxs-lookup"><span data-stu-id="c1f53-148">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="c1f53-149">例如，探索端點中的合約是固定的。</span><span class="sxs-lookup"><span data-stu-id="c1f53-149">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="c1f53-150">您也可以使用標準端點，以類似定義自訂繫結的新屬性擴充服務端點。</span><span class="sxs-lookup"><span data-stu-id="c1f53-150">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[<span data-ttu-id="c1f53-151">\<tracking></span><span class="sxs-lookup"><span data-stu-id="c1f53-151">\<tracking></span></span>](tracking-of-wcf.md)|<span data-ttu-id="c1f53-152">這個區段會定義工作流程服務的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="c1f53-152">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c1f53-153">父項目</span><span class="sxs-lookup"><span data-stu-id="c1f53-153">Parent Elements</span></span>  
  
|<span data-ttu-id="c1f53-154">項目</span><span class="sxs-lookup"><span data-stu-id="c1f53-154">Element</span></span>|<span data-ttu-id="c1f53-155">描述</span><span class="sxs-lookup"><span data-stu-id="c1f53-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1f53-156">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c1f53-156">\<configuration></span></span>|<span data-ttu-id="c1f53-157">.NET 組態檔中所有組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="c1f53-157">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1f53-158">備註</span><span class="sxs-lookup"><span data-stu-id="c1f53-158">Remarks</span></span>  
 <span data-ttu-id="c1f53-159">WCF 不會將元素新增至其他產品的設定區段。</span><span class="sxs-lookup"><span data-stu-id="c1f53-159">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="c1f53-160">WCF 服務是在設定檔`services`的區段中定義。</span><span class="sxs-lookup"><span data-stu-id="c1f53-160">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="c1f53-161">組件可包含任何數目的服務。</span><span class="sxs-lookup"><span data-stu-id="c1f53-161">An assembly can contain any number of services.</span></span> <span data-ttu-id="c1f53-162">各服務都有自己的 `service` 組態區段。</span><span class="sxs-lookup"><span data-stu-id="c1f53-162">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="c1f53-163">這個區段及其內容會定義特定服務的服務合約、行為和端點。</span><span class="sxs-lookup"><span data-stu-id="c1f53-163">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="c1f53-164">只有服務的 `name` 屬性才需要用到。</span><span class="sxs-lookup"><span data-stu-id="c1f53-164">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="c1f53-165">根據預設，服務名稱會說明用來實作服務的基礎 CLR 型別，但您可變更 <xref:System.ServiceModel.ServiceContractAttribute> 上的 ConfigurationName 屬性來覆寫 CLR 型別需求。</span><span class="sxs-lookup"><span data-stu-id="c1f53-165">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="c1f53-166">`behaviorConfiguration` 屬性是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="c1f53-166">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="c1f53-167">它會識別服務使用的服務行為。</span><span class="sxs-lookup"><span data-stu-id="c1f53-167">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="c1f53-168">此屬性指定的行為必須連結到相同組態檔範圍中 (如同一支檔案或父檔案) 定義的服務行為。</span><span class="sxs-lookup"><span data-stu-id="c1f53-168">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="c1f53-169">每個服務會公開一個或多個 `endpoint` 項目中定義的端點。</span><span class="sxs-lookup"><span data-stu-id="c1f53-169">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="c1f53-170">每個端點都有自己的位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="c1f53-170">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="c1f53-171">在組態檔中使用的所有繫結都必須定義在檔案的範圍內。</span><span class="sxs-lookup"><span data-stu-id="c1f53-171">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="c1f53-172">繫結會透過 `name` 和 `bindingConfiguration` 屬性的組合連結至端點。</span><span class="sxs-lookup"><span data-stu-id="c1f53-172">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="c1f53-173">`binding` 屬性會定義在哪一個區段定義繫結，</span><span class="sxs-lookup"><span data-stu-id="c1f53-173">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="c1f53-174">`bindingConfiguration` 屬性則會定義使用繫節區段中哪一個已設定的繫結。</span><span class="sxs-lookup"><span data-stu-id="c1f53-174">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="c1f53-175">繫結區段可定義數個已設定的繫結。</span><span class="sxs-lookup"><span data-stu-id="c1f53-175">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1f53-176">範例</span><span class="sxs-lookup"><span data-stu-id="c1f53-176">Example</span></span>  
 <span data-ttu-id="c1f53-177">下列是 WCF 組態檔的範例。</span><span class="sxs-lookup"><span data-stu-id="c1f53-177">This is an example of a WCF configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <!-- List of Behaviors -->
    </behaviors>
    <client>
      <!-- List of Endpoints -->
    </client>
    <diagnostics wmiProviderEnabled="false"
                 performanceCountersEnabled="false"
                 tracingEnabled="false">
    </diagnostics>
    <serviceHostingEnvironment>
      <!-- List of entries -->
    </serviceHostingEnvironment>
    <comContracts>
      <!-- List of COM+ Contracts -->
    </comContracts>
    <services>
      <!-- List of Services -->
    </services>
    <bindings>
      <!-- List of Bindings -->
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="c1f53-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1f53-178">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
