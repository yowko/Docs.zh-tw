---
title: <dateTimeSerialization> 項目
description: 本文描述專案 <dateTimeSerialization> ，它會決定 DateTime 物件的序列化模式。
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 1623517e66955c14b7e738c860ec16086fe30429
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678970"
---
# <a name="datetimeserialization-element"></a>\<dateTimeSerialization> 項目

判斷 <xref:System.DateTime> 物件的序列化模式。  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|----------------|-----------------|  
|`mode`|選擇性。 指定序列化模式。 設定為其中一個 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> 值。 預設值為 **RoundTrip**。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|system.xml.serialization|用來控制 XML 序列化的最上層項目。|  
  
## <a name="remarks"></a>備註  

當這個屬性設定為 [ **本機**] 時， <xref:System.DateTime> 物件一定會格式化為本地時間。 也就是說，本地時區資訊一定會包含在序列化資料中。
  
當這個屬性設定為 **往返** 時， <xref:System.DateTime> 會檢查物件以判斷它們是在本機、UTC 或未指定的時區。 然後 <xref:System.DateTime> 物件會以保留此資訊的方式序列化。 這是預設行為，並建議所有新的應用程式不要與舊版 Framework 進行通訊。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [設定檔架構](../../framework/configure-apps/file-schema/index.md)
- [\<schemaImporterExtensions> 元素](schemaimporterextensions-element.md)
- [\<add> 的元素 \<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization> 元素](system-xml-serialization-element.md)
