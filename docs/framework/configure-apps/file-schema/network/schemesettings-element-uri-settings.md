---
title: <schemeSettings> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154643"
---
# <a name="schemesettings-element-uri-settings"></a>\<schemeSettings> 項目 (URI 設定)
指定如何針對特定配置剖析 <xref:System.Uri>。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無  
  
### <a name="child-elements"></a>子元素  
  
|**元素**|**說明**|  
|-----------------|---------------------|  
|[add](add-element-for-schemesettings-uri-settings.md)|新增配置名稱的配置設定。|  
|[明確](clear-element-for-schemesettings-uri-settings.md)|清除所有現有的配置設定。|  
|[remove](remove-element-for-schemesettings-uri-settings.md)|移除配置名稱的配置設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|**元素**|**說明**|  
|-----------------|---------------------|  
|[uri](uri-element-uri-settings.md)|包含指定 .NET Framework 如何處理使用統一資源識別項（Uri）所表示之 web 位址的設定。|  
  
## <a name="remarks"></a>備註  
 根據預設， <xref:System.Uri?displayProperty=nameWithType> 類別會在執行路徑壓縮之前取消轉義百分比編碼的路徑分隔符號。 這會實作為安全性機制來對抗下列攻擊：  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 如果將此 URI 向下傳遞至未正確處理百分比編碼字元的模組，可能會導致伺服器執行下列命令：  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 因此，類別會 <xref:System.Uri?displayProperty=nameWithType> 先取消轉義路徑分隔符號，然後套用路徑壓縮。 將上述惡意 URL 傳遞給類別的函式的結果會 <xref:System.Uri?displayProperty=nameWithType> 產生下列 URI：  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 您可以使用特定配置的 Schemesettings 專案設定選項，修改這個預設行為，而不要解除轉義百分比編碼的路徑分隔符號。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例顯示類別所使用的設定 <xref:System.Uri> ，以支援不要將 HTTP 配置的百分比編碼路徑分隔符號進行轉義。  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a>項目資訊  
  
|||
|-|-|  
|命名空間|系統|  
|結構描述名稱||  
|驗證檔||  
|可以是空的||  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [網路設定結構描述](index.md)
