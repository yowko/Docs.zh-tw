---
title: '&lt;編譯器&gt;項目'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 84000d8762c5d5cfd8d2359a377ffcd5b50ab07c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502846"
---
# <a name="ltcompilergt-element"></a><span data-ttu-id="c9fcd-102">&lt;編譯器&gt;項目</span><span class="sxs-lookup"><span data-stu-id="c9fcd-102">&lt;compiler&gt; Element</span></span>

<span data-ttu-id="c9fcd-103">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-103">Specifies the compiler configuration attributes for a language provider.</span></span>

<span data-ttu-id="c9fcd-104">\<組態項目 > \<system.codedom 項目 > \<compilers 項目 >\<編譯器 > 項目</span><span class="sxs-lookup"><span data-stu-id="c9fcd-104">\<configuration Element> \<system.codedom Element> \<compilers Element> \<compiler> Element</span></span>

## <a name="syntax"></a><span data-ttu-id="c9fcd-105">語法</span><span class="sxs-lookup"><span data-stu-id="c9fcd-105">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9fcd-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c9fcd-106">Attributes and Elements</span></span>

<span data-ttu-id="c9fcd-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9fcd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c9fcd-108">Attributes</span></span>

|<span data-ttu-id="c9fcd-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c9fcd-109">Attribute</span></span>|<span data-ttu-id="c9fcd-110">描述</span><span class="sxs-lookup"><span data-stu-id="c9fcd-110">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="c9fcd-111">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c9fcd-112">指定編譯的其他編譯器特定引數。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-112">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="c9fcd-113">值`compilerOptions`屬性通常詳列於編譯器的編譯器選項主題。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-113">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="c9fcd-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="c9fcd-115">提供以分號分隔的原始程式檔使用的語言提供者的檔案名稱副檔名清單。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-115">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="c9fcd-116">例如，".cs"。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-116">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="c9fcd-117">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="c9fcd-118">提供語言提供者所支援的語言名稱以分號分隔的清單。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-118">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="c9fcd-119">例如，"c#; cs; csharp"。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-119">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="c9fcd-120">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="c9fcd-121">指定的語言提供者，包括包含的提供者實作的組件名稱的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-121">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="c9fcd-122">型別名稱必須符合中定義的需求[指定完整的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-122">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="c9fcd-123">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c9fcd-124">指定預設編譯器警告層級;判斷的語言提供者會將編譯警告視為錯誤的層級。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-124">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c9fcd-125">子元素</span><span class="sxs-lookup"><span data-stu-id="c9fcd-125">Child Elements</span></span>

|<span data-ttu-id="c9fcd-126">項目</span><span class="sxs-lookup"><span data-stu-id="c9fcd-126">Element</span></span>|<span data-ttu-id="c9fcd-127">描述</span><span class="sxs-lookup"><span data-stu-id="c9fcd-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9fcd-128">\<providerOption > 項目</span><span class="sxs-lookup"><span data-stu-id="c9fcd-128">\<providerOption> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|<span data-ttu-id="c9fcd-129">指定的語言提供者的編譯器版本屬性。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-129">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c9fcd-130">父項目</span><span class="sxs-lookup"><span data-stu-id="c9fcd-130">Parent Elements</span></span>

|<span data-ttu-id="c9fcd-131">項目</span><span class="sxs-lookup"><span data-stu-id="c9fcd-131">Element</span></span>|<span data-ttu-id="c9fcd-132">描述</span><span class="sxs-lookup"><span data-stu-id="c9fcd-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9fcd-133">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="c9fcd-133">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="c9fcd-134">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="c9fcd-135">\<system.codedom > 項目</span><span class="sxs-lookup"><span data-stu-id="c9fcd-135">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="c9fcd-136">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-136">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="c9fcd-137">\<編譯器 > 項目</span><span class="sxs-lookup"><span data-stu-id="c9fcd-137">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="c9fcd-138">編譯器組態項目; 容器包含零或多個`<compiler>`項目。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-138">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c9fcd-139">備註</span><span class="sxs-lookup"><span data-stu-id="c9fcd-139">Remarks</span></span>

<span data-ttu-id="c9fcd-140">每個`<compiler>`項目會指定特定的語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-140">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="c9fcd-141">提供者會延伸<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>類別特定的語言;`<compiler>`項目會定義編譯器和語言提供者的程式碼產生器設定。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-141">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="c9fcd-142">.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-142">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="c9fcd-143">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-143">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="c9fcd-144">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-144">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="c9fcd-145">編譯器在應用程式或 Web 組態檔中的項目可以補充或電腦組態檔中的設定會覆寫。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-145">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="c9fcd-146">如果一個以上的提供者實作設定為相同的語言名稱或相同的副檔名，最後一個相符的組態會覆寫任何先前設定的提供者針對該語言名稱或副檔名。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-146">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="c9fcd-147">組態檔</span><span class="sxs-lookup"><span data-stu-id="c9fcd-147">Configuration File</span></span>

<span data-ttu-id="c9fcd-148">這個項目可以用於電腦組態檔和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-148">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="c9fcd-149">範例</span><span class="sxs-lookup"><span data-stu-id="c9fcd-149">Example</span></span>

<span data-ttu-id="c9fcd-150">下列範例說明典型的編譯器組態項目：</span><span class="sxs-lookup"><span data-stu-id="c9fcd-150">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c9fcd-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9fcd-151">See Also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="c9fcd-152">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="c9fcd-152">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="c9fcd-153">\<編譯器 > 項目</span><span class="sxs-lookup"><span data-stu-id="c9fcd-153">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- <span data-ttu-id="c9fcd-154">[指定完整的型別名稱]-(.../../../../../ docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md）</span><span class="sxs-lookup"><span data-stu-id="c9fcd-154">[Specifying Fully Qualified Type Names]-(../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)</span></span>
- <span data-ttu-id="c9fcd-155">[編譯 （ASP.NET 設定結構描述） 之編譯器的 compiler 項目](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c9fcd-155">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span></span>
