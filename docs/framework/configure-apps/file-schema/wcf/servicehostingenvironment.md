---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 165dbed1b78d00f8d4dd3e482b9fee8a23db60da
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399619"
---
# <a name="servicehostingenvironment"></a><span data-ttu-id="e75d3-101">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="e75d3-101">\<serviceHostingEnvironment></span></span>
<span data-ttu-id="e75d3-102">此項目定義服務裝載環境為特定傳輸產生的類型。</span><span class="sxs-lookup"><span data-stu-id="e75d3-102">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="e75d3-103">如果這個項目是空白的，便會使用預設的類型。</span><span class="sxs-lookup"><span data-stu-id="e75d3-103">If this element is empty, the default type is used.</span></span> <span data-ttu-id="e75d3-104">這個項目只能用於應用程式或電腦層級的組態檔。</span><span class="sxs-lookup"><span data-stu-id="e75d3-104">This element can only be used at the application or machine level configuration files.</span></span>  
  
<span data-ttu-id="e75d3-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e75d3-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e75d3-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e75d3-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e75d3-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceHostingEnvironment >**</span><span class="sxs-lookup"><span data-stu-id="e75d3-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceHostingEnvironment>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e75d3-108">語法</span><span class="sxs-lookup"><span data-stu-id="e75d3-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean"
                           minFreeMemoryPercentageToActivateService="Integer"
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e75d3-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e75d3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e75d3-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e75d3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e75d3-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e75d3-111">Attributes</span></span>  
  
|<span data-ttu-id="e75d3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e75d3-112">Attribute</span></span>|<span data-ttu-id="e75d3-113">說明</span><span class="sxs-lookup"><span data-stu-id="e75d3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e75d3-114">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="e75d3-114">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="e75d3-115">布林值，指出是否已為目前的應用程式開啟 ASP.NET 相容性模式。</span><span class="sxs-lookup"><span data-stu-id="e75d3-115">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="e75d3-116">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="e75d3-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e75d3-117">當這個屬性設定為`true`時，對 Windows Communication Foundation （WCF）服務的要求會流經 ASP.NET HTTP 管線，而非 HTTP 通訊協定的通訊則是禁止的。</span><span class="sxs-lookup"><span data-stu-id="e75d3-117">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="e75d3-118">如需詳細資訊，請參閱[WCF 服務和 ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md)。</span><span class="sxs-lookup"><span data-stu-id="e75d3-118">For more information, see [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="e75d3-119">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="e75d3-119">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="e75d3-120">整數，指定可供系統使用的最小可用記憶體數量，然後才能啟動 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="e75d3-120">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="e75d3-121">**注意**：在 WCF 服務的 web.config 檔案中指定這個屬性和部分信任，將會在<xref:System.Security.SecurityException>服務執行時產生。</span><span class="sxs-lookup"><span data-stu-id="e75d3-121">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="e75d3-122">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="e75d3-122">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="e75d3-123">布林值，這個值會指定是否啟用每個網站的多個 IIS 繫結。</span><span class="sxs-lookup"><span data-stu-id="e75d3-123">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="e75d3-124">IIS 包含網站，是包含虛擬目錄之虛擬應用程式的容器。</span><span class="sxs-lookup"><span data-stu-id="e75d3-124">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="e75d3-125">網站中的應用程式則可以透過一個或多個 IIS 繫結來存取。</span><span class="sxs-lookup"><span data-stu-id="e75d3-125">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="e75d3-126">IIS 繫結提供兩項資訊：繫結通訊協定和繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="e75d3-126">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="e75d3-127">繫結通訊協定會定義產生通訊的配置，而繫結資訊則是用來存取網站的資訊。</span><span class="sxs-lookup"><span data-stu-id="e75d3-127">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="e75d3-128">繫結通訊協定的範例如 HTTP，其中繫結資訊可能會包含 IP 位址、連接埠、主機標題等。</span><span class="sxs-lookup"><span data-stu-id="e75d3-128">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="e75d3-129">IIS 支援為每個網站指定多個 IIS 繫結，讓每個配置能夠有多個基底位址。</span><span class="sxs-lookup"><span data-stu-id="e75d3-129">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="e75d3-130">不過，在網站底下裝載的 Windows Communication Foundation （WCF）服務，只允許每個配置系結至一個 baseAddress。</span><span class="sxs-lookup"><span data-stu-id="e75d3-130">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="e75d3-131">若要為 Windows Communication Foundation （WCF）服務啟用每個網站的多個 IIS 系結， `true`請將此屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="e75d3-131">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="e75d3-132">請注意，僅有 HTTP 通訊協定支援多個網站繫結。</span><span class="sxs-lookup"><span data-stu-id="e75d3-132">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="e75d3-133">組態檔中的端點位址必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="e75d3-133">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e75d3-134">子元素</span><span class="sxs-lookup"><span data-stu-id="e75d3-134">Child Elements</span></span>  
  
|<span data-ttu-id="e75d3-135">項目</span><span class="sxs-lookup"><span data-stu-id="e75d3-135">Element</span></span>|<span data-ttu-id="e75d3-136">描述</span><span class="sxs-lookup"><span data-stu-id="e75d3-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e75d3-137">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="e75d3-137">\<baseAddressPrefixFilters></span></span>](baseaddressprefixfilters.md)|<span data-ttu-id="e75d3-138">組態項目的集合，這些項目會指定服務主機使用之基底位址的前置詞篩選條件。</span><span class="sxs-lookup"><span data-stu-id="e75d3-138">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="e75d3-139">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="e75d3-139">\<serviceActivations></span></span>](serviceactivations.md)|<span data-ttu-id="e75d3-140">描述啟動設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="e75d3-140">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="e75d3-141">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="e75d3-141">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="e75d3-142">組態項目的集合，這些項目會識別特定傳輸的類型。</span><span class="sxs-lookup"><span data-stu-id="e75d3-142">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e75d3-143">父項目</span><span class="sxs-lookup"><span data-stu-id="e75d3-143">Parent Elements</span></span>  
  
