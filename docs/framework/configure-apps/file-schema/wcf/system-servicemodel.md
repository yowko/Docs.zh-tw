---
title: <system.serviceModel>
description: 瞭解可讓您設定 WCF 服務和用戶端應用程式的 WCF System.servicemodel configuration 元素。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 567cbd2cc07ee82e795daa067b9034b2b8dc1974
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85243954"
---
# \<system.serviceModel>
<span data-ttu-id="57cb6-103">此設定區段包含所有的 Windows Communication Foundation （WCF） System.servicemodel configuration 元素。</span><span class="sxs-lookup"><span data-stu-id="57cb6-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="57cb6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="57cb6-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57cb6-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="57cb6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="57cb6-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="57cb6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57cb6-107">屬性</span><span class="sxs-lookup"><span data-stu-id="57cb6-107">Attributes</span></span>  
 <span data-ttu-id="57cb6-108">None</span><span class="sxs-lookup"><span data-stu-id="57cb6-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57cb6-109">子元素</span><span class="sxs-lookup"><span data-stu-id="57cb6-109">Child Elements</span></span>  
  
|<span data-ttu-id="57cb6-110">元素</span><span class="sxs-lookup"><span data-stu-id="57cb6-110">Element</span></span>|<span data-ttu-id="57cb6-111">描述</span><span class="sxs-lookup"><span data-stu-id="57cb6-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors.md)|<span data-ttu-id="57cb6-112">這個區段會定義兩個名稱為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="57cb6-112">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="57cb6-113">每個集合會定義分別由端點和服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="57cb6-113">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="57cb6-114">每個行為項目都由其唯一的 `name` 屬性所識別。</span><span class="sxs-lookup"><span data-stu-id="57cb6-114">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[\<bindings>](bindings.md)|<span data-ttu-id="57cb6-115">這個區段保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="57cb6-115">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="57cb6-116">每一個項目都是由它的唯一 `name` 所識別。</span><span class="sxs-lookup"><span data-stu-id="57cb6-116">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="57cb6-117">服務會使用 `name` 來連結繫結，以便利用繫結。</span><span class="sxs-lookup"><span data-stu-id="57cb6-117">Services use bindings by linking them using the `name`.</span></span>|  
|[\<client>](client.md)|<span data-ttu-id="57cb6-118">這個區段包含用戶端用於連接服務之端點的清單。</span><span class="sxs-lookup"><span data-stu-id="57cb6-118">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[\<comContracts>](comcontracts.md)|<span data-ttu-id="57cb6-119">這個區段會定義為 WCF 與 COM interop 啟用的 COM 合約。</span><span class="sxs-lookup"><span data-stu-id="57cb6-119">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[\<commonBehaviors>](commonbehaviors.md)|<span data-ttu-id="57cb6-120">這個區段只能定義在 machine.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="57cb6-120">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="57cb6-121">它會定義兩個名為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="57cb6-121">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="57cb6-122">每個集合會分別定義機器上所有 WCF 端點和服務所使用的行為專案。</span><span class="sxs-lookup"><span data-stu-id="57cb6-122">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="57cb6-123">如果 `<commonBehaviors>` 和 `<behaviors>` 區段中都有定義某個行為，則會優先使用 \<behaviors> 區段中的行為。</span><span class="sxs-lookup"><span data-stu-id="57cb6-123">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="57cb6-124">這個區段包含 WCF 之診斷功能的設定。</span><span class="sxs-lookup"><span data-stu-id="57cb6-124">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="57cb6-125">使用者可以啟用/停用追蹤、效能計數器和 WMI 提供者，並且可以新增自訂訊息篩選條件。</span><span class="sxs-lookup"><span data-stu-id="57cb6-125">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[\<extensions>](extensions-section.md)|<span data-ttu-id="57cb6-126">這個區段包含延伸的集合，可讓使用者建立使用者定義的繫結程序、行為和其他方面的延伸。</span><span class="sxs-lookup"><span data-stu-id="57cb6-126">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="57cb6-127">這個區段會定義傳輸通訊協定配置 (例如 http、net.tcp、net.pipe 等) 和 WCF 繫結之間的一組預設通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="57cb6-127">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[\<routing>](routing.md)|<span data-ttu-id="57cb6-128">這個區段會定義一組路由篩選準則，決定在評估傳入訊息時所使用的 Windows Communication Foundation （WCF）類型 <xref:System.ServiceModel.Dispatcher.MessageFilter> ，以及定義當篩選準則相符時，要傳送訊息的目標端點的路由表。</span><span class="sxs-lookup"><span data-stu-id="57cb6-128">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="57cb6-129">這個區段會定義服務裝載環境為特定傳輸具現化的型別。</span><span class="sxs-lookup"><span data-stu-id="57cb6-129">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="57cb6-130">如果這個區段是空白的，便會使用預設的型別。</span><span class="sxs-lookup"><span data-stu-id="57cb6-130">If this section is empty, the default type is used.</span></span>|  
|[\<services>](services.md)|<span data-ttu-id="57cb6-131">這個區段包含服務的集合。</span><span class="sxs-lookup"><span data-stu-id="57cb6-131">The section contains a collection of services.</span></span> <span data-ttu-id="57cb6-132">對於在組件中定義的各個服務，此項目包含指定服務設定的 `service` 項目。</span><span class="sxs-lookup"><span data-stu-id="57cb6-132">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="57cb6-133">這個區段會定義標準端點的集合，這些端點是可重複使用的預先設定端點。</span><span class="sxs-lookup"><span data-stu-id="57cb6-133">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="57cb6-134">標準端點會有一個或多個位址、繫結，以及設為固定值的合約屬性。</span><span class="sxs-lookup"><span data-stu-id="57cb6-134">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="57cb6-135">例如，探索端點中的合約是固定的。</span><span class="sxs-lookup"><span data-stu-id="57cb6-135">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="57cb6-136">您也可以使用標準端點，以類似定義自訂繫結的新屬性擴充服務端點。</span><span class="sxs-lookup"><span data-stu-id="57cb6-136">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[\<tracking>](tracking-of-wcf.md)|<span data-ttu-id="57cb6-137">這個區段會定義工作流程服務的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="57cb6-137">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="57cb6-138">父項目</span><span class="sxs-lookup"><span data-stu-id="57cb6-138">Parent Elements</span></span>  
  
