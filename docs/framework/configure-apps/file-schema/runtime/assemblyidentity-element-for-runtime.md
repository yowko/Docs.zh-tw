---
title: <runtime> 的 <assemblyIdentity> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154305"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="f5d69-102">\<用於運行時>的\<程式集標識>元素</span><span class="sxs-lookup"><span data-stu-id="f5d69-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="f5d69-103">包含有關程式集的標識資訊。</span><span class="sxs-lookup"><span data-stu-id="f5d69-103">Contains identifying information about the assembly.</span></span>  
  
<span data-ttu-id="f5d69-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f5d69-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f5d69-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="f5d69-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="f5d69-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<程式集綁定>**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="f5d69-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="f5d69-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<從屬裝配>**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="f5d69-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="f5d69-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<程式集標識>**</span><span class="sxs-lookup"><span data-stu-id="f5d69-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5d69-109">語法</span><span class="sxs-lookup"><span data-stu-id="f5d69-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5d69-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f5d69-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f5d69-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f5d69-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5d69-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f5d69-112">Attributes</span></span>  
  
|<span data-ttu-id="f5d69-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f5d69-113">Attribute</span></span>|<span data-ttu-id="f5d69-114">描述</span><span class="sxs-lookup"><span data-stu-id="f5d69-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="f5d69-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f5d69-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="f5d69-116">程式集的名稱</span><span class="sxs-lookup"><span data-stu-id="f5d69-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="f5d69-117">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f5d69-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f5d69-118">指定程式集的語言和國家/區域的字串。</span><span class="sxs-lookup"><span data-stu-id="f5d69-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="f5d69-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f5d69-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f5d69-120">指定程式集的強式名稱的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="f5d69-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="f5d69-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f5d69-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f5d69-122">值"x86"、"amd64"、"msil"或"ia64"的值之一，指定包含特定于處理器代碼的程式集的處理器體系結構。</span><span class="sxs-lookup"><span data-stu-id="f5d69-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="f5d69-123">這些值不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f5d69-123">The values are not case-sensitive.</span></span> <span data-ttu-id="f5d69-124">如果為該屬性分配了任何其他值，則忽略`<assemblyIdentity>`整個元素。</span><span class="sxs-lookup"><span data-stu-id="f5d69-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="f5d69-125">請參閱＜<xref:System.Reflection.ProcessorArchitecture>＞。</span><span class="sxs-lookup"><span data-stu-id="f5d69-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="f5d69-126">處理器體系結構屬性</span><span class="sxs-lookup"><span data-stu-id="f5d69-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="f5d69-127">值</span><span class="sxs-lookup"><span data-stu-id="f5d69-127">Value</span></span>|<span data-ttu-id="f5d69-128">描述</span><span class="sxs-lookup"><span data-stu-id="f5d69-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="f5d69-129">僅限 AMD x86-64 架構。</span><span class="sxs-lookup"><span data-stu-id="f5d69-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="f5d69-130">僅限英特爾 Itanium 架構。</span><span class="sxs-lookup"><span data-stu-id="f5d69-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="f5d69-131">相對於處理器和每個字組的位元而言是中性的。</span><span class="sxs-lookup"><span data-stu-id="f5d69-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="f5d69-132">32 位 x86 處理器，本機處理器或 Windows 上 Windows （WOW） 環境中的 64 位平臺。</span><span class="sxs-lookup"><span data-stu-id="f5d69-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5d69-133">子元素</span><span class="sxs-lookup"><span data-stu-id="f5d69-133">Child Elements</span></span>  
 <span data-ttu-id="f5d69-134">無。</span><span class="sxs-lookup"><span data-stu-id="f5d69-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5d69-135">父項目</span><span class="sxs-lookup"><span data-stu-id="f5d69-135">Parent Elements</span></span>  
  
|<span data-ttu-id="f5d69-136">元素</span><span class="sxs-lookup"><span data-stu-id="f5d69-136">Element</span></span>|<span data-ttu-id="f5d69-137">描述</span><span class="sxs-lookup"><span data-stu-id="f5d69-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="f5d69-138">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="f5d69-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="f5d69-139">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f5d69-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="f5d69-140">封裝每一個組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="f5d69-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="f5d69-141">為每個程式集`<dependentAssembly>`使用一個元素。</span><span class="sxs-lookup"><span data-stu-id="f5d69-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="f5d69-142">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="f5d69-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5d69-143">備註</span><span class="sxs-lookup"><span data-stu-id="f5d69-143">Remarks</span></span>  
 <span data-ttu-id="f5d69-144">每個**\<依存性程式集>** 元素必須具有一個**\<程式集標識>** 子項目。</span><span class="sxs-lookup"><span data-stu-id="f5d69-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="f5d69-145">如果存在該`processorArchitecture`屬性，則`<assemblyIdentity>`該元素僅適用于具有相應處理器體系結構的程式集。</span><span class="sxs-lookup"><span data-stu-id="f5d69-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="f5d69-146">如果屬性`processorArchitecture`不存在，則`<assemblyIdentity>`元素可以應用於具有任何處理器體系結構的程式集。</span><span class="sxs-lookup"><span data-stu-id="f5d69-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="f5d69-147">下面的示例顯示了兩個具有相同名稱的程式集的設定檔，該檔針對的是兩個不同的兩個不同的處理器體系結構，並且其版本尚未同步維護。當應用程式在 x86 平臺上執行時，將`<assemblyIdentity>`應用第一個元素，忽略另一個元素。</span><span class="sxs-lookup"><span data-stu-id="f5d69-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="f5d69-148">如果應用程式在 x86 或 ia64 以外的平臺上執行，則兩者都將被忽略。</span><span class="sxs-lookup"><span data-stu-id="f5d69-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="f5d69-149">如果設定檔包含沒有`<assemblyIdentity>``processorArchitecture`屬性的元素，並且不包含與平臺匹配的元素，則使用沒有該`processorArchitecture`屬性的元素。</span><span class="sxs-lookup"><span data-stu-id="f5d69-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5d69-150">範例</span><span class="sxs-lookup"><span data-stu-id="f5d69-150">Example</span></span>  
 <span data-ttu-id="f5d69-151">下面的示例演示如何提供有關程式集的資訊。</span><span class="sxs-lookup"><span data-stu-id="f5d69-151">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f5d69-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5d69-152">See also</span></span>

- [<span data-ttu-id="f5d69-153">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f5d69-153">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f5d69-154">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="f5d69-154">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f5d69-155">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="f5d69-155">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
