---
title: "&lt;編譯器&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2ef50301a5188193cc13cd0e657f53593ef0d93e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcompilergt-element"></a><span data-ttu-id="31552-102">&lt;編譯器&gt;項目</span><span class="sxs-lookup"><span data-stu-id="31552-102">&lt;compiler&gt; Element</span></span>
<span data-ttu-id="31552-103">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="31552-103">Specifies the compiler configuration attributes for a language provider.</span></span>  
  
 <span data-ttu-id="31552-104">\<組態項目 ></span><span class="sxs-lookup"><span data-stu-id="31552-104">\<configuration Element></span></span>  
<span data-ttu-id="31552-105">\<system.codedom 項目 ></span><span class="sxs-lookup"><span data-stu-id="31552-105">\<system.codedom Element></span></span>  
<span data-ttu-id="31552-106">\<編譯器項目 ></span><span class="sxs-lookup"><span data-stu-id="31552-106">\<compilers Element></span></span>  
<span data-ttu-id="31552-107">\<編譯器 > 項目</span><span class="sxs-lookup"><span data-stu-id="31552-107">\<compiler> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31552-108">語法</span><span class="sxs-lookup"><span data-stu-id="31552-108">Syntax</span></span>  
  
```xml  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31552-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="31552-109">Attributes and Elements</span></span>  
 <span data-ttu-id="31552-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="31552-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31552-111">屬性</span><span class="sxs-lookup"><span data-stu-id="31552-111">Attributes</span></span>  
  
|<span data-ttu-id="31552-112">屬性</span><span class="sxs-lookup"><span data-stu-id="31552-112">Attribute</span></span>|<span data-ttu-id="31552-113">描述</span><span class="sxs-lookup"><span data-stu-id="31552-113">Description</span></span>|  
|---------------|-----------------|  
|`compilerOptions`|<span data-ttu-id="31552-114">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="31552-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="31552-115">指定編譯的其他特定編譯器的引數。</span><span class="sxs-lookup"><span data-stu-id="31552-115">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="31552-116">值`compilerOptions`屬性通常主題中列出編譯器選項的編譯器。</span><span class="sxs-lookup"><span data-stu-id="31552-116">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span> <span data-ttu-id="31552-117">Visual Studio 2005 文件中，您可以藉由尋找索引中的 < 編譯器選項 > 找到編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="31552-117">In the Visual Studio 2005 documentation, you can locate the options for the compiler by looking for "compiler options" in the index.</span></span>|  
|`extension`|<span data-ttu-id="31552-118">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="31552-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="31552-119">提供以分號分隔的原始程式檔所使用的語言提供者的檔案名稱的副檔名清單。</span><span class="sxs-lookup"><span data-stu-id="31552-119">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="31552-120">例如，".cs。 」</span><span class="sxs-lookup"><span data-stu-id="31552-120">For example, ".cs".</span></span>|  
|`language`|<span data-ttu-id="31552-121">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="31552-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="31552-122">提供以分號分隔清單的語言提供者所支援的語言名稱。</span><span class="sxs-lookup"><span data-stu-id="31552-122">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="31552-123">例如，"c#; cs; csharp"。</span><span class="sxs-lookup"><span data-stu-id="31552-123">For example, "c#;cs;csharp".</span></span>|  
|`type`|<span data-ttu-id="31552-124">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="31552-124">Required attribute.</span></span><br /><br /> <span data-ttu-id="31552-125">指定的語言提供者，包括包含的提供者實作的組件名稱的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="31552-125">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="31552-126">型別名稱必須符合中定義的需求[指定限定的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="31552-126">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`warningLevel`|<span data-ttu-id="31552-127">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="31552-127">Optional attribute.</span></span><br /><br /> <span data-ttu-id="31552-128">指定預設編譯器警告層級;決定的語言提供者會將編譯警告視為錯誤的層級。</span><span class="sxs-lookup"><span data-stu-id="31552-128">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31552-129">子元素</span><span class="sxs-lookup"><span data-stu-id="31552-129">Child Elements</span></span>  
  
|<span data-ttu-id="31552-130">項目</span><span class="sxs-lookup"><span data-stu-id="31552-130">Element</span></span>|<span data-ttu-id="31552-131">描述</span><span class="sxs-lookup"><span data-stu-id="31552-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31552-132">\<providerOption > 項目</span><span class="sxs-lookup"><span data-stu-id="31552-132">\<providerOption> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|<span data-ttu-id="31552-133">指定語言提供者的編譯器版本屬性。</span><span class="sxs-lookup"><span data-stu-id="31552-133">Specifies compiler version attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31552-134">父項目</span><span class="sxs-lookup"><span data-stu-id="31552-134">Parent Elements</span></span>  
  
|<span data-ttu-id="31552-135">項目</span><span class="sxs-lookup"><span data-stu-id="31552-135">Element</span></span>|<span data-ttu-id="31552-136">描述</span><span class="sxs-lookup"><span data-stu-id="31552-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31552-137">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="31552-137">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="31552-138">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="31552-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="31552-139">\<system.codedom > 項目</span><span class="sxs-lookup"><span data-stu-id="31552-139">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="31552-140">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="31552-140">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="31552-141">\<編譯器 > 項目</span><span class="sxs-lookup"><span data-stu-id="31552-141">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="31552-142">編譯器組態項目; 容器包含零或多個`<compiler>`項目。</span><span class="sxs-lookup"><span data-stu-id="31552-142">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31552-143">備註</span><span class="sxs-lookup"><span data-stu-id="31552-143">Remarks</span></span>  
 <span data-ttu-id="31552-144">每個`<compiler>`項目指定特定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="31552-144">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="31552-145">提供者會擴充<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>類別特定的語言;`<compiler>`項目會定義編譯器和語言提供者的程式碼產生器設定。</span><span class="sxs-lookup"><span data-stu-id="31552-145">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>  
  
 <span data-ttu-id="31552-146">.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="31552-146">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="31552-147">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="31552-147">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="31552-148">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="31552-148">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 <span data-ttu-id="31552-149">編譯器應用程式或 Web 組態檔中的項目可以補充或電腦組態檔中的設定會覆寫。</span><span class="sxs-lookup"><span data-stu-id="31552-149">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="31552-150">如果一個以上的提供者實作會設定為相同的語言名稱或相同的副檔名，最後一個相符的設定會覆寫任何先前設定的提供者針對該語言名稱或副檔名。</span><span class="sxs-lookup"><span data-stu-id="31552-150">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="31552-151">組態檔</span><span class="sxs-lookup"><span data-stu-id="31552-151">Configuration File</span></span>  
 <span data-ttu-id="31552-152">此項目可以用於電腦組態檔和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="31552-152">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31552-153">範例</span><span class="sxs-lookup"><span data-stu-id="31552-153">Example</span></span>  
 <span data-ttu-id="31552-154">下列範例說明典型的編譯器組態項目。</span><span class="sxs-lookup"><span data-stu-id="31552-154">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="31552-155">請參閱</span><span class="sxs-lookup"><span data-stu-id="31552-155">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="31552-156">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="31552-156">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="31552-157">\<編譯器 > 項目</span><span class="sxs-lookup"><span data-stu-id="31552-157">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="31552-158">指定完整的類型名稱</span><span class="sxs-lookup"><span data-stu-id="31552-158">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [<span data-ttu-id="31552-159">編譯器元素編譯器編譯 （ASP.NET 設定結構描述）</span><span class="sxs-lookup"><span data-stu-id="31552-159">compiler Element for compilers for compilation (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/en-us/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
