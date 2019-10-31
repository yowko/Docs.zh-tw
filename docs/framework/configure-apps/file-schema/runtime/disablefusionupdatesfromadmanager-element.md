---
title: <disableFusionUpdatesFromADManager> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: 4e7375fddaa98b45766b29d911d555f773edcafa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117449"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="e7506-102">\<disableFusionUpdatesFromADManager > 元素</span><span class="sxs-lookup"><span data-stu-id="e7506-102">\<disableFusionUpdatesFromADManager> Element</span></span>
<span data-ttu-id="e7506-103">指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。</span><span class="sxs-lookup"><span data-stu-id="e7506-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
<span data-ttu-id="e7506-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e7506-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e7506-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="e7506-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="e7506-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<disableFusionUpdatesFromADManager >**</span><span class="sxs-lookup"><span data-stu-id="e7506-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7506-107">語法</span><span class="sxs-lookup"><span data-stu-id="e7506-107">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7506-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e7506-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e7506-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e7506-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7506-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e7506-110">Attributes</span></span>  
  
|<span data-ttu-id="e7506-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e7506-111">Attribute</span></span>|<span data-ttu-id="e7506-112">描述</span><span class="sxs-lookup"><span data-stu-id="e7506-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7506-113">enabled</span><span class="sxs-lookup"><span data-stu-id="e7506-113">enabled</span></span>|<span data-ttu-id="e7506-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e7506-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="e7506-115">指定是否停用覆寫融合設定的預設功能。</span><span class="sxs-lookup"><span data-stu-id="e7506-115">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e7506-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="e7506-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="e7506-117">值</span><span class="sxs-lookup"><span data-stu-id="e7506-117">Value</span></span>|<span data-ttu-id="e7506-118">描述</span><span class="sxs-lookup"><span data-stu-id="e7506-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e7506-119">0</span><span class="sxs-lookup"><span data-stu-id="e7506-119">0</span></span>|<span data-ttu-id="e7506-120">請勿停用覆寫融合設定的功能。</span><span class="sxs-lookup"><span data-stu-id="e7506-120">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="e7506-121">這是預設行為，從 .NET Framework 4 開始。</span><span class="sxs-lookup"><span data-stu-id="e7506-121">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="e7506-122">1</span><span class="sxs-lookup"><span data-stu-id="e7506-122">1</span></span>|<span data-ttu-id="e7506-123">停用覆寫融合設定的功能。</span><span class="sxs-lookup"><span data-stu-id="e7506-123">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="e7506-124">這會還原成舊版 .NET Framework 的行為。</span><span class="sxs-lookup"><span data-stu-id="e7506-124">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7506-125">子項目</span><span class="sxs-lookup"><span data-stu-id="e7506-125">Child Elements</span></span>  
 <span data-ttu-id="e7506-126">無。</span><span class="sxs-lookup"><span data-stu-id="e7506-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7506-127">父項目</span><span class="sxs-lookup"><span data-stu-id="e7506-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e7506-128">項目</span><span class="sxs-lookup"><span data-stu-id="e7506-128">Element</span></span>|<span data-ttu-id="e7506-129">描述</span><span class="sxs-lookup"><span data-stu-id="e7506-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e7506-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e7506-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e7506-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="e7506-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7506-132">備註</span><span class="sxs-lookup"><span data-stu-id="e7506-132">Remarks</span></span>  
 <span data-ttu-id="e7506-133">從 .NET Framework 4 開始，預設行為是允許 <xref:System.AppDomainManager> 物件覆寫設定，方法是使用 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性或 <xref:System.AppDomainSetup> 物件的 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法，傳遞給您的 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> 方法的執行方式。，在 <xref:System.AppDomainManager>的子類別中。</span><span class="sxs-lookup"><span data-stu-id="e7506-133">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="e7506-134">針對預設應用程式域，您所變更的設定會覆寫應用程式佈建檔所指定的設定。</span><span class="sxs-lookup"><span data-stu-id="e7506-134">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="e7506-135">若是其他應用程式域，則會覆寫傳遞至 <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> 或 <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> 方法的設定。</span><span class="sxs-lookup"><span data-stu-id="e7506-135">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="e7506-136">您可以傳遞新的設定資訊，或傳遞 null （`Nothing` 在 Visual Basic 中），以排除傳入的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="e7506-136">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="e7506-137">請勿將設定資訊同時傳遞給 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性和 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e7506-137">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="e7506-138">如果您將設定資訊傳遞至兩者，則會忽略您傳遞給 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性的資訊，因為 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法會覆寫應用程式佈建檔中的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="e7506-138">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="e7506-139">如果您使用 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性，您可以將 Visual Basic 中的 null （`Nothing`）傳遞到 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法，以排除呼叫 <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> 或 <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> 方法時所指定的任何設定位元組。</span><span class="sxs-lookup"><span data-stu-id="e7506-139">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="e7506-140">除了設定資訊之外，您還可以在傳遞給您的 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> 方法執行的 <xref:System.AppDomainSetup> 物件上變更下列設定： <xref:System.AppDomainSetup.ApplicationBase%2A>、<xref:System.AppDomainSetup.ApplicationName%2A>、<xref:System.AppDomainSetup.CachePath%2A>、<xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>、<xref:System.AppDomainSetup.DisallowBindingRedirects%2A>、<xref:System.AppDomainSetup.DisallowCodeDownload%2A>、<xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>、<xref:System.AppDomainSetup.DynamicBase%2A>、<xref:System.AppDomainSetup.LoaderOptimization%2A>、<xref:System.AppDomainSetup.PrivateBinPath%2A>、<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>、<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>和 <xref:System.AppDomainSetup.ShadowCopyFiles%2A>。</span><span class="sxs-lookup"><span data-stu-id="e7506-140">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="e7506-141">除了使用 `<disableFusionUpdatesFromADManager>` 專案以外，您也可以藉由建立登錄設定或設定環境變數，來停用預設行為。</span><span class="sxs-lookup"><span data-stu-id="e7506-141">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="e7506-142">在登錄中，于 `HKCU\Software\Microsoft\.NETFramework` 或 `HKLM\Software\Microsoft\.NETFramework`底下建立名為 `COMPLUS_disableFusionUpdatesFromADManager` 的 DWORD 值，並將值設定為1。</span><span class="sxs-lookup"><span data-stu-id="e7506-142">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="e7506-143">在命令列中，將環境變數 `COMPLUS_disableFusionUpdatesFromADManager` 設為1。</span><span class="sxs-lookup"><span data-stu-id="e7506-143">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7506-144">範例</span><span class="sxs-lookup"><span data-stu-id="e7506-144">Example</span></span>  
 <span data-ttu-id="e7506-145">下列範例示範如何使用 `<disableFusionUpdatesFromADManager>` 專案停用覆寫融合設定的功能。</span><span class="sxs-lookup"><span data-stu-id="e7506-145">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7506-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="e7506-146">See also</span></span>

- [<span data-ttu-id="e7506-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e7506-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e7506-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="e7506-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e7506-149">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="e7506-149">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
