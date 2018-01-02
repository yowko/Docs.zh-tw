---
title: "&lt;disableFusionUpdatesFromADManager&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d3a1214b4aecf56c9a6440e31459573a5922676
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a><span data-ttu-id="05cdf-102">&lt;disableFusionUpdatesFromADManager&gt;項目</span><span class="sxs-lookup"><span data-stu-id="05cdf-102">&lt;disableFusionUpdatesFromADManager&gt; Element</span></span>
<span data-ttu-id="05cdf-103">指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。</span><span class="sxs-lookup"><span data-stu-id="05cdf-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
 <span data-ttu-id="05cdf-104">\<設定 > 項目</span><span class="sxs-lookup"><span data-stu-id="05cdf-104">\<configuration> Element</span></span>  
<span data-ttu-id="05cdf-105">\<runtime > 項目</span><span class="sxs-lookup"><span data-stu-id="05cdf-105">\<runtime> Element</span></span>  
<span data-ttu-id="05cdf-106">\<disableFusionUpdatesFromADManager ></span><span class="sxs-lookup"><span data-stu-id="05cdf-106">\<disableFusionUpdatesFromADManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05cdf-107">語法</span><span class="sxs-lookup"><span data-stu-id="05cdf-107">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05cdf-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="05cdf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="05cdf-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="05cdf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05cdf-110">屬性</span><span class="sxs-lookup"><span data-stu-id="05cdf-110">Attributes</span></span>  
  
|<span data-ttu-id="05cdf-111">屬性</span><span class="sxs-lookup"><span data-stu-id="05cdf-111">Attribute</span></span>|<span data-ttu-id="05cdf-112">描述</span><span class="sxs-lookup"><span data-stu-id="05cdf-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05cdf-113">enabled</span><span class="sxs-lookup"><span data-stu-id="05cdf-113">enabled</span></span>|<span data-ttu-id="05cdf-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="05cdf-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="05cdf-115">指定是否要停用覆寫融合設定的預設功能。</span><span class="sxs-lookup"><span data-stu-id="05cdf-115">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="05cdf-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="05cdf-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="05cdf-117">值</span><span class="sxs-lookup"><span data-stu-id="05cdf-117">Value</span></span>|<span data-ttu-id="05cdf-118">描述</span><span class="sxs-lookup"><span data-stu-id="05cdf-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05cdf-119">0</span><span class="sxs-lookup"><span data-stu-id="05cdf-119">0</span></span>|<span data-ttu-id="05cdf-120">請勿停用覆寫融合設定的功能。</span><span class="sxs-lookup"><span data-stu-id="05cdf-120">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="05cdf-121">這是預設行為，開頭[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="05cdf-121">This is the default behavior, starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
|<span data-ttu-id="05cdf-122">1</span><span class="sxs-lookup"><span data-stu-id="05cdf-122">1</span></span>|<span data-ttu-id="05cdf-123">停用覆寫融合設定的功能。</span><span class="sxs-lookup"><span data-stu-id="05cdf-123">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="05cdf-124">這會還原為舊版.NET Framework 的行為。</span><span class="sxs-lookup"><span data-stu-id="05cdf-124">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05cdf-125">子元素</span><span class="sxs-lookup"><span data-stu-id="05cdf-125">Child Elements</span></span>  
 <span data-ttu-id="05cdf-126">無。</span><span class="sxs-lookup"><span data-stu-id="05cdf-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05cdf-127">父項目</span><span class="sxs-lookup"><span data-stu-id="05cdf-127">Parent Elements</span></span>  
  
|<span data-ttu-id="05cdf-128">項目</span><span class="sxs-lookup"><span data-stu-id="05cdf-128">Element</span></span>|<span data-ttu-id="05cdf-129">描述</span><span class="sxs-lookup"><span data-stu-id="05cdf-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="05cdf-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="05cdf-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="05cdf-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="05cdf-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05cdf-132">備註</span><span class="sxs-lookup"><span data-stu-id="05cdf-132">Remarks</span></span>  
 <span data-ttu-id="05cdf-133">從開始[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，預設行為是允許<xref:System.AppDomainManager>物件來覆寫使用的組態設定<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性或<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法<xref:System.AppDomainSetup>物件傳遞至您的實作<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>方法，在您的子類別<xref:System.AppDomainManager>。</span><span class="sxs-lookup"><span data-stu-id="05cdf-133">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="05cdf-134">預設應用程式定義域中，您所變更的設定覆寫應用程式組態檔所指定的設定。</span><span class="sxs-lookup"><span data-stu-id="05cdf-134">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="05cdf-135">其他應用程式定義域，它們會覆寫的組態設定，傳遞給<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>或<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="05cdf-135">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="05cdf-136">您可以傳遞新組態資訊，或傳遞 null (`Nothing`在 Visual Basic 中) 若要消除傳入的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="05cdf-136">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="05cdf-137">不要將組態資訊傳遞給兩者<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性和<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="05cdf-137">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="05cdf-138">如果您同時將組態資訊，資訊您傳遞給<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性會被忽略，因為<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法會覆寫來自應用程式組態檔的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="05cdf-138">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="05cdf-139">如果您使用<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性，您可以將傳遞 null (`Nothing`在 Visual Basic 中) 以<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法，以排除指定的呼叫中的任何組態位元組<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>或<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="05cdf-139">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="05cdf-140">除了設定資訊，您可以變更下列設定<xref:System.AppDomainSetup>物件傳遞至您的實作<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>方法： <xref:System.AppDomainSetup.ApplicationBase%2A>， <xref:System.AppDomainSetup.ApplicationName%2A>， <xref:System.AppDomainSetup.CachePath%2A>， <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>， <xref:System.AppDomainSetup.DisallowBindingRedirects%2A><xref:System.AppDomainSetup.DisallowCodeDownload%2A>， <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>， <xref:System.AppDomainSetup.DynamicBase%2A>， <xref:System.AppDomainSetup.LoaderOptimization%2A>， <xref:System.AppDomainSetup.PrivateBinPath%2A>， <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>， <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>，和<xref:System.AppDomainSetup.ShadowCopyFiles%2A>。</span><span class="sxs-lookup"><span data-stu-id="05cdf-140">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="05cdf-141">做為使用替代`<disableFusionUpdatesFromADManager>`項目，您可以停用的預設行為建立登錄設定，或設定環境變數。</span><span class="sxs-lookup"><span data-stu-id="05cdf-141">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="05cdf-142">在登錄中，建立名為的 DWORD 值`COMPLUS_disableFusionUpdatesFromADManager`下`HKCU\Software\Microsoft\.NETFramework`或`HKLM\Software\Microsoft\.NETFramework`，並將值設定為 1。</span><span class="sxs-lookup"><span data-stu-id="05cdf-142">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="05cdf-143">在命令列中，設定環境變數`COMPLUS_disableFusionUpdatesFromADManager`設為 1。</span><span class="sxs-lookup"><span data-stu-id="05cdf-143">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05cdf-144">範例</span><span class="sxs-lookup"><span data-stu-id="05cdf-144">Example</span></span>  
 <span data-ttu-id="05cdf-145">下列範例示範如何停用的功能使用覆寫融合設定`<disableFusionUpdatesFromADManager>`項目。</span><span class="sxs-lookup"><span data-stu-id="05cdf-145">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="05cdf-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="05cdf-146">See Also</span></span>  
 [<span data-ttu-id="05cdf-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="05cdf-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="05cdf-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="05cdf-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="05cdf-149">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="05cdf-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
