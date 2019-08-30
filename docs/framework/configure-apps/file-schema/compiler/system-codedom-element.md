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
ms.openlocfilehash: 19f37095bd01b76fda8b1e29423c413dbdb06a65
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168909"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="298a7-102">\<system.object > 元素</span><span class="sxs-lookup"><span data-stu-id="298a7-102">\<system.codedom> Element</span></span>
<span data-ttu-id="298a7-103">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="298a7-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[<span data-ttu-id="298a7-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="298a7-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="298a7-105">&nbsp;&nbsp; **\<system.object >**</span><span class="sxs-lookup"><span data-stu-id="298a7-105">&nbsp;&nbsp;**\<system.codedom>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="298a7-106">語法</span><span class="sxs-lookup"><span data-stu-id="298a7-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="298a7-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="298a7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="298a7-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="298a7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="298a7-109">屬性</span><span class="sxs-lookup"><span data-stu-id="298a7-109">Attributes</span></span>  
 <span data-ttu-id="298a7-110">無。</span><span class="sxs-lookup"><span data-stu-id="298a7-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="298a7-111">子元素</span><span class="sxs-lookup"><span data-stu-id="298a7-111">Child Elements</span></span>  
  
|<span data-ttu-id="298a7-112">項目</span><span class="sxs-lookup"><span data-stu-id="298a7-112">Element</span></span>|<span data-ttu-id="298a7-113">描述</span><span class="sxs-lookup"><span data-stu-id="298a7-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="298a7-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="298a7-114">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="298a7-115">編譯器組態項目的容器；內含零或多個 [\<compiler>](compiler-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="298a7-115">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="298a7-116">父項目</span><span class="sxs-lookup"><span data-stu-id="298a7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="298a7-117">項目</span><span class="sxs-lookup"><span data-stu-id="298a7-117">Element</span></span>|<span data-ttu-id="298a7-118">描述</span><span class="sxs-lookup"><span data-stu-id="298a7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="298a7-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="298a7-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="298a7-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="298a7-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="298a7-121">備註</span><span class="sxs-lookup"><span data-stu-id="298a7-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="298a7-122">.NET Framework 版本2。0</span><span class="sxs-lookup"><span data-stu-id="298a7-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="298a7-123">System codedom > 專案包含電腦上所安裝之語言提供者的編譯器設定<xref:Microsoft.CSharp.CSharpCodeProvider> , 以及隨 .NET Framework 安裝的預設提供者, 例如和[ \< ](system-codedom-element.md)<xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="298a7-123">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="298a7-124">編譯器 > 元素包含零或多個[ \<編譯器 >](compiler-element.md)元素。 [ \< ](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="298a7-124">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="298a7-125">每個[ \<編譯器 >](compiler-element.md)元素都會指定特定語言提供者的編譯器設定屬性。</span><span class="sxs-lookup"><span data-stu-id="298a7-125">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="298a7-126">開發人員和編譯器廠商可以針對新<xref:System.CodeDom.Compiler.CodeDomProvider>的執行, 將設定值新增至電腦設定檔 (machine.config)。</span><span class="sxs-lookup"><span data-stu-id="298a7-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="298a7-127"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>使用方法, 以程式設計方式列舉電腦上的編譯器設定所識別的預設語言提供者和語言提供者。</span><span class="sxs-lookup"><span data-stu-id="298a7-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="298a7-128">在 .NET Framework 版本1.0 和1.1 中, .NET Framework 所提供的預設語言提供者會在[ \<編譯器 >](compilers-element.md)元素中識別出來。</span><span class="sxs-lookup"><span data-stu-id="298a7-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="298a7-129">在 .NET Framework 版本2.0 中, [ \<編譯器 >](compilers-element.md)元素中不會識別預設語言提供者, 但可以使用<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>方法來列舉。</span><span class="sxs-lookup"><span data-stu-id="298a7-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="298a7-130">.NET Framework 版本1.0 和1。1</span><span class="sxs-lookup"><span data-stu-id="298a7-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="298a7-131">System.web > 元素包含電腦上語言提供者的編譯器設定。 [ \< ](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="298a7-131">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="298a7-132">編譯器 > 元素包含零或多個[ \<編譯器 >](compiler-element.md)元素。 [ \< ](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="298a7-132">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="298a7-133">每個[ \<編譯器 >](compiler-element.md)元素都會指定特定語言提供者的編譯器設定屬性。</span><span class="sxs-lookup"><span data-stu-id="298a7-133">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="298a7-134">.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="298a7-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="298a7-135">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="298a7-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="298a7-136">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="298a7-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="298a7-137">組態檔</span><span class="sxs-lookup"><span data-stu-id="298a7-137">Configuration File</span></span>  
 <span data-ttu-id="298a7-138">此元素可以在電腦設定檔和應用程式佈建檔中使用。</span><span class="sxs-lookup"><span data-stu-id="298a7-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="298a7-139">範例</span><span class="sxs-lookup"><span data-stu-id="298a7-139">Example</span></span>  
 <span data-ttu-id="298a7-140">下列範例說明典型的編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="298a7-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="298a7-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="298a7-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="298a7-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="298a7-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="298a7-143">編譯器和語言提供者設定結構描述</span><span class="sxs-lookup"><span data-stu-id="298a7-143">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="298a7-144">\<編譯器> 項目</span><span class="sxs-lookup"><span data-stu-id="298a7-144">\<compiler> Element</span></span>](compiler-element.md)
