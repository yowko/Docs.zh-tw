---
title: <disableFusionUpdatesFromADManager> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1923e70143ea2a158447eccdb35d347fe4f51ea
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663775"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="6ef4c-102">\<disableFusionUpdatesFromADManager > 元素</span><span class="sxs-lookup"><span data-stu-id="6ef4c-102">\<disableFusionUpdatesFromADManager> Element</span></span>
<span data-ttu-id="6ef4c-103">指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
 <span data-ttu-id="6ef4c-104">\<configuration > 元素</span><span class="sxs-lookup"><span data-stu-id="6ef4c-104">\<configuration> Element</span></span>  
<span data-ttu-id="6ef4c-105">\<執行時間 > 元素</span><span class="sxs-lookup"><span data-stu-id="6ef4c-105">\<runtime> Element</span></span>  
<span data-ttu-id="6ef4c-106">\<disableFusionUpdatesFromADManager></span><span class="sxs-lookup"><span data-stu-id="6ef4c-106">\<disableFusionUpdatesFromADManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ef4c-107">語法</span><span class="sxs-lookup"><span data-stu-id="6ef4c-107">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ef4c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6ef4c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6ef4c-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ef4c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6ef4c-110">Attributes</span></span>  
  
|<span data-ttu-id="6ef4c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6ef4c-111">Attribute</span></span>|<span data-ttu-id="6ef4c-112">描述</span><span class="sxs-lookup"><span data-stu-id="6ef4c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6ef4c-113">enabled</span><span class="sxs-lookup"><span data-stu-id="6ef4c-113">enabled</span></span>|<span data-ttu-id="6ef4c-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="6ef4c-115">指定是否停用覆寫融合設定的預設功能。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-115">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6ef4c-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="6ef4c-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="6ef4c-117">值</span><span class="sxs-lookup"><span data-stu-id="6ef4c-117">Value</span></span>|<span data-ttu-id="6ef4c-118">描述</span><span class="sxs-lookup"><span data-stu-id="6ef4c-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6ef4c-119">0</span><span class="sxs-lookup"><span data-stu-id="6ef4c-119">0</span></span>|<span data-ttu-id="6ef4c-120">請勿停用覆寫融合設定的功能。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-120">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="6ef4c-121">這是預設行為, 從 .NET Framework 4 開始。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-121">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="6ef4c-122">1</span><span class="sxs-lookup"><span data-stu-id="6ef4c-122">1</span></span>|<span data-ttu-id="6ef4c-123">停用覆寫融合設定的功能。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-123">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="6ef4c-124">這會還原成舊版 .NET Framework 的行為。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-124">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ef4c-125">子元素</span><span class="sxs-lookup"><span data-stu-id="6ef4c-125">Child Elements</span></span>  
 <span data-ttu-id="6ef4c-126">無。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ef4c-127">父項目</span><span class="sxs-lookup"><span data-stu-id="6ef4c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="6ef4c-128">項目</span><span class="sxs-lookup"><span data-stu-id="6ef4c-128">Element</span></span>|<span data-ttu-id="6ef4c-129">說明</span><span class="sxs-lookup"><span data-stu-id="6ef4c-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6ef4c-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6ef4c-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ef4c-132">備註</span><span class="sxs-lookup"><span data-stu-id="6ef4c-132">Remarks</span></span>  
 <span data-ttu-id="6ef4c-133">從 .NET Framework 4 開始, 預設行為是<xref:System.AppDomainManager>允許物件<xref:System.AppDomainSetup.ConfigurationFile%2A>使用屬性或<xref:System.AppDomainSetup.SetConfigurationBytes%2A>傳遞至您的<xref:System.AppDomainSetup>實作為物件的方法來覆寫設定在的子<xref:System.AppDomainManager>類別中的方法。<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6ef4c-133">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="6ef4c-134">針對預設應用程式域, 您所變更的設定會覆寫應用程式佈建檔所指定的設定。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-134">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="6ef4c-135">若是其他應用程式域, 則會覆寫傳遞至<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>或<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>方法的設定。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-135">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="6ef4c-136">您可以傳遞新的設定資訊, 或傳遞 null (`Nothing`在 Visual Basic 中), 以排除傳入的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-136">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="6ef4c-137">請勿將設定資訊同時<xref:System.AppDomainSetup.ConfigurationFile%2A>傳遞給屬性<xref:System.AppDomainSetup.SetConfigurationBytes%2A>和方法。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-137">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="6ef4c-138">如果您將設定資訊傳遞至兩者, 則會忽略傳遞給<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性的資訊, <xref:System.AppDomainSetup.SetConfigurationBytes%2A>因為方法會覆寫應用程式佈建檔中的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-138">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="6ef4c-139">如果<xref:System.AppDomainSetup.ConfigurationFile%2A>您使用屬性, 您可以將 null ( <xref:System.AppDomainSetup.SetConfigurationBytes%2A> `Nothing`在 Visual Basic 中) 傳遞至方法, 以排除呼叫<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>或<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>方法時所指定的任何設定位元組。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-139">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="6ef4c-140">除了設定資訊之外, 您還<xref:System.AppDomainSetup>可以在傳遞給<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>方法之執行的物件上變更下列設定: <xref:System.AppDomainSetup.ApplicationBase%2A>、 <xref:System.AppDomainSetup.ApplicationName%2A>、 <xref:System.AppDomainSetup.CachePath%2A>、、 <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>、 <xref:System.AppDomainSetup.DisallowCodeDownload%2A>、 <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> 、<xref:System.AppDomainSetup.DynamicBase%2A>、 、<xref:System.AppDomainSetup.PrivateBinPath%2A>、、和<xref:System.AppDomainSetup.ShadowCopyFiles%2A>。 <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A></span><span class="sxs-lookup"><span data-stu-id="6ef4c-140">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="6ef4c-141">除了使用`<disableFusionUpdatesFromADManager>`專案以外, 您還可以藉由建立登錄設定或設定環境變數, 來停用預設行為。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-141">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="6ef4c-142">在登錄中, 建立名為`COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework`或`HKLM\Software\Microsoft\.NETFramework`的 DWORD 值, 並將值設定為1。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-142">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="6ef4c-143">在命令列中, 將環境變數`COMPLUS_disableFusionUpdatesFromADManager`設定為1。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-143">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ef4c-144">範例</span><span class="sxs-lookup"><span data-stu-id="6ef4c-144">Example</span></span>  
 <span data-ttu-id="6ef4c-145">下列範例顯示如何使用專案停用`<disableFusionUpdatesFromADManager>`覆寫融合設定的功能。</span><span class="sxs-lookup"><span data-stu-id="6ef4c-145">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ef4c-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ef4c-146">See also</span></span>

- [<span data-ttu-id="6ef4c-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6ef4c-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6ef4c-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="6ef4c-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6ef4c-149">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="6ef4c-149">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