|<span data-ttu-id="e75d3-144">項目</span><span class="sxs-lookup"><span data-stu-id="e75d3-144">Element</span></span>|<span data-ttu-id="e75d3-145">描述</span><span class="sxs-lookup"><span data-stu-id="e75d3-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e75d3-146">serviceModel</span><span class="sxs-lookup"><span data-stu-id="e75d3-146">serviceModel</span></span>|<span data-ttu-id="e75d3-147">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="e75d3-147">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e75d3-148">備註</span><span class="sxs-lookup"><span data-stu-id="e75d3-148">Remarks</span></span>  
 <span data-ttu-id="e75d3-149">根據預設，WCF 服務會與 ASP.NET 在裝載的應用程式定義域 (AppDomain) 中並存執行。</span><span class="sxs-lookup"><span data-stu-id="e75d3-149">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="e75d3-150">即使 WCF 與 ASP.NET 可共存於相同的 AppDomain，但 WCF 要求依預設不會由 ASP.NET HTTP 管線處理。</span><span class="sxs-lookup"><span data-stu-id="e75d3-150">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="e75d3-151">因此，WCF 服務無法使用 ASP.NET 應用程式平台的某些元素，</span><span class="sxs-lookup"><span data-stu-id="e75d3-151">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="e75d3-152">包括：</span><span class="sxs-lookup"><span data-stu-id="e75d3-152">These include</span></span>  
  
- <span data-ttu-id="e75d3-153">ASP.NET 檔案/URL 授權</span><span class="sxs-lookup"><span data-stu-id="e75d3-153">ASP.NET File/URL Authorization</span></span>  
  
- <span data-ttu-id="e75d3-154">ASP.NET 模擬</span><span class="sxs-lookup"><span data-stu-id="e75d3-154">ASP.NET Impersonation</span></span>  
  
