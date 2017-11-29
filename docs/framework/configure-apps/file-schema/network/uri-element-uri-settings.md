---
title: "&lt;Uri&gt;項目 （Uri 設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 44ef28ca2188973ccd353f4e8615c7c95f5674a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="lturigt-element-uri-settings"></a>&lt;Uri&gt;項目 （Uri 設定）
包含會指定.NET Framework 如何處理使用統一資源識別元 (Uri) 表示的 web 位址設定。  
  
## <a name="schema-hierarchy"></a>結構描述階層架構  
 [\<configuration> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<uri >](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a>語法  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|**目**|**說明**|  
|-----------------|---------------------|  
|[idn](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。|  
|[iriParsing](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|指定是否套用國際資源識別項 (IRI) 剖析至<xref:System.Uri>，以及是否應該套用 IRI 剖析規則。|  
|[schemeSettings](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|指定如何針對特定配置剖析 <xref:System.Uri>。|  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**說明**|  
|-----------------|---------------------|  
|[組態](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|包含所有命名空間的設定。|  
  
## <a name="remarks"></a>備註  
 `uri`項目包含的成員設定<xref:System.Uri>類別中的類別使用<xref:System.Net>命名空間。 這些設定會設定 IRI 和 IDN 支援。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>說明  
 下列範例示範使用組態<xref:System.Uri>類別，以支援 IRI 剖析和 IDN 名稱。 此範例也會清除所有配置設定，然後新增 支援的未逸出的 http 配置的百分比編碼路徑分隔符號。  
  
### <a name="code"></a>程式碼  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
