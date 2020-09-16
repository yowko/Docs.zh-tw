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
ms.openlocfilehash: 0abbe594754cbd70ec4732a1e7ef98e8e88bf167
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544748"
---
# <a name="compiler-element"></a><span data-ttu-id="c4ad1-102">\<compiler> 項目</span><span class="sxs-lookup"><span data-stu-id="c4ad1-102">\<compiler> Element</span></span>

<span data-ttu-id="c4ad1-103">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-103">Specifies the compiler configuration attributes for a language provider.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compiler>**

## <a name="syntax"></a><span data-ttu-id="c4ad1-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4ad1-104">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4ad1-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c4ad1-105">Attributes and Elements</span></span>

<span data-ttu-id="c4ad1-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4ad1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c4ad1-107">Attributes</span></span>

|<span data-ttu-id="c4ad1-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c4ad1-108">Attribute</span></span>|<span data-ttu-id="c4ad1-109">描述</span><span class="sxs-lookup"><span data-stu-id="c4ad1-109">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="c4ad1-110">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c4ad1-111">指定編譯的其他編譯器特定引數。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-111">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="c4ad1-112">屬性的值 `compilerOptions` 通常會列在編譯器的編譯器選項主題中。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-112">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="c4ad1-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c4ad1-114">提供語言提供者的原始程式檔所使用的副檔名（以分號分隔）。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-114">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="c4ad1-115">例如，".cs"。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-115">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="c4ad1-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="c4ad1-117">提供語言提供者所支援的語言名稱清單（以分號分隔）。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-117">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="c4ad1-118">例如，"C#;cs;csharp"。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-118">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="c4ad1-119">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="c4ad1-120">指定語言提供者的型別名稱，包括包含提供者執行的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-120">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="c4ad1-121">型別名稱必須符合 [指定完整限定型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所定義的需求。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-121">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="c4ad1-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c4ad1-123">指定預設的編譯器警告層級;決定語言提供者將編譯警告視為錯誤的層級。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-123">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c4ad1-124">子元素</span><span class="sxs-lookup"><span data-stu-id="c4ad1-124">Child Elements</span></span>

|<span data-ttu-id="c4ad1-125">項目</span><span class="sxs-lookup"><span data-stu-id="c4ad1-125">Element</span></span>|<span data-ttu-id="c4ad1-126">描述</span><span class="sxs-lookup"><span data-stu-id="c4ad1-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4ad1-127">\<providerOption> 元素</span><span class="sxs-lookup"><span data-stu-id="c4ad1-127">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="c4ad1-128">指定語言提供者的編譯器版本屬性。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-128">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c4ad1-129">父項目</span><span class="sxs-lookup"><span data-stu-id="c4ad1-129">Parent Elements</span></span>

|<span data-ttu-id="c4ad1-130">項目</span><span class="sxs-lookup"><span data-stu-id="c4ad1-130">Element</span></span>|<span data-ttu-id="c4ad1-131">描述</span><span class="sxs-lookup"><span data-stu-id="c4ad1-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4ad1-132">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="c4ad1-132">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="c4ad1-133">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="c4ad1-134">\<system.codedom> 元素</span><span class="sxs-lookup"><span data-stu-id="c4ad1-134">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="c4ad1-135">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-135">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="c4ad1-136">\<compilers> 元素</span><span class="sxs-lookup"><span data-stu-id="c4ad1-136">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="c4ad1-137">編譯器設定元素的容器;包含零或多個 `<compiler>` 元素。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-137">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c4ad1-138">備註</span><span class="sxs-lookup"><span data-stu-id="c4ad1-138">Remarks</span></span>

<span data-ttu-id="c4ad1-139">每個 `<compiler>` 元素都會指定特定語言提供者的編譯器設定屬性。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-139">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="c4ad1-140">提供者會擴充 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 特定語言的類別; 元素會 `<compiler>` 定義語言提供者的編譯器和程式碼產生器設定。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-140">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="c4ad1-141">.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-141">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="c4ad1-142">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-142">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="c4ad1-143">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-143">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="c4ad1-144">應用程式或 Web 設定檔中的編譯器元素可以補充或覆寫電腦設定檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-144">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="c4ad1-145">如果針對相同的語言名稱或相同的副檔名設定了多個提供者，則最後一個相符的設定會覆寫該語言名稱或副檔名的任何先前設定的提供者。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-145">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="c4ad1-146">組態檔</span><span class="sxs-lookup"><span data-stu-id="c4ad1-146">Configuration File</span></span>

<span data-ttu-id="c4ad1-147">此元素可用於電腦設定檔和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="c4ad1-147">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="c4ad1-148">範例</span><span class="sxs-lookup"><span data-stu-id="c4ad1-148">Example</span></span>

<span data-ttu-id="c4ad1-149">下列範例說明典型的編譯器設定元素：</span><span class="sxs-lookup"><span data-stu-id="c4ad1-149">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c4ad1-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4ad1-150">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="c4ad1-151">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="c4ad1-151">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c4ad1-152">\<compilers> 元素</span><span class="sxs-lookup"><span data-stu-id="c4ad1-152">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="c4ad1-153">指定完整的類型名稱</span><span class="sxs-lookup"><span data-stu-id="c4ad1-153">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="c4ad1-154">[編譯之編譯器的 compiler 項目 (ASP.NET 設定結構描述)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c4ad1-154">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
