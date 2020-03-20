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
ms.openlocfilehash: 74e83900c68ab4b3fe01beb3f97657b0140d78ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153915"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="c889b-102">\<限定裝配>元素</span><span class="sxs-lookup"><span data-stu-id="c889b-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="c889b-103">指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="c889b-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
<span data-ttu-id="c889b-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c889b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c889b-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="c889b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="c889b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<程式集綁定>**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="c889b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="c889b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<符合條件>**</span><span class="sxs-lookup"><span data-stu-id="c889b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c889b-108">語法</span><span class="sxs-lookup"><span data-stu-id="c889b-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c889b-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c889b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c889b-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c889b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c889b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c889b-111">Attributes</span></span>  
  
|<span data-ttu-id="c889b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c889b-112">Attribute</span></span>|<span data-ttu-id="c889b-113">描述</span><span class="sxs-lookup"><span data-stu-id="c889b-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="c889b-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c889b-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="c889b-115">指定程式集的部分名稱，因為它出現在代碼中。</span><span class="sxs-lookup"><span data-stu-id="c889b-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="c889b-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c889b-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="c889b-117">指定程式集的全名，因為它出現在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="c889b-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c889b-118">子元素</span><span class="sxs-lookup"><span data-stu-id="c889b-118">Child Elements</span></span>  
 <span data-ttu-id="c889b-119">無。</span><span class="sxs-lookup"><span data-stu-id="c889b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c889b-120">父項目</span><span class="sxs-lookup"><span data-stu-id="c889b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c889b-121">元素</span><span class="sxs-lookup"><span data-stu-id="c889b-121">Element</span></span>|<span data-ttu-id="c889b-122">描述</span><span class="sxs-lookup"><span data-stu-id="c889b-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="c889b-123">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="c889b-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="c889b-124">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c889b-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c889b-125">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="c889b-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c889b-126">備註</span><span class="sxs-lookup"><span data-stu-id="c889b-126">Remarks</span></span>  
 <span data-ttu-id="c889b-127">使用部分<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>程式集名稱調用 方法會導致公共語言運行時僅在應用程式基目錄中查找程式集。</span><span class="sxs-lookup"><span data-stu-id="c889b-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="c889b-128">使用應用程式佈建檔中的**\<限定程式集>** 元素提供完整的程式集資訊（名稱、版本、公開金鑰權杖和區域性），並導致通用語言運行時在全域組件快取中搜索程式集。</span><span class="sxs-lookup"><span data-stu-id="c889b-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="c889b-129">**fullName**屬性必須包括程式集標識的四個欄位：名稱、版本、公開金鑰權杖和區域性。</span><span class="sxs-lookup"><span data-stu-id="c889b-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="c889b-130">**部分名稱**屬性必須部分引用程式集。</span><span class="sxs-lookup"><span data-stu-id="c889b-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="c889b-131">必須至少指定程式集的文本名稱（最常見的情況），但還可以包括版本、公開金鑰權杖或區域性（或四者中的任何組合，但不是全部四個）。</span><span class="sxs-lookup"><span data-stu-id="c889b-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="c889b-132">**部分名稱**必須與呼叫中指定的名稱匹配。</span><span class="sxs-lookup"><span data-stu-id="c889b-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="c889b-133">例如，您不能在設定檔中`"math"`指定為**部分Name**屬性，並在代碼中調用`Assembly.Load("math, Version=3.3.3.3")`。</span><span class="sxs-lookup"><span data-stu-id="c889b-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c889b-134">範例</span><span class="sxs-lookup"><span data-stu-id="c889b-134">Example</span></span>  
 <span data-ttu-id="c889b-135">以下示例從邏輯上將調用`Assembly.Load("math")`轉換為`Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`。</span><span class="sxs-lookup"><span data-stu-id="c889b-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c889b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c889b-136">See also</span></span>

- [<span data-ttu-id="c889b-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c889b-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c889b-138">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="c889b-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="c889b-139">[部分組件參考](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c889b-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
