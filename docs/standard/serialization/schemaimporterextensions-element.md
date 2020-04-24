---
title: <schemaImporterExtensions> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5ed80ac370e34d6b62bb2b601cb7bd978228a302
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159815"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="2c0fe-102">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="2c0fe-102">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="2c0fe-103">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 用來對應 XSD 型別至 .NET Framework 型別的型別。</span><span class="sxs-lookup"><span data-stu-id="2c0fe-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="2c0fe-104">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2c0fe-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c0fe-105">語法</span><span class="sxs-lookup"><span data-stu-id="2c0fe-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="2c0fe-106">子元素</span><span class="sxs-lookup"><span data-stu-id="2c0fe-106">Child Elements</span></span>  
  
|<span data-ttu-id="2c0fe-107">元素</span><span class="sxs-lookup"><span data-stu-id="2c0fe-107">Element</span></span>|<span data-ttu-id="2c0fe-108">描述</span><span class="sxs-lookup"><span data-stu-id="2c0fe-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c0fe-109">\<新增 schemaImporterExtensions>的\<> 元素</span><span class="sxs-lookup"><span data-stu-id="2c0fe-109">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="2c0fe-110">新增 <xref:System.Xml.Serialization.XmlSchemaImporter> 所使用的類型來建立對應。</span><span class="sxs-lookup"><span data-stu-id="2c0fe-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="2c0fe-111">父項目</span><span class="sxs-lookup"><span data-stu-id="2c0fe-111">Parent Elements</span></span>  
  
|<span data-ttu-id="2c0fe-112">元素</span><span class="sxs-lookup"><span data-stu-id="2c0fe-112">Element</span></span>|<span data-ttu-id="2c0fe-113">描述</span><span class="sxs-lookup"><span data-stu-id="2c0fe-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c0fe-114">\<> 元素的 system.object 序列化</span><span class="sxs-lookup"><span data-stu-id="2c0fe-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="2c0fe-115">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="2c0fe-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2c0fe-116">範例</span><span class="sxs-lookup"><span data-stu-id="2c0fe-116">Example</span></span>  
 <span data-ttu-id="2c0fe-117">下列程式碼範例描述如何加入 <xref:System.Xml.Serialization.XmlSchemaImporter> 在對應 XSD 型別至 .NET Framework 型別時使用的型別。</span><span class="sxs-lookup"><span data-stu-id="2c0fe-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c0fe-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c0fe-118">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="2c0fe-119">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="2c0fe-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="2c0fe-120">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="2c0fe-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="2c0fe-121">\<新增 schemaImporterExtensions>的\<> 元素</span><span class="sxs-lookup"><span data-stu-id="2c0fe-121">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="2c0fe-122">\<> 元素的 system.object 序列化</span><span class="sxs-lookup"><span data-stu-id="2c0fe-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
