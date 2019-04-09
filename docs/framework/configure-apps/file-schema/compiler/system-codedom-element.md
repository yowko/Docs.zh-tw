---
title: <system.codedom> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 0f47255bb4073007a847e4a8b85ccfd34100582b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101610"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="e9572-102">\<system.codedom > 項目</span><span class="sxs-lookup"><span data-stu-id="e9572-102">\<system.codedom> Element</span></span>
<span data-ttu-id="e9572-103">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="e9572-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="e9572-104">\<組態 > 項目</span><span class="sxs-lookup"><span data-stu-id="e9572-104">\<configuration> Element</span></span>  
<span data-ttu-id="e9572-105">\<system.codedom > 項目</span><span class="sxs-lookup"><span data-stu-id="e9572-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9572-106">語法</span><span class="sxs-lookup"><span data-stu-id="e9572-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9572-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e9572-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e9572-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e9572-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9572-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e9572-109">Attributes</span></span>  
 <span data-ttu-id="e9572-110">無。</span><span class="sxs-lookup"><span data-stu-id="e9572-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e9572-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e9572-111">Child Elements</span></span>  
  
|<span data-ttu-id="e9572-112">項目</span><span class="sxs-lookup"><span data-stu-id="e9572-112">Element</span></span>|<span data-ttu-id="e9572-113">描述</span><span class="sxs-lookup"><span data-stu-id="e9572-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9572-114">\<編譯器 ></span><span class="sxs-lookup"><span data-stu-id="e9572-114">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="e9572-115">編譯器組態項目的容器；內含零或多個 [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="e9572-115">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9572-116">父項目</span><span class="sxs-lookup"><span data-stu-id="e9572-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e9572-117">項目</span><span class="sxs-lookup"><span data-stu-id="e9572-117">Element</span></span>|<span data-ttu-id="e9572-118">描述</span><span class="sxs-lookup"><span data-stu-id="e9572-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9572-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e9572-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="e9572-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e9572-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9572-121">備註</span><span class="sxs-lookup"><span data-stu-id="e9572-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="e9572-122">.NET framework 2.0 版</span><span class="sxs-lookup"><span data-stu-id="e9572-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="e9572-123">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)項目包含除了會隨.NET Framework 中，這類的預設提供者的電腦上安裝的語言提供者的編譯器組態設定<xref:Microsoft.CSharp.CSharpCodeProvider>而<xref:Microsoft.VisualBasic.VBCodeProvider>。</span><span class="sxs-lookup"><span data-stu-id="e9572-123">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="e9572-124">[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)項目包含零或多個[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="e9572-124">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="e9572-125">每個[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)項目會指定特定的語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="e9572-125">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="e9572-126">開發人員和編譯器廠商可以將組態設定加入電腦組態檔 (Machine.config) 的新<xref:System.CodeDom.Compiler.CodeDomProvider>實作。</span><span class="sxs-lookup"><span data-stu-id="e9572-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="e9572-127">使用<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>方法來以程式設計方式列舉在預設的語言提供者和編譯器組態設定，在電腦上所識別的語言提供者。</span><span class="sxs-lookup"><span data-stu-id="e9572-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9572-128">在.NET framework 1.0 和 1.1 版，.NET Framework 所提供的提供者中所識別的預設語言[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="e9572-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span></span> <span data-ttu-id="e9572-129">在.NET Framework 2.0 版中，預設的語言提供者不會識別在[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)項目，但可以使用列舉<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e9572-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="e9572-130">.NET framework 1.0 和 1.1 版</span><span class="sxs-lookup"><span data-stu-id="e9572-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="e9572-131">[ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)項目包含的電腦上的語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="e9572-131">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="e9572-132">[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)項目包含零或多個[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="e9572-132">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="e9572-133">每個[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)項目會指定特定的語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="e9572-133">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="e9572-134">.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="e9572-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="e9572-135">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="e9572-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="e9572-136">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="e9572-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="e9572-137">組態檔</span><span class="sxs-lookup"><span data-stu-id="e9572-137">Configuration File</span></span>  
 <span data-ttu-id="e9572-138">這個項目可以用於電腦組態檔和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="e9572-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9572-139">範例</span><span class="sxs-lookup"><span data-stu-id="e9572-139">Example</span></span>  
 <span data-ttu-id="e9572-140">下列範例說明典型的編譯器組態。</span><span class="sxs-lookup"><span data-stu-id="e9572-140">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9572-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9572-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="e9572-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="e9572-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="e9572-143">編譯器和語言提供者設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e9572-143">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [<span data-ttu-id="e9572-144">\<編譯器 > 項目</span><span class="sxs-lookup"><span data-stu-id="e9572-144">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
