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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154305"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="18202-102">\<runtime> 的 \<assemblyIdentity> 項目</span><span class="sxs-lookup"><span data-stu-id="18202-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="18202-103">包含元件的識別資訊。</span><span class="sxs-lookup"><span data-stu-id="18202-103">Contains identifying information about the assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
## <a name="syntax"></a><span data-ttu-id="18202-104">語法</span><span class="sxs-lookup"><span data-stu-id="18202-104">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18202-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="18202-105">Attributes and Elements</span></span>  
 <span data-ttu-id="18202-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="18202-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18202-107">屬性</span><span class="sxs-lookup"><span data-stu-id="18202-107">Attributes</span></span>  
  
|<span data-ttu-id="18202-108">屬性</span><span class="sxs-lookup"><span data-stu-id="18202-108">Attribute</span></span>|<span data-ttu-id="18202-109">描述</span><span class="sxs-lookup"><span data-stu-id="18202-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="18202-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="18202-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="18202-111">元件的名稱</span><span class="sxs-lookup"><span data-stu-id="18202-111">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="18202-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="18202-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="18202-113">字串，指定元件的語言和國家/地區。</span><span class="sxs-lookup"><span data-stu-id="18202-113">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="18202-114">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="18202-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="18202-115">指定元件強式名稱的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="18202-115">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="18202-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="18202-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="18202-117">其中一個值「x86」、「amd64」、「msil」或「ia64」，指定包含處理器特定程式碼之元件的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="18202-117">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="18202-118">這些值不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="18202-118">The values are not case-sensitive.</span></span> <span data-ttu-id="18202-119">如果屬性被指派任何其他值，則 `<assemblyIdentity>` 會忽略整個元素。</span><span class="sxs-lookup"><span data-stu-id="18202-119">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="18202-120">請參閱＜<xref:System.Reflection.ProcessorArchitecture>＞。</span><span class="sxs-lookup"><span data-stu-id="18202-120">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="18202-121">processorArchitecture 屬性</span><span class="sxs-lookup"><span data-stu-id="18202-121">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="18202-122">值</span><span class="sxs-lookup"><span data-stu-id="18202-122">Value</span></span>|<span data-ttu-id="18202-123">描述</span><span class="sxs-lookup"><span data-stu-id="18202-123">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="18202-124">僅適用于 AMD x86-64 架構。</span><span class="sxs-lookup"><span data-stu-id="18202-124">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="18202-125">僅限 Intel Itanium 架構。</span><span class="sxs-lookup"><span data-stu-id="18202-125">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="18202-126">相對於處理器和每個字組的位元而言是中性的。</span><span class="sxs-lookup"><span data-stu-id="18202-126">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="18202-127">32位 x86 處理器（原生或在64位平臺上 Windows on Windows （WOW）環境中）。</span><span class="sxs-lookup"><span data-stu-id="18202-127">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18202-128">子元素</span><span class="sxs-lookup"><span data-stu-id="18202-128">Child Elements</span></span>  
 <span data-ttu-id="18202-129">無。</span><span class="sxs-lookup"><span data-stu-id="18202-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18202-130">父項目</span><span class="sxs-lookup"><span data-stu-id="18202-130">Parent Elements</span></span>  
  
|<span data-ttu-id="18202-131">元素</span><span class="sxs-lookup"><span data-stu-id="18202-131">Element</span></span>|<span data-ttu-id="18202-132">描述</span><span class="sxs-lookup"><span data-stu-id="18202-132">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="18202-133">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="18202-133">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="18202-134">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="18202-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="18202-135">封裝每一個組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="18202-135">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="18202-136">`<dependentAssembly>`針對每個元件使用一個元素。</span><span class="sxs-lookup"><span data-stu-id="18202-136">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="18202-137">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="18202-137">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18202-138">備註</span><span class="sxs-lookup"><span data-stu-id="18202-138">Remarks</span></span>  
 <span data-ttu-id="18202-139">每個 **\<dependentAssembly>** 元素都必須有一個 **\<assemblyIdentity>** 子項目。</span><span class="sxs-lookup"><span data-stu-id="18202-139">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="18202-140">如果 `processorArchitecture` 屬性存在， `<assemblyIdentity>` 元素只會套用至具有對應處理器架構的元件。</span><span class="sxs-lookup"><span data-stu-id="18202-140">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="18202-141">如果 `processorArchitecture` 屬性不存在， `<assemblyIdentity>` 元素可以套用至具有任何處理器架構的元件。</span><span class="sxs-lookup"><span data-stu-id="18202-141">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="18202-142">下列範例顯示兩個元件的設定檔，其名稱相同，其目標為兩個不同的兩個處理器架構，且其版本尚未保持同步。當應用程式在 x86 平臺上執行時， `<assemblyIdentity>` 會套用第一個專案，而另一個元素會被忽略。</span><span class="sxs-lookup"><span data-stu-id="18202-142">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="18202-143">如果應用程式是在 x86 或 ia64 以外的平臺上執行，則會忽略兩者。</span><span class="sxs-lookup"><span data-stu-id="18202-143">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="18202-144">如果設定檔包含 `<assemblyIdentity>` 沒有屬性的專案 `processorArchitecture` ，而且未包含符合平臺的元素，則會使用沒有屬性的專案 `processorArchitecture` 。</span><span class="sxs-lookup"><span data-stu-id="18202-144">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18202-145">範例</span><span class="sxs-lookup"><span data-stu-id="18202-145">Example</span></span>  
 <span data-ttu-id="18202-146">下列範例顯示如何提供元件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="18202-146">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="18202-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18202-147">See also</span></span>

- [<span data-ttu-id="18202-148">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="18202-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="18202-149">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="18202-149">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="18202-150">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="18202-150">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
