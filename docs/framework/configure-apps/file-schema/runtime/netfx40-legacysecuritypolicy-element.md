---
title: "&lt;NetFx40_LegacySecurityPolicy&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 636b7020a8728978ea13529382a822d99cd36f74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetfx40legacysecuritypolicygt-element"></a><span data-ttu-id="3a5c1-102">&lt;NetFx40_LegacySecurityPolicy&gt;項目</span><span class="sxs-lookup"><span data-stu-id="3a5c1-102">&lt;NetFx40_LegacySecurityPolicy&gt; Element</span></span>
<span data-ttu-id="3a5c1-103">指定執行階段是否使用舊版程式碼存取安全性 (CAS) 原則。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>  
  
 <span data-ttu-id="3a5c1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3a5c1-104">\<configuration></span></span>  
<span data-ttu-id="3a5c1-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="3a5c1-105">\<runtime></span></span>  
<span data-ttu-id="3a5c1-106">< NetFx40_LegacySecurityPolicy ></span><span class="sxs-lookup"><span data-stu-id="3a5c1-106"><NetFx40_LegacySecurityPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a5c1-107">語法</span><span class="sxs-lookup"><span data-stu-id="3a5c1-107">Syntax</span></span>  
  
```xml  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a5c1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3a5c1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3a5c1-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a5c1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3a5c1-110">Attributes</span></span>  
  
|<span data-ttu-id="3a5c1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="3a5c1-111">Attribute</span></span>|<span data-ttu-id="3a5c1-112">描述</span><span class="sxs-lookup"><span data-stu-id="3a5c1-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3a5c1-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3a5c1-114">指定執行階段是否使用舊版 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3a5c1-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="3a5c1-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3a5c1-116">值</span><span class="sxs-lookup"><span data-stu-id="3a5c1-116">Value</span></span>|<span data-ttu-id="3a5c1-117">描述</span><span class="sxs-lookup"><span data-stu-id="3a5c1-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="3a5c1-118">執行階段不會使用舊版 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="3a5c1-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="3a5c1-120">執行階段會使用舊版 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-120">The runtime uses legacy CAS policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a5c1-121">子元素</span><span class="sxs-lookup"><span data-stu-id="3a5c1-121">Child Elements</span></span>  
 <span data-ttu-id="3a5c1-122">無。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a5c1-123">父項目</span><span class="sxs-lookup"><span data-stu-id="3a5c1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3a5c1-124">項目</span><span class="sxs-lookup"><span data-stu-id="3a5c1-124">Element</span></span>|<span data-ttu-id="3a5c1-125">描述</span><span class="sxs-lookup"><span data-stu-id="3a5c1-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3a5c1-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3a5c1-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a5c1-128">備註</span><span class="sxs-lookup"><span data-stu-id="3a5c1-128">Remarks</span></span>  
 <span data-ttu-id="3a5c1-129">在.NET Framework 3.5 版和舊版的 CAS 原則一律為作用中。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="3a5c1-130">在[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，必須啟用 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], CAS policy must be enabled.</span></span>  
  
 <span data-ttu-id="3a5c1-131">特定版本的 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-131">CAS policy is version-specific.</span></span> <span data-ttu-id="3a5c1-132">必須指定自訂的 CAS 原則存在於較早版本的.NET Framework 中，在[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="3a5c1-133">套用`<NetFx40_LegacySecurityPolicy>`元素[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]組件不會影響[安全性透明程式碼](../../../../../docs/framework/misc/security-transparent-code.md); 透明度規則仍然適用。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] assembly does not affect [security-transparent code](../../../../../docs/framework/misc/security-transparent-code.md); the transparency rules still apply.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3a5c1-134">套用`<NetFx40_LegacySecurityPolicy>`項目所建立的原生映像組件可以產生顯著的效能降低[原生映像產生器 (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) ，不會安裝在[全域組件快取](../../../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="3a5c1-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../../../docs/framework/app-domains/gac.md).</span></span> <span data-ttu-id="3a5c1-135">效能降低的起因是執行階段無法套用屬性時，為原生映像載入組件，導致其被載入為以 just-in-time 組件。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a5c1-136">如果您指定的目標.NET Framework 版本早於[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]在 Visual Studio 專案的專案設定中，CAS 原則就會啟用，包括任何自訂的 CAS 原則，您指定為該版本。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-136">If you specify a target .NET Framework version that is earlier than the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="3a5c1-137">不過，您將無法使用新[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]型別和成員。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-137">However, you will not be able to use new [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] types and members.</span></span> <span data-ttu-id="3a5c1-138">您也可以藉由指定舊版的.NET Framework [ \<supportedRuntime > 項目](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)啟動設定結構描述中您[應用程式組態檔](../../../../../docs/framework/configure-apps/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../../../../docs/framework/configure-apps/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a5c1-139">組態檔語法會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="3a5c1-140">所提供的語法和範例區段中，您應該使用的語法。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="3a5c1-141">組態檔</span><span class="sxs-lookup"><span data-stu-id="3a5c1-141">Configuration File</span></span>  
 <span data-ttu-id="3a5c1-142">此項目只能用於應用程式組態檔中。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-142">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a5c1-143">範例</span><span class="sxs-lookup"><span data-stu-id="3a5c1-143">Example</span></span>  
 <span data-ttu-id="3a5c1-144">下列範例會示範如何啟用舊版 CAS 原則的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3a5c1-144">The following example shows how to enable legacy CAS policy for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a5c1-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="3a5c1-145">See Also</span></span>  
 [<span data-ttu-id="3a5c1-146">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="3a5c1-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="3a5c1-147">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="3a5c1-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
