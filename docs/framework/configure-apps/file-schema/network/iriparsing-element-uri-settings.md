---
title: <iriParsing> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: ec2610e47957d5560bc7f51e0641afc9ba60c814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158886"
---
# <a name="iriparsing-element-uri-settings"></a>\<iriParsing> 項目 (URI 設定)

指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|`enabled`|指定是否啟用 IRI 剖析。 預設值是 `false`。|  
  
### <a name="child-elements"></a>子元素  

 無  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[uri](uri-element-uri-settings.md)|包含的設定會指定 .NET Framework 如何處理使用統一資源識別項 (Uri) 所表示的 web 位址。|  
  
## <a name="remarks"></a>備註  

 現有的 <xref:System.Uri> 類別已在 .NET Framework 3.5 中擴充。 3.0 SP1 和 2.0 SP1，以提供國際資源識別碼的支援 (IRI) 和國際化功能變數名稱 (IDN) 。 除非使用者特別啟用 IRI 和 IDN 支援，否則目前的使用者不會看到 .NET Framework 2.0 行為的任何變更。 這可確保應用程式與舊版 .NET framework 相容。  
  
 若要啟用對 IRI 的支援，需要進行下列兩項變更：  
  
1. 將下列程式程式碼新增至 .NET Framework 2.0 目錄下的 machine.config 檔案  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. 指定是否應套用 IRI 剖析規則。 此作業可在 machine.config 或 app.config 檔案中完成。  
  
 啟用 IRI 剖析 (g enabled = `true`) 會根據 RFC 3987 中最新的 IRI 規則進行正規化和字元檢查。 預設值為 `false` ，而且會根據 rfc 2396 和 rfc 3986 (針對 IPv6 常值) 進行正規化和字元檢查。  
  
### <a name="configuration-files"></a>組態檔  

 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  

 下列範例顯示 <xref:System.Uri> 類別用來支援 IRI 剖析和 IDN 名稱的設定。  
  
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

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [網路設定結構描述](index.md)
