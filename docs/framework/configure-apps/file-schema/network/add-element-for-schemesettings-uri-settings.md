---
title: schemeSettings 的 <add> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: e7606a1185d406384a926ca4dcb7c42586461574
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674697"
---
# <a name="add-element-for-schemesettings-uri-settings"></a>\<新增 > schemeSettings （Uri 設定） 的項目
新增為結構描述名稱的配置設定。  
  
 \<configuration>  
\<uri>  
\<schemeSettings>  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|名稱|這項設定適用於配置名稱。 僅支援的值為名稱 ="http"和名稱 ="https"。|  
  
## <a name="attribute-name-attribute"></a>{屬性 name}屬性  
  
|值|描述|  
|-----------|-----------------|  
|genericUriParserOptions|此配置剖析器選項。 僅支援的值是 genericUriParserOptions ="DontUnescapePathDotsAndSlashes 」。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<schemeSettings> 項目 (URI 設定)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|指定如何針對特定配置剖析 <xref:System.Uri>。|  
  
## <a name="remarks"></a>備註  
 根據預設，<xref:System.Uri?displayProperty=nameWithType>類別取消逸出百分比編碼路徑分隔符號，然後再執行路徑壓縮。 這被實作為安全性機制，抵禦攻擊，如下所示：  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 如果這個 URI 會傳遞到模組不會處理百分比編碼字元正確，可能會造成伺服器正在執行下列命令：  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 基於這個理由，<xref:System.Uri?displayProperty=nameWithType>類別第一個取消逸出路徑分隔符號，然後再套用路徑壓縮。 傳遞至以上惡意 URL 的結果<xref:System.Uri?displayProperty=nameWithType>類別建構函式結果，在下列 URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 此預設行為可以修改為不取消逸出百分比編碼的路徑分隔符號使用 schemeSettings 組態選項的特定結構描述中。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例顯示所使用的組態<xref:System.Uri>類別，以支援不逸出的 http 配置的百分比編碼的路徑分隔符號。  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
