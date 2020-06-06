---
title: <schemaImporterExtensions> 的 <add> 項目
description: <add>元素會加入 XmlSchemaImporter 類別用來將 XSD 類型對應至 .NET Framework 類型的類型。
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 6fd8113ad39a22c927035fca574151ae8f002685
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "84288325"
---
# <a name="add-element-for-schemaimporterextensions"></a>\<schemaImporterExtensions> 的 \<add> 項目
加入 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的型別，將 XSD 型別對應至 .NET Framework 型別。 如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../framework/configure-apps/file-schema/index.md)。  
  
 \<configuration>  
\<system.xml.serialization>  
\<schemaImporterExtensions>  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**name**|用來尋找執行個體的簡單名稱。|  
|**type**|必要。 指定要加入的結構描述擴充功能類別。 **type** 屬性值必須在同一行，且包括完整類型名稱。 當組件置於全域組件快取 (GAC) 中時，也必須包含簽署組件的版本、文化特性和公開金鑰語彙基元。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|\<schemaImporterExtensions>|包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的型別。|  
  
## <a name="example"></a>範例  
 下列程式碼範例會加入 XmlSchemaImporter 在對應型別時可使用的副檔名類型。  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <schemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a" />
    </schemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [\<system.xml.serialization>元素](system-xml-serialization-element.md)
- [\<schemaImporterExtensions>元素](schemaimporterextensions-element.md)
