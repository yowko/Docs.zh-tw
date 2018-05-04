---
title: '&lt;idn&gt;項目 （Uri 設定）'
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 17f68fbb92797928be911e530232e8638793687f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltidngt-element-uri-settings"></a>&lt;idn&gt;項目 （Uri 設定）
指定是否國際化網域名稱 (IDN) 剖析會套用至網域名稱。  
  
## <a name="schema-hierarchy"></a>結構描述階層架構  
 [\<configuration> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri > 項目 （Uri 設定）](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<idn >](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a>語法  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|`enabled`|指定是否國際化網域名稱 (IDN) 剖析套用至網域名稱的預設值為 none。|  
  
### <a name="child-elements"></a>子項目  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[Uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|包含會指定.NET Framework 如何處理使用統一資源識別元 (Uri) 表示的 web 位址設定。|  
  
## <a name="remarks"></a>備註  
 現有<xref:System.Uri>類別已經過擴充，在.NET Framework 3.5。 3.0 SP1 和 2.0 SP1，可以支援國際資源識別項 (IRI) 和國際化網域名稱 (IDN)。 目前的使用者不會看到從.NET Framework 2.0 行為的任何變更，除非它們特別啟用 IRI 和 IDN 支援。 這可確保應用程式與舊版 .NET framework 相容。  
  
 若要啟用 IRI 的支援，下列兩項變更是必要的：  
  
1.  加入至 machine.config 檔案的.NET Framework 2.0 目錄下面這行  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  指定是否要國際化網域名稱 (IDN) 剖析套用至網域名稱，以及是否應該套用 IRI 剖析規則。 此作業可在 machine.config 或 app.config 檔案中完成。  
  
 有三個可能的值為 IDN 根據所使用的 DNS 伺服器：  
  
-   啟用 idn = All  
  
     這個值會將任何 Unicode 網域名稱轉換成 Punycode 的對等 （IDN 名稱）。  
  
-   啟用 idn = AllExceptIntranet  
  
     此值將轉換為不在近端內部網路使用 Punycode 對等項目 （IDN 名稱） 上的所有 Unicode 網域名稱。 在此情況下，若要處理國際性近端內部網路上的名稱，用於內部網路的 DNS 伺服器應該支援 Unicode 名稱解析。  
  
-   啟用 idn = 無  
  
     此值不會將轉換使用 Punycode 任何 Unicode 網域名稱。 這是預設值是與.NET Framework 2.0 的行為一致。  
  
 啟用 IDN 會將網域名稱中所有的 Unicode 標籤轉換成對等的 Punycode。 Punycode 名稱只包含 ASCII 字元，而且開頭一律為前置詞 xn--。 這是為了支援網際網路上現有的 DNS 伺服器，因為大部分的 DNS 伺服器僅支援 ASCII 字元 (請參閱 RFC 3940)。  
  
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
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
