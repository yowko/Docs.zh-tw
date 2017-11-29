---
title: '&lt;system.serviceModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 563825a92dbdeb90cd17d107795525686b7b4080
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemservicemodelgt"></a><span data-ttu-id="acf62-102">&lt;system.serviceModel&gt;</span><span class="sxs-lookup"><span data-stu-id="acf62-102">&lt;system.serviceModel&gt;</span></span>
<span data-ttu-id="acf62-103">此組態區段包含所有 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel 組態項目。</span><span class="sxs-lookup"><span data-stu-id="acf62-103">This configuration section contains all the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf62-104">語法</span><span class="sxs-lookup"><span data-stu-id="acf62-104">Syntax</span></span>  
  
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
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="acf62-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="acf62-105">Attributes and Elements</span></span>  
 <span data-ttu-id="acf62-106">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="acf62-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="acf62-107">屬性</span><span class="sxs-lookup"><span data-stu-id="acf62-107">Attributes</span></span>  
 <span data-ttu-id="acf62-108">無</span><span class="sxs-lookup"><span data-stu-id="acf62-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="acf62-109">子元素</span><span class="sxs-lookup"><span data-stu-id="acf62-109">Child Elements</span></span>  
  
|<span data-ttu-id="acf62-110">項目</span><span class="sxs-lookup"><span data-stu-id="acf62-110">Element</span></span>|<span data-ttu-id="acf62-111">說明</span><span class="sxs-lookup"><span data-stu-id="acf62-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="acf62-112">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="acf62-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|<span data-ttu-id="acf62-113">這個區段會定義兩個名稱為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="acf62-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="acf62-114">每個集合會定義分別由端點和服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="acf62-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="acf62-115">每個行為項目都由其唯一的 `name` 屬性所識別。</span><span class="sxs-lookup"><span data-stu-id="acf62-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="acf62-116">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="acf62-116">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="acf62-117">這個區段保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="acf62-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="acf62-118">每一個項目都是由它的唯一 `name` 所識別。</span><span class="sxs-lookup"><span data-stu-id="acf62-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="acf62-119">服務會使用 `name` 來連結繫結，以便利用繫結。</span><span class="sxs-lookup"><span data-stu-id="acf62-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="acf62-120">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="acf62-120">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="acf62-121">這個區段包含用戶端用於連接服務之端點的清單。</span><span class="sxs-lookup"><span data-stu-id="acf62-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="acf62-122">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="acf62-122">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|<span data-ttu-id="acf62-123">這個區段會定義為 WCF 與 COM interop 啟用的 COM 合約。</span><span class="sxs-lookup"><span data-stu-id="acf62-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="acf62-124">\<commonBehaviors ></span><span class="sxs-lookup"><span data-stu-id="acf62-124">\<commonBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|<span data-ttu-id="acf62-125">這個區段只能定義在 machine.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="acf62-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="acf62-126">它會定義兩個名為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="acf62-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="acf62-127">每個集合會分別定義由所有 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 端點和電腦上服務所使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="acf62-127">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="acf62-128">如果在定義某個行為`<commonBehaviors>`和`<behaviors>`區段中的行為\<行為 > 一節會給予喜好設定。</span><span class="sxs-lookup"><span data-stu-id="acf62-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="acf62-129">\<擴充功能 ></span><span class="sxs-lookup"><span data-stu-id="acf62-129">\<extensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|<span data-ttu-id="acf62-130">這個區段包含延伸的集合，可讓使用者建立使用者定義的繫結、行為和其他方面的延伸。</span><span class="sxs-lookup"><span data-stu-id="acf62-130">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="acf62-131">\<診斷 ></span><span class="sxs-lookup"><span data-stu-id="acf62-131">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="acf62-132">這個區段包含 WCF 之診斷功能的設定。</span><span class="sxs-lookup"><span data-stu-id="acf62-132">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="acf62-133">使用者可以啟用/停用追蹤、效能計數器和 WMI 提供者，並且可以新增自訂訊息篩選條件。</span><span class="sxs-lookup"><span data-stu-id="acf62-133">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="acf62-134">\<p ></span><span class="sxs-lookup"><span data-stu-id="acf62-134">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="acf62-135">這個區段會定義一組預設傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 和 WCF 繫結之間的通訊協定對應。</span><span class="sxs-lookup"><span data-stu-id="acf62-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="acf62-136">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="acf62-136">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="acf62-137">這個區段會定義一組路由篩選條件，這些篩選條件會判斷傳入訊息時所用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別及路由表 (定義當篩選條件相符時的傳送訊息的目標端點)。</span><span class="sxs-lookup"><span data-stu-id="acf62-137">This section defines a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="acf62-138">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="acf62-138">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="acf62-139">這個區段會定義服務裝載環境為特定傳輸具現化的型別。</span><span class="sxs-lookup"><span data-stu-id="acf62-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="acf62-140">如果這個區段是空白的，便會使用預設的型別。</span><span class="sxs-lookup"><span data-stu-id="acf62-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="acf62-141">\<服務 ></span><span class="sxs-lookup"><span data-stu-id="acf62-141">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="acf62-142">這個區段包含服務的集合。</span><span class="sxs-lookup"><span data-stu-id="acf62-142">The section contains a collection of services.</span></span> <span data-ttu-id="acf62-143">對於在組件中定義的各個服務，此項目包含指定服務設定的 `service` 項目。</span><span class="sxs-lookup"><span data-stu-id="acf62-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="acf62-144">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="acf62-144">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="acf62-145">這個區段會定義標準端點的集合，這些端點是可重複使用的預先設定端點。</span><span class="sxs-lookup"><span data-stu-id="acf62-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="acf62-146">標準端點會有一個或多個位址、繫結，以及設為固定值的合約屬性。</span><span class="sxs-lookup"><span data-stu-id="acf62-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="acf62-147">例如，探索端點中的合約是固定的。</span><span class="sxs-lookup"><span data-stu-id="acf62-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="acf62-148">您也可以使用標準端點，以類似定義自訂繫結的新屬性擴充服務端點。</span><span class="sxs-lookup"><span data-stu-id="acf62-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="acf62-149">父項目</span><span class="sxs-lookup"><span data-stu-id="acf62-149">Parent Elements</span></span>  
  
