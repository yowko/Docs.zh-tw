---
title: <NetFx40_LegacySecurityPolicy> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
ms.openlocfilehash: d5192eb56bb8b640544bdc52a0bb9d8a5277efef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116245"
---
# <a name="netfx40_legacysecuritypolicy-element"></a><span data-ttu-id="99a8b-102">\<NetFx40_LegacySecurityPolicy > 元素</span><span class="sxs-lookup"><span data-stu-id="99a8b-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="99a8b-103">指定執行階段是否使用舊版程式碼存取安全性 (CAS) 原則。</span><span class="sxs-lookup"><span data-stu-id="99a8b-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

<span data-ttu-id="99a8b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="99a8b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="99a8b-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="99a8b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="99a8b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx40_LegacySecurityPolicy >**</span><span class="sxs-lookup"><span data-stu-id="99a8b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_LegacySecurityPolicy>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="99a8b-107">語法</span><span class="sxs-lookup"><span data-stu-id="99a8b-107">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="99a8b-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="99a8b-108">Attributes and Elements</span></span>

<span data-ttu-id="99a8b-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="99a8b-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="99a8b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="99a8b-110">Attributes</span></span>

|<span data-ttu-id="99a8b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="99a8b-111">Attribute</span></span>|<span data-ttu-id="99a8b-112">描述</span><span class="sxs-lookup"><span data-stu-id="99a8b-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="99a8b-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="99a8b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="99a8b-114">指定執行時間是否使用舊版 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="99a8b-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="99a8b-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="99a8b-115">enabled Attribute</span></span>

|<span data-ttu-id="99a8b-116">值</span><span class="sxs-lookup"><span data-stu-id="99a8b-116">Value</span></span>|<span data-ttu-id="99a8b-117">描述</span><span class="sxs-lookup"><span data-stu-id="99a8b-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="99a8b-118">執行時間不會使用舊版的 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="99a8b-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="99a8b-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="99a8b-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="99a8b-120">執行時間會使用舊版的 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="99a8b-120">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="99a8b-121">子項目</span><span class="sxs-lookup"><span data-stu-id="99a8b-121">Child Elements</span></span>

<span data-ttu-id="99a8b-122">無。</span><span class="sxs-lookup"><span data-stu-id="99a8b-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="99a8b-123">父項目</span><span class="sxs-lookup"><span data-stu-id="99a8b-123">Parent Elements</span></span>

|<span data-ttu-id="99a8b-124">項目</span><span class="sxs-lookup"><span data-stu-id="99a8b-124">Element</span></span>|<span data-ttu-id="99a8b-125">描述</span><span class="sxs-lookup"><span data-stu-id="99a8b-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="99a8b-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="99a8b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="99a8b-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="99a8b-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="99a8b-128">備註</span><span class="sxs-lookup"><span data-stu-id="99a8b-128">Remarks</span></span>

<span data-ttu-id="99a8b-129">在 .NET Framework 版本3.5 和更早版本中，CAS 原則一律會生效。</span><span class="sxs-lookup"><span data-stu-id="99a8b-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="99a8b-130">在 .NET Framework 4 中，必須啟用 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="99a8b-130">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="99a8b-131">CAS 原則是特定版本。</span><span class="sxs-lookup"><span data-stu-id="99a8b-131">CAS policy is version-specific.</span></span> <span data-ttu-id="99a8b-132">存在於舊版 .NET Framework 中的自訂 CAS 原則必須在 .NET Framework 4 中 respecified。</span><span class="sxs-lookup"><span data-stu-id="99a8b-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="99a8b-133">將 `<NetFx40_LegacySecurityPolicy>` 專案套用至 .NET Framework 4 元件，並不會影響到[安全性透明的程式碼](../../../misc/security-transparent-code.md);透明度規則仍然適用。</span><span class="sxs-lookup"><span data-stu-id="99a8b-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99a8b-134">套用 `<NetFx40_LegacySecurityPolicy>` 元素可能會對[原生映射產生器（ngen.exe）](../../../tools/ngen-exe-native-image-generator.md)所建立的原生映射元件（未安裝在[全域組件快取](../../../app-domains/gac.md)中）造成明顯的效能影響。</span><span class="sxs-lookup"><span data-stu-id="99a8b-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../app-domains/gac.md).</span></span> <span data-ttu-id="99a8b-135">效能降低的原因是，當套用屬性時，執行時間無法將元件載入為原生映射，導致其載入為即時元件。</span><span class="sxs-lookup"><span data-stu-id="99a8b-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="99a8b-136">如果您在 Visual Studio 專案的專案設定中指定早于 .NET Framework 4 的目標 .NET Framework 版本，將會啟用 CAS 原則，包括您為該版本指定的任何自訂 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="99a8b-136">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="99a8b-137">不過，您將無法使用新的 .NET Framework 4 種類型和成員。</span><span class="sxs-lookup"><span data-stu-id="99a8b-137">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="99a8b-138">您也可以在[應用程式佈建檔](../../index.md)的 [啟動設定] 架構中，使用[\<supportedruntime> > 元素](../startup/supportedruntime-element.md)，指定舊版的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="99a8b-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="99a8b-139">設定檔語法會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="99a8b-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="99a8b-140">您應該使用語法和範例小節中所提供的語法。</span><span class="sxs-lookup"><span data-stu-id="99a8b-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="99a8b-141">組態檔</span><span class="sxs-lookup"><span data-stu-id="99a8b-141">Configuration File</span></span>

<span data-ttu-id="99a8b-142">這個元素只能用在應用程式佈建檔中。</span><span class="sxs-lookup"><span data-stu-id="99a8b-142">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="99a8b-143">範例</span><span class="sxs-lookup"><span data-stu-id="99a8b-143">Example</span></span>

<span data-ttu-id="99a8b-144">下列範例顯示如何為應用程式啟用舊版 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="99a8b-144">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="99a8b-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="99a8b-145">See also</span></span>

- [<span data-ttu-id="99a8b-146">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="99a8b-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="99a8b-147">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="99a8b-147">Configuration File Schema</span></span>](../index.md)
