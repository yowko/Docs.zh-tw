---
title: <disableCachingBindingFailures> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c2ed46e1d26d829fbe832e44efb40844ae7d56f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592717"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="1e60e-102">\<disableCachingBindingFailures > 項目</span><span class="sxs-lookup"><span data-stu-id="1e60e-102">\<disableCachingBindingFailures> Element</span></span>
<span data-ttu-id="1e60e-103">指定是否要停用的繫結失敗發生因為藉由探查來找不到組件快取。</span><span class="sxs-lookup"><span data-stu-id="1e60e-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
 <span data-ttu-id="1e60e-104">\<組態 > 項目</span><span class="sxs-lookup"><span data-stu-id="1e60e-104">\<configuration> Element</span></span>  
<span data-ttu-id="1e60e-105">\<執行階段 > 項目</span><span class="sxs-lookup"><span data-stu-id="1e60e-105">\<runtime> Element</span></span>  
<span data-ttu-id="1e60e-106">\<disableCachingBindingFailures></span><span class="sxs-lookup"><span data-stu-id="1e60e-106">\<disableCachingBindingFailures></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e60e-107">語法</span><span class="sxs-lookup"><span data-stu-id="1e60e-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e60e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1e60e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1e60e-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1e60e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e60e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1e60e-110">Attributes</span></span>  
  
|<span data-ttu-id="1e60e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1e60e-111">Attribute</span></span>|<span data-ttu-id="1e60e-112">描述</span><span class="sxs-lookup"><span data-stu-id="1e60e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e60e-113">enabled</span><span class="sxs-lookup"><span data-stu-id="1e60e-113">enabled</span></span>|<span data-ttu-id="1e60e-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1e60e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="1e60e-115">指定是否要停用的繫結失敗發生因為藉由探查來找不到組件快取。</span><span class="sxs-lookup"><span data-stu-id="1e60e-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1e60e-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="1e60e-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="1e60e-117">值</span><span class="sxs-lookup"><span data-stu-id="1e60e-117">Value</span></span>|<span data-ttu-id="1e60e-118">描述</span><span class="sxs-lookup"><span data-stu-id="1e60e-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e60e-119">0</span><span class="sxs-lookup"><span data-stu-id="1e60e-119">0</span></span>|<span data-ttu-id="1e60e-120">請勿停用的繫結失敗發生因為藉由探查來找不到組件快取。</span><span class="sxs-lookup"><span data-stu-id="1e60e-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="1e60e-121">這是從.NET Framework 2.0 版開始的預設繫結行為。</span><span class="sxs-lookup"><span data-stu-id="1e60e-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="1e60e-122">1</span><span class="sxs-lookup"><span data-stu-id="1e60e-122">1</span></span>|<span data-ttu-id="1e60e-123">停用的繫結失敗發生因為藉由探查來找不到組件快取。</span><span class="sxs-lookup"><span data-stu-id="1e60e-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="1e60e-124">此設定會還原為.NET Framework 1.1 版的繫結行為。</span><span class="sxs-lookup"><span data-stu-id="1e60e-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e60e-125">子元素</span><span class="sxs-lookup"><span data-stu-id="1e60e-125">Child Elements</span></span>  
 <span data-ttu-id="1e60e-126">無。</span><span class="sxs-lookup"><span data-stu-id="1e60e-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e60e-127">父項目</span><span class="sxs-lookup"><span data-stu-id="1e60e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1e60e-128">項目</span><span class="sxs-lookup"><span data-stu-id="1e60e-128">Element</span></span>|<span data-ttu-id="1e60e-129">描述</span><span class="sxs-lookup"><span data-stu-id="1e60e-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1e60e-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="1e60e-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1e60e-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="1e60e-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e60e-132">備註</span><span class="sxs-lookup"><span data-stu-id="1e60e-132">Remarks</span></span>  
 <span data-ttu-id="1e60e-133">從.NET Framework 2.0 版開始，載入組件的預設行為是快取所有的繫結和載入失敗。</span><span class="sxs-lookup"><span data-stu-id="1e60e-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="1e60e-134">也就是嘗試載入組件時，載入相同組件的後續要求會立即失敗，而不需要任何嘗試找出組件。</span><span class="sxs-lookup"><span data-stu-id="1e60e-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="1e60e-135">這個項目會停用繫結失敗發生因為探查路徑中找不到組件的預設行為。</span><span class="sxs-lookup"><span data-stu-id="1e60e-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="1e60e-136">這些失敗擲回<xref:System.IO.FileNotFoundException>。</span><span class="sxs-lookup"><span data-stu-id="1e60e-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="1e60e-137">繫結的某些載入失敗不會受到這個項目，並一律會快取。</span><span class="sxs-lookup"><span data-stu-id="1e60e-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="1e60e-138">找不到組件，但無法載入，就會發生這些失敗。</span><span class="sxs-lookup"><span data-stu-id="1e60e-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="1e60e-139">則會擲回<xref:System.BadImageFormatException>或<xref:System.IO.FileLoadException>。</span><span class="sxs-lookup"><span data-stu-id="1e60e-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="1e60e-140">下列清單包含這類失敗的一些範例。</span><span class="sxs-lookup"><span data-stu-id="1e60e-140">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="1e60e-141">如果您嘗試載入的檔案不是有效的組件，即使不正確的檔案隨即取代成正確的組件，載入組件的後續嘗試將會失敗。</span><span class="sxs-lookup"><span data-stu-id="1e60e-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="1e60e-142">如果您嘗試載入組件鎖定的檔案系統，後續的嘗試載入組件將會失敗，即使檔案系統所發行的組件。</span><span class="sxs-lookup"><span data-stu-id="1e60e-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="1e60e-143">如果您嘗試載入的組件的一或多個版本是在探查路徑中，但您所要求的特定版本不是在它們之間，後續嘗試載入該版本將會失敗，即使正確的版本會移到探查路徑。</span><span class="sxs-lookup"><span data-stu-id="1e60e-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e60e-144">範例</span><span class="sxs-lookup"><span data-stu-id="1e60e-144">Example</span></span>  
 <span data-ttu-id="1e60e-145">下列範例示範如何停用快取發生因為藉由探查來找不到組件的組件繫結失敗。</span><span class="sxs-lookup"><span data-stu-id="1e60e-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e60e-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e60e-146">See also</span></span>

- [<span data-ttu-id="1e60e-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1e60e-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="1e60e-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="1e60e-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="1e60e-149">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="1e60e-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
