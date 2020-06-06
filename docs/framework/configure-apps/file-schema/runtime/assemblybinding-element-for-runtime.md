---
title: <runtime> 的 <assemblyBinding> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154318"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="7f65b-102">\<runtime> 的 \<assemblyBinding> 項目</span><span class="sxs-lookup"><span data-stu-id="7f65b-102">\<assemblyBinding> Element for \<runtime></span></span>
<span data-ttu-id="7f65b-103">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="7f65b-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="7f65b-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f65b-104">Syntax</span></span>  
  
```xml  
      <assemblyBinding
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f65b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7f65b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7f65b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7f65b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f65b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="7f65b-107">Attributes</span></span>  
  
|<span data-ttu-id="7f65b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7f65b-108">Attribute</span></span>|<span data-ttu-id="7f65b-109">描述</span><span class="sxs-lookup"><span data-stu-id="7f65b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f65b-110">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="7f65b-110">**xmlns**</span></span>|<span data-ttu-id="7f65b-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="7f65b-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="7f65b-112">指定組件繫結所需的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="7f65b-112">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="7f65b-113">使用字串 "urn:schemas-microsoft-com:asm.v1" 做為值。</span><span class="sxs-lookup"><span data-stu-id="7f65b-113">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="7f65b-114">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="7f65b-114">**appliesTo**</span></span>|<span data-ttu-id="7f65b-115">指定 .NET Framework 組件重新導向適用的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="7f65b-115">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="7f65b-116">這個選擇性屬性會使用 .NET Framework 版本號碼，以表示它適用於哪一個版本。</span><span class="sxs-lookup"><span data-stu-id="7f65b-116">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="7f65b-117">如果未指定**appliesTo**屬性，元素會 **\<assemblyBinding>** 套用至 .NET Framework 的所有版本。</span><span class="sxs-lookup"><span data-stu-id="7f65b-117">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="7f65b-118">**AppliesTo**屬性是在 .NET Framework 版本1.1 中引進。.NET Framework 版本1.0 會忽略它。</span><span class="sxs-lookup"><span data-stu-id="7f65b-118">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="7f65b-119">這表示 **\<assemblyBinding>** 使用 .NET Framework 版本1.0 時，即使指定了**appliesTo**屬性，還是會套用所有元素。</span><span class="sxs-lookup"><span data-stu-id="7f65b-119">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f65b-120">子元素</span><span class="sxs-lookup"><span data-stu-id="7f65b-120">Child Elements</span></span>  
  
|<span data-ttu-id="7f65b-121">元素</span><span class="sxs-lookup"><span data-stu-id="7f65b-121">Element</span></span>|<span data-ttu-id="7f65b-122">描述</span><span class="sxs-lookup"><span data-stu-id="7f65b-122">Description</span></span>|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|<span data-ttu-id="7f65b-123">封裝組件的繫結原則和組件位置。</span><span class="sxs-lookup"><span data-stu-id="7f65b-123">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="7f65b-124">**\<dependentAssembly>** 針對每個元件使用一個標記。</span><span class="sxs-lookup"><span data-stu-id="7f65b-124">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[\<probing>](probing-element.md)|<span data-ttu-id="7f65b-125">指定載入組件時，Common Language Runtime 會搜尋的子目錄。</span><span class="sxs-lookup"><span data-stu-id="7f65b-125">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[\<publisherPolicy>](publisherpolicy-element.md)|<span data-ttu-id="7f65b-126">指定執行階段是否套用發行者原則。</span><span class="sxs-lookup"><span data-stu-id="7f65b-126">Specifies whether the runtime applies publisher policy.</span></span>|  
|[\<qualifyAssembly>](qualifyassembly-element.md)|<span data-ttu-id="7f65b-127">指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="7f65b-127">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f65b-128">父項目</span><span class="sxs-lookup"><span data-stu-id="7f65b-128">Parent Elements</span></span>  
  
|<span data-ttu-id="7f65b-129">元素</span><span class="sxs-lookup"><span data-stu-id="7f65b-129">Element</span></span>|<span data-ttu-id="7f65b-130">描述</span><span class="sxs-lookup"><span data-stu-id="7f65b-130">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7f65b-131">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="7f65b-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7f65b-132">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="7f65b-132">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7f65b-133">範例</span><span class="sxs-lookup"><span data-stu-id="7f65b-133">Example</span></span>  
 <span data-ttu-id="7f65b-134">下列範例將示範如何將某一個組件版本重新導向至另一個版本，並提供程式碼庫。</span><span class="sxs-lookup"><span data-stu-id="7f65b-134">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
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
  
 <span data-ttu-id="7f65b-135">下列範例顯示如何使用**appliesTo**屬性重新導向 .NET Framework 元件的系結。</span><span class="sxs-lookup"><span data-stu-id="7f65b-135">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f65b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f65b-136">See also</span></span>

- [<span data-ttu-id="7f65b-137">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="7f65b-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7f65b-138">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="7f65b-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7f65b-139">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="7f65b-139">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
