---
title: '&lt;disableFusionUpdatesFromADManager&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e5e33cd3d250b26f0a83a87c4f7ce438af22e96
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a><span data-ttu-id="dde00-102">&lt;disableFusionUpdatesFromADManager&gt;項目</span><span class="sxs-lookup"><span data-stu-id="dde00-102">&lt;disableFusionUpdatesFromADManager&gt; Element</span></span>
<span data-ttu-id="dde00-103">指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。</span><span class="sxs-lookup"><span data-stu-id="dde00-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
 <span data-ttu-id="dde00-104">\<設定 > 項目</span><span class="sxs-lookup"><span data-stu-id="dde00-104">\<configuration> Element</span></span>  
<span data-ttu-id="dde00-105">\<runtime > 項目</span><span class="sxs-lookup"><span data-stu-id="dde00-105">\<runtime> Element</span></span>  
<span data-ttu-id="dde00-106">\<disableFusionUpdatesFromADManager ></span><span class="sxs-lookup"><span data-stu-id="dde00-106">\<disableFusionUpdatesFromADManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dde00-107">語法</span><span class="sxs-lookup"><span data-stu-id="dde00-107">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dde00-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dde00-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dde00-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dde00-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dde00-110">屬性</span><span class="sxs-lookup"><span data-stu-id="dde00-110">Attributes</span></span>  
  
|<span data-ttu-id="dde00-111">屬性</span><span class="sxs-lookup"><span data-stu-id="dde00-111">Attribute</span></span>|<span data-ttu-id="dde00-112">描述</span><span class="sxs-lookup"><span data-stu-id="dde00-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dde00-113">enabled</span><span class="sxs-lookup"><span data-stu-id="dde00-113">enabled</span></span>|<span data-ttu-id="dde00-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="dde00-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="dde00-115">指定是否要停用覆寫融合設定的預設功能。</span><span class="sxs-lookup"><span data-stu-id="dde00-115">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="dde00-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="dde00-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="dde00-117">值</span><span class="sxs-lookup"><span data-stu-id="dde00-117">Value</span></span>|<span data-ttu-id="dde00-118">描述</span><span class="sxs-lookup"><span data-stu-id="dde00-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dde00-119">0</span><span class="sxs-lookup"><span data-stu-id="dde00-119">0</span></span>|<span data-ttu-id="dde00-120">請勿停用覆寫融合設定的功能。</span><span class="sxs-lookup"><span data-stu-id="dde00-120">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="dde00-121">這是預設行為，開頭[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dde00-121">This is the default behavior, starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
|<span data-ttu-id="dde00-122">1</span><span class="sxs-lookup"><span data-stu-id="dde00-122">1</span></span>|<span data-ttu-id="dde00-123">停用覆寫融合設定的功能。</span><span class="sxs-lookup"><span data-stu-id="dde00-123">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="dde00-124">這會還原為舊版.NET Framework 的行為。</span><span class="sxs-lookup"><span data-stu-id="dde00-124">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dde00-125">子項目</span><span class="sxs-lookup"><span data-stu-id="dde00-125">Child Elements</span></span>  
 <span data-ttu-id="dde00-126">無。</span><span class="sxs-lookup"><span data-stu-id="dde00-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dde00-127">父項目</span><span class="sxs-lookup"><span data-stu-id="dde00-127">Parent Elements</span></span>  
  
|<span data-ttu-id="dde00-128">項目</span><span class="sxs-lookup"><span data-stu-id="dde00-128">Element</span></span>|<span data-ttu-id="dde00-129">描述</span><span class="sxs-lookup"><span data-stu-id="dde00-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dde00-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="dde00-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="dde00-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="dde00-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dde00-132">備註</span><span class="sxs-lookup"><span data-stu-id="dde00-132">Remarks</span></span>  
 <span data-ttu-id="dde00-133">從開始[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，預設行為是允許<xref:System.AppDomainManager>物件來覆寫使用的組態設定<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性或<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法<xref:System.AppDomainSetup>物件傳遞至您的實作<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>方法，在您的子類別<xref:System.AppDomainManager>。</span><span class="sxs-lookup"><span data-stu-id="dde00-133">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="dde00-134">預設應用程式定義域中，您所變更的設定覆寫應用程式組態檔所指定的設定。</span><span class="sxs-lookup"><span data-stu-id="dde00-134">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="dde00-135">其他應用程式定義域，它們會覆寫的組態設定，傳遞給<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>或<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="dde00-135">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="dde00-136">您可以傳遞新組態資訊，或傳遞 null (`Nothing`在 Visual Basic 中) 若要消除傳入的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="dde00-136">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="dde00-137">不要將組態資訊傳遞給兩者<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性和<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="dde00-137">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="dde00-138">如果您同時將組態資訊，資訊您傳遞給<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性會被忽略，因為<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法會覆寫來自應用程式組態檔的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="dde00-138">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="dde00-139">如果您使用<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性，您可以將傳遞 null (`Nothing`在 Visual Basic 中) 以<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法，以排除指定的呼叫中的任何組態位元組<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>或<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="dde00-139">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="dde00-140">除了設定資訊，您可以變更下列設定<xref:System.AppDomainSetup>物件傳遞至您的實作<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>方法： <xref:System.AppDomainSetup.ApplicationBase%2A>， <xref:System.AppDomainSetup.ApplicationName%2A>， <xref:System.AppDomainSetup.CachePath%2A>， <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>， <xref:System.AppDomainSetup.DisallowBindingRedirects%2A><xref:System.AppDomainSetup.DisallowCodeDownload%2A>， <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>， <xref:System.AppDomainSetup.DynamicBase%2A>， <xref:System.AppDomainSetup.LoaderOptimization%2A>， <xref:System.AppDomainSetup.PrivateBinPath%2A>， <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>， <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>，和<xref:System.AppDomainSetup.ShadowCopyFiles%2A>。</span><span class="sxs-lookup"><span data-stu-id="dde00-140">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="dde00-141">做為使用替代`<disableFusionUpdatesFromADManager>`項目，您可以停用的預設行為建立登錄設定，或設定環境變數。</span><span class="sxs-lookup"><span data-stu-id="dde00-141">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="dde00-142">在登錄中，建立名為的 DWORD 值`COMPLUS_disableFusionUpdatesFromADManager`下`HKCU\Software\Microsoft\.NETFramework`或`HKLM\Software\Microsoft\.NETFramework`，並將值設定為 1。</span><span class="sxs-lookup"><span data-stu-id="dde00-142">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="dde00-143">在命令列中，設定環境變數`COMPLUS_disableFusionUpdatesFromADManager`設為 1。</span><span class="sxs-lookup"><span data-stu-id="dde00-143">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dde00-144">範例</span><span class="sxs-lookup"><span data-stu-id="dde00-144">Example</span></span>  
 <span data-ttu-id="dde00-145">下列範例示範如何停用的功能使用覆寫融合設定`<disableFusionUpdatesFromADManager>`項目。</span><span class="sxs-lookup"><span data-stu-id="dde00-145">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dde00-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dde00-146">See Also</span></span>  
 [<span data-ttu-id="dde00-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="dde00-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="dde00-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="dde00-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="dde00-149">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="dde00-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
