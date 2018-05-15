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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fc85610f5c3db7929f824fda2dd211300d9b05c1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltcompilersgt-element"></a><span data-ttu-id="8ddc4-102">&lt;編譯器&gt;項目</span><span class="sxs-lookup"><span data-stu-id="8ddc4-102">&lt;compilers&gt; Element</span></span>
<span data-ttu-id="8ddc4-103">編譯器組態項目的容器；內含零或多個 [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-103">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="8ddc4-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8ddc4-104">\<configuration></span></span>  
<span data-ttu-id="8ddc4-105">\<system.codedom ></span><span class="sxs-lookup"><span data-stu-id="8ddc4-105">\<system.codedom></span></span>  
<span data-ttu-id="8ddc4-106">\<編譯器 > 項目</span><span class="sxs-lookup"><span data-stu-id="8ddc4-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ddc4-107">語法</span><span class="sxs-lookup"><span data-stu-id="8ddc4-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ddc4-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8ddc4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8ddc4-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ddc4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="8ddc4-110">Attributes</span></span>  
 <span data-ttu-id="8ddc4-111">無。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8ddc4-112">子項目</span><span class="sxs-lookup"><span data-stu-id="8ddc4-112">Child Elements</span></span>  
  
|<span data-ttu-id="8ddc4-113">項目</span><span class="sxs-lookup"><span data-stu-id="8ddc4-113">Element</span></span>|<span data-ttu-id="8ddc4-114">描述</span><span class="sxs-lookup"><span data-stu-id="8ddc4-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ddc4-115">\<編譯器> 項目</span><span class="sxs-lookup"><span data-stu-id="8ddc4-115">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="8ddc4-116">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ddc4-117">父項目</span><span class="sxs-lookup"><span data-stu-id="8ddc4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8ddc4-118">項目</span><span class="sxs-lookup"><span data-stu-id="8ddc4-118">Element</span></span>|<span data-ttu-id="8ddc4-119">描述</span><span class="sxs-lookup"><span data-stu-id="8ddc4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ddc4-120">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="8ddc4-120">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="8ddc4-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="8ddc4-122">\<system.codedom > 項目</span><span class="sxs-lookup"><span data-stu-id="8ddc4-122">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="8ddc4-123">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ddc4-124">備註</span><span class="sxs-lookup"><span data-stu-id="8ddc4-124">Remarks</span></span>  
 <span data-ttu-id="8ddc4-125">[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)元素包含語言提供者的電腦上的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-125">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="8ddc4-126">每個[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)項目指定特定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-126">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="8ddc4-127">.NET Framework 定義的初始編譯器和語言提供者設定，電腦組態檔 (Machine.config) 中。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="8ddc4-128">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="8ddc4-129">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="8ddc4-130">組態檔</span><span class="sxs-lookup"><span data-stu-id="8ddc4-130">Configuration File</span></span>  
 <span data-ttu-id="8ddc4-131">此項目可以用於電腦組態檔和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ddc4-132">範例</span><span class="sxs-lookup"><span data-stu-id="8ddc4-132">Example</span></span>  
 <span data-ttu-id="8ddc4-133">下列範例說明典型的編譯器組態項目。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ddc4-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ddc4-134">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="8ddc4-135">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="8ddc4-135">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="8ddc4-136">編譯器和語言提供者設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8ddc4-136">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="8ddc4-137">\<編譯器> 項目</span><span class="sxs-lookup"><span data-stu-id="8ddc4-137">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
