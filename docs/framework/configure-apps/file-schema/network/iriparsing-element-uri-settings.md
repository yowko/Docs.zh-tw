---
title: '&lt;iriParsing&gt;項目 （Uri 設定）'
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f05f7e35d69f789d3ebb371689aafbc84004b732
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743299"
---
# <a name="ltiriparsinggt-element-uri-settings"></a>&lt;iriParsing&gt;項目 （Uri 設定）
指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。  
  
## <a name="schema-hierarchy"></a>結構描述階層架構  
 [\<configuration> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri > 項目 （Uri 設定）](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<iriParsing >](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a>語法  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|`enabled`|指定是否啟用 IRI 剖析。 預設值是 `false`。|  
  
### <a name="child-elements"></a>子項目  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[Uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|包含會指定.NET Framework 如何處理使用統一資源識別元 (Uri) 表示的 web 位址設定。|  
  
## <a name="remarks"></a>備註  
 現有<xref:System.Uri>類別已經過擴充，在.NET Framework 3.5。 3.0 SP1 和 2.0 SP1，以提供支援國際資源識別項 (IRI) 和國際化網域名稱 (IDN)。 目前的使用者不會看到從.NET Framework 2.0 行為的任何變更，除非它們特別啟用 IRI 和 IDN 支援。 這可確保應用程式與舊版 .NET framework 相容。  
  
 若要啟用 IRI 的支援，下列兩項變更是必要的：  
  
1.  加入至 machine.config 檔案的.NET Framework 2.0 目錄下面這行  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  指定是否應該套用 IRI 剖析規則。 此作業可在 machine.config 或 app.config 檔案中完成。  
  
 啟用 IRI 剖析 (啟用 iriParsing = `true`) 將會執行正規化和 RFC 3987 字元檢查最新 IRI 根據規則。 預設值是`false`會執行正規化和字元檢查根據 RFC 2396 和 RFC 3986 （適用於 IPv6 常值）。  
  
### <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例示範使用組態<xref:System.Uri>類別，以支援 IRI 剖析和 IDN 名稱。  
  
### <a name="code"></a>程式碼  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