|<span data-ttu-id="57cb6-139">元素</span><span class="sxs-lookup"><span data-stu-id="57cb6-139">Element</span></span>|<span data-ttu-id="57cb6-140">描述</span><span class="sxs-lookup"><span data-stu-id="57cb6-140">Description</span></span>|  
|-------------|-----------------|  
|\<configuration>|<span data-ttu-id="57cb6-141">.NET 組態檔中所有組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="57cb6-141">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57cb6-142">備註</span><span class="sxs-lookup"><span data-stu-id="57cb6-142">Remarks</span></span>  
 <span data-ttu-id="57cb6-143">WCF 不會將元素新增至其他產品的設定區段。</span><span class="sxs-lookup"><span data-stu-id="57cb6-143">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="57cb6-144">WCF 服務是在 `services` 設定檔的區段中定義。</span><span class="sxs-lookup"><span data-stu-id="57cb6-144">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="57cb6-145">組件可包含任何數目的服務。</span><span class="sxs-lookup"><span data-stu-id="57cb6-145">An assembly can contain any number of services.</span></span> <span data-ttu-id="57cb6-146">各服務都有自己的 `service` 組態區段。</span><span class="sxs-lookup"><span data-stu-id="57cb6-146">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="57cb6-147">這個區段及其內容會定義特定服務的服務合約、行為和端點。</span><span class="sxs-lookup"><span data-stu-id="57cb6-147">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="57cb6-148">只有服務的 `name` 屬性才需要用到。</span><span class="sxs-lookup"><span data-stu-id="57cb6-148">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="57cb6-149">根據預設，服務名稱會說明用來實作服務的基礎 CLR 型別，但您可變更 <xref:System.ServiceModel.ServiceContractAttribute> 上的 ConfigurationName 屬性來覆寫 CLR 型別需求。</span><span class="sxs-lookup"><span data-stu-id="57cb6-149">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="57cb6-150">`behaviorConfiguration` 屬性是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="57cb6-150">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="57cb6-151">它會識別服務使用的服務行為。</span><span class="sxs-lookup"><span data-stu-id="57cb6-151">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="57cb6-152">此屬性指定的行為必須連結到相同組態檔範圍中 (如同一支檔案或父檔案) 定義的服務行為。</span><span class="sxs-lookup"><span data-stu-id="57cb6-152">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="57cb6-153">每個服務會公開一個或多個 `endpoint` 項目中定義的端點。</span><span class="sxs-lookup"><span data-stu-id="57cb6-153">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="57cb6-154">每個端點都有自己的位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="57cb6-154">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="57cb6-155">在組態檔中使用的所有繫結都必須定義在檔案的範圍內。</span><span class="sxs-lookup"><span data-stu-id="57cb6-155">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="57cb6-156">繫結會透過 `name` 和 `bindingConfiguration` 屬性的組合連結至端點。</span><span class="sxs-lookup"><span data-stu-id="57cb6-156">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="57cb6-157">`binding` 屬性會定義在哪一個區段定義繫結，</span><span class="sxs-lookup"><span data-stu-id="57cb6-157">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="57cb6-158">`bindingConfiguration` 屬性則會定義使用繫節區段中哪一個已設定的繫結。</span><span class="sxs-lookup"><span data-stu-id="57cb6-158">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="57cb6-159">繫結區段可定義數個已設定的繫結。</span><span class="sxs-lookup"><span data-stu-id="57cb6-159">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57cb6-160">範例</span><span class="sxs-lookup"><span data-stu-id="57cb6-160">Example</span></span>  
 <span data-ttu-id="57cb6-161">下列是 WCF 組態檔的範例。</span><span class="sxs-lookup"><span data-stu-id="57cb6-161">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57cb6-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57cb6-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
