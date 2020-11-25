---
title: <schemaImporterExtensions> 項目
description: <schemaImporterExtensions>元素包含 XmlSchemaImporter 用來將 XSD 類型對應至 .net 類型的類型。
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 6b644ed1112b748be4dd301d6fa6f2a6416dc67e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722137"
---
# <a name="schemaimporterextensions-element"></a>\<schemaImporterExtensions> 項目

包含用來將 <xref:System.Xml.Serialization.XmlSchemaImporter> XSD 類型對應至 .net 類型的類型。 如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../framework/configure-apps/file-schema/index.md)。  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<add> 的元素 \<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)|新增 <xref:System.Xml.Serialization.XmlSchemaImporter> 所使用的類型來建立對應。|  
  
## <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<system.xml.serialization> 元素](system-xml-serialization-element.md)|用來控制 XML 序列化的最上層項目。|  
  
## <a name="example"></a>範例  

 下列程式碼範例說明如何 <xref:System.Xml.Serialization.XmlSchemaImporter> 在將 XSD 類型對應至 .net 類型時，加入所使用的類型。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [設定檔架構](../../framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> 元素](datetimeserialization-element.md)
- [\<add> 的元素 \<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization> 元素](system-xml-serialization-element.md)