- <span data-ttu-id="e75d3-155">Cookie 架構工作階段狀態</span><span class="sxs-lookup"><span data-stu-id="e75d3-155">Cookie-based Session State</span></span>  
  
- <span data-ttu-id="e75d3-156">HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="e75d3-156">HttpContext.Current</span></span>  
  
- <span data-ttu-id="e75d3-157">透過自訂 HttpModule 的管線擴充性</span><span class="sxs-lookup"><span data-stu-id="e75d3-157">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="e75d3-158">如果您的 WCF 服務需要在 ASP.NET 內容中運作，而且只透過 HTTP 進行通訊，可使用 WCF 的 ASP.NET 相容性模式。</span><span class="sxs-lookup"><span data-stu-id="e75d3-158">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="e75d3-159">當 `aspNetCompatibilityEnabled` 屬性在應用程式層級設為 `true` 時，便會開啟這個模式。</span><span class="sxs-lookup"><span data-stu-id="e75d3-159">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="e75d3-160">服務實作必須使用 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 類別宣告其可在相容性模式執行。</span><span class="sxs-lookup"><span data-stu-id="e75d3-160">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="e75d3-161">啟用相容性模式時，</span><span class="sxs-lookup"><span data-stu-id="e75d3-161">When the compatibility mode is enabled,</span></span>  
  
- <span data-ttu-id="e75d3-162">ASP.NET 檔案/URL 驗證會在 WCF 驗證前強制執行。</span><span class="sxs-lookup"><span data-stu-id="e75d3-162">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="e75d3-163">驗證決策是以要求的傳輸層級身分識別為基礎，</span><span class="sxs-lookup"><span data-stu-id="e75d3-163">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="e75d3-164">訊息層級的身分識別則會被忽略。</span><span class="sxs-lookup"><span data-stu-id="e75d3-164">Identities at the message level are ignored.</span></span>  
  
- <span data-ttu-id="e75d3-165">WCF 服務作業會開始在 ASP.NET 模擬內容中執行。</span><span class="sxs-lookup"><span data-stu-id="e75d3-165">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="e75d3-166">如果同時啟用特定服務的 ASP.NET 模擬與 WCF 模擬，則會使用 WCF 模擬內容。</span><span class="sxs-lookup"><span data-stu-id="e75d3-166">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
- <span data-ttu-id="e75d3-167">HttpContext.Current 可從 WCF 服務程式碼使用，而且服務不可以公開非 HTTP 端點。</span><span class="sxs-lookup"><span data-stu-id="e75d3-167">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
- <span data-ttu-id="e75d3-168">WCF 要求是由 ASP.NET 管線處理。</span><span class="sxs-lookup"><span data-stu-id="e75d3-168">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="e75d3-169">已設定為處理傳入要求的 HttpModules 也可以處理 WCF 要求，</span><span class="sxs-lookup"><span data-stu-id="e75d3-169">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="e75d3-170">其中可包含 ASP.NET 平台元件 (如 <xref:System.Web.SessionState.SessionStateModule>) 以及自訂的協力廠商模組。</span><span class="sxs-lookup"><span data-stu-id="e75d3-170">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e75d3-171">範例</span><span class="sxs-lookup"><span data-stu-id="e75d3-171">Example</span></span>  
 <span data-ttu-id="e75d3-172">下列程式碼範例會示範如何啟用 ASP 相容性模式。</span><span class="sxs-lookup"><span data-stu-id="e75d3-172">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="e75d3-173">程式碼</span><span class="sxs-lookup"><span data-stu-id="e75d3-173">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="e75d3-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e75d3-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="e75d3-175">裝載</span><span class="sxs-lookup"><span data-stu-id="e75d3-175">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
- [<span data-ttu-id="e75d3-176">WCF 服務與 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e75d3-176">WCF Services and ASP.NET</span></span>](../../../wcf/feature-details/wcf-services-and-aspnet.md)
