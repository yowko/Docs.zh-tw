---
title: <Uri> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 80d71da5ca680872e4948fa8ff135fbbdf08cffe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663970"
---
# <a name="uri-element-uri-settings"></a>\<Uri > 元素 (Uri 設定)
包含指定 .NET Framework 如何處理使用統一資源識別項 (Uri) 所表示之 web 位址的設定。  
  
## <a name="schema-hierarchy"></a>結構描述階層架構  
 [\<configuration> 項目](../configuration-element.md)  
  
 [\<uri>](uri-element-uri-settings.md)  
  
## <a name="syntax"></a>語法  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[idn](idn-element-uri-settings.md)|指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。|  
|[g](iriparsing-element-uri-settings.md)|指定是否要<xref:System.Uri>套用國際資源識別碼 (IRI) 剖析, 以及是否應該套用 IRI 剖析規則。|  
|[schemeSettings](schemesettings-element-uri-settings.md)|指定如何針對特定配置剖析 <xref:System.Uri>。|  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[configuration](../configuration-element.md)|包含所有命名空間的設定。|  
  
## <a name="remarks"></a>備註  
 元素包含<xref:System.Net>命名空間中類別所<xref:System.Uri>使用之類別成員的設定。 `uri` 設定會設定 IRI 和 IDN 的支援。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>說明  
 下列範例顯示<xref:System.Uri>類別用來支援 IRI 剖析和 IDN 名稱的設定。 此範例也會清除所有配置設定, 然後針對 HTTP 配置新增不以轉義百分比編碼之路徑分隔符號的支援。  
  
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

- [網路設定結構描述](index.md)
