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
ms.openlocfilehash: 40a3c84e1deed4d215383670176623a6a79ac41d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155384"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="cbe68-102">\<系統.代碼>元素</span><span class="sxs-lookup"><span data-stu-id="cbe68-102">\<system.codedom> Element</span></span>
<span data-ttu-id="cbe68-103">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="cbe68-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[<span data-ttu-id="cbe68-104">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="cbe68-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="cbe68-105">&nbsp;&nbsp;**\<系統.代碼>**</span><span class="sxs-lookup"><span data-stu-id="cbe68-105">&nbsp;&nbsp;**\<system.codedom>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbe68-106">語法</span><span class="sxs-lookup"><span data-stu-id="cbe68-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbe68-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cbe68-107">Attributes and Elements</span></span>  
 <span data-ttu-id="cbe68-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cbe68-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbe68-109">屬性</span><span class="sxs-lookup"><span data-stu-id="cbe68-109">Attributes</span></span>  
 <span data-ttu-id="cbe68-110">無。</span><span class="sxs-lookup"><span data-stu-id="cbe68-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cbe68-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cbe68-111">Child Elements</span></span>  
  
|<span data-ttu-id="cbe68-112">元素</span><span class="sxs-lookup"><span data-stu-id="cbe68-112">Element</span></span>|<span data-ttu-id="cbe68-113">描述</span><span class="sxs-lookup"><span data-stu-id="cbe68-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbe68-114">\<編譯器></span><span class="sxs-lookup"><span data-stu-id="cbe68-114">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="cbe68-115">用於編譯器配置元素的容器;包含零個或多個[\<編譯器>](compiler-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="cbe68-115">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cbe68-116">父項目</span><span class="sxs-lookup"><span data-stu-id="cbe68-116">Parent Elements</span></span>  
  
|<span data-ttu-id="cbe68-117">元素</span><span class="sxs-lookup"><span data-stu-id="cbe68-117">Element</span></span>|<span data-ttu-id="cbe68-118">描述</span><span class="sxs-lookup"><span data-stu-id="cbe68-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbe68-119">\<配置></span><span class="sxs-lookup"><span data-stu-id="cbe68-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="cbe68-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="cbe68-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbe68-121">備註</span><span class="sxs-lookup"><span data-stu-id="cbe68-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="cbe68-122">.NET 框架版本 2.0</span><span class="sxs-lookup"><span data-stu-id="cbe68-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="cbe68-123">[ \<系統.codedom>](system-codedom-element.md)元素包含電腦上安裝的語言提供程式的編譯器配置設置，以及隨 .NET 框架一起安裝的預設提供程式（如 和<xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider>。</span><span class="sxs-lookup"><span data-stu-id="cbe68-123">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="cbe68-124">[ \<編譯器>](compilers-element.md)元素包含零個或多個[\<編譯器>](compiler-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="cbe68-124">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="cbe68-125">每個[\<編譯器>](compiler-element.md)元素指定特定語言提供程式的編譯器配置屬性。</span><span class="sxs-lookup"><span data-stu-id="cbe68-125">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="cbe68-126">開發人員和編譯器供應商可以將配置設置添加到電腦設定檔 （Machine.config） 以用於新<xref:System.CodeDom.Compiler.CodeDomProvider>實現。</span><span class="sxs-lookup"><span data-stu-id="cbe68-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="cbe68-127">使用<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>方法以程式設計方式枚舉電腦上的編譯器配置設置標識的預設語言提供程式和語言提供程式。</span><span class="sxs-lookup"><span data-stu-id="cbe68-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbe68-128">在 .NET 框架版本 1.0 和 1.1 中，.NET Framework 提供的預設語言提供程式在[\<編譯器>](compilers-element.md)元素中標識。</span><span class="sxs-lookup"><span data-stu-id="cbe68-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="cbe68-129">在 .NET Framework 版本 2.0 中，預設語言提供程式不會在[\<編譯器>](compilers-element.md)元素中標識，但可以使用 方法<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>枚舉。</span><span class="sxs-lookup"><span data-stu-id="cbe68-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="cbe68-130">.NET 框架版本 1.0 和 1.1</span><span class="sxs-lookup"><span data-stu-id="cbe68-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="cbe68-131">[ \<系統.codedom>](system-codedom-element.md)元素包含電腦上的語言提供程式的編譯器配置設置。</span><span class="sxs-lookup"><span data-stu-id="cbe68-131">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="cbe68-132">[ \<編譯器>](compilers-element.md)元素包含零個或多個[\<編譯器>](compiler-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="cbe68-132">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="cbe68-133">每個[\<編譯器>](compiler-element.md)元素指定特定語言提供程式的編譯器配置屬性。</span><span class="sxs-lookup"><span data-stu-id="cbe68-133">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="cbe68-134">.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="cbe68-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="cbe68-135">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="cbe68-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="cbe68-136">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="cbe68-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="cbe68-137">組態檔</span><span class="sxs-lookup"><span data-stu-id="cbe68-137">Configuration File</span></span>  
 <span data-ttu-id="cbe68-138">此元素可用於電腦設定檔和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="cbe68-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbe68-139">範例</span><span class="sxs-lookup"><span data-stu-id="cbe68-139">Example</span></span>  
 <span data-ttu-id="cbe68-140">下面的示例說明了典型的編譯器配置。</span><span class="sxs-lookup"><span data-stu-id="cbe68-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cbe68-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbe68-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="cbe68-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="cbe68-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cbe68-143">編譯器和語言提供程式設置架構</span><span class="sxs-lookup"><span data-stu-id="cbe68-143">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cbe68-144">\<編譯器>元素</span><span class="sxs-lookup"><span data-stu-id="cbe68-144">\<compiler> Element</span></span>](compiler-element.md)
