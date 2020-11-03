---
title: <system.xml.serialization> 項目
description: 本文描述 <的 system.xml 序列化> 元素，這是用來控制 XML 序列化的最上層元素。
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 6291799aadc429e943996f2256d773ac36dd370f
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282394"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="ec882-103">\<system.xml.serialization> 項目</span><span class="sxs-lookup"><span data-stu-id="ec882-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="ec882-104">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="ec882-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="ec882-105">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ec882-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a><span data-ttu-id="ec882-106">語法</span><span class="sxs-lookup"><span data-stu-id="ec882-106">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec882-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ec882-107">Attributes and Elements</span></span>

<span data-ttu-id="ec882-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ec882-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec882-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ec882-109">Attributes</span></span>

<span data-ttu-id="ec882-110">無。</span><span class="sxs-lookup"><span data-stu-id="ec882-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ec882-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ec882-111">Child Elements</span></span>

|<span data-ttu-id="ec882-112">項目</span><span class="sxs-lookup"><span data-stu-id="ec882-112">Element</span></span>|<span data-ttu-id="ec882-113">描述</span><span class="sxs-lookup"><span data-stu-id="ec882-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec882-114">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="ec882-114">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)|<span data-ttu-id="ec882-115">判斷 <xref:System.DateTime> 物件的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="ec882-115">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="ec882-116">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="ec882-116">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)|<span data-ttu-id="ec882-117">包含用來將 <xref:System.Xml.Serialization.XmlSchemaImporter> XSD 類型對應至 .net 類型的類型。</span><span class="sxs-lookup"><span data-stu-id="ec882-117">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ec882-118">父項目</span><span class="sxs-lookup"><span data-stu-id="ec882-118">Parent Elements</span></span>

|<span data-ttu-id="ec882-119">項目</span><span class="sxs-lookup"><span data-stu-id="ec882-119">Element</span></span>|<span data-ttu-id="ec882-120">描述</span><span class="sxs-lookup"><span data-stu-id="ec882-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec882-121">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="ec882-121">\<configuration> Element</span></span>](../../framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="ec882-122">Common Language Runtime 與 .NET Framework 應用程式使用的所有組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ec882-122">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="ec882-123">範例</span><span class="sxs-lookup"><span data-stu-id="ec882-123">Example</span></span>

<span data-ttu-id="ec882-124">下列程式碼範例說明如何指定物件的序列化模式 <xref:System.DateTime> ，以及在將 <xref:System.Xml.Serialization.XmlSchemaImporter> XSD 類型對應至 .net 類型時，所使用的型別加入。</span><span class="sxs-lookup"><span data-stu-id="ec882-124">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET types.</span></span>

```xml
<system.xml.serialization>
    <xmlSerializer checkDeserializeAdvances="false" />
    <dateTimeSerialization mode = "Local" />
    <schemaImporterExtensions>
        <add
        name = "MobileCapabilities"
        type = "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f6f11d40a3a" />
    </schemaImporterExtensions>
</system.xml.serialization>
```

## <a name="see-also"></a><span data-ttu-id="ec882-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec882-125">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="ec882-126">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="ec882-126">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="ec882-127">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="ec882-127">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="ec882-128">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="ec882-128">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="ec882-129">\<add> 的元素 \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="ec882-129">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
