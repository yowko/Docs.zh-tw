---
title: '&lt;Iriparsing>&gt;項目 （Uri 設定）'
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 446447f0d279755dbc06e0e3a25d50ad86ad555b
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028250"
---
# <a name="ltiriparsinggt-element-uri-settings"></a>&lt;Iriparsing>&gt;項目 （Uri 設定）
指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。  
  
## <a name="schema-hierarchy"></a>結構描述階層架構  
 [\<configuration> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri > 項目 （Uri 設定）](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<Iriparsing> >](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
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
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[Uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|包含指定.NET Framework 如何處理使用統一資源識別元 (Uri) 表示的 web 位址的設定。|  
  
## <a name="remarks"></a>備註  
 現有<xref:System.Uri>類別已擴充.NET Framework 3.5 中。 3.0 SP1 和 2.0 SP1 提供支援國際資源識別項 (IRI) 和國際化網域名稱 (IDN)。 目前的使用者不會看到任何變更從.NET Framework 2.0 的行為，除非它們特別啟用 IRI 和 IDN 支援。 這可確保應用程式與舊版 .NET framework 相容。  
  
 若要啟用 IRI 支援，下列兩項變更是必要的：  
  
1.  將下行新增至.NET Framework 2.0 目錄下的 machine.config 檔案  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  指定是否應該套用 IRI 剖析規則。 此作業可在 machine.config 或 app.config 檔案中完成。  
  
 啟用 IRI 剖析 (啟用 Iriparsing> = `true`) 會執行正規化和字元檢查根據最新的 IRI 規則在 RFC 3987。 預設值是`false`會執行正規化和字元檢查根據 RFC 2396 和 RFC 3986 （適用於 IPv6 常值）。  
  
### <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例顯示所使用的組態<xref:System.Uri>類別，以支援 IRI 剖析和 IDN 名稱。  
  
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