|<span data-ttu-id="acf62-150">項目</span><span class="sxs-lookup"><span data-stu-id="acf62-150">Element</span></span>|<span data-ttu-id="acf62-151">說明</span><span class="sxs-lookup"><span data-stu-id="acf62-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="acf62-152">\<configuration></span><span class="sxs-lookup"><span data-stu-id="acf62-152">\<configuration></span></span>|<span data-ttu-id="acf62-153">.NET 組態檔中所有組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="acf62-153">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acf62-154">備註</span><span class="sxs-lookup"><span data-stu-id="acf62-154">Remarks</span></span>  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="acf62-155"> 不會在其他產品的組態區段中新增項目。</span><span class="sxs-lookup"><span data-stu-id="acf62-155"> does not add elements to the configuration sections of other products.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="acf62-156">服務是在組態檔的 `services` 區段中定義。</span><span class="sxs-lookup"><span data-stu-id="acf62-156"> services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="acf62-157">組件可包含任何數目的服務。</span><span class="sxs-lookup"><span data-stu-id="acf62-157">An assembly can contain any number of services.</span></span> <span data-ttu-id="acf62-158">各服務都有自己的 `service` 組態區段。</span><span class="sxs-lookup"><span data-stu-id="acf62-158">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="acf62-159">這個區段及其內容會定義特定服務的服務合約、行為和端點。</span><span class="sxs-lookup"><span data-stu-id="acf62-159">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="acf62-160">只有服務的 `name` 屬性才需要用到。</span><span class="sxs-lookup"><span data-stu-id="acf62-160">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="acf62-161">根據預設，服務名稱會說明用來實作服務的基礎 CLR 型別，但您可變更 <xref:System.ServiceModel.ServiceContractAttribute> 上的 ConfigurationName 屬性來覆寫 CLR 型別需求。</span><span class="sxs-lookup"><span data-stu-id="acf62-161">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="acf62-162">`behaviorConfiguration` 屬性是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="acf62-162">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="acf62-163">它會識別服務使用的服務行為。</span><span class="sxs-lookup"><span data-stu-id="acf62-163">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="acf62-164">此屬性指定的行為必須連結到相同組態檔範圍中 (如同一支檔案或父檔案) 定義的服務行為。</span><span class="sxs-lookup"><span data-stu-id="acf62-164">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="acf62-165">每個服務會公開一個或多個 `endpoint` 項目中定義的端點。</span><span class="sxs-lookup"><span data-stu-id="acf62-165">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="acf62-166">每個端點都有自己的位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="acf62-166">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="acf62-167">在組態檔中使用的所有繫結都必須定義在檔案的範圍內。</span><span class="sxs-lookup"><span data-stu-id="acf62-167">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="acf62-168">繫結會透過 `name` 和 `bindingConfiguration` 屬性的組合連結至端點。</span><span class="sxs-lookup"><span data-stu-id="acf62-168">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="acf62-169">`binding` 屬性會定義在哪一個區段定義繫結，</span><span class="sxs-lookup"><span data-stu-id="acf62-169">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="acf62-170">`bindingConfiguration` 屬性則會定義使用繫節區段中哪一個已設定的繫結。</span><span class="sxs-lookup"><span data-stu-id="acf62-170">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="acf62-171">繫結區段可定義數個已設定的繫結。</span><span class="sxs-lookup"><span data-stu-id="acf62-171">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acf62-172">範例</span><span class="sxs-lookup"><span data-stu-id="acf62-172">Example</span></span>  
 <span data-ttu-id="acf62-173">下列是 WCF 組態檔的範例。</span><span class="sxs-lookup"><span data-stu-id="acf62-173">This is an example of a WCF configuration file.</span></span>  
  
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
        <diagnostics wmiProviderEnabled="false" performanceCountersEnabled="false" tracingEnabled="false">  
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
  
## <a name="see-also"></a><span data-ttu-id="acf62-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acf62-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
