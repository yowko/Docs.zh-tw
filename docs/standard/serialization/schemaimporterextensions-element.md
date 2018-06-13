---
title: '&lt;schemaImporterExtensions&gt; 元素'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: c9f4f6800c2718c3b2c2b9b5b2b6d97e1114dbcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581325"
---
# <a name="ltschemaimporterextensionsgt-element"></a>&lt;schemaImporterExtensions&gt; 元素
包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 用來對應 XSD 型別至 .NET Framework 型別的型別。 如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)。  
  
## <a name="syntax"></a>語法  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<xmlSchemaImporterExtensions> 的 \<add> 項目](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|新增 <xref:System.Xml.Serialization.XmlSchemaImporter> 所使用的類型來建立對應。|  
  
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
/system.sxml.serializaiton>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<dateTimeSerialization> 元素](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [\<xmlSchemaImporterExtensions> 的 \<add> 項目](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [\<system.xml.serialization> 項目](../../../docs/standard/serialization/system-xml-serialization-element.md)
