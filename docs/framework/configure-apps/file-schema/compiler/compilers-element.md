---
title: '&lt;編譯器&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 7d9deda5e0ffeb95483eebbbb0a63831db08ac0b
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083362"
---
# <a name="ltcompilersgt-element"></a><span data-ttu-id="975ea-102">&lt;編譯器&gt;項目</span><span class="sxs-lookup"><span data-stu-id="975ea-102">&lt;compilers&gt; Element</span></span>
<span data-ttu-id="975ea-103">編譯器組態項目的容器；內含零或多個 [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="975ea-103">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="975ea-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="975ea-104">\<configuration></span></span>  
<span data-ttu-id="975ea-105">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="975ea-105">\<system.codedom></span></span>  
<span data-ttu-id="975ea-106">\<編譯器 > 項目</span><span class="sxs-lookup"><span data-stu-id="975ea-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="975ea-107">語法</span><span class="sxs-lookup"><span data-stu-id="975ea-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="975ea-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="975ea-108">Attributes and Elements</span></span>  
 <span data-ttu-id="975ea-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="975ea-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="975ea-110">屬性</span><span class="sxs-lookup"><span data-stu-id="975ea-110">Attributes</span></span>  
 <span data-ttu-id="975ea-111">無。</span><span class="sxs-lookup"><span data-stu-id="975ea-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="975ea-112">子元素</span><span class="sxs-lookup"><span data-stu-id="975ea-112">Child Elements</span></span>  
  
|<span data-ttu-id="975ea-113">項目</span><span class="sxs-lookup"><span data-stu-id="975ea-113">Element</span></span>|<span data-ttu-id="975ea-114">描述</span><span class="sxs-lookup"><span data-stu-id="975ea-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="975ea-115">\<編譯器> 項目</span><span class="sxs-lookup"><span data-stu-id="975ea-115">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="975ea-116">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="975ea-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="975ea-117">父項目</span><span class="sxs-lookup"><span data-stu-id="975ea-117">Parent Elements</span></span>  
  
|<span data-ttu-id="975ea-118">項目</span><span class="sxs-lookup"><span data-stu-id="975ea-118">Element</span></span>|<span data-ttu-id="975ea-119">描述</span><span class="sxs-lookup"><span data-stu-id="975ea-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="975ea-120">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="975ea-120">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="975ea-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="975ea-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="975ea-122">\<system.codedom > 項目</span><span class="sxs-lookup"><span data-stu-id="975ea-122">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="975ea-123">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="975ea-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="975ea-124">備註</span><span class="sxs-lookup"><span data-stu-id="975ea-124">Remarks</span></span>  
 <span data-ttu-id="975ea-125">[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)項目包含的電腦上的語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="975ea-125">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="975ea-126">每個[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)項目會指定特定的語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="975ea-126">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="975ea-127">.NET Framework 會定義初始編譯器和語言提供者設定電腦組態檔 (Machine.config) 中。</span><span class="sxs-lookup"><span data-stu-id="975ea-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="975ea-128">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="975ea-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="975ea-129">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="975ea-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="975ea-130">組態檔</span><span class="sxs-lookup"><span data-stu-id="975ea-130">Configuration File</span></span>  
 <span data-ttu-id="975ea-131">這個項目可以用於電腦組態檔和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="975ea-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="975ea-132">範例</span><span class="sxs-lookup"><span data-stu-id="975ea-132">Example</span></span>  
 <span data-ttu-id="975ea-133">下列範例說明典型的編譯器組態項目。</span><span class="sxs-lookup"><span data-stu-id="975ea-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="975ea-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="975ea-134">See also</span></span>
- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="975ea-135">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="975ea-135">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="975ea-136">編譯器和語言提供者設定結構描述</span><span class="sxs-lookup"><span data-stu-id="975ea-136">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [<span data-ttu-id="975ea-137">\<編譯器> 項目</span><span class="sxs-lookup"><span data-stu-id="975ea-137">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
