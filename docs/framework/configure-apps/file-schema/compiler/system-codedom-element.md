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
ms.openlocfilehash: 2bbd81867b3c20d8ac16bdd79fcc9a3cc7bbb55c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659690"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="7f86a-102">\<system.object > 元素</span><span class="sxs-lookup"><span data-stu-id="7f86a-102">\<system.codedom> Element</span></span>
<span data-ttu-id="7f86a-103">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="7f86a-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="7f86a-104">\<configuration > 元素</span><span class="sxs-lookup"><span data-stu-id="7f86a-104">\<configuration> Element</span></span>  
<span data-ttu-id="7f86a-105">\<system.object > 元素</span><span class="sxs-lookup"><span data-stu-id="7f86a-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f86a-106">語法</span><span class="sxs-lookup"><span data-stu-id="7f86a-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f86a-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7f86a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7f86a-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7f86a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f86a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7f86a-109">Attributes</span></span>  
 <span data-ttu-id="7f86a-110">無。</span><span class="sxs-lookup"><span data-stu-id="7f86a-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7f86a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7f86a-111">Child Elements</span></span>  
  
|<span data-ttu-id="7f86a-112">項目</span><span class="sxs-lookup"><span data-stu-id="7f86a-112">Element</span></span>|<span data-ttu-id="7f86a-113">說明</span><span class="sxs-lookup"><span data-stu-id="7f86a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f86a-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="7f86a-114">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="7f86a-115">編譯器組態項目的容器；內含零或多個 [\<compiler>](compiler-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="7f86a-115">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f86a-116">父項目</span><span class="sxs-lookup"><span data-stu-id="7f86a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7f86a-117">項目</span><span class="sxs-lookup"><span data-stu-id="7f86a-117">Element</span></span>|<span data-ttu-id="7f86a-118">描述</span><span class="sxs-lookup"><span data-stu-id="7f86a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f86a-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7f86a-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="7f86a-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="7f86a-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f86a-121">備註</span><span class="sxs-lookup"><span data-stu-id="7f86a-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="7f86a-122">.NET Framework 版本2。0</span><span class="sxs-lookup"><span data-stu-id="7f86a-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="7f86a-123">System codedom > 專案包含電腦上所安裝之語言提供者的編譯器設定<xref:Microsoft.CSharp.CSharpCodeProvider> , 以及隨 .NET Framework 安裝的預設提供者, 例如和[ \< ](system-codedom-element.md)<xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="7f86a-123">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="7f86a-124">編譯器 > 元素包含零或多個[ \<編譯器 >](compiler-element.md)元素。 [ \< ](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="7f86a-124">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="7f86a-125">每個[ \<編譯器 >](compiler-element.md)元素都會指定特定語言提供者的編譯器設定屬性。</span><span class="sxs-lookup"><span data-stu-id="7f86a-125">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="7f86a-126">開發人員和編譯器廠商可以針對新<xref:System.CodeDom.Compiler.CodeDomProvider>的執行, 將設定值新增至電腦設定檔 (machine.config)。</span><span class="sxs-lookup"><span data-stu-id="7f86a-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="7f86a-127"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>使用方法, 以程式設計方式列舉電腦上的編譯器設定所識別的預設語言提供者和語言提供者。</span><span class="sxs-lookup"><span data-stu-id="7f86a-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f86a-128">在 .NET Framework 版本1.0 和1.1 中, .NET Framework 所提供的預設語言提供者會在[ \<編譯器 >](compilers-element.md)元素中識別出來。</span><span class="sxs-lookup"><span data-stu-id="7f86a-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="7f86a-129">在 .NET Framework 版本2.0 中, [ \<編譯器 >](compilers-element.md)元素中不會識別預設語言提供者, 但可以使用<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>方法來列舉。</span><span class="sxs-lookup"><span data-stu-id="7f86a-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="7f86a-130">.NET Framework 版本1.0 和1。1</span><span class="sxs-lookup"><span data-stu-id="7f86a-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="7f86a-131">System.web > 元素包含電腦上語言提供者的編譯器設定。 [ \< ](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="7f86a-131">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="7f86a-132">編譯器 > 元素包含零或多個[ \<編譯器 >](compiler-element.md)元素。 [ \< ](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="7f86a-132">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="7f86a-133">每個[ \<編譯器 >](compiler-element.md)元素都會指定特定語言提供者的編譯器設定屬性。</span><span class="sxs-lookup"><span data-stu-id="7f86a-133">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="7f86a-134">.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="7f86a-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="7f86a-135">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="7f86a-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="7f86a-136">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="7f86a-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="7f86a-137">組態檔</span><span class="sxs-lookup"><span data-stu-id="7f86a-137">Configuration File</span></span>  
 <span data-ttu-id="7f86a-138">此元素可以在電腦設定檔和應用程式佈建檔中使用。</span><span class="sxs-lookup"><span data-stu-id="7f86a-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f86a-139">範例</span><span class="sxs-lookup"><span data-stu-id="7f86a-139">Example</span></span>  
 <span data-ttu-id="7f86a-140">下列範例說明典型的編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="7f86a-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f86a-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f86a-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="7f86a-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="7f86a-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7f86a-143">編譯器和語言提供者設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7f86a-143">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7f86a-144">\<編譯器> 項目</span><span class="sxs-lookup"><span data-stu-id="7f86a-144">\<compiler> Element</span></span>](compiler-element.md)
