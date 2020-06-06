---
title: <compilers> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 09b1efe321c39402c9280eda0e9def9112462470
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155410"
---
# <a name="compilers-element"></a><span data-ttu-id="e1be0-102">\<compilers> 項目</span><span class="sxs-lookup"><span data-stu-id="e1be0-102">\<compilers> Element</span></span>
<span data-ttu-id="e1be0-103">編譯器設定元素的容器;包含零個或多個 [\<compiler>](compiler-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="e1be0-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**

## <a name="syntax"></a><span data-ttu-id="e1be0-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1be0-104">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1be0-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e1be0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e1be0-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e1be0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1be0-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e1be0-107">Attributes</span></span>  
 <span data-ttu-id="e1be0-108">無。</span><span class="sxs-lookup"><span data-stu-id="e1be0-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e1be0-109">子元素</span><span class="sxs-lookup"><span data-stu-id="e1be0-109">Child Elements</span></span>  
  
|<span data-ttu-id="e1be0-110">元素</span><span class="sxs-lookup"><span data-stu-id="e1be0-110">Element</span></span>|<span data-ttu-id="e1be0-111">描述</span><span class="sxs-lookup"><span data-stu-id="e1be0-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1be0-112">\<compiler>元素</span><span class="sxs-lookup"><span data-stu-id="e1be0-112">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="e1be0-113">指定語言提供者的編譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="e1be0-113">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e1be0-114">父項目</span><span class="sxs-lookup"><span data-stu-id="e1be0-114">Parent Elements</span></span>  
  
|<span data-ttu-id="e1be0-115">元素</span><span class="sxs-lookup"><span data-stu-id="e1be0-115">Element</span></span>|<span data-ttu-id="e1be0-116">描述</span><span class="sxs-lookup"><span data-stu-id="e1be0-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1be0-117">\<configuration>元素</span><span class="sxs-lookup"><span data-stu-id="e1be0-117">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="e1be0-118">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e1be0-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="e1be0-119">\<system.codedom>元素</span><span class="sxs-lookup"><span data-stu-id="e1be0-119">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="e1be0-120">指定可用語言提供者的編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="e1be0-120">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1be0-121">備註</span><span class="sxs-lookup"><span data-stu-id="e1be0-121">Remarks</span></span>  
 <span data-ttu-id="e1be0-122">[\<compilers>](compilers-element.md)元素包含電腦上語言提供者的編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="e1be0-122">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="e1be0-123">每個 [\<compiler>](compiler-element.md) 元素都會指定特定語言提供者的編譯器設定屬性。</span><span class="sxs-lookup"><span data-stu-id="e1be0-123">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="e1be0-124">.NET Framework 會定義電腦設定檔（Machine.config）中的初始編譯器和語言提供者設定。</span><span class="sxs-lookup"><span data-stu-id="e1be0-124">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="e1be0-125">開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 實作新增組態設定。</span><span class="sxs-lookup"><span data-stu-id="e1be0-125">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="e1be0-126">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。</span><span class="sxs-lookup"><span data-stu-id="e1be0-126">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="e1be0-127">組態檔</span><span class="sxs-lookup"><span data-stu-id="e1be0-127">Configuration File</span></span>  
 <span data-ttu-id="e1be0-128">此元素可以在電腦設定檔和應用程式佈建檔中使用。</span><span class="sxs-lookup"><span data-stu-id="e1be0-128">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1be0-129">範例</span><span class="sxs-lookup"><span data-stu-id="e1be0-129">Example</span></span>  
 <span data-ttu-id="e1be0-130">下列範例說明典型的編譯器組態項目。</span><span class="sxs-lookup"><span data-stu-id="e1be0-130">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e1be0-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1be0-131">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="e1be0-132">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="e1be0-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e1be0-133">編譯器和語言提供者設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e1be0-133">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e1be0-134">\<compiler>元素</span><span class="sxs-lookup"><span data-stu-id="e1be0-134">\<compiler> Element</span></span>](compiler-element.md)
