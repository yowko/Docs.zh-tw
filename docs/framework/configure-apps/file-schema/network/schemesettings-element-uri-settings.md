---
title: <schemeSettings> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154643"
---
# <a name="schemesettings-element-uri-settings"></a>\<schemeSettings> 項目 (URI 設定)
指定如何針對特定配置剖析 <xref:System.Uri>。  
  
[**\<配置>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<烏裡>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<方案設置>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 None  
  
### <a name="child-elements"></a>子元素  
  
|**Element**|**描述**|  
|-----------------|---------------------|  
|[新增](add-element-for-schemesettings-uri-settings.md)|添加方案名稱的方案設置。|  
|[清楚](clear-element-for-schemesettings-uri-settings.md)|清除所有現有方案設置。|  
|[移除](remove-element-for-schemesettings-uri-settings.md)|刪除方案名稱的方案設置。|  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**描述**|  
|-----------------|---------------------|  
|[Uri](uri-element-uri-settings.md)|包含指定 .NET 框架如何處理使用統一資源識別項 （URI） 表示的 Web 位址的設置。|  
  
## <a name="remarks"></a>備註  
 預設情況下，<xref:System.Uri?displayProperty=nameWithType>類取消轉義百分比編碼的路徑分隔符號，然後再執行路徑壓縮。 這是作為針對以下攻擊的安全機制實現的：  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 如果此 URI 傳遞給未正確處理編碼百分比的模組，則可能導致伺服器執行以下命令：  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 因此，<xref:System.Uri?displayProperty=nameWithType>類首先取消轉義路徑分隔符號，然後應用路徑壓縮。 將上述惡意 URL 傳遞給<xref:System.Uri?displayProperty=nameWithType>類建構函式的結果會導致以下 URI：  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 可以使用方案設置配置選項修改此預設行為，以不取消轉義百分比編碼路徑分隔符號。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下面的示例顯示了<xref:System.Uri>類用於支援不為 HTTP 方案提供百分比編碼的路徑分隔符號的配置。  
  
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
|可以為空||  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [網路設置架構](index.md)
