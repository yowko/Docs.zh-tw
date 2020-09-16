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
ms.openlocfilehash: 7e006adb86886d22ec08dc61fa092bf677b4da96
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544735"
---
# <a name="provideroption-element"></a><span data-ttu-id="27704-102">\<providerOption> 項目</span><span class="sxs-lookup"><span data-stu-id="27704-102">\<providerOption> Element</span></span>
<span data-ttu-id="27704-103">指定語言提供者的編譯器版本屬性。</span><span class="sxs-lookup"><span data-stu-id="27704-103">Specifies the compiler version attributes for a language provider.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**

## <a name="syntax"></a><span data-ttu-id="27704-104">語法</span><span class="sxs-lookup"><span data-stu-id="27704-104">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27704-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="27704-105">Attributes and Elements</span></span>  
 <span data-ttu-id="27704-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="27704-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27704-107">屬性</span><span class="sxs-lookup"><span data-stu-id="27704-107">Attributes</span></span>  
  
|<span data-ttu-id="27704-108">屬性</span><span class="sxs-lookup"><span data-stu-id="27704-108">Attribute</span></span>|<span data-ttu-id="27704-109">描述</span><span class="sxs-lookup"><span data-stu-id="27704-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="27704-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="27704-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="27704-111">指定選項的名稱;例如，"CompilerVersion"。</span><span class="sxs-lookup"><span data-stu-id="27704-111">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="27704-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="27704-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="27704-113">指定選項的值。例如「v 3.5」。</span><span class="sxs-lookup"><span data-stu-id="27704-113">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27704-114">子元素</span><span class="sxs-lookup"><span data-stu-id="27704-114">Child Elements</span></span>  
 <span data-ttu-id="27704-115">無。</span><span class="sxs-lookup"><span data-stu-id="27704-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27704-116">父項目</span><span class="sxs-lookup"><span data-stu-id="27704-116">Parent Elements</span></span>  
  
|<span data-ttu-id="27704-117">項目</span><span class="sxs-lookup"><span data-stu-id="27704-117">Element</span></span>|<span data-ttu-id="27704-118">描述</span><span class="sxs-lookup"><span data-stu-id="27704-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27704-119">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="27704-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="27704-120">Common Language Runtime 與 .NET Framework 應用程式使用的所有組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="27704-120">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="27704-121">\<system.codedom> 元素</span><span class="sxs-lookup"><span data-stu-id="27704-121">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="27704-122">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="27704-122">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="27704-123">\<compilers> 元素</span><span class="sxs-lookup"><span data-stu-id="27704-123">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="27704-124">編譯器設定元素的容器;包含零或多個 `<compiler>` 元素。</span><span class="sxs-lookup"><span data-stu-id="27704-124">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="27704-125">\<compiler> 元素</span><span class="sxs-lookup"><span data-stu-id="27704-125">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="27704-126">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="27704-126">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27704-127">備註</span><span class="sxs-lookup"><span data-stu-id="27704-127">Remarks</span></span>  
 <span data-ttu-id="27704-128">在 .NET Framework 3.5 版中，程式碼檔物件模型 (CodeDOM) 程式碼提供者可以使用專案來支援提供者特定的選項 `<providerOption>` 。</span><span class="sxs-lookup"><span data-stu-id="27704-128">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="27704-129">.NET Framework 3.5 包含更新的 .NET Framework 2.0 元件，並提供新的3.5 版元件，其中包含新的類型。</span><span class="sxs-lookup"><span data-stu-id="27704-129">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="27704-130">Microsoft c # 和 Visual Basic 程式碼提供者包含在 .NET Framework 2.0 元件中，但已更新為支援3.5 版編譯器。</span><span class="sxs-lookup"><span data-stu-id="27704-130">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="27704-131">根據預設，更新的程式碼提供者會產生2.0 版編譯器的程式碼。</span><span class="sxs-lookup"><span data-stu-id="27704-131">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="27704-132">您可以使用 `<providerOption>` 元素將目標編譯器版本變更為3.5。</span><span class="sxs-lookup"><span data-stu-id="27704-132">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="27704-133">若要這樣做，請指定 "CompilerVersion" 作為 `name` 屬性，並指定 "v 3.5" 作為 `value` 屬性。</span><span class="sxs-lookup"><span data-stu-id="27704-133">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="27704-134">您必須在版本號碼之前加上小寫的 "v"。</span><span class="sxs-lookup"><span data-stu-id="27704-134">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="27704-135">您可以將專案新增 `<providerOption>` 至 .NET Framework 2.0 Machine.config 或根 Web.config 檔，以將版本規格設為全域。</span><span class="sxs-lookup"><span data-stu-id="27704-135">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="27704-136">如果您將 Machine.config 檔案中的預設編譯器版本更新為3.5，您可以使用 `<providerOption>` 應用程式佈建檔中的專案，以每個應用程式為基礎將它變更回2.0。</span><span class="sxs-lookup"><span data-stu-id="27704-136">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="27704-137">CodeDOM 程式碼提供者可提供接受型別參數的函式，來處理自訂選項 `providerOptions` <xref:System.Collections.Generic.IDictionary%602> 。</span><span class="sxs-lookup"><span data-stu-id="27704-137">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27704-138">範例</span><span class="sxs-lookup"><span data-stu-id="27704-138">Example</span></span>  
 <span data-ttu-id="27704-139">下列範例將示範如何指定應該使用版本3.5 的 c # 程式碼提供者。</span><span class="sxs-lookup"><span data-stu-id="27704-139">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="27704-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27704-140">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="27704-141">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="27704-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="27704-142">\<compilers> 元素</span><span class="sxs-lookup"><span data-stu-id="27704-142">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="27704-143">指定完整的類型名稱</span><span class="sxs-lookup"><span data-stu-id="27704-143">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="27704-144">[編譯之編譯器的 compiler 項目 (ASP.NET 設定結構描述)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="27704-144">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
