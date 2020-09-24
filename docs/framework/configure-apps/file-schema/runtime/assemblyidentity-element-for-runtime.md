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
ms.openlocfilehash: f3e74b05ac0fd7c57963f2aad047ba3f2d63a10a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170177"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="581f7-102">\<runtime> 的 \<assemblyIdentity> 項目</span><span class="sxs-lookup"><span data-stu-id="581f7-102">\<assemblyIdentity> Element for \<runtime></span></span>

<span data-ttu-id="581f7-103">包含元件的識別相關資訊。</span><span class="sxs-lookup"><span data-stu-id="581f7-103">Contains identifying information about the assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
## <a name="syntax"></a><span data-ttu-id="581f7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="581f7-104">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="581f7-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="581f7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="581f7-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="581f7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="581f7-107">屬性</span><span class="sxs-lookup"><span data-stu-id="581f7-107">Attributes</span></span>  
  
|<span data-ttu-id="581f7-108">屬性</span><span class="sxs-lookup"><span data-stu-id="581f7-108">Attribute</span></span>|<span data-ttu-id="581f7-109">描述</span><span class="sxs-lookup"><span data-stu-id="581f7-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="581f7-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="581f7-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="581f7-111">元件的名稱</span><span class="sxs-lookup"><span data-stu-id="581f7-111">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="581f7-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="581f7-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="581f7-113">字串，指定元件的語言和國家/地區。</span><span class="sxs-lookup"><span data-stu-id="581f7-113">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="581f7-114">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="581f7-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="581f7-115">指定元件強式名稱的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="581f7-115">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="581f7-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="581f7-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="581f7-117">其中一個值「x86」、「amd64」、「msil」或「ia64」，指定包含處理器特定程式碼之元件的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="581f7-117">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="581f7-118">這些值不會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="581f7-118">The values are not case-sensitive.</span></span> <span data-ttu-id="581f7-119">如果屬性被指派任何其他值，則 `<assemblyIdentity>` 會忽略整個元素。</span><span class="sxs-lookup"><span data-stu-id="581f7-119">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="581f7-120">請參閱 <xref:System.Reflection.ProcessorArchitecture>。</span><span class="sxs-lookup"><span data-stu-id="581f7-120">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="581f7-121">processorArchitecture 屬性</span><span class="sxs-lookup"><span data-stu-id="581f7-121">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="581f7-122">值</span><span class="sxs-lookup"><span data-stu-id="581f7-122">Value</span></span>|<span data-ttu-id="581f7-123">描述</span><span class="sxs-lookup"><span data-stu-id="581f7-123">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="581f7-124">AMD x86-64 架構。</span><span class="sxs-lookup"><span data-stu-id="581f7-124">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="581f7-125">僅限 Intel Itanium 架構。</span><span class="sxs-lookup"><span data-stu-id="581f7-125">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="581f7-126">相對於處理器和每個字組的位元而言是中性的。</span><span class="sxs-lookup"><span data-stu-id="581f7-126">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="581f7-127">32位 x86 處理器（原生或 windows on Windows (WOW) 在64位平臺上的環境。</span><span class="sxs-lookup"><span data-stu-id="581f7-127">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="581f7-128">子元素</span><span class="sxs-lookup"><span data-stu-id="581f7-128">Child Elements</span></span>  

 <span data-ttu-id="581f7-129">無。</span><span class="sxs-lookup"><span data-stu-id="581f7-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="581f7-130">父項目</span><span class="sxs-lookup"><span data-stu-id="581f7-130">Parent Elements</span></span>  
  
|<span data-ttu-id="581f7-131">項目</span><span class="sxs-lookup"><span data-stu-id="581f7-131">Element</span></span>|<span data-ttu-id="581f7-132">描述</span><span class="sxs-lookup"><span data-stu-id="581f7-132">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="581f7-133">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="581f7-133">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="581f7-134">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="581f7-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="581f7-135">封裝每一個組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="581f7-135">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="581f7-136">`<dependentAssembly>`針對每個元件使用一個元素。</span><span class="sxs-lookup"><span data-stu-id="581f7-136">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="581f7-137">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="581f7-137">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="581f7-138">備註</span><span class="sxs-lookup"><span data-stu-id="581f7-138">Remarks</span></span>  

 <span data-ttu-id="581f7-139">每個 **\<dependentAssembly>** 元素都必須有一個 **\<assemblyIdentity>** 子項目。</span><span class="sxs-lookup"><span data-stu-id="581f7-139">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="581f7-140">如果 `processorArchitecture` 屬性存在， `<assemblyIdentity>` 元素只會套用至具有對應處理器架構的元件。</span><span class="sxs-lookup"><span data-stu-id="581f7-140">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="581f7-141">如果 `processorArchitecture` 屬性不存在， `<assemblyIdentity>` 元素可以套用至具有任何處理器架構的元件。</span><span class="sxs-lookup"><span data-stu-id="581f7-141">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="581f7-142">下列範例顯示兩個元件的設定檔，其名稱會以兩個不同的雙處理器架構為目標，而且其版本未維持同步。當應用程式在 x86 平臺上執行時， `<assemblyIdentity>` 會套用第一個元素，並忽略另一個專案。</span><span class="sxs-lookup"><span data-stu-id="581f7-142">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="581f7-143">如果應用程式在 x86 或 ia64 以外的平臺上執行，則會忽略兩者。</span><span class="sxs-lookup"><span data-stu-id="581f7-143">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="581f7-144">如果設定檔包含 `<assemblyIdentity>` 沒有屬性的專案 `processorArchitecture` ，而且不包含符合平臺的元素，則 `processorArchitecture` 會使用沒有屬性的元素。</span><span class="sxs-lookup"><span data-stu-id="581f7-144">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="581f7-145">範例</span><span class="sxs-lookup"><span data-stu-id="581f7-145">Example</span></span>  

 <span data-ttu-id="581f7-146">下列範例顯示如何提供元件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="581f7-146">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="581f7-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="581f7-147">See also</span></span>

- [<span data-ttu-id="581f7-148">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="581f7-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="581f7-149">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="581f7-149">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="581f7-150">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="581f7-150">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
