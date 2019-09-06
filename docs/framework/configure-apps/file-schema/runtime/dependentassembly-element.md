---
title: <dependentAssembly> 項目
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
ms.openlocfilehash: 3a0604161ed6e7c3ead4a2e518daebc8414689af
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252711"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="ae4c5-102">\<dependentAssembly > 元素</span><span class="sxs-lookup"><span data-stu-id="ae4c5-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="ae4c5-103">封裝每一個組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="ae4c5-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="ae4c5-104">針對每`dependentAssembly`個元件使用一個元素。</span><span class="sxs-lookup"><span data-stu-id="ae4c5-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
<span data-ttu-id="ae4c5-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ae4c5-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ae4c5-106">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ae4c5-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="ae4c5-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="ae4c5-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="ae4c5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dependentAssembly>**</span><span class="sxs-lookup"><span data-stu-id="ae4c5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae4c5-109">語法</span><span class="sxs-lookup"><span data-stu-id="ae4c5-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae4c5-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ae4c5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ae4c5-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ae4c5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae4c5-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ae4c5-112">Attributes</span></span>  
 <span data-ttu-id="ae4c5-113">無。</span><span class="sxs-lookup"><span data-stu-id="ae4c5-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ae4c5-114">子元素</span><span class="sxs-lookup"><span data-stu-id="ae4c5-114">Child Elements</span></span>  
  
|<span data-ttu-id="ae4c5-115">項目</span><span class="sxs-lookup"><span data-stu-id="ae4c5-115">Element</span></span>|<span data-ttu-id="ae4c5-116">描述</span><span class="sxs-lookup"><span data-stu-id="ae4c5-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="ae4c5-117">包含元件的識別資訊。</span><span class="sxs-lookup"><span data-stu-id="ae4c5-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="ae4c5-118">此元素必須包含在每個`dependentAssembly`元素中。</span><span class="sxs-lookup"><span data-stu-id="ae4c5-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="ae4c5-119">指定如果電腦上未安裝共用元件，執行時間可以在何處找到。</span><span class="sxs-lookup"><span data-stu-id="ae4c5-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="ae4c5-120">將一個組件版本重新導向至另一個版本。</span><span class="sxs-lookup"><span data-stu-id="ae4c5-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="ae4c5-121">指定執行時間是否套用此元件的發行者原則。</span><span class="sxs-lookup"><span data-stu-id="ae4c5-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae4c5-122">父項目</span><span class="sxs-lookup"><span data-stu-id="ae4c5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ae4c5-123">項目</span><span class="sxs-lookup"><span data-stu-id="ae4c5-123">Element</span></span>|<span data-ttu-id="ae4c5-124">說明</span><span class="sxs-lookup"><span data-stu-id="ae4c5-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="ae4c5-125">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="ae4c5-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="ae4c5-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ae4c5-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ae4c5-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="ae4c5-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ae4c5-128">範例</span><span class="sxs-lookup"><span data-stu-id="ae4c5-128">Example</span></span>  
 <span data-ttu-id="ae4c5-129">下列範例顯示如何封裝兩個元件的元件資訊。</span><span class="sxs-lookup"><span data-stu-id="ae4c5-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ae4c5-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae4c5-130">See also</span></span>

- [<span data-ttu-id="ae4c5-131">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ae4c5-131">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ae4c5-132">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="ae4c5-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ae4c5-133">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="ae4c5-133">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
