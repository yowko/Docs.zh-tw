---
title: <schemaImporterExtensions> 項目
description: <schemaImporterExtensions>元素包含 XmlSchemaImporter 用來將 XSD 類型對應至 .NET Framework 類型的類型。
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5b9820ccdf2c75bed9beda72358c4c4d82ff9ff7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379796"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="2a1a2-103">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="2a1a2-103">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="2a1a2-104">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 用來對應 XSD 型別至 .NET Framework 型別的型別。</span><span class="sxs-lookup"><span data-stu-id="2a1a2-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="2a1a2-105">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2a1a2-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a1a2-106">語法</span><span class="sxs-lookup"><span data-stu-id="2a1a2-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="2a1a2-107">子元素</span><span class="sxs-lookup"><span data-stu-id="2a1a2-107">Child Elements</span></span>  
  
|<span data-ttu-id="2a1a2-108">元素</span><span class="sxs-lookup"><span data-stu-id="2a1a2-108">Element</span></span>|<span data-ttu-id="2a1a2-109">描述</span><span class="sxs-lookup"><span data-stu-id="2a1a2-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a1a2-110">\<新增 schemaImporterExtensions>的> 元素 \<</span><span class="sxs-lookup"><span data-stu-id="2a1a2-110">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="2a1a2-111">新增 <xref:System.Xml.Serialization.XmlSchemaImporter> 所使用的類型來建立對應。</span><span class="sxs-lookup"><span data-stu-id="2a1a2-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="2a1a2-112">父項目</span><span class="sxs-lookup"><span data-stu-id="2a1a2-112">Parent Elements</span></span>  
  
|<span data-ttu-id="2a1a2-113">元素</span><span class="sxs-lookup"><span data-stu-id="2a1a2-113">Element</span></span>|<span data-ttu-id="2a1a2-114">描述</span><span class="sxs-lookup"><span data-stu-id="2a1a2-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a1a2-115">\<> 元素的 system.object 序列化</span><span class="sxs-lookup"><span data-stu-id="2a1a2-115">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="2a1a2-116">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="2a1a2-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2a1a2-117">範例</span><span class="sxs-lookup"><span data-stu-id="2a1a2-117">Example</span></span>  
 <span data-ttu-id="2a1a2-118">下列程式碼範例描述如何加入 <xref:System.Xml.Serialization.XmlSchemaImporter> 在對應 XSD 型別至 .NET Framework 型別時使用的型別。</span><span class="sxs-lookup"><span data-stu-id="2a1a2-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2a1a2-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a1a2-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="2a1a2-120">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="2a1a2-120">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="2a1a2-121">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="2a1a2-121">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="2a1a2-122">\<新增 schemaImporterExtensions>的> 元素 \<</span><span class="sxs-lookup"><span data-stu-id="2a1a2-122">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="2a1a2-123">\<> 元素的 system.object 序列化</span><span class="sxs-lookup"><span data-stu-id="2a1a2-123">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
