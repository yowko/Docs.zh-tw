---
title: <schemeSettings> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 46012b15d41422fb3357e57438e320136809ef41
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664001"
---
# <a name="schemesettings-element-uri-settings"></a>\<Schemesettings 專案 > 元素 (Uri 設定)
指定如何針對特定配置剖析 <xref:System.Uri>。  
  
 \<configuration>  
\<uri >  
\<schemeSettings>  
  
## <a name="syntax"></a>語法  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無  
  
### <a name="child-elements"></a>子元素  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[add](add-element-for-schemesettings-uri-settings.md)|新增配置名稱的配置設定。|  
|[clear](clear-element-for-schemesettings-uri-settings.md)|清除所有現有的配置設定。|  
|[remove](remove-element-for-schemesettings-uri-settings.md)|移除配置名稱的配置設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[uri](uri-element-uri-settings.md)|包含指定 .NET Framework 如何處理使用統一資源識別項 (Uri) 所表示之 web 位址的設定。|  
  
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
 下列範例顯示類別所<xref:System.Uri>使用的設定, 以支援不要將 HTTP 配置的百分比編碼路徑分隔符號進行轉義。  
  
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
