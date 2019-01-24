---
title: '&lt;schemaImporterExtensions&gt; 元素'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: dbe85ea817a597db84ddad530d67b1c2b7953f75
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535358"
---
# <a name="ltschemaimporterextensionsgt-element"></a>&lt;schemaImporterExtensions&gt; 元素
包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 用來對應 XSD 型別至 .NET Framework 型別的型別。 如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)。  
  
## <a name="syntax"></a>語法  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<新增 > 項目\<schemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|新增 <xref:System.Xml.Serialization.XmlSchemaImporter> 所使用的類型來建立對應。|  
  
## <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.xml.serialization> 項目](../../../docs/standard/serialization/system-xml-serialization-element.md)|用來控制 XML 序列化的最上層項目。|  
  
## <a name="example"></a>範例  
 下列程式碼範例描述如何加入 <xref:System.Xml.Serialization.XmlSchemaImporter> 在對應 XSD 型別至 .NET Framework 型別時使用的型別。  
  
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
- [組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> 元素](../../../docs/standard/serialization/datetimeserialization-element.md)
- [\<新增 > 項目\<schemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization> 項目](../../../docs/standard/serialization/system-xml-serialization-element.md)
