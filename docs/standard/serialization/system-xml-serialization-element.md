---
title: <system.xml.serialization> 項目
description: 本文描述 <system.string> 元素，這是用來控制 XML 序列化的最上層元素。
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 1e66220004d561f937d03c506e6f30db4ccc635b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380120"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="f8d00-103">\<> 元素的 system.object 序列化</span><span class="sxs-lookup"><span data-stu-id="f8d00-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="f8d00-104">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="f8d00-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="f8d00-105">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f8d00-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="f8d00-106">\<configuration> </span><span class="sxs-lookup"><span data-stu-id="f8d00-106">\<configuration></span></span>\
<span data-ttu-id="f8d00-107">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="f8d00-107">\<system.xml.serialization></span></span>

## <a name="syntax"></a><span data-ttu-id="f8d00-108">語法</span><span class="sxs-lookup"><span data-stu-id="f8d00-108">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8d00-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f8d00-109">Attributes and Elements</span></span>

<span data-ttu-id="f8d00-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f8d00-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8d00-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f8d00-111">Attributes</span></span>

<span data-ttu-id="f8d00-112">無。</span><span class="sxs-lookup"><span data-stu-id="f8d00-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8d00-113">子元素</span><span class="sxs-lookup"><span data-stu-id="f8d00-113">Child Elements</span></span>

|<span data-ttu-id="f8d00-114">元素</span><span class="sxs-lookup"><span data-stu-id="f8d00-114">Element</span></span>|<span data-ttu-id="f8d00-115">描述</span><span class="sxs-lookup"><span data-stu-id="f8d00-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8d00-116">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="f8d00-116">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="f8d00-117">判斷 <xref:System.DateTime> 物件的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="f8d00-117">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="f8d00-118">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="f8d00-118">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="f8d00-119">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 用來對應 XSD 型別至 .NET Framework 型別的型別。</span><span class="sxs-lookup"><span data-stu-id="f8d00-119">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f8d00-120">父項目</span><span class="sxs-lookup"><span data-stu-id="f8d00-120">Parent Elements</span></span>

|<span data-ttu-id="f8d00-121">元素</span><span class="sxs-lookup"><span data-stu-id="f8d00-121">Element</span></span>|<span data-ttu-id="f8d00-122">描述</span><span class="sxs-lookup"><span data-stu-id="f8d00-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8d00-123">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="f8d00-123">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="f8d00-124">Common Language Runtime 與 .NET Framework 應用程式使用的所有組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f8d00-124">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="f8d00-125">範例</span><span class="sxs-lookup"><span data-stu-id="f8d00-125">Example</span></span>

<span data-ttu-id="f8d00-126">下列程式碼範例描述如何指定 <xref:System.DateTime> 物件的序列化模式，以及在對應 XSD 型別至 .NET Framework 型別時 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的新增型別。</span><span class="sxs-lookup"><span data-stu-id="f8d00-126">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f8d00-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="f8d00-127">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="f8d00-128">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="f8d00-128">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f8d00-129">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="f8d00-129">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="f8d00-130">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="f8d00-130">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="f8d00-131">\<新增 schemaImporterExtensions>的> 元素 \<</span><span class="sxs-lookup"><span data-stu-id="f8d00-131">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
