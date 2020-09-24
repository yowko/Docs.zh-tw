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
ms.openlocfilehash: 6c35e24696be040788a0c44cbb100ebb35d37157
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149565"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="6b3d2-102">\<system.codedom> 項目</span><span class="sxs-lookup"><span data-stu-id="6b3d2-102">\<system.codedom> Element</span></span>

<span data-ttu-id="6b3d2-103">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a><span data-ttu-id="6b3d2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6b3d2-104">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b3d2-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6b3d2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6b3d2-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b3d2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6b3d2-107">Attributes</span></span>  

 <span data-ttu-id="6b3d2-108">無。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6b3d2-109">子元素</span><span class="sxs-lookup"><span data-stu-id="6b3d2-109">Child Elements</span></span>  
  
|<span data-ttu-id="6b3d2-110">項目</span><span class="sxs-lookup"><span data-stu-id="6b3d2-110">Element</span></span>|<span data-ttu-id="6b3d2-111">描述</span><span class="sxs-lookup"><span data-stu-id="6b3d2-111">Description</span></span>|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="6b3d2-112">編譯器設定元素的容器;包含零或多個 [\<compiler>](compiler-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-112">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b3d2-113">父項目</span><span class="sxs-lookup"><span data-stu-id="6b3d2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="6b3d2-114">項目</span><span class="sxs-lookup"><span data-stu-id="6b3d2-114">Element</span></span>|<span data-ttu-id="6b3d2-115">描述</span><span class="sxs-lookup"><span data-stu-id="6b3d2-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="6b3d2-116">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b3d2-117">備註</span><span class="sxs-lookup"><span data-stu-id="6b3d2-117">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="6b3d2-118">.NET Framework 版本2。0</span><span class="sxs-lookup"><span data-stu-id="6b3d2-118">.NET Framework Version 2.0</span></span>  

 <span data-ttu-id="6b3d2-119">[\<system.codedom>](system-codedom-element.md)除了隨 .NET Framework 安裝的預設提供者之外，元素還包含安裝在電腦上的語言提供者的編譯器設定，例如 <xref:Microsoft.CSharp.CSharpCodeProvider> 和 <xref:Microsoft.VisualBasic.VBCodeProvider> 。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-119">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="6b3d2-120">[\<compilers>](compilers-element.md)元素包含零或多個 [\<compiler>](compiler-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-120">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="6b3d2-121">每個 [\<compiler>](compiler-element.md) 元素都會指定特定語言提供者的編譯器設定屬性。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-121">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="6b3d2-122">開發人員和編譯器廠商可以將設定設定新增至電腦設定檔， ( # A0) 來進行新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 執行。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-122">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="6b3d2-123">您 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 可以使用方法，以程式設計方式列舉電腦上編譯器設定設定所識別的預設語言提供者和語言提供者。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-123">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b3d2-124">在 .NET Framework 1.0 和1.1 版中，.NET Framework 所提供的預設語言提供者會在元素中識別 [\<compilers>](compilers-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-124">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="6b3d2-125">在 .NET Framework 2.0 版中，專案中不會識別預設的語言提供者 [\<compilers>](compilers-element.md) ，但可以使用方法來列舉 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> 。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-125">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="6b3d2-126">.NET Framework 版本1.0 和1。1</span><span class="sxs-lookup"><span data-stu-id="6b3d2-126">.NET Framework Versions 1.0 and 1.1</span></span>  

 <span data-ttu-id="6b3d2-127">[\<system.codedom>](system-codedom-element.md)元素包含電腦上語言提供者的編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-127">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="6b3d2-128">[\<compilers>](compilers-element.md)元素包含零或多個 [\<compiler>](compiler-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-128">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="6b3d2-129">每個 [\<compiler>](compiler-element.md) 元素都會指定特定語言提供者的編譯器設定屬性。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-129">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="6b3d2-130">.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-130">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="6b3d2-131">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-131">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="6b3d2-132">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-132">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="6b3d2-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="6b3d2-133">Configuration File</span></span>  

 <span data-ttu-id="6b3d2-134">此元素可用於電腦設定檔和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-134">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b3d2-135">範例</span><span class="sxs-lookup"><span data-stu-id="6b3d2-135">Example</span></span>  

 <span data-ttu-id="6b3d2-136">下列範例說明典型的編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="6b3d2-136">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b3d2-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b3d2-137">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="6b3d2-138">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="6b3d2-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6b3d2-139">編譯器和語言提供者設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6b3d2-139">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6b3d2-140">\<compiler> 元素</span><span class="sxs-lookup"><span data-stu-id="6b3d2-140">\<compiler> Element</span></span>](compiler-element.md)
