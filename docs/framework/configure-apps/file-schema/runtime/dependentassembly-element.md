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
ms.openlocfilehash: 2de8c752867d00708173d11d1851f415a2e8518d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154201"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="6f706-102">\<dependentAssembly> 項目</span><span class="sxs-lookup"><span data-stu-id="6f706-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="6f706-103">封裝每一個組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="6f706-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="6f706-104">`dependentAssembly`針對每個元件使用一個元素。</span><span class="sxs-lookup"><span data-stu-id="6f706-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="6f706-105">語法</span><span class="sxs-lookup"><span data-stu-id="6f706-105">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f706-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6f706-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6f706-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6f706-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f706-108">屬性</span><span class="sxs-lookup"><span data-stu-id="6f706-108">Attributes</span></span>  
 <span data-ttu-id="6f706-109">無。</span><span class="sxs-lookup"><span data-stu-id="6f706-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f706-110">子元素</span><span class="sxs-lookup"><span data-stu-id="6f706-110">Child Elements</span></span>  
  
|<span data-ttu-id="6f706-111">元素</span><span class="sxs-lookup"><span data-stu-id="6f706-111">Element</span></span>|<span data-ttu-id="6f706-112">描述</span><span class="sxs-lookup"><span data-stu-id="6f706-112">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="6f706-113">包含元件的識別資訊。</span><span class="sxs-lookup"><span data-stu-id="6f706-113">Contains identifying information about the assembly.</span></span> <span data-ttu-id="6f706-114">此元素必須包含在每個 `dependentAssembly` 元素中。</span><span class="sxs-lookup"><span data-stu-id="6f706-114">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="6f706-115">指定如果電腦上未安裝共用元件，執行時間可以在何處找到。</span><span class="sxs-lookup"><span data-stu-id="6f706-115">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="6f706-116">將一個組件版本重新導向至另一個版本。</span><span class="sxs-lookup"><span data-stu-id="6f706-116">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="6f706-117">指定執行時間是否套用此元件的發行者原則。</span><span class="sxs-lookup"><span data-stu-id="6f706-117">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f706-118">父項目</span><span class="sxs-lookup"><span data-stu-id="6f706-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6f706-119">元素</span><span class="sxs-lookup"><span data-stu-id="6f706-119">Element</span></span>|<span data-ttu-id="6f706-120">描述</span><span class="sxs-lookup"><span data-stu-id="6f706-120">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="6f706-121">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="6f706-121">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="6f706-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6f706-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6f706-123">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="6f706-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6f706-124">範例</span><span class="sxs-lookup"><span data-stu-id="6f706-124">Example</span></span>  
 <span data-ttu-id="6f706-125">下列範例顯示如何封裝兩個元件的元件資訊。</span><span class="sxs-lookup"><span data-stu-id="6f706-125">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f706-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f706-126">See also</span></span>

- [<span data-ttu-id="6f706-127">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="6f706-127">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6f706-128">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="6f706-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6f706-129">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="6f706-129">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
