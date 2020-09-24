---
title: 編譯器和語言提供者設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- configuration settings [.NET Framework], compilers
- compiler configuration elements, schema
- compiler configuration elements
- language providers
- compiler configuration settings, schema
- configuration schema [.NET Framework], compiler settings
- language providers, settings schema
- compiler configuration settings
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
ms.openlocfilehash: 457e90c92530e04070575e42e3fc282ce45b3d03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153946"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="a67ae-102">編譯器和語言提供者設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a67ae-102">Compiler and Language Provider Settings Schema</span></span>

<span data-ttu-id="a67ae-103">編譯器和語言提供者設定會指定可用語言提供者的編譯器組態項目。</span><span class="sxs-lookup"><span data-stu-id="a67ae-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="a67ae-104">每個編譯器組態項目會指定程式碼提供者的類型名稱、編譯器參數、支援的語言名稱和副檔名。</span><span class="sxs-lookup"><span data-stu-id="a67ae-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
<span data-ttu-id="a67ae-105">.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="a67ae-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="a67ae-106">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="a67ae-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="a67ae-107">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="a67ae-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)
  
|<span data-ttu-id="a67ae-108">項目</span><span class="sxs-lookup"><span data-stu-id="a67ae-108">Element</span></span>|<span data-ttu-id="a67ae-109">描述</span><span class="sxs-lookup"><span data-stu-id="a67ae-109">Description</span></span>|  
|-------------|-----------------|  
|[\<system.codedom>](system-codedom-element.md)|<span data-ttu-id="a67ae-110">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="a67ae-110">Specifies compiler configuration settings for available language providers.</span></span>|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="a67ae-111">編譯器設定元素的容器;包含零或多個 [\<compiler>](compiler-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="a67ae-111">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
|[\<compiler>](compiler-element.md)|<span data-ttu-id="a67ae-112">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="a67ae-112">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a67ae-113">範例</span><span class="sxs-lookup"><span data-stu-id="a67ae-113">Example</span></span>  

 <span data-ttu-id="a67ae-114">下列範例說明典型的編譯器組態項目。</span><span class="sxs-lookup"><span data-stu-id="a67ae-114">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler  
          language="c#;cs;csharp"  
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""  
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a67ae-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a67ae-115">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="a67ae-116">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="a67ae-116">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a67ae-117">\<compiler> 元素</span><span class="sxs-lookup"><span data-stu-id="a67ae-117">\<compiler> Element</span></span>](compiler-element.md)
