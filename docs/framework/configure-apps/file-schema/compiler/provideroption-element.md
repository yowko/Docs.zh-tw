---
title: '&lt;providerOption&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 449bc1a7f9d74ba9b38d70ef36303e0ff399c187
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182577"
---
# <a name="ltprovideroptiongt-element"></a><span data-ttu-id="dcd19-102">&lt;providerOption&gt;項目</span><span class="sxs-lookup"><span data-stu-id="dcd19-102">&lt;providerOption&gt; Element</span></span>
<span data-ttu-id="dcd19-103">指定的語言提供者的編譯器版本屬性。</span><span class="sxs-lookup"><span data-stu-id="dcd19-103">Specifies the compiler version attributes for a language provider.</span></span>  
  
 <span data-ttu-id="dcd19-104">\<組態項目 ></span><span class="sxs-lookup"><span data-stu-id="dcd19-104">\<configuration Element></span></span>  
<span data-ttu-id="dcd19-105">\<system.codedom 項目 ></span><span class="sxs-lookup"><span data-stu-id="dcd19-105">\<system.codedom Element></span></span>  
<span data-ttu-id="dcd19-106">\<compilers 項目 ></span><span class="sxs-lookup"><span data-stu-id="dcd19-106">\<compilers Element></span></span>  
<span data-ttu-id="dcd19-107">\<編譯器 > 項目</span><span class="sxs-lookup"><span data-stu-id="dcd19-107">\<compiler> Element</span></span>  
<span data-ttu-id="dcd19-108">\<providerOption > 項目</span><span class="sxs-lookup"><span data-stu-id="dcd19-108">\<providerOption> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcd19-109">語法</span><span class="sxs-lookup"><span data-stu-id="dcd19-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcd19-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dcd19-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dcd19-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dcd19-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcd19-112">屬性</span><span class="sxs-lookup"><span data-stu-id="dcd19-112">Attributes</span></span>  
  
|<span data-ttu-id="dcd19-113">屬性</span><span class="sxs-lookup"><span data-stu-id="dcd19-113">Attribute</span></span>|<span data-ttu-id="dcd19-114">描述</span><span class="sxs-lookup"><span data-stu-id="dcd19-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="dcd19-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="dcd19-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="dcd19-116">指定名稱的選項;例如，"CompilerVersion。 」</span><span class="sxs-lookup"><span data-stu-id="dcd19-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="dcd19-117">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="dcd19-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="dcd19-118">指定的選項; 的值例如，"v3.5。"</span><span class="sxs-lookup"><span data-stu-id="dcd19-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcd19-119">子元素</span><span class="sxs-lookup"><span data-stu-id="dcd19-119">Child Elements</span></span>  
 <span data-ttu-id="dcd19-120">無。</span><span class="sxs-lookup"><span data-stu-id="dcd19-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dcd19-121">父項目</span><span class="sxs-lookup"><span data-stu-id="dcd19-121">Parent Elements</span></span>  
  
|<span data-ttu-id="dcd19-122">項目</span><span class="sxs-lookup"><span data-stu-id="dcd19-122">Element</span></span>|<span data-ttu-id="dcd19-123">描述</span><span class="sxs-lookup"><span data-stu-id="dcd19-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcd19-124">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="dcd19-124">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="dcd19-125">Common Language Runtime 與 .NET Framework 應用程式使用的所有組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="dcd19-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="dcd19-126">\<system.codedom > 項目</span><span class="sxs-lookup"><span data-stu-id="dcd19-126">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="dcd19-127">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="dcd19-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="dcd19-128">\<編譯器 > 項目</span><span class="sxs-lookup"><span data-stu-id="dcd19-128">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="dcd19-129">編譯器組態項目; 容器包含零或多個`<compiler>`項目。</span><span class="sxs-lookup"><span data-stu-id="dcd19-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="dcd19-130">\<編譯器> 項目</span><span class="sxs-lookup"><span data-stu-id="dcd19-130">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="dcd19-131">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="dcd19-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcd19-132">備註</span><span class="sxs-lookup"><span data-stu-id="dcd19-132">Remarks</span></span>  
 <span data-ttu-id="dcd19-133">在.NET Framework 3.5 版中，程式碼文件物件模型 (CodeDOM) 的程式碼提供者可以使用支援提供者特定選項`<providerOption>`項目。</span><span class="sxs-lookup"><span data-stu-id="dcd19-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="dcd19-134">.NET Framework 3.5 包含更新的.NET Framework 2.0 組件，並提供新的 3.5 版組件包含新的類型。</span><span class="sxs-lookup"><span data-stu-id="dcd19-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="dcd19-135">Microsoft C# 和 Visual Basic 程式碼提供者會包含在.NET Framework 2.0 組件，但已更新為支援版本 3.5 編譯器。</span><span class="sxs-lookup"><span data-stu-id="dcd19-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="dcd19-136">根據預設，更新的程式碼提供者會產生適用於版本 2.0 編譯器的程式碼。</span><span class="sxs-lookup"><span data-stu-id="dcd19-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="dcd19-137">您可以使用`<providerOption>`項目，若要變更目標的編譯器版本為 3.5。</span><span class="sxs-lookup"><span data-stu-id="dcd19-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="dcd19-138">若要這樣做，請指定"CompilerVersion 」`name`屬性和"v3.5"，如`value`屬性。</span><span class="sxs-lookup"><span data-stu-id="dcd19-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="dcd19-139">您必須在之前的版本號碼，以小寫的"v"。</span><span class="sxs-lookup"><span data-stu-id="dcd19-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="dcd19-140">您可以藉此版本規格全域新增`<providerOption>`.NET Framework 2.0 Machine.config 或根 Web.config 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="dcd19-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="dcd19-141">如果您更新預設的編譯器版本 3.5 Machine.config 檔案中，您可以將它變更回 2.0 針對每個應用程式使用`<providerOption>`應用程式組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="dcd19-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="dcd19-142">CodeDOM 程式碼提供者實作器可以處理自訂的選項，藉由提供的建構函式`providerOptions`型別的參數<xref:System.Collections.Generic.IDictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="dcd19-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcd19-143">範例</span><span class="sxs-lookup"><span data-stu-id="dcd19-143">Example</span></span>  
 <span data-ttu-id="dcd19-144">下列範例示範如何指定應該用於 3.5 版的 C# 程式碼提供者。</span><span class="sxs-lookup"><span data-stu-id="dcd19-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dcd19-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcd19-145">See Also</span></span>  
- <xref:System.CodeDom.Compiler.CompilerInfo>  
- <xref:System.CodeDom.Compiler.CodeDomProvider>  
- [<span data-ttu-id="dcd19-146">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="dcd19-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="dcd19-147">\<編譯器 > 項目</span><span class="sxs-lookup"><span data-stu-id="dcd19-147">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
- [<span data-ttu-id="dcd19-148">指定完整的類型名稱</span><span class="sxs-lookup"><span data-stu-id="dcd19-148">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
- [<span data-ttu-id="dcd19-149">編譯 （ASP.NET 設定結構描述） 之編譯器的 compiler 項目</span><span class="sxs-lookup"><span data-stu-id="dcd19-149">compiler Element for compilers for compilation (ASP.NET Settings Schema)</span></span>](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
