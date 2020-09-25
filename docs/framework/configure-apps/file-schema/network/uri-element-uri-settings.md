---
title: <uri> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 2f22d70407d10dbb38f0cb8d3a8ac74ff3fe8763
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190198"
---
# <a name="uri-element-uri-settings"></a>\<uri> 項目 (URI 設定)

包含的設定會指定 .NET Framework 如何處理使用統一資源識別項 (Uri) 所表示的 web 位址。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  

 無。  
  
### <a name="child-elements"></a>子元素  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[Idn](idn-element-uri-settings.md)|指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。|  
|[g](iriparsing-element-uri-settings.md)|指定是否套用國際資源識別碼 (IRI) 剖析套用至 <xref:System.Uri> ，以及是否應套用 iri 剖析規則。|  
|[schemeSettings](schemesettings-element-uri-settings.md)|指定如何針對特定配置剖析 <xref:System.Uri>。|  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[設定](../configuration-element.md)|包含所有命名空間的設定。|  
  
## <a name="remarks"></a>備註  

 `uri`元素包含 <xref:System.Uri> 命名空間中類別所使用之類別的成員設定 <xref:System.Net> 。 這些設定會設定對 IRI 和 IDN 的支援。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  

 下列範例顯示 <xref:System.Uri> 類別用來支援 IRI 剖析和 IDN 名稱的設定。 此範例也會清除所有配置設定，然後新增對 HTTP 配置不會將百分比編碼路徑分隔符號的支援。  
  
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
