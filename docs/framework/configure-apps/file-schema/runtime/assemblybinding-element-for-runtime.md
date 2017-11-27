---
title: "&lt;assemblyBinding&gt;元素&lt;執行階段&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fdf2bc90c496c9906b5d31bad0065e01bdb47942
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltassemblybindinggt-element-for-ltruntimegt"></a><span data-ttu-id="9cd3a-102">&lt;assemblyBinding&gt;元素&lt;執行階段&gt;</span><span class="sxs-lookup"><span data-stu-id="9cd3a-102">&lt;assemblyBinding&gt; Element for &lt;runtime&gt;</span></span>
<span data-ttu-id="9cd3a-103">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
 <span data-ttu-id="9cd3a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9cd3a-104">\<configuration></span></span>  
<span data-ttu-id="9cd3a-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="9cd3a-105">\<runtime></span></span>  
<span data-ttu-id="9cd3a-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="9cd3a-106">\<assemblyBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cd3a-107">語法</span><span class="sxs-lookup"><span data-stu-id="9cd3a-107">Syntax</span></span>  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cd3a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9cd3a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9cd3a-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cd3a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9cd3a-110">Attributes</span></span>  
  
|<span data-ttu-id="9cd3a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="9cd3a-111">Attribute</span></span>|<span data-ttu-id="9cd3a-112">說明</span><span class="sxs-lookup"><span data-stu-id="9cd3a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9cd3a-113">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="9cd3a-113">**xmlns**</span></span>|<span data-ttu-id="9cd3a-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="9cd3a-115">指定組件繫結所需的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-115">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="9cd3a-116">使用字串 "urn:schemas-microsoft-com:asm.v1" 做為值。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-116">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="9cd3a-117">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="9cd3a-117">**appliesTo**</span></span>|<span data-ttu-id="9cd3a-118">指定 .NET Framework 組件重新導向適用的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-118">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="9cd3a-119">這個選擇性屬性會使用 .NET Framework 版本號碼，以表示它適用於哪一個版本。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-119">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="9cd3a-120">如果未指定 **appliesTo** 屬性，則 **\<assemblyBinding>** 項目會套用至所有的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-120">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="9cd3a-121">**AppliesTo**屬性.NET Framework 1.1 版中引進，.NET Framework 1.0 版會忽略它。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-121">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="9cd3a-122">這表示在使用 .NET Framework 1.0 版時，會套用所有 **\<assemblyBinding>** 項目，即使已指定 **appliesTo** 屬性時也是如此。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-122">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9cd3a-123">子元素</span><span class="sxs-lookup"><span data-stu-id="9cd3a-123">Child Elements</span></span>  
  
|<span data-ttu-id="9cd3a-124">項目</span><span class="sxs-lookup"><span data-stu-id="9cd3a-124">Element</span></span>|<span data-ttu-id="9cd3a-125">說明</span><span class="sxs-lookup"><span data-stu-id="9cd3a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9cd3a-126">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="9cd3a-126">\<dependentAssembly></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|<span data-ttu-id="9cd3a-127">封裝組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-127">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="9cd3a-128">使用其中一個 **\<dependentAssembly >**標記每個組件。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-128">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[<span data-ttu-id="9cd3a-129">\<probing></span><span class="sxs-lookup"><span data-stu-id="9cd3a-129">\<probing></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|<span data-ttu-id="9cd3a-130">指定載入組件時，Common Language Runtime 會搜尋的子目錄。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-130">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[<span data-ttu-id="9cd3a-131">\<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="9cd3a-131">\<publisherPolicy></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|<span data-ttu-id="9cd3a-132">指定執行階段是否套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-132">Specifies whether the runtime applies publisher policy.</span></span>|  
|[<span data-ttu-id="9cd3a-133">\<qualifyAssembly></span><span class="sxs-lookup"><span data-stu-id="9cd3a-133">\<qualifyAssembly></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|<span data-ttu-id="9cd3a-134">指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-134">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9cd3a-135">父項目</span><span class="sxs-lookup"><span data-stu-id="9cd3a-135">Parent Elements</span></span>  
  
|<span data-ttu-id="9cd3a-136">項目</span><span class="sxs-lookup"><span data-stu-id="9cd3a-136">Element</span></span>|<span data-ttu-id="9cd3a-137">描述</span><span class="sxs-lookup"><span data-stu-id="9cd3a-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9cd3a-138">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9cd3a-139">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-139">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9cd3a-140">範例</span><span class="sxs-lookup"><span data-stu-id="9cd3a-140">Example</span></span>  
 <span data-ttu-id="9cd3a-141">下列範例將示範如何將某一個組件版本重新導向至另一個版本，並提供程式碼庫。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-141">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="9cd3a-142">下列範例示範如何使用**appliesTo**重新導向.NET Framework 組件的繫結的屬性。</span><span class="sxs-lookup"><span data-stu-id="9cd3a-142">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>   
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9cd3a-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cd3a-143">See Also</span></span>  
 [<span data-ttu-id="9cd3a-144">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="9cd3a-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="9cd3a-145">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="9cd3a-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="9cd3a-146">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="9cd3a-146">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
