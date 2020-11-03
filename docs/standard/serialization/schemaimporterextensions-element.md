---
title: <schemaImporterExtensions> 項目
description: <schemaImporterExtensions>元素包含 XmlSchemaImporter 用來將 XSD 類型對應至 .net 類型的類型。
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 35626618a8dd7c63a7008d10bc3568484836a488
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282272"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="72821-103">\<schemaImporterExtensions> 項目</span><span class="sxs-lookup"><span data-stu-id="72821-103">\<schemaImporterExtensions> element</span></span>

<span data-ttu-id="72821-104">包含用來將 <xref:System.Xml.Serialization.XmlSchemaImporter> XSD 類型對應至 .net 類型的類型。</span><span class="sxs-lookup"><span data-stu-id="72821-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET types.</span></span> <span data-ttu-id="72821-105">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="72821-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72821-106">語法</span><span class="sxs-lookup"><span data-stu-id="72821-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="72821-107">子元素</span><span class="sxs-lookup"><span data-stu-id="72821-107">Child Elements</span></span>  
  
|<span data-ttu-id="72821-108">項目</span><span class="sxs-lookup"><span data-stu-id="72821-108">Element</span></span>|<span data-ttu-id="72821-109">描述</span><span class="sxs-lookup"><span data-stu-id="72821-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72821-110">\<add> 的元素 \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="72821-110">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)|<span data-ttu-id="72821-111">新增 <xref:System.Xml.Serialization.XmlSchemaImporter> 所使用的類型來建立對應。</span><span class="sxs-lookup"><span data-stu-id="72821-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="72821-112">父項目</span><span class="sxs-lookup"><span data-stu-id="72821-112">Parent Elements</span></span>  
  
|<span data-ttu-id="72821-113">項目</span><span class="sxs-lookup"><span data-stu-id="72821-113">Element</span></span>|<span data-ttu-id="72821-114">描述</span><span class="sxs-lookup"><span data-stu-id="72821-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72821-115">\<system.xml.serialization> 元素</span><span class="sxs-lookup"><span data-stu-id="72821-115">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="72821-116">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="72821-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="72821-117">範例</span><span class="sxs-lookup"><span data-stu-id="72821-117">Example</span></span>  
 <span data-ttu-id="72821-118">下列程式碼範例說明如何 <xref:System.Xml.Serialization.XmlSchemaImporter> 在將 XSD 類型對應至 .net 類型時，加入所使用的類型。</span><span class="sxs-lookup"><span data-stu-id="72821-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72821-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72821-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="72821-120">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="72821-120">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="72821-121">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="72821-121">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="72821-122">\<add> 的元素 \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="72821-122">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="72821-123">\<system.xml.serialization> 元素</span><span class="sxs-lookup"><span data-stu-id="72821-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
