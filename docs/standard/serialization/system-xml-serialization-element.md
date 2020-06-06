---
title: <system.xml.serialization> 項目
description: 本文描述 < system.string > 元素，這是用來控制 XML 序列化的最上層元素。
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: f69e80592e9321de64421b977a63b83d8be2ad9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289482"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="ef6ef-103">\<system.xml.serialization> 項目</span><span class="sxs-lookup"><span data-stu-id="ef6ef-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="ef6ef-104">用來控制 XML 序列化的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="ef6ef-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="ef6ef-105">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ef6ef-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a><span data-ttu-id="ef6ef-106">語法</span><span class="sxs-lookup"><span data-stu-id="ef6ef-106">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef6ef-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ef6ef-107">Attributes and Elements</span></span>

<span data-ttu-id="ef6ef-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ef6ef-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef6ef-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ef6ef-109">Attributes</span></span>

<span data-ttu-id="ef6ef-110">無。</span><span class="sxs-lookup"><span data-stu-id="ef6ef-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef6ef-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ef6ef-111">Child Elements</span></span>

|<span data-ttu-id="ef6ef-112">元素</span><span class="sxs-lookup"><span data-stu-id="ef6ef-112">Element</span></span>|<span data-ttu-id="ef6ef-113">描述</span><span class="sxs-lookup"><span data-stu-id="ef6ef-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef6ef-114">\<dateTimeSerialization>元素</span><span class="sxs-lookup"><span data-stu-id="ef6ef-114">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)|<span data-ttu-id="ef6ef-115">判斷 <xref:System.DateTime> 物件的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="ef6ef-115">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="ef6ef-116">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="ef6ef-116">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)|<span data-ttu-id="ef6ef-117">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 用來對應 XSD 型別至 .NET Framework 型別的型別。</span><span class="sxs-lookup"><span data-stu-id="ef6ef-117">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ef6ef-118">父項目</span><span class="sxs-lookup"><span data-stu-id="ef6ef-118">Parent Elements</span></span>

|<span data-ttu-id="ef6ef-119">元素</span><span class="sxs-lookup"><span data-stu-id="ef6ef-119">Element</span></span>|<span data-ttu-id="ef6ef-120">描述</span><span class="sxs-lookup"><span data-stu-id="ef6ef-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef6ef-121">\<configuration>元素</span><span class="sxs-lookup"><span data-stu-id="ef6ef-121">\<configuration> Element</span></span>](../../framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="ef6ef-122">Common Language Runtime 與 .NET Framework 應用程式使用的所有組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ef6ef-122">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="ef6ef-123">範例</span><span class="sxs-lookup"><span data-stu-id="ef6ef-123">Example</span></span>

<span data-ttu-id="ef6ef-124">下列程式碼範例描述如何指定 <xref:System.DateTime> 物件的序列化模式，以及在對應 XSD 型別至 .NET Framework 型別時 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的新增型別。</span><span class="sxs-lookup"><span data-stu-id="ef6ef-124">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ef6ef-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef6ef-125">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="ef6ef-126">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="ef6ef-126">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="ef6ef-127">\<dateTimeSerialization>元素</span><span class="sxs-lookup"><span data-stu-id="ef6ef-127">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="ef6ef-128">\<schemaImporterExtensions>元素</span><span class="sxs-lookup"><span data-stu-id="ef6ef-128">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="ef6ef-129">\<add>的元素\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="ef6ef-129">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
