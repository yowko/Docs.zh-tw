---
title: '&lt;assemblyIdentity&gt;項目&lt;執行階段&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2d82aed13e185b2957a22f097b60e12265a5f190
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128202"
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a><span data-ttu-id="5ea4e-102">&lt;assemblyIdentity&gt;項目&lt;執行階段&gt;</span><span class="sxs-lookup"><span data-stu-id="5ea4e-102">&lt;assemblyIdentity&gt; Element for &lt;runtime&gt;</span></span>
<span data-ttu-id="5ea4e-103">包含組件的識別資訊。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-103">Contains identifying information about the assembly.</span></span>  
  
 <span data-ttu-id="5ea4e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5ea4e-104">\<configuration></span></span>  
<span data-ttu-id="5ea4e-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="5ea4e-105">\<runtime></span></span>  
<span data-ttu-id="5ea4e-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="5ea4e-106">\<assemblyBinding></span></span>  
<span data-ttu-id="5ea4e-107">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="5ea4e-107">\<dependentAssembly></span></span>  
<span data-ttu-id="5ea4e-108">\<組件識別 ></span><span class="sxs-lookup"><span data-stu-id="5ea4e-108">\<assemblyIdentity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ea4e-109">語法</span><span class="sxs-lookup"><span data-stu-id="5ea4e-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ea4e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5ea4e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ea4e-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ea4e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="5ea4e-112">Attributes</span></span>  
  
|<span data-ttu-id="5ea4e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="5ea4e-113">Attribute</span></span>|<span data-ttu-id="5ea4e-114">描述</span><span class="sxs-lookup"><span data-stu-id="5ea4e-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="5ea4e-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="5ea4e-116">組件名稱</span><span class="sxs-lookup"><span data-stu-id="5ea4e-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="5ea4e-117">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5ea4e-118">字串，指定的語言和國家/地區的組件。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="5ea4e-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5ea4e-120">十六進位值，指定組件的強式名稱。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="5ea4e-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5ea4e-122">其中一個值"x86"、"amd64"、"msil"或"ia64"，指定包含處理器特定程式碼組件的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="5ea4e-123">值不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-123">The values are not case-sensitive.</span></span> <span data-ttu-id="5ea4e-124">如果屬性被指派任何其他值，整個`<assemblyIdentity>`項目會被忽略。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="5ea4e-125">請參閱 <xref:System.Reflection.ProcessorArchitecture>。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="5ea4e-126">processorArchitecture 屬性</span><span class="sxs-lookup"><span data-stu-id="5ea4e-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="5ea4e-127">值</span><span class="sxs-lookup"><span data-stu-id="5ea4e-127">Value</span></span>|<span data-ttu-id="5ea4e-128">描述</span><span class="sxs-lookup"><span data-stu-id="5ea4e-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="5ea4e-129">AMD x86 64 架構。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="5ea4e-130">Intel Itanium 架構。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="5ea4e-131">相對於處理器和每個字組的位元的中性。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="5ea4e-132">32 位元 x86 處理器、 原生或 Windows 上的 64 位元平台上的 Windows (WOW) 環境中。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ea4e-133">子元素</span><span class="sxs-lookup"><span data-stu-id="5ea4e-133">Child Elements</span></span>  
 <span data-ttu-id="5ea4e-134">無。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ea4e-135">父項目</span><span class="sxs-lookup"><span data-stu-id="5ea4e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="5ea4e-136">項目</span><span class="sxs-lookup"><span data-stu-id="5ea4e-136">Element</span></span>|<span data-ttu-id="5ea4e-137">描述</span><span class="sxs-lookup"><span data-stu-id="5ea4e-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="5ea4e-138">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="5ea4e-139">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="5ea4e-140">封裝每一個組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="5ea4e-141">使用其中一個`<dependentAssembly>`每個組件的項目。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="5ea4e-142">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ea4e-143">備註</span><span class="sxs-lookup"><span data-stu-id="5ea4e-143">Remarks</span></span>  
 <span data-ttu-id="5ea4e-144">每隔 **\<dependentAssembly >** 項目必須有一個**\<組件識別 >** 子項目。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="5ea4e-145">如果`processorArchitecture`屬性，就`<assemblyIdentity>`項目僅適用於具有對應的處理器架構的組件。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="5ea4e-146">如果`processorArchitecture`屬性不存在，`<assemblyIdentity>`項目可以套用至組件的任何處理器架構。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="5ea4e-147">下列範例顯示兩個組件具有相同名稱的目標兩個不同的兩個處理器架構，和其版本已不受到維護的同步處理組態檔。時，應用程式執行 x86 平台的第一個`<assemblyIdentity>`適用於項目，且另會被忽略。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="5ea4e-148">如果應用程式執行 x86 或 ia64 以外的平台上，兩者都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="5ea4e-149">如果組態檔包含`<assemblyIdentity>`含的項目`processorArchitecture`屬性，而且不包含符合的平台，而不需要的項目之項目`processorArchitecture`屬性使用。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ea4e-150">範例</span><span class="sxs-lookup"><span data-stu-id="5ea4e-150">Example</span></span>  
 <span data-ttu-id="5ea4e-151">下列範例示範如何提供組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5ea4e-151">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ea4e-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ea4e-152">See Also</span></span>  
 [<span data-ttu-id="5ea4e-153">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5ea4e-153">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5ea4e-154">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5ea4e-154">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="5ea4e-155">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="5ea4e-155">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
