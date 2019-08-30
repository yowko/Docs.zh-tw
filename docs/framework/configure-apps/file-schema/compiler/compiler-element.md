---
title: <compiler> 項目
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
ms.openlocfilehash: a19cf8182cdb338fd8596ef38311916de0daae37
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168946"
---
# <a name="compiler-element"></a><span data-ttu-id="a79bb-102">\<編譯器 > 元素</span><span class="sxs-lookup"><span data-stu-id="a79bb-102">\<compiler> Element</span></span>

<span data-ttu-id="a79bb-103">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="a79bb-103">Specifies the compiler configuration attributes for a language provider.</span></span>

[<span data-ttu-id="a79bb-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="a79bb-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a79bb-105">&nbsp;&nbsp;[ **\<system.object >** ](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="a79bb-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>  
<span data-ttu-id="a79bb-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<編譯器 >** ](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="a79bb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>  
<span data-ttu-id="a79bb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<編譯器 >**</span><span class="sxs-lookup"><span data-stu-id="a79bb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compiler>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="a79bb-108">語法</span><span class="sxs-lookup"><span data-stu-id="a79bb-108">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a79bb-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a79bb-109">Attributes and Elements</span></span>

<span data-ttu-id="a79bb-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a79bb-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a79bb-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a79bb-111">Attributes</span></span>

|<span data-ttu-id="a79bb-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a79bb-112">Attribute</span></span>|<span data-ttu-id="a79bb-113">描述</span><span class="sxs-lookup"><span data-stu-id="a79bb-113">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="a79bb-114">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="a79bb-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a79bb-115">指定編譯的其他編譯器特定引數。</span><span class="sxs-lookup"><span data-stu-id="a79bb-115">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="a79bb-116">`compilerOptions`屬性的值通常會列在編譯器的編譯器選項主題中。</span><span class="sxs-lookup"><span data-stu-id="a79bb-116">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="a79bb-117">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a79bb-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="a79bb-118">提供語言提供者的原始程式檔所使用的檔案名副檔名清單 (以分號分隔)。</span><span class="sxs-lookup"><span data-stu-id="a79bb-118">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="a79bb-119">例如, ".cs"。</span><span class="sxs-lookup"><span data-stu-id="a79bb-119">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="a79bb-120">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a79bb-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="a79bb-121">提供語言提供者所支援的語言名稱清單 (以分號分隔)。</span><span class="sxs-lookup"><span data-stu-id="a79bb-121">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="a79bb-122">例如, "c #; cs; csharp"。</span><span class="sxs-lookup"><span data-stu-id="a79bb-122">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="a79bb-123">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a79bb-123">Required attribute.</span></span><br /><br /> <span data-ttu-id="a79bb-124">指定語言提供者的類型名稱, 包括包含提供者實作為元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="a79bb-124">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="a79bb-125">型別名稱必須符合[指定完整限定型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)中所定義的需求。</span><span class="sxs-lookup"><span data-stu-id="a79bb-125">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="a79bb-126">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="a79bb-126">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a79bb-127">指定預設的編譯器警告層級;決定語言提供者將編譯警告視為錯誤的層級。</span><span class="sxs-lookup"><span data-stu-id="a79bb-127">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a79bb-128">子元素</span><span class="sxs-lookup"><span data-stu-id="a79bb-128">Child Elements</span></span>

|<span data-ttu-id="a79bb-129">項目</span><span class="sxs-lookup"><span data-stu-id="a79bb-129">Element</span></span>|<span data-ttu-id="a79bb-130">描述</span><span class="sxs-lookup"><span data-stu-id="a79bb-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a79bb-131">\<providerOption > 元素</span><span class="sxs-lookup"><span data-stu-id="a79bb-131">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="a79bb-132">指定語言提供者的編譯器版本屬性。</span><span class="sxs-lookup"><span data-stu-id="a79bb-132">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a79bb-133">父項目</span><span class="sxs-lookup"><span data-stu-id="a79bb-133">Parent Elements</span></span>

|<span data-ttu-id="a79bb-134">項目</span><span class="sxs-lookup"><span data-stu-id="a79bb-134">Element</span></span>|<span data-ttu-id="a79bb-135">描述</span><span class="sxs-lookup"><span data-stu-id="a79bb-135">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a79bb-136">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="a79bb-136">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="a79bb-137">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a79bb-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="a79bb-138">\<system.object > 元素</span><span class="sxs-lookup"><span data-stu-id="a79bb-138">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="a79bb-139">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="a79bb-139">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="a79bb-140">\<編譯器 > 元素</span><span class="sxs-lookup"><span data-stu-id="a79bb-140">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="a79bb-141">編譯器設定元素的容器;包含零個或`<compiler>`多個元素。</span><span class="sxs-lookup"><span data-stu-id="a79bb-141">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a79bb-142">備註</span><span class="sxs-lookup"><span data-stu-id="a79bb-142">Remarks</span></span>

<span data-ttu-id="a79bb-143">每`<compiler>`個元素都會指定特定語言提供者的編譯器設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a79bb-143">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="a79bb-144">提供者會擴充<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>特定語言的類別`<compiler>` ; 元素會定義語言提供者的編譯器和程式碼產生器設定。</span><span class="sxs-lookup"><span data-stu-id="a79bb-144">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="a79bb-145">.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="a79bb-145">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="a79bb-146">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="a79bb-146">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="a79bb-147">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="a79bb-147">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="a79bb-148">應用程式或 Web 設定檔中的編譯器元素可以補充或覆寫電腦設定檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="a79bb-148">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="a79bb-149">如果針對相同的語言名稱或相同的副檔名設定了一個以上的提供者, 則最後一個比對設定會覆寫任何先前針對該語言名稱或副檔名所設定的提供者。</span><span class="sxs-lookup"><span data-stu-id="a79bb-149">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="a79bb-150">組態檔</span><span class="sxs-lookup"><span data-stu-id="a79bb-150">Configuration File</span></span>

<span data-ttu-id="a79bb-151">此元素可以在電腦設定檔和應用程式佈建檔中使用。</span><span class="sxs-lookup"><span data-stu-id="a79bb-151">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="a79bb-152">範例</span><span class="sxs-lookup"><span data-stu-id="a79bb-152">Example</span></span>

<span data-ttu-id="a79bb-153">下列範例說明典型的編譯器設定元素:</span><span class="sxs-lookup"><span data-stu-id="a79bb-153">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a79bb-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a79bb-154">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="a79bb-155">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="a79bb-155">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a79bb-156">\<編譯器 > 元素</span><span class="sxs-lookup"><span data-stu-id="a79bb-156">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="a79bb-157">指定完整的類型名稱</span><span class="sxs-lookup"><span data-stu-id="a79bb-157">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="a79bb-158">[編譯編譯器的編譯器元素 (ASP.NET 設定架構)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a79bb-158">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
