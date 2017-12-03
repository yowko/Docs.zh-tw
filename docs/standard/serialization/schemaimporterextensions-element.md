---
title: "&lt;schemaImporterExtensions&gt; 元素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0296b207af0ed439c90374eb6db21fe11e00dd42
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltschemaimporterextensionsgt-element"></a><span data-ttu-id="20fc3-102">&lt;schemaImporterExtensions&gt; 元素</span><span class="sxs-lookup"><span data-stu-id="20fc3-102">&lt;schemaImporterExtensions&gt; Element</span></span>
<span data-ttu-id="20fc3-103">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 用來對應 XSD 型別至 .NET Framework 型別的型別。</span><span class="sxs-lookup"><span data-stu-id="20fc3-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="20fc3-104">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="20fc3-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20fc3-105">語法</span><span class="sxs-lookup"><span data-stu-id="20fc3-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="20fc3-106">子元素</span><span class="sxs-lookup"><span data-stu-id="20fc3-106">Child Elements</span></span>  
  
|<span data-ttu-id="20fc3-107">項目</span><span class="sxs-lookup"><span data-stu-id="20fc3-107">Element</span></span>|<span data-ttu-id="20fc3-108">說明</span><span class="sxs-lookup"><span data-stu-id="20fc3-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20fc3-109">\<xmlSchemaImporterExtensions> 的 \<add> 項目</span><span class="sxs-lookup"><span data-stu-id="20fc3-109">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|<span data-ttu-id="20fc3-110">新增 <xref:System.Xml.Serialization.XmlSchemaImporter> 所使用的類型來建立對應。</span><span class="sxs-lookup"><span data-stu-id="20fc3-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="20fc3-111">父項目</span><span class="sxs-lookup"><span data-stu-id="20fc3-111">Parent Elements</span></span>  
  
|<span data-ttu-id="20fc3-112">項目</span><span class="sxs-lookup"><span data-stu-id="20fc3-112">Element</span></span>|<span data-ttu-id="20fc3-113">說明</span><span class="sxs-lookup"><span data-stu-id="20fc3-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20fc3-114">\<system.xml.serialization> 項目</span><span class="sxs-lookup"><span data-stu-id="20fc3-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="20fc3-115">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="20fc3-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="20fc3-116">範例</span><span class="sxs-lookup"><span data-stu-id="20fc3-116">Example</span></span>  
 <span data-ttu-id="20fc3-117">下列程式碼範例描述如何加入 <xref:System.Xml.Serialization.XmlSchemaImporter> 在對應 XSD 型別至 .NET Framework 型別時使用的型別。</span><span class="sxs-lookup"><span data-stu-id="20fc3-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
/system.sxml.serializaiton>  
```  
  
## <a name="see-also"></a><span data-ttu-id="20fc3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20fc3-118">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="20fc3-119">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="20fc3-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="20fc3-120">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="20fc3-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="20fc3-121">\<xmlSchemaImporterExtensions> 的 \<add> 項目</span><span class="sxs-lookup"><span data-stu-id="20fc3-121">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [<span data-ttu-id="20fc3-122">\<system.xml.serialization> 項目</span><span class="sxs-lookup"><span data-stu-id="20fc3-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
