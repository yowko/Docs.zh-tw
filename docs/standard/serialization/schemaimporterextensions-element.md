---
title: <schemaImporterExtensions> 項目
description: <schemaImporterExtensions>元素包含 XmlSchemaImporter 用來將 XSD 類型對應至 .NET Framework 類型的類型。
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: c46c5cb6e01463723f0f2ce3873fb4a6ec0b4e60
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "84278398"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="601ea-103">\<schemaImporterExtensions> 項目</span><span class="sxs-lookup"><span data-stu-id="601ea-103">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="601ea-104">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 用來對應 XSD 型別至 .NET Framework 型別的型別。</span><span class="sxs-lookup"><span data-stu-id="601ea-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="601ea-105">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="601ea-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="601ea-106">語法</span><span class="sxs-lookup"><span data-stu-id="601ea-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="601ea-107">子元素</span><span class="sxs-lookup"><span data-stu-id="601ea-107">Child Elements</span></span>  
  
|<span data-ttu-id="601ea-108">元素</span><span class="sxs-lookup"><span data-stu-id="601ea-108">Element</span></span>|<span data-ttu-id="601ea-109">描述</span><span class="sxs-lookup"><span data-stu-id="601ea-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="601ea-110">\<add>的元素\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="601ea-110">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)|<span data-ttu-id="601ea-111">新增 <xref:System.Xml.Serialization.XmlSchemaImporter> 所使用的類型來建立對應。</span><span class="sxs-lookup"><span data-stu-id="601ea-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="601ea-112">父項目</span><span class="sxs-lookup"><span data-stu-id="601ea-112">Parent Elements</span></span>  
  
|<span data-ttu-id="601ea-113">元素</span><span class="sxs-lookup"><span data-stu-id="601ea-113">Element</span></span>|<span data-ttu-id="601ea-114">描述</span><span class="sxs-lookup"><span data-stu-id="601ea-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="601ea-115">\<system.xml.serialization>元素</span><span class="sxs-lookup"><span data-stu-id="601ea-115">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="601ea-116">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="601ea-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="601ea-117">範例</span><span class="sxs-lookup"><span data-stu-id="601ea-117">Example</span></span>  
 <span data-ttu-id="601ea-118">下列程式碼範例描述如何加入 <xref:System.Xml.Serialization.XmlSchemaImporter> 在對應 XSD 型別至 .NET Framework 型別時使用的型別。</span><span class="sxs-lookup"><span data-stu-id="601ea-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =
        "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="601ea-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="601ea-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="601ea-120">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="601ea-120">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="601ea-121">\<dateTimeSerialization>元素</span><span class="sxs-lookup"><span data-stu-id="601ea-121">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="601ea-122">\<add>的元素\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="601ea-122">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="601ea-123">\<system.xml.serialization>元素</span><span class="sxs-lookup"><span data-stu-id="601ea-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
