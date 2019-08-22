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
ms.openlocfilehash: 80eea3373e2f4b7e45ebeb31dd6552ea02c109e1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659736"
---
# <a name="compiler-element"></a><span data-ttu-id="89fbd-102">\<編譯器 > 元素</span><span class="sxs-lookup"><span data-stu-id="89fbd-102">\<compiler> Element</span></span>

<span data-ttu-id="89fbd-103">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="89fbd-103">Specifies the compiler configuration attributes for a language provider.</span></span>

<span data-ttu-id="89fbd-104">\<configuration 元素 > \<system.object 元素 > \<編譯器元素 > \<編譯器 > 元素</span><span class="sxs-lookup"><span data-stu-id="89fbd-104">\<configuration Element> \<system.codedom Element> \<compilers Element> \<compiler> Element</span></span>

## <a name="syntax"></a><span data-ttu-id="89fbd-105">語法</span><span class="sxs-lookup"><span data-stu-id="89fbd-105">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="89fbd-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="89fbd-106">Attributes and Elements</span></span>

<span data-ttu-id="89fbd-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="89fbd-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="89fbd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="89fbd-108">Attributes</span></span>

|<span data-ttu-id="89fbd-109">屬性</span><span class="sxs-lookup"><span data-stu-id="89fbd-109">Attribute</span></span>|<span data-ttu-id="89fbd-110">描述</span><span class="sxs-lookup"><span data-stu-id="89fbd-110">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="89fbd-111">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="89fbd-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="89fbd-112">指定編譯的其他編譯器特定引數。</span><span class="sxs-lookup"><span data-stu-id="89fbd-112">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="89fbd-113">`compilerOptions`屬性的值通常會列在編譯器的編譯器選項主題中。</span><span class="sxs-lookup"><span data-stu-id="89fbd-113">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="89fbd-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="89fbd-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="89fbd-115">提供語言提供者的原始程式檔所使用的檔案名副檔名清單 (以分號分隔)。</span><span class="sxs-lookup"><span data-stu-id="89fbd-115">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="89fbd-116">例如, ".cs"。</span><span class="sxs-lookup"><span data-stu-id="89fbd-116">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="89fbd-117">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="89fbd-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="89fbd-118">提供語言提供者所支援的語言名稱清單 (以分號分隔)。</span><span class="sxs-lookup"><span data-stu-id="89fbd-118">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="89fbd-119">例如, "c #; cs; csharp"。</span><span class="sxs-lookup"><span data-stu-id="89fbd-119">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="89fbd-120">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="89fbd-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="89fbd-121">指定語言提供者的類型名稱, 包括包含提供者實作為元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="89fbd-121">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="89fbd-122">型別名稱必須符合[指定完整限定型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)中所定義的需求。</span><span class="sxs-lookup"><span data-stu-id="89fbd-122">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="89fbd-123">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="89fbd-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="89fbd-124">指定預設的編譯器警告層級;決定語言提供者將編譯警告視為錯誤的層級。</span><span class="sxs-lookup"><span data-stu-id="89fbd-124">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="89fbd-125">子元素</span><span class="sxs-lookup"><span data-stu-id="89fbd-125">Child Elements</span></span>

|<span data-ttu-id="89fbd-126">項目</span><span class="sxs-lookup"><span data-stu-id="89fbd-126">Element</span></span>|<span data-ttu-id="89fbd-127">描述</span><span class="sxs-lookup"><span data-stu-id="89fbd-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89fbd-128">\<providerOption > 元素</span><span class="sxs-lookup"><span data-stu-id="89fbd-128">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="89fbd-129">指定語言提供者的編譯器版本屬性。</span><span class="sxs-lookup"><span data-stu-id="89fbd-129">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="89fbd-130">父項目</span><span class="sxs-lookup"><span data-stu-id="89fbd-130">Parent Elements</span></span>

|<span data-ttu-id="89fbd-131">項目</span><span class="sxs-lookup"><span data-stu-id="89fbd-131">Element</span></span>|<span data-ttu-id="89fbd-132">描述</span><span class="sxs-lookup"><span data-stu-id="89fbd-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89fbd-133">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="89fbd-133">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="89fbd-134">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="89fbd-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="89fbd-135">\<system.object > 元素</span><span class="sxs-lookup"><span data-stu-id="89fbd-135">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="89fbd-136">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="89fbd-136">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="89fbd-137">\<編譯器 > 元素</span><span class="sxs-lookup"><span data-stu-id="89fbd-137">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="89fbd-138">編譯器設定元素的容器;包含零個或`<compiler>`多個元素。</span><span class="sxs-lookup"><span data-stu-id="89fbd-138">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89fbd-139">備註</span><span class="sxs-lookup"><span data-stu-id="89fbd-139">Remarks</span></span>

<span data-ttu-id="89fbd-140">每`<compiler>`個元素都會指定特定語言提供者的編譯器設定屬性。</span><span class="sxs-lookup"><span data-stu-id="89fbd-140">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="89fbd-141">提供者會擴充<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>特定語言的類別`<compiler>` ; 元素會定義語言提供者的編譯器和程式碼產生器設定。</span><span class="sxs-lookup"><span data-stu-id="89fbd-141">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="89fbd-142">.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="89fbd-142">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="89fbd-143">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="89fbd-143">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="89fbd-144">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="89fbd-144">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="89fbd-145">應用程式或 Web 設定檔中的編譯器元素可以補充或覆寫電腦設定檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="89fbd-145">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="89fbd-146">如果針對相同的語言名稱或相同的副檔名設定了一個以上的提供者, 則最後一個比對設定會覆寫任何先前針對該語言名稱或副檔名所設定的提供者。</span><span class="sxs-lookup"><span data-stu-id="89fbd-146">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="89fbd-147">組態檔</span><span class="sxs-lookup"><span data-stu-id="89fbd-147">Configuration File</span></span>

<span data-ttu-id="89fbd-148">此元素可以在電腦設定檔和應用程式佈建檔中使用。</span><span class="sxs-lookup"><span data-stu-id="89fbd-148">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="89fbd-149">範例</span><span class="sxs-lookup"><span data-stu-id="89fbd-149">Example</span></span>

<span data-ttu-id="89fbd-150">下列範例說明典型的編譯器設定元素:</span><span class="sxs-lookup"><span data-stu-id="89fbd-150">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="89fbd-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89fbd-151">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="89fbd-152">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="89fbd-152">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="89fbd-153">\<編譯器 > 元素</span><span class="sxs-lookup"><span data-stu-id="89fbd-153">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="89fbd-154">指定完整的類型名稱</span><span class="sxs-lookup"><span data-stu-id="89fbd-154">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="89fbd-155">[編譯編譯器的編譯器元素 (ASP.NET 設定架構)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="89fbd-155">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
