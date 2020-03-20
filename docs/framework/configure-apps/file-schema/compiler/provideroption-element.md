---
title: <providerOption> 項目
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155397"
---
# <a name="provideroption-element"></a><span data-ttu-id="bfbff-102">\<提供程式選項>元素</span><span class="sxs-lookup"><span data-stu-id="bfbff-102">\<providerOption> Element</span></span>
<span data-ttu-id="bfbff-103">指定語言提供程式的編譯器版本屬性。</span><span class="sxs-lookup"><span data-stu-id="bfbff-103">Specifies the compiler version attributes for a language provider.</span></span>  

<span data-ttu-id="bfbff-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bfbff-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bfbff-105">&nbsp;&nbsp;[**\<系統.代碼>**](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="bfbff-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="bfbff-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<編譯器>**](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="bfbff-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>\
<span data-ttu-id="bfbff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<編譯器>**](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="bfbff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)</span></span>\
<span data-ttu-id="bfbff-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<供應商選項>**</span><span class="sxs-lookup"><span data-stu-id="bfbff-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**</span></span>

## <a name="syntax"></a><span data-ttu-id="bfbff-109">語法</span><span class="sxs-lookup"><span data-stu-id="bfbff-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfbff-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bfbff-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bfbff-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bfbff-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfbff-112">屬性</span><span class="sxs-lookup"><span data-stu-id="bfbff-112">Attributes</span></span>  
  
|<span data-ttu-id="bfbff-113">屬性</span><span class="sxs-lookup"><span data-stu-id="bfbff-113">Attribute</span></span>|<span data-ttu-id="bfbff-114">描述</span><span class="sxs-lookup"><span data-stu-id="bfbff-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="bfbff-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="bfbff-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="bfbff-116">指定選項的名稱;例如，"編譯器版本"。</span><span class="sxs-lookup"><span data-stu-id="bfbff-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="bfbff-117">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="bfbff-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="bfbff-118">指定選項的值;例如，"v3.5"。</span><span class="sxs-lookup"><span data-stu-id="bfbff-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfbff-119">子元素</span><span class="sxs-lookup"><span data-stu-id="bfbff-119">Child Elements</span></span>  
 <span data-ttu-id="bfbff-120">無。</span><span class="sxs-lookup"><span data-stu-id="bfbff-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bfbff-121">父項目</span><span class="sxs-lookup"><span data-stu-id="bfbff-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bfbff-122">元素</span><span class="sxs-lookup"><span data-stu-id="bfbff-122">Element</span></span>|<span data-ttu-id="bfbff-123">描述</span><span class="sxs-lookup"><span data-stu-id="bfbff-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bfbff-124">\<配置>元素</span><span class="sxs-lookup"><span data-stu-id="bfbff-124">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="bfbff-125">Common Language Runtime 與 .NET Framework 應用程式使用的所有組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="bfbff-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="bfbff-126">\<系統.代碼>元素</span><span class="sxs-lookup"><span data-stu-id="bfbff-126">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="bfbff-127">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="bfbff-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="bfbff-128">\<編譯器>元素</span><span class="sxs-lookup"><span data-stu-id="bfbff-128">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="bfbff-129">用於編譯器配置元素的容器;包含零個或多個`<compiler>`元素。</span><span class="sxs-lookup"><span data-stu-id="bfbff-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="bfbff-130">\<編譯器>元素</span><span class="sxs-lookup"><span data-stu-id="bfbff-130">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="bfbff-131">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="bfbff-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfbff-132">備註</span><span class="sxs-lookup"><span data-stu-id="bfbff-132">Remarks</span></span>  
 <span data-ttu-id="bfbff-133">在 .NET 框架版本 3.5 中，代碼文件物件模型 （CodeDOM） 代碼提供程式可以使用`<providerOption>`元素支援特定于提供程式的選項。</span><span class="sxs-lookup"><span data-stu-id="bfbff-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="bfbff-134">.NET 框架 3.5 包括更新的 .NET 框架 2.0 程式集，並提供包含新類型的新版本 3.5 程式集。</span><span class="sxs-lookup"><span data-stu-id="bfbff-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="bfbff-135">Microsoft C# 和 Visual Basic 代碼提供套裝程式含在 .NET 框架 2.0 程式集中，但已更新以支援版本 3.5 編譯器。</span><span class="sxs-lookup"><span data-stu-id="bfbff-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="bfbff-136">預設情況下，更新的代碼提供程式為版本 2.0 編譯器生成代碼。</span><span class="sxs-lookup"><span data-stu-id="bfbff-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="bfbff-137">可以使用 元素`<providerOption>`將目標編譯器版本更改為 3.5。</span><span class="sxs-lookup"><span data-stu-id="bfbff-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="bfbff-138">為此，請為`name`屬性指定"編譯器版本"，為`value`屬性指定"v3.5"。</span><span class="sxs-lookup"><span data-stu-id="bfbff-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="bfbff-139">必須在版本號前面加上小寫"v"。</span><span class="sxs-lookup"><span data-stu-id="bfbff-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="bfbff-140">通過將元素添加到 .NET 框架 2.0 電腦.config 或 root Web.config 檔，`<providerOption>`可以使版本規範成為全域。</span><span class="sxs-lookup"><span data-stu-id="bfbff-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="bfbff-141">如果在 Machine.config 檔中將預設編譯器版本更新為 3.5，則可以使用應用程式佈建檔中`<providerOption>`的元素，按應用程式將其更改回 2.0。</span><span class="sxs-lookup"><span data-stu-id="bfbff-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="bfbff-142">CodeDOM 代碼提供程式實現者可以通過提供採用`providerOptions`類型 參數<xref:System.Collections.Generic.IDictionary%602>的建構函式來處理自訂選項。</span><span class="sxs-lookup"><span data-stu-id="bfbff-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfbff-143">範例</span><span class="sxs-lookup"><span data-stu-id="bfbff-143">Example</span></span>  
 <span data-ttu-id="bfbff-144">下面的示例演示如何指定應使用 C# 代碼提供程式的版本 3.5。</span><span class="sxs-lookup"><span data-stu-id="bfbff-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bfbff-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfbff-145">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="bfbff-146">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="bfbff-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bfbff-147">\<編譯器>元素</span><span class="sxs-lookup"><span data-stu-id="bfbff-147">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="bfbff-148">指定完整的類型名稱</span><span class="sxs-lookup"><span data-stu-id="bfbff-148">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="bfbff-149">[編譯之編譯器的 compiler 項目 (ASP.NET 設定結構描述)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bfbff-149">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
