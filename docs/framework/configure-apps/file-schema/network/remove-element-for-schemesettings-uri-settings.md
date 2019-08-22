---
title: schemeSettings 的 <remove> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 4a891eb8a2fd2d66b6435e2ae774ecd4a157c0f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659225"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a>\<移除 Schemesettings 專案的 > 元素 (Uri 設定)
移除配置名稱的配置設定。  
  
 \<configuration>  
\<uri >  
\<schemeSettings>  
\<remove>  
  
## <a name="syntax"></a>語法  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|NAME|套用此設定的配置名稱。 唯一支援的值為 name = "HTTP" 和 name = "HTTPs"。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<schemeSettings> 項目 (URI 設定)](schemesettings-element-uri-settings.md)|指定如何針對特定配置剖析 <xref:System.Uri>。|  
  
## <a name="remarks"></a>備註  
 根據預設, <xref:System.Uri?displayProperty=nameWithType>類別會在執行路徑壓縮之前取消轉義百分比編碼的路徑分隔符號。 這會實作為安全性機制來對抗下列攻擊:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 如果將此 URI 向下傳遞至未正確處理百分比編碼字元的模組, 可能會導致伺服器執行下列命令:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 因此, <xref:System.Uri?displayProperty=nameWithType>類別會先取消轉義路徑分隔符號, 然後套用路徑壓縮。 將上述惡意 URL 傳遞給<xref:System.Uri?displayProperty=nameWithType>類別的函式的結果會產生下列 URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 您可以使用特定配置的 Schemesettings 專案設定選項, 修改這個預設行為, 而不要解除轉義百分比編碼的路徑分隔符號。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會示範類別所使用的設定<xref:System.Uri> , 其會移除 HTTP 配置的任何配置設定。  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
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
- [網路設定結構描述](index.md)
