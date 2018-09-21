---
title: '&lt;system.xml.serialization&gt; 元素'
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: b67c1ec1ec737976e4e50b80b42f34e508dc0224
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493454"
---
# <a name="ltsystemxmlserializationgt-element"></a><span data-ttu-id="380a1-102">&lt;system.xml.serialization&gt; 元素</span><span class="sxs-lookup"><span data-stu-id="380a1-102">&lt;system.xml.serialization&gt; Element</span></span>
<span data-ttu-id="380a1-103">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="380a1-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="380a1-104">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="380a1-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="380a1-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="380a1-105">\<configuration></span></span>  
<span data-ttu-id="380a1-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="380a1-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="380a1-107">語法</span><span class="sxs-lookup"><span data-stu-id="380a1-107">Syntax</span></span>  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="380a1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="380a1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="380a1-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="380a1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="380a1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="380a1-110">Attributes</span></span>  
 <span data-ttu-id="380a1-111">無。</span><span class="sxs-lookup"><span data-stu-id="380a1-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="380a1-112">子元素</span><span class="sxs-lookup"><span data-stu-id="380a1-112">Child Elements</span></span>  
  
|<span data-ttu-id="380a1-113">項目</span><span class="sxs-lookup"><span data-stu-id="380a1-113">Element</span></span>|<span data-ttu-id="380a1-114">描述</span><span class="sxs-lookup"><span data-stu-id="380a1-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="380a1-115">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="380a1-115">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="380a1-116">判斷 <xref:System.DateTime> 物件的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="380a1-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|  
|[<span data-ttu-id="380a1-117">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="380a1-117">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="380a1-118">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 用來對應 XSD 型別至 .NET Framework 型別的型別。</span><span class="sxs-lookup"><span data-stu-id="380a1-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="380a1-119">父項目</span><span class="sxs-lookup"><span data-stu-id="380a1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="380a1-120">項目</span><span class="sxs-lookup"><span data-stu-id="380a1-120">Element</span></span>|<span data-ttu-id="380a1-121">描述</span><span class="sxs-lookup"><span data-stu-id="380a1-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="380a1-122">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="380a1-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="380a1-123">Common Language Runtime 與 .NET Framework 應用程式使用的所有組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="380a1-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="380a1-124">範例</span><span class="sxs-lookup"><span data-stu-id="380a1-124">Example</span></span>  
 <span data-ttu-id="380a1-125">下列程式碼範例描述如何指定 <xref:System.DateTime> 物件的序列化模式，以及在對應 XSD 型別至 .NET Framework 型別時 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的新增型別。</span><span class="sxs-lookup"><span data-stu-id="380a1-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
    <dateTimeSerialization mode = "Local" />  
    <schemaImporterExtensions>  
        <add   
        name = "MobileCapabilities"   
        type = "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neuutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.sxml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="380a1-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="380a1-126">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>  
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
- [<span data-ttu-id="380a1-127">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="380a1-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="380a1-128">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="380a1-128">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
- [<span data-ttu-id="380a1-129">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="380a1-129">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
- [<span data-ttu-id="380a1-130">\<新增 > 項目\<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="380a1-130">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
