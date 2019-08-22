---
title: <compilers> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 53dc67d0046ef2f184535f373c5bf19c484c505a
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664325"
---
# <a name="compilers-element"></a><span data-ttu-id="2b3a2-102">\<編譯器 > 元素</span><span class="sxs-lookup"><span data-stu-id="2b3a2-102">\<compilers> Element</span></span>
<span data-ttu-id="2b3a2-103">編譯器組態項目的容器；內含零或多個 [\<compiler>](compiler-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="2b3a2-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="2b3a2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2b3a2-104">\<configuration></span></span>  
<span data-ttu-id="2b3a2-105">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="2b3a2-105">\<system.codedom></span></span>  
<span data-ttu-id="2b3a2-106">\<編譯器 > 元素</span><span class="sxs-lookup"><span data-stu-id="2b3a2-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b3a2-107">語法</span><span class="sxs-lookup"><span data-stu-id="2b3a2-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b3a2-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2b3a2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2b3a2-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2b3a2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b3a2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2b3a2-110">Attributes</span></span>  
 <span data-ttu-id="2b3a2-111">無。</span><span class="sxs-lookup"><span data-stu-id="2b3a2-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2b3a2-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2b3a2-112">Child Elements</span></span>  
  
|<span data-ttu-id="2b3a2-113">項目</span><span class="sxs-lookup"><span data-stu-id="2b3a2-113">Element</span></span>|<span data-ttu-id="2b3a2-114">說明</span><span class="sxs-lookup"><span data-stu-id="2b3a2-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b3a2-115">\<編譯器> 項目</span><span class="sxs-lookup"><span data-stu-id="2b3a2-115">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="2b3a2-116">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="2b3a2-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b3a2-117">父項目</span><span class="sxs-lookup"><span data-stu-id="2b3a2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2b3a2-118">項目</span><span class="sxs-lookup"><span data-stu-id="2b3a2-118">Element</span></span>|<span data-ttu-id="2b3a2-119">描述</span><span class="sxs-lookup"><span data-stu-id="2b3a2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b3a2-120">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="2b3a2-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="2b3a2-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2b3a2-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="2b3a2-122">\<system.object > 元素</span><span class="sxs-lookup"><span data-stu-id="2b3a2-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="2b3a2-123">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="2b3a2-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b3a2-124">備註</span><span class="sxs-lookup"><span data-stu-id="2b3a2-124">Remarks</span></span>  
 <span data-ttu-id="2b3a2-125">編譯器 > 元素包含電腦上語言提供者的編譯器設定。 [ \< ](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b3a2-125">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="2b3a2-126">每個[ \<編譯器 >](compiler-element.md)元素都會指定特定語言提供者的編譯器設定屬性。</span><span class="sxs-lookup"><span data-stu-id="2b3a2-126">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="2b3a2-127">.NET Framework 會定義電腦設定檔 (Machine.config) 中的初始編譯器和語言提供者設定。</span><span class="sxs-lookup"><span data-stu-id="2b3a2-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="2b3a2-128">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="2b3a2-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="2b3a2-129">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="2b3a2-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="2b3a2-130">組態檔</span><span class="sxs-lookup"><span data-stu-id="2b3a2-130">Configuration File</span></span>  
 <span data-ttu-id="2b3a2-131">此元素可以在電腦設定檔和應用程式佈建檔中使用。</span><span class="sxs-lookup"><span data-stu-id="2b3a2-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b3a2-132">範例</span><span class="sxs-lookup"><span data-stu-id="2b3a2-132">Example</span></span>  
 <span data-ttu-id="2b3a2-133">下列範例說明典型的編譯器組態項目。</span><span class="sxs-lookup"><span data-stu-id="2b3a2-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler   
          language="c#;cs;csharp"   
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""    
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b3a2-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b3a2-134">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="2b3a2-135">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="2b3a2-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2b3a2-136">編譯器和語言提供者設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2b3a2-136">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2b3a2-137">\<編譯器> 項目</span><span class="sxs-lookup"><span data-stu-id="2b3a2-137">\<compiler> Element</span></span>](compiler-element.md)
