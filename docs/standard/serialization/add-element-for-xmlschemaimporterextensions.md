---
title: "&lt;xmlSchemaImporterExtensions&gt; 的 &lt;add&gt; 元素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <xmlSchemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd73d6dfe6659cd973054a14d0d4e5e73d3cd8d7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-element-for-ltxmlschemaimporterextensionsgt"></a><span data-ttu-id="59617-102">&lt;xmlSchemaImporterExtensions&gt; 的 &lt;add&gt; 元素</span><span class="sxs-lookup"><span data-stu-id="59617-102">&lt;add&gt; Element for &lt;xmlSchemaImporterExtensions&gt;</span></span>
<span data-ttu-id="59617-103">加入 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的型別，將 XSD 型別對應至 .NET Framework 型別。</span><span class="sxs-lookup"><span data-stu-id="59617-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="59617-104">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="59617-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="59617-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="59617-105">\<configuration></span></span>  
<span data-ttu-id="59617-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="59617-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="59617-107">\<XmlSchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="59617-107">\<XmlSchemaImporterExtensions></span></span>  
<span data-ttu-id="59617-108">\<add></span><span class="sxs-lookup"><span data-stu-id="59617-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59617-109">語法</span><span class="sxs-lookup"><span data-stu-id="59617-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59617-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="59617-110">Attributes and Elements</span></span>  
 <span data-ttu-id="59617-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="59617-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59617-112">屬性</span><span class="sxs-lookup"><span data-stu-id="59617-112">Attributes</span></span>  
  
|<span data-ttu-id="59617-113">屬性</span><span class="sxs-lookup"><span data-stu-id="59617-113">Attribute</span></span>|<span data-ttu-id="59617-114">說明</span><span class="sxs-lookup"><span data-stu-id="59617-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59617-115">**name**</span><span class="sxs-lookup"><span data-stu-id="59617-115">**name**</span></span>|<span data-ttu-id="59617-116">用來尋找執行個體的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="59617-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="59617-117">**type**</span><span class="sxs-lookup"><span data-stu-id="59617-117">**type**</span></span>|<span data-ttu-id="59617-118">必要項。</span><span class="sxs-lookup"><span data-stu-id="59617-118">Required.</span></span> <span data-ttu-id="59617-119">指定要加入的結構描述擴充功能類別。</span><span class="sxs-lookup"><span data-stu-id="59617-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="59617-120">**type** 屬性值必須在同一行，且包括完整類型名稱。</span><span class="sxs-lookup"><span data-stu-id="59617-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="59617-121">當組件置於全域組件快取 (GAC) 中時，也必須包含簽署組件的版本、文化特性和公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="59617-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59617-122">子元素</span><span class="sxs-lookup"><span data-stu-id="59617-122">Child Elements</span></span>  
 <span data-ttu-id="59617-123">無。</span><span class="sxs-lookup"><span data-stu-id="59617-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59617-124">父項目</span><span class="sxs-lookup"><span data-stu-id="59617-124">Parent Elements</span></span>  
  
|<span data-ttu-id="59617-125">項目</span><span class="sxs-lookup"><span data-stu-id="59617-125">Element</span></span>|<span data-ttu-id="59617-126">說明</span><span class="sxs-lookup"><span data-stu-id="59617-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="59617-127">\<xmlSchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="59617-127">\<xmlSchemaImporterExtensions></span></span>|<span data-ttu-id="59617-128">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的型別。</span><span class="sxs-lookup"><span data-stu-id="59617-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="59617-129">範例</span><span class="sxs-lookup"><span data-stu-id="59617-129">Example</span></span>  
 <span data-ttu-id="59617-130">下列程式碼範例會加入 XmlSchemaImporter 在對應型別時可使用的副檔名類型。</span><span class="sxs-lookup"><span data-stu-id="59617-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSchemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,   
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a" />   
    </xmlSchemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="59617-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59617-131">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 [<span data-ttu-id="59617-132">\<system.xml.serialization> 項目</span><span class="sxs-lookup"><span data-stu-id="59617-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="59617-133">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="59617-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
