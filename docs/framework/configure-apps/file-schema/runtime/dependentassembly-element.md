---
title: '&lt;dependentAssembly&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2cf4d9940873c04ee6f0ab2d378a3d1253be4ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729193"
---
# <a name="ltdependentassemblygt-element"></a><span data-ttu-id="146e6-102">&lt;dependentAssembly&gt;項目</span><span class="sxs-lookup"><span data-stu-id="146e6-102">&lt;dependentAssembly&gt; Element</span></span>
<span data-ttu-id="146e6-103">封裝每一個組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="146e6-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="146e6-104">使用其中一個`dependentAssembly`每個組件的項目。</span><span class="sxs-lookup"><span data-stu-id="146e6-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
 <span data-ttu-id="146e6-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="146e6-105">\<configuration></span></span>  
<span data-ttu-id="146e6-106">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="146e6-106">\<runtime></span></span>  
<span data-ttu-id="146e6-107">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="146e6-107">\<assemblyBinding></span></span>  
<span data-ttu-id="146e6-108">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="146e6-108">\<dependentAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="146e6-109">語法</span><span class="sxs-lookup"><span data-stu-id="146e6-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="146e6-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="146e6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="146e6-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="146e6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="146e6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="146e6-112">Attributes</span></span>  
 <span data-ttu-id="146e6-113">無。</span><span class="sxs-lookup"><span data-stu-id="146e6-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="146e6-114">子元素</span><span class="sxs-lookup"><span data-stu-id="146e6-114">Child Elements</span></span>  
  
|<span data-ttu-id="146e6-115">項目</span><span class="sxs-lookup"><span data-stu-id="146e6-115">Element</span></span>|<span data-ttu-id="146e6-116">描述</span><span class="sxs-lookup"><span data-stu-id="146e6-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="146e6-117">包含組件的識別資訊。</span><span class="sxs-lookup"><span data-stu-id="146e6-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="146e6-118">這個項目必須包含在每個`dependentAssembly`項目。</span><span class="sxs-lookup"><span data-stu-id="146e6-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="146e6-119">指定執行階段可以找到共用的組件如果它不會安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="146e6-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="146e6-120">將一個組件版本重新導向至另一個版本。</span><span class="sxs-lookup"><span data-stu-id="146e6-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="146e6-121">指定執行階段是否套用發行者原則，這個組件。</span><span class="sxs-lookup"><span data-stu-id="146e6-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="146e6-122">父項目</span><span class="sxs-lookup"><span data-stu-id="146e6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="146e6-123">項目</span><span class="sxs-lookup"><span data-stu-id="146e6-123">Element</span></span>|<span data-ttu-id="146e6-124">描述</span><span class="sxs-lookup"><span data-stu-id="146e6-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="146e6-125">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="146e6-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="146e6-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="146e6-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="146e6-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="146e6-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="146e6-128">範例</span><span class="sxs-lookup"><span data-stu-id="146e6-128">Example</span></span>  
 <span data-ttu-id="146e6-129">下列範例示範如何將封裝的兩個組件的組件資訊。</span><span class="sxs-lookup"><span data-stu-id="146e6-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="146e6-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="146e6-130">See also</span></span>
- [<span data-ttu-id="146e6-131">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="146e6-131">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="146e6-132">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="146e6-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="146e6-133">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="146e6-133">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
