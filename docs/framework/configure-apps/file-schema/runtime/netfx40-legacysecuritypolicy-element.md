---
title: <NetFx40_LegacySecurityPolicy> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5bfa5449ece1b24d4f47fe3e77e36b26bbe430c
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689840"
---
# <a name="netfx40legacysecuritypolicy-element"></a><span data-ttu-id="5d8f7-102">\<NetFx40_LegacySecurityPolicy > 項目</span><span class="sxs-lookup"><span data-stu-id="5d8f7-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="5d8f7-103">指定執行階段是否使用舊版程式碼存取安全性 (CAS) 原則。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

<span data-ttu-id="5d8f7-104">\<configuration>\\</span><span class="sxs-lookup"><span data-stu-id="5d8f7-104">\<configuration>\\</span></span>
<span data-ttu-id="5d8f7-105">\<runtime>\\</span><span class="sxs-lookup"><span data-stu-id="5d8f7-105">\<runtime>\\</span></span>
<span data-ttu-id="5d8f7-106">\<NetFx40_LegacySecurityPolicy></span><span class="sxs-lookup"><span data-stu-id="5d8f7-106">\<NetFx40_LegacySecurityPolicy></span></span>

## <a name="syntax"></a><span data-ttu-id="5d8f7-107">語法</span><span class="sxs-lookup"><span data-stu-id="5d8f7-107">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5d8f7-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5d8f7-108">Attributes and Elements</span></span>

<span data-ttu-id="5d8f7-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5d8f7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5d8f7-110">Attributes</span></span>

|<span data-ttu-id="5d8f7-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5d8f7-111">Attribute</span></span>|<span data-ttu-id="5d8f7-112">描述</span><span class="sxs-lookup"><span data-stu-id="5d8f7-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="5d8f7-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5d8f7-114">指定執行階段是否使用舊版 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="5d8f7-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="5d8f7-115">enabled Attribute</span></span>

|<span data-ttu-id="5d8f7-116">值</span><span class="sxs-lookup"><span data-stu-id="5d8f7-116">Value</span></span>|<span data-ttu-id="5d8f7-117">描述</span><span class="sxs-lookup"><span data-stu-id="5d8f7-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="5d8f7-118">執行階段不使用舊版 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="5d8f7-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="5d8f7-120">執行階段會使用舊版 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-120">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5d8f7-121">子元素</span><span class="sxs-lookup"><span data-stu-id="5d8f7-121">Child Elements</span></span>

<span data-ttu-id="5d8f7-122">無。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5d8f7-123">父項目</span><span class="sxs-lookup"><span data-stu-id="5d8f7-123">Parent Elements</span></span>

|<span data-ttu-id="5d8f7-124">項目</span><span class="sxs-lookup"><span data-stu-id="5d8f7-124">Element</span></span>|<span data-ttu-id="5d8f7-125">描述</span><span class="sxs-lookup"><span data-stu-id="5d8f7-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="5d8f7-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="5d8f7-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5d8f7-128">備註</span><span class="sxs-lookup"><span data-stu-id="5d8f7-128">Remarks</span></span>

<span data-ttu-id="5d8f7-129">在.NET Framework 3.5 版和更早版本中，CAS 原則一律是作用中。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="5d8f7-130">在.NET Framework 4 中，您必須啟用 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-130">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="5d8f7-131">特定版本的 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-131">CAS policy is version-specific.</span></span> <span data-ttu-id="5d8f7-132">在.NET Framework 4 中，必須重新指定存在於較早版本的.NET Framework 中的自訂 CA 原則。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="5d8f7-133">套用`<NetFx40_LegacySecurityPolicy>`.NET Framework 4 組件的項目不會影響[安全性透明程式碼](../../../../../docs/framework/misc/security-transparent-code.md); 透明度規則仍適用。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../../../docs/framework/misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d8f7-134">套用`<NetFx40_LegacySecurityPolicy>`項目可以原生映像所建立的組件會導致重大的效能損失[原生映像產生器 (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) ，不會安裝在[全域組件快取](../../../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="5d8f7-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../../../docs/framework/app-domains/gac.md).</span></span> <span data-ttu-id="5d8f7-135">效能降低因執行階段無法載入組件為原生映像，套用屬性時，導致其被載入，在 just-in-time 組件。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="5d8f7-136">如果您指定的目標.NET Framework 版本早於.NET Framework 4 中的專案設定 Visual Studio 專案時，就會啟用 CAS 原則，包括您為該版本所指定的任何自訂 CA 原則。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-136">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="5d8f7-137">不過，您將無法使用新的.NET Framework 4 類型和成員。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-137">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="5d8f7-138">您也可以藉由指定舊版的.NET framework [ \<Supportedruntime> > 項目](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)啟動設定結構描述中您[應用程式組態檔](../../../../../docs/framework/configure-apps/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../../../../docs/framework/configure-apps/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5d8f7-139">組態檔語法會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="5d8f7-140">提供語法和範例區段中，您應該使用的語法。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="5d8f7-141">組態檔</span><span class="sxs-lookup"><span data-stu-id="5d8f7-141">Configuration File</span></span>

<span data-ttu-id="5d8f7-142">此元素只用於應用程式組態檔中。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-142">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="5d8f7-143">範例</span><span class="sxs-lookup"><span data-stu-id="5d8f7-143">Example</span></span>

<span data-ttu-id="5d8f7-144">下列範例示範如何啟用舊版 CAS 原則，對應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d8f7-144">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5d8f7-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d8f7-145">See also</span></span>

- [<span data-ttu-id="5d8f7-146">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5d8f7-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="5d8f7-147">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5d8f7-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
