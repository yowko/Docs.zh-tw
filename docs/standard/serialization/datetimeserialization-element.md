---
title: <dateTimeSerialization> 項目
description: 本文描述專案 <dateTimeSerialization> ，這個元素會決定 DateTime 物件的序列化模式。
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: a2684ab72c1fb109d711e333e01836d3399caf86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289638"
---
# <a name="datetimeserialization-element"></a>\<dateTimeSerialization> 項目
判斷 <xref:System.DateTime> 物件的序列化模式。  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>語法  
  
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
 在版本1.0、1.1、2.0 和更新版本的 .NET Framework 中，當這個屬性設定為**local**時， <xref:System.DateTime> 物件一律會格式化為當地時間。 也就是說，本地時區資訊一定會包含在序列化資料中。 將此屬性設定為 **Local**，確保與舊版 .NET Framework 的相容性。  
  
 在版本2.0 和更新版本的 .NET Framework 中，將此屬性設定為 [**往返**]， <xref:System.DateTime> 會檢查物件以判斷它們是在當地、UTC 還是未指定的時區。 然後 <xref:System.DateTime> 物件會以保留此資訊的方式序列化。 這是預設行為，並建議所有新的應用程式不要與舊版 Framework 進行通訊。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [設定檔架構](../../framework/configure-apps/file-schema/index.md)
- [\<schemaImporterExtensions>元素](schemaimporterextensions-element.md)
- [\<add>的元素\<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization>元素](system-xml-serialization-element.md)
