---
title: <qualifyAssembly> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 581b19cf74dcb5c2d5c4a549847629503fe0b6ff
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252363"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="14c99-102">\<qualifyAssembly > 元素</span><span class="sxs-lookup"><span data-stu-id="14c99-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="14c99-103">指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="14c99-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
<span data-ttu-id="14c99-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="14c99-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="14c99-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="14c99-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="14c99-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="14c99-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="14c99-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<qualifyAssembly>**</span><span class="sxs-lookup"><span data-stu-id="14c99-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14c99-108">語法</span><span class="sxs-lookup"><span data-stu-id="14c99-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14c99-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="14c99-109">Attributes and Elements</span></span>  
 <span data-ttu-id="14c99-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="14c99-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14c99-111">屬性</span><span class="sxs-lookup"><span data-stu-id="14c99-111">Attributes</span></span>  
  
|<span data-ttu-id="14c99-112">屬性</span><span class="sxs-lookup"><span data-stu-id="14c99-112">Attribute</span></span>|<span data-ttu-id="14c99-113">說明</span><span class="sxs-lookup"><span data-stu-id="14c99-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="14c99-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="14c99-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="14c99-115">指定元件出現在程式碼中的部分名稱。</span><span class="sxs-lookup"><span data-stu-id="14c99-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="14c99-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="14c99-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="14c99-117">指定元件出現在全域組件快取中的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="14c99-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14c99-118">子元素</span><span class="sxs-lookup"><span data-stu-id="14c99-118">Child Elements</span></span>  
 <span data-ttu-id="14c99-119">無。</span><span class="sxs-lookup"><span data-stu-id="14c99-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14c99-120">父項目</span><span class="sxs-lookup"><span data-stu-id="14c99-120">Parent Elements</span></span>  
  
|<span data-ttu-id="14c99-121">項目</span><span class="sxs-lookup"><span data-stu-id="14c99-121">Element</span></span>|<span data-ttu-id="14c99-122">描述</span><span class="sxs-lookup"><span data-stu-id="14c99-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="14c99-123">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="14c99-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="14c99-124">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="14c99-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="14c99-125">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="14c99-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14c99-126">備註</span><span class="sxs-lookup"><span data-stu-id="14c99-126">Remarks</span></span>  
 <span data-ttu-id="14c99-127">使用部分元件名稱呼叫方法,會導致commonlanguageruntime只在應用程式基底目錄中尋找元件。<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="14c99-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="14c99-128">使用應用程式佈建檔中的 **\<qualifyAssembly >** 專案, 提供完整的元件資訊 (名稱、版本、公開金鑰標記和文化特性), 並導致 common language runtime 在中搜尋元件。全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="14c99-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="14c99-129">**FullName**屬性必須包含元件識別的四個欄位: 名稱、版本、公開金鑰標記和文化特性。</span><span class="sxs-lookup"><span data-stu-id="14c99-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="14c99-130">**PartialName**屬性必須部分參考元件。</span><span class="sxs-lookup"><span data-stu-id="14c99-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="14c99-131">您至少必須指定元件的文字名稱 (最常見的情況), 但您也可以包含版本、公開金鑰標記或文化特性 (或四個 (但不是全部四個) 的任何組合。</span><span class="sxs-lookup"><span data-stu-id="14c99-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="14c99-132">**PartialName**必須符合您的呼叫中所指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="14c99-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="14c99-133">例如, 您無法在配置`"math"`檔中指定做為**partialName**屬性, 並在`Assembly.Load("math, Version=3.3.3.3")`您的程式碼中呼叫。</span><span class="sxs-lookup"><span data-stu-id="14c99-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14c99-134">範例</span><span class="sxs-lookup"><span data-stu-id="14c99-134">Example</span></span>  
 <span data-ttu-id="14c99-135">下列範例會以邏輯方式將`Assembly.Load("math")`呼叫`Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`變成。</span><span class="sxs-lookup"><span data-stu-id="14c99-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="14c99-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14c99-136">See also</span></span>

- [<span data-ttu-id="14c99-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="14c99-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="14c99-138">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="14c99-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="14c99-139">[部分元件參考](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="14c99-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
