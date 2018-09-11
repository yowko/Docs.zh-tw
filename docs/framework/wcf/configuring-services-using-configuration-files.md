---
title: 使用組態檔設定服務
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 904abff4f3cae5873fe3cc9705dee84f73e2a523
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361530"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="7cd91-102">使用組態檔設定服務</span><span class="sxs-lookup"><span data-stu-id="7cd91-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="7cd91-103">使用組態檔中設定 Windows Communication Foundation (WCF) 服務可讓您彈性提供端點，並設計階段部署而不是在服務行為資料。</span><span class="sxs-lookup"><span data-stu-id="7cd91-103">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="7cd91-104">本主題概要說明可用的主要技巧。</span><span class="sxs-lookup"><span data-stu-id="7cd91-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="7cd91-105">WCF 服務是可設定使用[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]技術設定。</span><span class="sxs-lookup"><span data-stu-id="7cd91-105">A WCF service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="7cd91-106">大多數情況下，XML 項目會新增至裝載的 WCF 服務的 Internet Information Services (IIS) 網站的 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="7cd91-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="7cd91-107">這些項目允許您變更詳細資料，例如各電腦的端點位址 (用於與服務通訊的實際位址)。</span><span class="sxs-lookup"><span data-stu-id="7cd91-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="7cd91-108">此外，WCF 會包含數個系統提供的項目可讓您快速地選取 服務最基本的功能。</span><span class="sxs-lookup"><span data-stu-id="7cd91-108">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="7cd91-109">從開始[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]，WCF 本身就有新的預設組態模型，可簡化 WCF 組態需求。</span><span class="sxs-lookup"><span data-stu-id="7cd91-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="7cd91-110">如果您未提供任何特定服務的 WCF 組態，執行階段會使用一些標準端點和預設繫結/行為自動設定您的服務。</span><span class="sxs-lookup"><span data-stu-id="7cd91-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="7cd91-111">在實務上，撰寫組態是主要的程式設計 WCF 應用程式一部分。</span><span class="sxs-lookup"><span data-stu-id="7cd91-111">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="7cd91-112">如需詳細資訊，請參閱 <<c0> [ 服務的設定繫結](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7cd91-112">For more information, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="7cd91-113">如需的最常用的項目，請參閱 < [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="7cd91-113">For a list of of the most commonly used elements, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="7cd91-114">如需預設端點、繫結和行為的詳細資訊，請參閱[簡化的組態](../../../docs/framework/wcf/simplified-configuration.md)和 [WCF 服務的簡化組態](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7cd91-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7cd91-115">部署並存案例時，如果部署了兩個不同的服務版本，您就必須指定組態檔所參考之組件的部分名稱。</span><span class="sxs-lookup"><span data-stu-id="7cd91-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="7cd91-116">這是因為組態檔會在所有服務版本之間共用，而且它們可能會在不同的 .NET Framework 版本底下執行。</span><span class="sxs-lookup"><span data-stu-id="7cd91-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="7cd91-117">System.Configuration：Web.config 和 App.config</span><span class="sxs-lookup"><span data-stu-id="7cd91-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="7cd91-118">WCF 會使用的 System.Configuration 組態系統[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7cd91-118">WCF uses the System.Configuration configuration system of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="7cd91-119">設定服務時在 Visual Studio 中，使用 web.config 或 App.config 檔案以指定的設定。</span><span class="sxs-lookup"><span data-stu-id="7cd91-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="7cd91-120">組態檔名稱的選擇取決於您為服務選擇的裝載環境。</span><span class="sxs-lookup"><span data-stu-id="7cd91-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="7cd91-121">如果您選擇使用 IIS 來裝載服務，請使用 Web.config 檔。</span><span class="sxs-lookup"><span data-stu-id="7cd91-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="7cd91-122">如果您使用其他任何裝載環境，請使用 App.config 檔。</span><span class="sxs-lookup"><span data-stu-id="7cd91-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="7cd91-123">在 Visual Studio 中，名為 App.config 的檔案用來建立最後的組態檔。</span><span class="sxs-lookup"><span data-stu-id="7cd91-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="7cd91-124">最後實際使用的組態名稱取決於組件名稱。</span><span class="sxs-lookup"><span data-stu-id="7cd91-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="7cd91-125">例如，名為 "Cohowinery.exe" 的組件，其最後的組態檔名為 "Cohowinery.exe.config"。</span><span class="sxs-lookup"><span data-stu-id="7cd91-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="7cd91-126">但是，您只需要修改 App.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="7cd91-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="7cd91-127">對該檔案進行的變更，會在編譯階段自動套用至最後的應用程式組態檔中。</span><span class="sxs-lookup"><span data-stu-id="7cd91-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="7cd91-128">在使用 App.config 檔案時，一旦應用程式啟動且套用了組態，組態系統會將 App.config 檔案與 Machine.config 檔案的內容合併。</span><span class="sxs-lookup"><span data-stu-id="7cd91-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="7cd91-129">這項機制可讓您透過 Machine.config 檔案來設定整部電腦。</span><span class="sxs-lookup"><span data-stu-id="7cd91-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="7cd91-130">App.config 檔案可以用來覆寫 Machine.config 檔案的設定，您也可以鎖定 Machine.config 檔案的設定以便加以取用。</span><span class="sxs-lookup"><span data-stu-id="7cd91-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="7cd91-131">在 Web.config 情況中，組態系統會將所有目錄乃至應用程式目錄中的 Web.config 檔案合併至已套用的組態。</span><span class="sxs-lookup"><span data-stu-id="7cd91-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="7cd91-132">如需有關組態和設定值優先權的詳細資訊，請參閱主題<xref:System.Configuration>命名空間。</span><span class="sxs-lookup"><span data-stu-id="7cd91-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="7cd91-133">組態檔的主要區段</span><span class="sxs-lookup"><span data-stu-id="7cd91-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="7cd91-134">組態檔的主要區段包含下列項目。</span><span class="sxs-lookup"><span data-stu-id="7cd91-134">The main sections in the configuration file include the following elements.</span></span>  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!—- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->   
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="7cd91-135">繫結和行為區段都是選用的，而且只會在必要時才納入。</span><span class="sxs-lookup"><span data-stu-id="7cd91-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="7cd91-136">\<服務 > 項目</span><span class="sxs-lookup"><span data-stu-id="7cd91-136">The \<services> Element</span></span>  
 <span data-ttu-id="7cd91-137">`services` 項目包含所有由應用程式裝載的服務規格。</span><span class="sxs-lookup"><span data-stu-id="7cd91-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="7cd91-138">從 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]簡化的組態模型開始，本節為選擇性。</span><span class="sxs-lookup"><span data-stu-id="7cd91-138">Starting with the simplified configuration model in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], this section is optional.</span></span>  
  
 [<span data-ttu-id="7cd91-139">\<services></span><span class="sxs-lookup"><span data-stu-id="7cd91-139">\<services></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="7cd91-140">\<服務 > 項目</span><span class="sxs-lookup"><span data-stu-id="7cd91-140">The \<service> Element</span></span>  
 <span data-ttu-id="7cd91-141">每項服務都有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7cd91-141">Each service has these attributes:</span></span>  
  
-   <span data-ttu-id="7cd91-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="7cd91-142">`name`.</span></span> <span data-ttu-id="7cd91-143">指定用來提供服務合約實作的型別。</span><span class="sxs-lookup"><span data-stu-id="7cd91-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="7cd91-144">這是由命名空間、句號和型別名稱組成的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="7cd91-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="7cd91-145">例如 `"MyNameSpace.myServiceType"`。</span><span class="sxs-lookup"><span data-stu-id="7cd91-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
-   <span data-ttu-id="7cd91-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="7cd91-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="7cd91-147">指定在 `behavior` 項目中找到的其中一個 `behaviors` 項目名稱。</span><span class="sxs-lookup"><span data-stu-id="7cd91-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="7cd91-148">指定的行為會掌管服務是否允許模擬之類的動作。</span><span class="sxs-lookup"><span data-stu-id="7cd91-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="7cd91-149">如果其值為空白名稱或未提供 `behaviorConfiguration` ，則會將一組預設的服務行為加入至服務。</span><span class="sxs-lookup"><span data-stu-id="7cd91-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
-   [<span data-ttu-id="7cd91-150">\<service></span><span class="sxs-lookup"><span data-stu-id="7cd91-150">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="7cd91-151">\<端點 > 項目</span><span class="sxs-lookup"><span data-stu-id="7cd91-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="7cd91-152">每個端點都需要下列屬性代表的位址、繫結和合約：</span><span class="sxs-lookup"><span data-stu-id="7cd91-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
-   <span data-ttu-id="7cd91-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="7cd91-153">`address`.</span></span> <span data-ttu-id="7cd91-154">指定服務的統一資源識別元 (URI)，此識別元可以是絕對位址，或是相對於服務基底位址的相對位址。</span><span class="sxs-lookup"><span data-stu-id="7cd91-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="7cd91-155">如果設為空字串，則代表在建立服務的 <xref:System.ServiceModel.ServiceHost> 時，指定的基底位址將有可用的端點。</span><span class="sxs-lookup"><span data-stu-id="7cd91-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
-   <span data-ttu-id="7cd91-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="7cd91-156">`binding`.</span></span> <span data-ttu-id="7cd91-157">一般來說，會指定系統提供的繫結，例如 <xref:System.ServiceModel.WSHttpBinding>，但是也可以指定使用者定義的繫結。</span><span class="sxs-lookup"><span data-stu-id="7cd91-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="7cd91-158">指定的繫結會決定使用的傳輸類型、安全性和編碼，以及是否支援或啟用可靠工作階段、交易或資料流處理。</span><span class="sxs-lookup"><span data-stu-id="7cd91-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
-   <span data-ttu-id="7cd91-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="7cd91-159">`bindingConfiguration`.</span></span> <span data-ttu-id="7cd91-160">如果必須修改預設的繫結值，可以藉由設定 `binding` 項目中的適當 `bindings` 項目來達成。</span><span class="sxs-lookup"><span data-stu-id="7cd91-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="7cd91-161">此屬性應該被賦予與用來變更預設值時所用的 `name` 項目的 `binding` 屬性相同的值。</span><span class="sxs-lookup"><span data-stu-id="7cd91-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="7cd91-162">如果未指定名稱或在繫結中未指定 `bindingConfiguration` ，則會將繫結型別的預設繫結用於端點。</span><span class="sxs-lookup"><span data-stu-id="7cd91-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
-   <span data-ttu-id="7cd91-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="7cd91-163">`contract`.</span></span> <span data-ttu-id="7cd91-164">指定可定義合約的介面。</span><span class="sxs-lookup"><span data-stu-id="7cd91-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="7cd91-165">這個介面是由 `name` 項目的 `service` 屬性所指定的 Common Language Runtime (CLR) 型別所實作。</span><span class="sxs-lookup"><span data-stu-id="7cd91-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
-   [<span data-ttu-id="7cd91-166">\<結束點 > 項目參考</span><span class="sxs-lookup"><span data-stu-id="7cd91-166">\<endpoint> element reference</span></span>](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="7cd91-167">\<繫結 > 項目</span><span class="sxs-lookup"><span data-stu-id="7cd91-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="7cd91-168">`bindings` 項目包含所有繫結的規格，在任何服務中定義的任何端點都可以使用這些繫結。</span><span class="sxs-lookup"><span data-stu-id="7cd91-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="7cd91-169">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7cd91-169">\<bindings></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="7cd91-170">\<繫結 > 項目</span><span class="sxs-lookup"><span data-stu-id="7cd91-170">The \<binding> Element</span></span>  
 <span data-ttu-id="7cd91-171">`binding`中所包含的項目`bindings`項目可以是其中一個系統提供繫結 (請參閱[System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) 或自訂繫結 (請參閱[自訂繫結](../../../docs/framework/wcf/extending/custom-bindings.md))。</span><span class="sxs-lookup"><span data-stu-id="7cd91-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) or a custom binding (see [Custom Bindings](../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="7cd91-172">`binding` 項目具有的 `name` 屬性可將繫結與 `bindingConfiguration` 項目的 `endpoint` 屬性所指定的端點相互關聯。</span><span class="sxs-lookup"><span data-stu-id="7cd91-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="7cd91-173">如果未指定名稱，則該繫結會對應於該繫結型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="7cd91-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
 <span data-ttu-id="7cd91-174">如需有關如何設定服務和用戶端的詳細資訊，請參閱 <<c0> [ 設定的 Windows Communication Foundation 應用程式](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)。</span><span class="sxs-lookup"><span data-stu-id="7cd91-174">For more information about configuring services and clients, see [Configuring Windows Communication Foundation Applications](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
 [<span data-ttu-id="7cd91-175">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7cd91-175">\<binding></span></span>](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="7cd91-176">\<行為 > 項目</span><span class="sxs-lookup"><span data-stu-id="7cd91-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="7cd91-177">這是定義服務行為之 `behavior` 項目的容器項目。</span><span class="sxs-lookup"><span data-stu-id="7cd91-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="7cd91-178">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7cd91-178">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="7cd91-179">\<行為 > 項目</span><span class="sxs-lookup"><span data-stu-id="7cd91-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="7cd91-180">每個 `behavior` 項目都是由 `name` 屬性所識別，並可提供系統提供的行為，例如 <`throttling`>，或是自訂行為。</span><span class="sxs-lookup"><span data-stu-id="7cd91-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="7cd91-181">如果未指定名稱，則該行為項目會對應於預設服務或端點行為。</span><span class="sxs-lookup"><span data-stu-id="7cd91-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="7cd91-182">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7cd91-182">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="7cd91-183">如何使用繫結與行為組態</span><span class="sxs-lookup"><span data-stu-id="7cd91-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="7cd91-184">WCF 可讓您更容易使用的參考系統組態中的端點之間共用組態。</span><span class="sxs-lookup"><span data-stu-id="7cd91-184">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="7cd91-185">與其直接指派組態值給端點，繫結相關的組態值會被分類到 `bindingConfiguration` 區段的 `<binding>` 項目群組中。</span><span class="sxs-lookup"><span data-stu-id="7cd91-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="7cd91-186">一個繫結組態是繫結上的一個具名的設定群組。</span><span class="sxs-lookup"><span data-stu-id="7cd91-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="7cd91-187">然後，端點可以依照名稱來參考 `bindingConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="7cd91-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!—- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint   
          address="myAddress" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint   
          address="myAddress2" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint   
          address="myAddress3" binding="basicHttpBinding"   
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="7cd91-188">`name` 的 `bindingConfiguration` 會在 `<binding>` 項目中設定。</span><span class="sxs-lookup"><span data-stu-id="7cd91-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="7cd91-189">`name`必須是唯一的字串繫結類型的範圍內，在此情況下[< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)，或空的值來參考預設繫結。</span><span class="sxs-lookup"><span data-stu-id="7cd91-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="7cd91-190">端點會將 `bindingConfiguration` 屬性設為此字串來連結至組態。</span><span class="sxs-lookup"><span data-stu-id="7cd91-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="7cd91-191">如下列範例所示， `behaviorConfiguration` 也是以同樣方式來實作。</span><span class="sxs-lookup"><span data-stu-id="7cd91-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint   
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="7cd91-192">請注意，預設的服務行為集合會加入至服務。</span><span class="sxs-lookup"><span data-stu-id="7cd91-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="7cd91-193">此系統允許端點共用組態，而不用重新定義設定。</span><span class="sxs-lookup"><span data-stu-id="7cd91-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="7cd91-194">如果需要整部電腦範圍，請在 Machine.config 中建立繫結或行為組態。所有 App.config 檔都提供組態設定。</span><span class="sxs-lookup"><span data-stu-id="7cd91-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="7cd91-195">[Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) 可讓您輕易地建立組態。</span><span class="sxs-lookup"><span data-stu-id="7cd91-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="7cd91-196">行為合併</span><span class="sxs-lookup"><span data-stu-id="7cd91-196">Behavior Merge</span></span>  
 <span data-ttu-id="7cd91-197">當您想要以一致的方式使用一組通用行為時，行為合併功能可讓您輕鬆地管理行為。</span><span class="sxs-lookup"><span data-stu-id="7cd91-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="7cd91-198">這項功能可讓您以不同的組態階層層級指定行為，並且讓服務從多個組態階層層級繼承行為。</span><span class="sxs-lookup"><span data-stu-id="7cd91-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="7cd91-199">為了說明這項功能的運作方式，假設您在 IIS 中設有下列虛擬目錄配置：</span><span class="sxs-lookup"><span data-stu-id="7cd91-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 <span data-ttu-id="7cd91-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span><span class="sxs-lookup"><span data-stu-id="7cd91-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span></span>  
  
 <span data-ttu-id="7cd91-201">而且，您的 ~\Web.config 檔案具有下列內容：</span><span class="sxs-lookup"><span data-stu-id="7cd91-201">And your ~\Web.config file has the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="7cd91-202">而且，您有一個位於 ~\Child\Web.config 的子系 Web.config，其中包含下列內容：</span><span class="sxs-lookup"><span data-stu-id="7cd91-202">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="7cd91-203">位於 ~\Child\Service.svc 的服務會表現成同時具有 serviceDebug 和 serviceMetadata 行為。</span><span class="sxs-lookup"><span data-stu-id="7cd91-203">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="7cd91-204">位於 ~\Service.svc 的服務則只有 serviceDebug 行為。</span><span class="sxs-lookup"><span data-stu-id="7cd91-204">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="7cd91-205">結果是，系統會合併這兩個具有相同名稱的行為集合 (在本例中，名稱為空字串)。</span><span class="sxs-lookup"><span data-stu-id="7cd91-205">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="7cd91-206">您也可以使用來清除行為集合\<清除 > 標記，並移除集合中的個別行為，使用\<移除 > 標記。</span><span class="sxs-lookup"><span data-stu-id="7cd91-206">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="7cd91-207">例如，下列兩個組態會產生只有 serviceMetadata 行為的子服務：</span><span class="sxs-lookup"><span data-stu-id="7cd91-207">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="7cd91-208">系統會針對沒有名稱的行為集合 (如上所示) 以及具名的行為集合進行行為合併。</span><span class="sxs-lookup"><span data-stu-id="7cd91-208">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="7cd91-209">行為合併適用於 IIS 裝載環境，其中 Web.config 檔案會以階層方式與根 Web.config 檔案和 machine.config 合併。不過，它也適用於應用程式環境，其中 machine.config 可以與 App.config 檔案合併。</span><span class="sxs-lookup"><span data-stu-id="7cd91-209">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="7cd91-210">行為合併會同時套用至組態中的端點行為和服務行為。</span><span class="sxs-lookup"><span data-stu-id="7cd91-210">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="7cd91-211">如果子行為集合包含已經存在父行為集合中的行為，子行為就會覆寫父代。</span><span class="sxs-lookup"><span data-stu-id="7cd91-211">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="7cd91-212">因此，如果父行為集合具有`<serviceMetadata httpGetEnabled="False" />`，而且子行為集合具有`<serviceMetadata httpGetEnabled="True" />`，子行為將會覆寫行為集合中的父行為，而且 httpGetEnabled 會是"true"。</span><span class="sxs-lookup"><span data-stu-id="7cd91-212">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cd91-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cd91-213">See Also</span></span>  
 [<span data-ttu-id="7cd91-214">簡化設定</span><span class="sxs-lookup"><span data-stu-id="7cd91-214">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="7cd91-215">設定 Windows Communication Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="7cd91-215">Configuring Windows Communication Foundation Applications</span></span>](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [<span data-ttu-id="7cd91-216">\<service></span><span class="sxs-lookup"><span data-stu-id="7cd91-216">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
 [<span data-ttu-id="7cd91-217">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7cd91-217">\<binding></span></span>](../../../docs/framework/misc/binding.md)
