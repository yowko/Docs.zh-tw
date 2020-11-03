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
# <a name="systemxmlserialization-element"></a>\<system.xml.serialization> 項目

用來控制 XML 序列化的最上層項目。 如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../framework/configure-apps/file-schema/index.md)。

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a>語法

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[\<dateTimeSerialization> 元素](datetimeserialization-element.md)|判斷 <xref:System.DateTime> 物件的序列化模式。|
|[\<schemaImporterExtensions> 元素](schemaimporterextensions-element.md)|包含用來將 <xref:System.Xml.Serialization.XmlSchemaImporter> XSD 類型對應至 .net 類型的類型。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[\<configuration> 元素](../../framework/configure-apps/file-schema/configuration-element.md)|Common Language Runtime 與 .NET Framework 應用程式使用的所有組態檔中的根項目。|

## <a name="example"></a>範例

下列程式碼範例說明如何指定物件的序列化模式 <xref:System.DateTime> ，以及在將 <xref:System.Xml.Serialization.XmlSchemaImporter> XSD 類型對應至 .net 類型時，所使用的型別加入。

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

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [設定檔架構](../../framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> 元素](datetimeserialization-element.md)
- [\<schemaImporterExtensions> 元素](schemaimporterextensions-element.md)
- [\<add> 的元素 \<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
