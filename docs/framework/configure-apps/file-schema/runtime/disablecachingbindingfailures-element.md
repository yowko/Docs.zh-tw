---
title: '&lt;disableCachingBindingFailures&gt;項目'
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
ms.openlocfilehash: 422888a595e8fdea01f9cb9d256830467d6822ac
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltdisablecachingbindingfailuresgt-element"></a><span data-ttu-id="190b2-102">&lt;disableCachingBindingFailures&gt;項目</span><span class="sxs-lookup"><span data-stu-id="190b2-102">&lt;disableCachingBindingFailures&gt; Element</span></span>
<span data-ttu-id="190b2-103">指定是否要停用的繫結失敗發生因為由探查找不到組件快取。</span><span class="sxs-lookup"><span data-stu-id="190b2-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
 <span data-ttu-id="190b2-104">\<設定 > 項目</span><span class="sxs-lookup"><span data-stu-id="190b2-104">\<configuration> Element</span></span>  
<span data-ttu-id="190b2-105">\<runtime > 項目</span><span class="sxs-lookup"><span data-stu-id="190b2-105">\<runtime> Element</span></span>  
<span data-ttu-id="190b2-106">\<disableCachingBindingFailures ></span><span class="sxs-lookup"><span data-stu-id="190b2-106">\<disableCachingBindingFailures></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="190b2-107">語法</span><span class="sxs-lookup"><span data-stu-id="190b2-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="190b2-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="190b2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="190b2-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="190b2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="190b2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="190b2-110">Attributes</span></span>  
  
|<span data-ttu-id="190b2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="190b2-111">Attribute</span></span>|<span data-ttu-id="190b2-112">描述</span><span class="sxs-lookup"><span data-stu-id="190b2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="190b2-113">enabled</span><span class="sxs-lookup"><span data-stu-id="190b2-113">enabled</span></span>|<span data-ttu-id="190b2-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="190b2-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="190b2-115">指定是否要停用的繫結失敗發生因為由探查找不到組件快取。</span><span class="sxs-lookup"><span data-stu-id="190b2-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="190b2-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="190b2-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="190b2-117">值</span><span class="sxs-lookup"><span data-stu-id="190b2-117">Value</span></span>|<span data-ttu-id="190b2-118">描述</span><span class="sxs-lookup"><span data-stu-id="190b2-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="190b2-119">0</span><span class="sxs-lookup"><span data-stu-id="190b2-119">0</span></span>|<span data-ttu-id="190b2-120">請勿停用的繫結失敗發生因為由探查找不到組件快取。</span><span class="sxs-lookup"><span data-stu-id="190b2-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="190b2-121">這是從.NET Framework 2.0 版的預設繫結行為。</span><span class="sxs-lookup"><span data-stu-id="190b2-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="190b2-122">1</span><span class="sxs-lookup"><span data-stu-id="190b2-122">1</span></span>|<span data-ttu-id="190b2-123">停用的繫結失敗發生因為由探查找不到組件快取。</span><span class="sxs-lookup"><span data-stu-id="190b2-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="190b2-124">這項設定會還原為.NET Framework 1.1 版的繫結行為。</span><span class="sxs-lookup"><span data-stu-id="190b2-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="190b2-125">子項目</span><span class="sxs-lookup"><span data-stu-id="190b2-125">Child Elements</span></span>  
 <span data-ttu-id="190b2-126">無。</span><span class="sxs-lookup"><span data-stu-id="190b2-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="190b2-127">父項目</span><span class="sxs-lookup"><span data-stu-id="190b2-127">Parent Elements</span></span>  
  
|<span data-ttu-id="190b2-128">項目</span><span class="sxs-lookup"><span data-stu-id="190b2-128">Element</span></span>|<span data-ttu-id="190b2-129">描述</span><span class="sxs-lookup"><span data-stu-id="190b2-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="190b2-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="190b2-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="190b2-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="190b2-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="190b2-132">備註</span><span class="sxs-lookup"><span data-stu-id="190b2-132">Remarks</span></span>  
 <span data-ttu-id="190b2-133">從.NET Framework 2.0 版開始，載入組件的預設行為是快取所有的繫結和載入失敗。</span><span class="sxs-lookup"><span data-stu-id="190b2-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="190b2-134">也就是說，如果嘗試載入組件失敗，後續要求載入相同組件會立即失敗，而不再嘗試找出組件。</span><span class="sxs-lookup"><span data-stu-id="190b2-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="190b2-135">這個項目會停用繫結失敗發生因為探查路徑中找不到組件的預設的行為。</span><span class="sxs-lookup"><span data-stu-id="190b2-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="190b2-136">這些失敗擲回<xref:System.IO.FileNotFoundException>。</span><span class="sxs-lookup"><span data-stu-id="190b2-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="190b2-137">繫結的某些並載入失敗不會影響這個項目，並一律會快取。</span><span class="sxs-lookup"><span data-stu-id="190b2-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="190b2-138">找不到組件，但無法載入，就會發生這些失敗。</span><span class="sxs-lookup"><span data-stu-id="190b2-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="190b2-139">它們會擲回<xref:System.BadImageFormatException>或<xref:System.IO.FileLoadException>。</span><span class="sxs-lookup"><span data-stu-id="190b2-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="190b2-140">下列清單包含這類失敗的一些範例。</span><span class="sxs-lookup"><span data-stu-id="190b2-140">The following list includes some examples of such failures.</span></span>  
  
-   <span data-ttu-id="190b2-141">如果您嘗試載入檔案不是有效的組件，載入組件的後續嘗試將會失敗，即使不正確的檔案取代正確的組件。</span><span class="sxs-lookup"><span data-stu-id="190b2-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
-   <span data-ttu-id="190b2-142">如果您嘗試載入組件是由檔案系統鎖定時，後續嘗試載入組件將會失敗，即使組件由檔案系統發行。</span><span class="sxs-lookup"><span data-stu-id="190b2-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
-   <span data-ttu-id="190b2-143">如果您嘗試載入的組件的一個或多個版本之探查路徑中，但是它們之間不是您所要求的特定版本，後續嘗試載入該版本將會失敗，即使正確版本會移至之探查路徑中。</span><span class="sxs-lookup"><span data-stu-id="190b2-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="190b2-144">範例</span><span class="sxs-lookup"><span data-stu-id="190b2-144">Example</span></span>  
 <span data-ttu-id="190b2-145">下列範例會示範如何停用組件繫結失敗發生因為由探查找不到組件快取。</span><span class="sxs-lookup"><span data-stu-id="190b2-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="190b2-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="190b2-146">See Also</span></span>  
 [<span data-ttu-id="190b2-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="190b2-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="190b2-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="190b2-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="190b2-149">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="190b2-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
