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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 8992c9e47e2b62e90191a67fc7353e138502ebf1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185663"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="7756a-102">編譯器和語言提供者設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7756a-102">Compiler and Language Provider Settings Schema</span></span>
<span data-ttu-id="7756a-103">編譯器和語言提供者設定會指定可用語言提供者的編譯器組態項目。</span><span class="sxs-lookup"><span data-stu-id="7756a-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="7756a-104">每個編譯器組態項目會指定程式碼提供者的類型名稱、編譯器參數、支援的語言名稱和副檔名。</span><span class="sxs-lookup"><span data-stu-id="7756a-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
 <span data-ttu-id="7756a-105">.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="7756a-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="7756a-106">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="7756a-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="7756a-107">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="7756a-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 [<span data-ttu-id="7756a-108">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="7756a-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="7756a-109">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="7756a-109">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [<span data-ttu-id="7756a-110">\<compilers></span><span class="sxs-lookup"><span data-stu-id="7756a-110">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [<span data-ttu-id="7756a-111">\<compiler></span><span class="sxs-lookup"><span data-stu-id="7756a-111">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|<span data-ttu-id="7756a-112">元素</span><span class="sxs-lookup"><span data-stu-id="7756a-112">Element</span></span>|<span data-ttu-id="7756a-113">描述</span><span class="sxs-lookup"><span data-stu-id="7756a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7756a-114">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="7756a-114">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="7756a-115">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="7756a-115">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="7756a-116">\<compilers></span><span class="sxs-lookup"><span data-stu-id="7756a-116">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="7756a-117">編譯器組態項目的容器；內含零或多個 [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="7756a-117">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
|[<span data-ttu-id="7756a-118">\<compiler></span><span class="sxs-lookup"><span data-stu-id="7756a-118">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="7756a-119">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="7756a-119">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7756a-120">範例</span><span class="sxs-lookup"><span data-stu-id="7756a-120">Example</span></span>  
 <span data-ttu-id="7756a-121">下列範例說明典型的編譯器組態項目。</span><span class="sxs-lookup"><span data-stu-id="7756a-121">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7756a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7756a-122">See Also</span></span>  
- <xref:System.CodeDom.Compiler.CompilerInfo>  
- <xref:System.CodeDom.Compiler.CodeDomProvider>  
- [<span data-ttu-id="7756a-123">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="7756a-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="7756a-124">\<編譯器> 項目</span><span class="sxs-lookup"><span data-stu-id="7756a-124">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
