---
title: <dateTimeSerialization> 項目
description: 本文描述專案 <dateTimeSerialization> ，這個元素會決定 DateTime 物件的序列化模式。
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 652a88e25f59cd905e47ef71351e47e67f375286
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375818"
---
# <a name="datetimeserialization-element"></a>\<dateTimeSerialization> 元素
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
  
## <a name="see-also"></a>請參閱

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [設定檔架構](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<schemaImporterExtensions> 元素](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [\<新增 schemaImporterExtensions>的> 元素 \<](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [\<> 元素的 system.object 序列化](../../../docs/standard/serialization/system-xml-serialization-element.md)
