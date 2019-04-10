---
title: <idn> 項目 （Uri 設定）
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 2d2729f9120d6b6fe673904ad2bf6d005ddf5469
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321749"
---
# <a name="idn-element-uri-settings"></a>\<idn > 項目 （Uri 設定）
指定是否國際化網域名稱 (IDN) 剖析套用至網域名稱。  
  
## <a name="schema-hierarchy"></a>結構描述階層架構  
 [\<組態 > 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri > 項目 （Uri 設定）](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<idn>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a>語法  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|**項目**|**描述**|  
|-----------------|---------------------|  
|`enabled`|指定是否國際化網域名稱 (IDN) 剖析套用至網域名稱的預設值為 none。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|**項目**|**描述**|  
|-----------------|---------------------|  
|[uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|包含指定.NET Framework 如何處理使用統一資源識別元 (Uri) 表示的 web 位址的設定。|  
  
## <a name="remarks"></a>備註  
 現有<xref:System.Uri>類別已擴充.NET Framework 3.5 中。 3.0 SP1 和 2.0 SP1 支援國際資源識別項 (IRI) 和國際化網域名稱 (IDN)。 目前的使用者不會看到任何變更從.NET Framework 2.0 的行為，除非它們特別啟用 IRI 和 IDN 支援。 這可確保應用程式與舊版 .NET framework 相容。  
  
 若要啟用 IRI 支援，下列兩項變更是必要的：  
  
1. 將下行新增至.NET Framework 2.0 目錄下的 machine.config 檔案  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. 指定是否要國際化網域名稱 (IDN) 剖析套用至網域名稱以及是否應該套用 IRI 剖析規則。 此作業可在 machine.config 或 app.config 檔案中完成。  
  
 有三個可能的值進行 IDN 根據所使用的 DNS 伺服器：  
  
-   啟用 idn = All  
  
     這個值會將任何 Unicode 網域名稱轉換成 Punycode 的對等名稱 （IDN 名稱）。  
  
-   啟用 idn = AllExceptIntranet  
  
     這個值會轉換不是在本機的內部網路使用 Punycode 的對等名稱 （IDN 名稱） 上的所有 Unicode 網域名稱。 在此情況下，若要處理在本機的內部網路上的國際性名稱，用於內部網路的 DNS 伺服器應該支援 Unicode 名稱解析。  
  
-   啟用 idn = 無  
  
     此值不會轉換任何 Unicode 網域名稱，即可使用 Punycode。 這是預設值是與.NET Framework 2.0 行為一致。  
  
 啟用 IDN 會將網域名稱中所有的 Unicode 標籤轉換成對等的 Punycode。 Punycode 名稱只包含 ASCII 字元，而且開頭一律為前置詞 xn--。 這是為了支援網際網路上現有的 DNS 伺服器，因為大部分的 DNS 伺服器僅支援 ASCII 字元 (請參閱 RFC 3940)。  
  
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

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
