---
title: "&lt;assemblyIdentity&gt;元素&lt;執行階段&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0dadf0e07f5e3a9f9152ae7cd57c62721402bff0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a><span data-ttu-id="27055-102">&lt;assemblyIdentity&gt;元素&lt;執行階段&gt;</span><span class="sxs-lookup"><span data-stu-id="27055-102">&lt;assemblyIdentity&gt; Element for &lt;runtime&gt;</span></span>
<span data-ttu-id="27055-103">包含有關組件的識別資訊。</span><span class="sxs-lookup"><span data-stu-id="27055-103">Contains identifying information about the assembly.</span></span>  
  
 <span data-ttu-id="27055-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="27055-104">\<configuration></span></span>  
<span data-ttu-id="27055-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="27055-105">\<runtime></span></span>  
<span data-ttu-id="27055-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="27055-106">\<assemblyBinding></span></span>  
<span data-ttu-id="27055-107">\<y ></span><span class="sxs-lookup"><span data-stu-id="27055-107">\<dependentAssembly></span></span>  
<span data-ttu-id="27055-108">\<assemblyIdentity ></span><span class="sxs-lookup"><span data-stu-id="27055-108">\<assemblyIdentity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27055-109">語法</span><span class="sxs-lookup"><span data-stu-id="27055-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27055-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="27055-110">Attributes and Elements</span></span>  
 <span data-ttu-id="27055-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="27055-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27055-112">屬性</span><span class="sxs-lookup"><span data-stu-id="27055-112">Attributes</span></span>  
  
|<span data-ttu-id="27055-113">屬性</span><span class="sxs-lookup"><span data-stu-id="27055-113">Attribute</span></span>|<span data-ttu-id="27055-114">描述</span><span class="sxs-lookup"><span data-stu-id="27055-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="27055-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="27055-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="27055-116">組件名稱</span><span class="sxs-lookup"><span data-stu-id="27055-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="27055-117">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="27055-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="27055-118">字串，指定的語言和國家/地區的組件。</span><span class="sxs-lookup"><span data-stu-id="27055-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="27055-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="27055-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="27055-120">指定組件的強式名稱的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="27055-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="27055-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="27055-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="27055-122">其中一個值"x86"、"amd64"、"msil"或"ia64"，指定包含處理器特定程式碼組件的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="27055-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="27055-123">值不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="27055-123">The values are not case-sensitive.</span></span> <span data-ttu-id="27055-124">如果屬性被指派任何其他值，將整個`<assemblyIdentity>`項目會被忽略。</span><span class="sxs-lookup"><span data-stu-id="27055-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="27055-125">請參閱 <xref:System.Reflection.ProcessorArchitecture>。</span><span class="sxs-lookup"><span data-stu-id="27055-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="27055-126">processorArchitecture 屬性</span><span class="sxs-lookup"><span data-stu-id="27055-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="27055-127">值</span><span class="sxs-lookup"><span data-stu-id="27055-127">Value</span></span>|<span data-ttu-id="27055-128">描述</span><span class="sxs-lookup"><span data-stu-id="27055-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="27055-129">將 64 位元的 AMD 處理器只。</span><span class="sxs-lookup"><span data-stu-id="27055-129">A 64-bit AMD processor only.</span></span>|  
|`ia64`|<span data-ttu-id="27055-130">64 位元 Intel 處理器只。</span><span class="sxs-lookup"><span data-stu-id="27055-130">A 64-bit Intel processor only.</span></span>|  
|`msil`|<span data-ttu-id="27055-131">處理器和每個字組的位元中性</span><span class="sxs-lookup"><span data-stu-id="27055-131">Neutral with respect to processor and bits-per-word</span></span>|  
|`x86`|<span data-ttu-id="27055-132">32 位元 Intel 處理器，其中一個原生或 Windows on Windows (WOW) 的 64 位元平台上的環境中。</span><span class="sxs-lookup"><span data-stu-id="27055-132">A 32-bit Intel processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27055-133">子元素</span><span class="sxs-lookup"><span data-stu-id="27055-133">Child Elements</span></span>  
 <span data-ttu-id="27055-134">無。</span><span class="sxs-lookup"><span data-stu-id="27055-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27055-135">父項目</span><span class="sxs-lookup"><span data-stu-id="27055-135">Parent Elements</span></span>  
  
|<span data-ttu-id="27055-136">項目</span><span class="sxs-lookup"><span data-stu-id="27055-136">Element</span></span>|<span data-ttu-id="27055-137">描述</span><span class="sxs-lookup"><span data-stu-id="27055-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="27055-138">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="27055-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="27055-139">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="27055-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="27055-140">封裝每一個組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="27055-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="27055-141">使用其中一個`<dependentAssembly>`每個組件的項目。</span><span class="sxs-lookup"><span data-stu-id="27055-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="27055-142">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="27055-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27055-143">備註</span><span class="sxs-lookup"><span data-stu-id="27055-143">Remarks</span></span>  
 <span data-ttu-id="27055-144">每個 **\<dependentAssembly >**項目必須有一個 **\<assemblyIdentity >**子項目。</span><span class="sxs-lookup"><span data-stu-id="27055-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="27055-145">如果`processorArchitecture`屬性已存在，`<assemblyIdentity>`項目只適用於具有對應的處理器架構的組件。</span><span class="sxs-lookup"><span data-stu-id="27055-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="27055-146">如果`processorArchitecture`屬性不存在，`<assemblyIdentity>`項目可以套用至任何處理器架構的組件。</span><span class="sxs-lookup"><span data-stu-id="27055-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="27055-147">下列範例顯示兩個組件具有相同名稱以兩個不同的兩個處理器架構，以及其版本已受到維護的同步處理不組態檔。當應用程式執行 x86 平台的第一個`<assemblyIdentity>`元素會套用，而其他都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="27055-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="27055-148">如果在非 x86 或 ia64 平台上，執行應用程式，兩者都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="27055-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"   
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"   
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"   
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="27055-149">如果組態檔包含`<assemblyIdentity>`項目不含`processorArchitecture`屬性，而且不包含符合的平台的項目不含的項目`processorArchitecture`屬性使用。</span><span class="sxs-lookup"><span data-stu-id="27055-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27055-150">範例</span><span class="sxs-lookup"><span data-stu-id="27055-150">Example</span></span>  
 <span data-ttu-id="27055-151">下列範例會示範如何提供組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="27055-151">The following example shows how to provide information about an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27055-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="27055-152">See Also</span></span>  
 [<span data-ttu-id="27055-153">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="27055-153">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="27055-154">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="27055-154">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="27055-155">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="27055-155">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
