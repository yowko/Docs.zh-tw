---
title: '&lt;dateTimeSerialization&gt; 元素'
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 15fad472288a72a079991f41e6c2859776d78cca
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723353"
---
# <a name="ltdatetimeserializationgt-element"></a>&lt;dateTimeSerialization&gt; 元素
判斷 <xref:System.DateTime> 物件的序列化模式。  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>語法  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|----------------|-----------------|  
|`mode`|選擇項。 指定序列化模式。 設定為其中一個 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> 值。 預設值為 **RoundTrip**。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|system.xml.serialization|用來控制 XML 序列化的最上層項目。|  
  
## <a name="remarks"></a>備註  
 在 .NET Framework 的 1.0、1.1 和 2.0 版以及更新版本中，將此屬性設定為 **Local** 時，<xref:System.DateTime> 物件一定會格式化為當地時間。 也就是說，本地時區資訊一定會包含在序列化資料中。 將此屬性設定為 **Local**，確保與舊版 .NET Framework 的相容性。  
  
 在將此屬性設定為 **Roundtrip** 的 .NET Framework 2.0 版及更新版本中，會檢查 <xref:System.DateTime> 物件以判斷其位於當地時區、UTC 或非特定時區。 然後 <xref:System.DateTime> 物件會以保留此資訊的方式序列化。 這是預設行為，並建議所有新的應用程式不要與舊版 Framework 進行通訊。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.DateTime>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<schemaImporterExtensions>元素](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [\<新增 > 項目\<schemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)  
 [\<system.xml.serialization> 項目](../../../docs/standard/serialization/system-xml-serialization-element.md)
