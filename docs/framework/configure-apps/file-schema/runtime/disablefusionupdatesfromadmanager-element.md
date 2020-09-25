---
title: <disableFusionUpdatesFromADManager> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: c3971379b358ae16fc463df2b8d6288cf8881391
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205031"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="f83ce-102">\<disableFusionUpdatesFromADManager> 項目</span><span class="sxs-lookup"><span data-stu-id="f83ce-102">\<disableFusionUpdatesFromADManager> Element</span></span>

<span data-ttu-id="f83ce-103">指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。</span><span class="sxs-lookup"><span data-stu-id="f83ce-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a><span data-ttu-id="f83ce-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f83ce-104">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f83ce-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f83ce-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f83ce-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f83ce-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f83ce-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f83ce-107">Attributes</span></span>  
  
|<span data-ttu-id="f83ce-108">屬性</span><span class="sxs-lookup"><span data-stu-id="f83ce-108">Attribute</span></span>|<span data-ttu-id="f83ce-109">描述</span><span class="sxs-lookup"><span data-stu-id="f83ce-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f83ce-110">已啟用</span><span class="sxs-lookup"><span data-stu-id="f83ce-110">enabled</span></span>|<span data-ttu-id="f83ce-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f83ce-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="f83ce-112">指定是否停用覆寫融合設定的預設功能。</span><span class="sxs-lookup"><span data-stu-id="f83ce-112">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f83ce-113">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="f83ce-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="f83ce-114">值</span><span class="sxs-lookup"><span data-stu-id="f83ce-114">Value</span></span>|<span data-ttu-id="f83ce-115">描述</span><span class="sxs-lookup"><span data-stu-id="f83ce-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f83ce-116">0</span><span class="sxs-lookup"><span data-stu-id="f83ce-116">0</span></span>|<span data-ttu-id="f83ce-117">請勿停用覆寫融合設定的功能。</span><span class="sxs-lookup"><span data-stu-id="f83ce-117">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="f83ce-118">這是預設行為，從 .NET Framework 4 開始。</span><span class="sxs-lookup"><span data-stu-id="f83ce-118">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="f83ce-119">1</span><span class="sxs-lookup"><span data-stu-id="f83ce-119">1</span></span>|<span data-ttu-id="f83ce-120">停用覆寫融合設定的功能。</span><span class="sxs-lookup"><span data-stu-id="f83ce-120">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="f83ce-121">這會還原為舊版 .NET Framework 的行為。</span><span class="sxs-lookup"><span data-stu-id="f83ce-121">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f83ce-122">子元素</span><span class="sxs-lookup"><span data-stu-id="f83ce-122">Child Elements</span></span>  

 <span data-ttu-id="f83ce-123">無。</span><span class="sxs-lookup"><span data-stu-id="f83ce-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f83ce-124">父項目</span><span class="sxs-lookup"><span data-stu-id="f83ce-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f83ce-125">項目</span><span class="sxs-lookup"><span data-stu-id="f83ce-125">Element</span></span>|<span data-ttu-id="f83ce-126">描述</span><span class="sxs-lookup"><span data-stu-id="f83ce-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f83ce-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f83ce-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f83ce-128">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="f83ce-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f83ce-129">備註</span><span class="sxs-lookup"><span data-stu-id="f83ce-129">Remarks</span></span>  

 <span data-ttu-id="f83ce-130">從 .NET Framework 4 開始，預設行為是允許 <xref:System.AppDomainManager> 物件覆寫設定，方法是使用 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性或 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 物件的方法，該 <xref:System.AppDomainSetup> 物件會傳遞至您的子 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> 類別中的方法執行 <xref:System.AppDomainManager> 。</span><span class="sxs-lookup"><span data-stu-id="f83ce-130">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="f83ce-131">針對預設的應用程式域，您所變更的設定會覆寫應用程式佈建檔所指定的設定。</span><span class="sxs-lookup"><span data-stu-id="f83ce-131">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="f83ce-132">針對其他應用程式域，它們會覆寫傳遞給 <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> 或方法的設定 <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f83ce-132">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="f83ce-133">您可以傳遞新的設定資訊，或 `Nothing` 在 Visual Basic) 中傳遞 null (，以消除傳入的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="f83ce-133">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="f83ce-134">請勿將設定資訊傳遞給 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性和 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f83ce-134">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="f83ce-135">如果您將設定資訊傳遞至兩者，則會忽略您傳遞給屬性的資訊 <xref:System.AppDomainSetup.ConfigurationFile%2A> ，因為 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法會覆寫應用程式佈建檔中的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="f83ce-135">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="f83ce-136">如果您使用 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性，則可以將 Visual Basic) 中的 null (傳遞 `Nothing` 給 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法，以排除呼叫或方法時所指定的任何設定位元組 <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f83ce-136">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="f83ce-137">除了設定資訊之外，您還可以變更 <xref:System.AppDomainSetup> 傳遞給方法之實值的物件上的下列設定 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> ：、、、、、、、、、、、 <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> 和 <xref:System.AppDomainSetup.ShadowCopyFiles%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f83ce-137">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="f83ce-138">除了使用專案以外 `<disableFusionUpdatesFromADManager>` ，您也可以藉由建立登錄設定或設定環境變數來停用預設行為。</span><span class="sxs-lookup"><span data-stu-id="f83ce-138">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="f83ce-139">在登錄中，建立名為或的 DWORD 值， `COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework` `HKLM\Software\Microsoft\.NETFramework` 並將值設定為1。</span><span class="sxs-lookup"><span data-stu-id="f83ce-139">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="f83ce-140">在命令列中，將環境變數設定 `COMPLUS_disableFusionUpdatesFromADManager` 為1。</span><span class="sxs-lookup"><span data-stu-id="f83ce-140">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f83ce-141">範例</span><span class="sxs-lookup"><span data-stu-id="f83ce-141">Example</span></span>  

 <span data-ttu-id="f83ce-142">下列範例示範如何使用元素停用覆寫融合設定的功能 `<disableFusionUpdatesFromADManager>` 。</span><span class="sxs-lookup"><span data-stu-id="f83ce-142">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f83ce-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f83ce-143">See also</span></span>

- [<span data-ttu-id="f83ce-144">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f83ce-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f83ce-145">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="f83ce-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f83ce-146">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="f83ce-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
