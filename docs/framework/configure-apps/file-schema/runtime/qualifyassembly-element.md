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
ms.openlocfilehash: 4aa90a378630c9aff74923d8e8600aed15a77a5e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663494"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="bc60d-102">\<qualifyAssembly > 元素</span><span class="sxs-lookup"><span data-stu-id="bc60d-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="bc60d-103">指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="bc60d-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
 <span data-ttu-id="bc60d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="bc60d-104">\<configuration></span></span>  
<span data-ttu-id="bc60d-105">\<執行時間 ></span><span class="sxs-lookup"><span data-stu-id="bc60d-105">\<runtime></span></span>  
<span data-ttu-id="bc60d-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="bc60d-106">\<assemblyBinding></span></span>  
<span data-ttu-id="bc60d-107">\<qualifyAssembly></span><span class="sxs-lookup"><span data-stu-id="bc60d-107">\<qualifyAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc60d-108">語法</span><span class="sxs-lookup"><span data-stu-id="bc60d-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc60d-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bc60d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bc60d-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bc60d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc60d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="bc60d-111">Attributes</span></span>  
  
|<span data-ttu-id="bc60d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="bc60d-112">Attribute</span></span>|<span data-ttu-id="bc60d-113">描述</span><span class="sxs-lookup"><span data-stu-id="bc60d-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="bc60d-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="bc60d-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="bc60d-115">指定元件出現在程式碼中的部分名稱。</span><span class="sxs-lookup"><span data-stu-id="bc60d-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="bc60d-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="bc60d-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="bc60d-117">指定元件出現在全域組件快取中的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="bc60d-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc60d-118">子元素</span><span class="sxs-lookup"><span data-stu-id="bc60d-118">Child Elements</span></span>  
 <span data-ttu-id="bc60d-119">無。</span><span class="sxs-lookup"><span data-stu-id="bc60d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc60d-120">父項目</span><span class="sxs-lookup"><span data-stu-id="bc60d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="bc60d-121">項目</span><span class="sxs-lookup"><span data-stu-id="bc60d-121">Element</span></span>|<span data-ttu-id="bc60d-122">說明</span><span class="sxs-lookup"><span data-stu-id="bc60d-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="bc60d-123">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="bc60d-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="bc60d-124">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="bc60d-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bc60d-125">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="bc60d-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc60d-126">備註</span><span class="sxs-lookup"><span data-stu-id="bc60d-126">Remarks</span></span>  
 <span data-ttu-id="bc60d-127">使用部分元件名稱呼叫方法,會導致commonlanguageruntime只在應用程式基底目錄中尋找元件。<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bc60d-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="bc60d-128">使用應用程式佈建檔中的 **\<qualifyAssembly >** 專案, 提供完整的元件資訊 (名稱、版本、公開金鑰標記和文化特性), 並導致 common language runtime 在中搜尋元件。全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="bc60d-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="bc60d-129">**FullName**屬性必須包含元件識別的四個欄位: 名稱、版本、公開金鑰標記和文化特性。</span><span class="sxs-lookup"><span data-stu-id="bc60d-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="bc60d-130">**PartialName**屬性必須部分參考元件。</span><span class="sxs-lookup"><span data-stu-id="bc60d-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="bc60d-131">您至少必須指定元件的文字名稱 (最常見的情況), 但您也可以包含版本、公開金鑰標記或文化特性 (或四個 (但不是全部四個) 的任何組合。</span><span class="sxs-lookup"><span data-stu-id="bc60d-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="bc60d-132">**PartialName**必須符合您的呼叫中所指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="bc60d-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="bc60d-133">例如, 您無法在配置`"math"`檔中指定做為**partialName**屬性, 並在`Assembly.Load("math, Version=3.3.3.3")`您的程式碼中呼叫。</span><span class="sxs-lookup"><span data-stu-id="bc60d-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc60d-134">範例</span><span class="sxs-lookup"><span data-stu-id="bc60d-134">Example</span></span>  
 <span data-ttu-id="bc60d-135">下列範例會以邏輯方式將`Assembly.Load("math")`呼叫`Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`變成。</span><span class="sxs-lookup"><span data-stu-id="bc60d-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bc60d-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc60d-136">See also</span></span>

- [<span data-ttu-id="bc60d-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="bc60d-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bc60d-138">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="bc60d-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="bc60d-139">[部分元件參考](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bc60d-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
