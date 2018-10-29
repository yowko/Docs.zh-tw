---
title: '&lt;httpListener&gt;項目 （網路設定）'
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 58228eed71dd6a5f5af8e26c02db9633da6ceef6
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197778"
---
# <a name="lthttplistenergt-element-network-settings"></a>&lt;httpListener&gt;項目 （網路設定）
自訂所使用的參數<xref:System.Net.HttpListener>類別。  
  
 \<configuration>  
\<system.net>  
\<設定 >  
\<httpListener >  
  
## <a name="syntax"></a>語法  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>類型  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|unescapeRequestUrl|布林值，指出如果<xref:System.Net.HttpListener>執行個體會使用原始未逸出的 URI，而不是轉換的 URI。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  
 **UnescapeRequestUrl**屬性會指出如果<xref:System.Net.HttpListener>使用原始未逸出的 URI，而不是轉換的 URI，其中任何百分比編碼的值會轉換，並且會採取其他的正規化步驟。  
  
 當<xref:System.Net.HttpListener>執行個體收到的要求，透過`http.sys`服務，它會建立所提供的 URI 字串的執行個體`http.sys`，並公開為<xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>屬性。  
  
 `http.sys`服務會公開兩個要求的 URI 字串：  
  
-   原始 URI  
  
-   轉換的 URI  
  
 未經處理的 URI 是<xref:System.Uri?displayProperty=nameWithType>HTTP 要求的要求行中提供：  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 所提供的原始 URI`http.sys`前面所述，此要求是"/ 路徑 /"。 這表示透過網路傳送下列 HTTP 動詞命令的字串。  
  
 `http.sys`服務會使用 HTTP 要求行中所提供的 URI 要求中所提供的資訊來建立轉換的 URI 和主機標頭，以判斷原始伺服器要求應該轉送到。 這是藉由比較從已註冊的 URI 前置詞的一組與要求的資訊。 HTTP 伺服器 SDK 文件會將稱為 HTTP_COOKED_URL 結構的這個轉換的 URI。  
  
 為了能夠比較要求，並已註冊的 URI 前置詞，要求一些正規化必須完成。 上述轉換的 URI 範例會是，如下所示：  
  
 `http://www.contoso.com/path/`  
  
 `http.sys`服務結合了<xref:System.Uri.Host%2A?displayProperty=nameWithType>屬性值，並建立轉換的 URI 要求行中的字串。 颾魤 ㄛ`http.sys`而<xref:System.Uri?displayProperty=nameWithType>類別也會進行下列作業：  
  
-   取消-逸出所有百分比編碼的值。  
  
-   將百分比編碼為 utf-16 字元表示法的非 ASCII 字元。 請注意，Unicode 字元 （Unicode 編碼使用 %uxxxx 格式） 以及支援 utf-8 和 ANSI/DBCS 字元。  
  
-   執行其他的正規化步驟，例如路徑壓縮。  
  
 因為要求未包含任何百分比編碼的值使用的編碼方式相關資訊，它可能無法判斷正確的編碼方式，就只是藉由剖析的百分比編碼的值。  
  
 因此`http.sys`提供兩個登錄機碼修改程序：  
  
|登錄機碼|預設值|描述|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|如果是零，`http.sys`接受僅 UTF-8 編碼的 Url。<br /><br /> 如果不是零，`http.sys`也接受 ANSI 編碼或 DBCS 編碼在要求中的 Url。|  
|FavorUTF8|1|如果不是零，`http.sys`一律要解碼的 URL 為 utf-8 第一次; 如果該轉換會失敗，而且 EnableNonUTF8 為非零的嘗試，Http.sys，然後嘗試將它解碼為 ANSI 或 DBCS。<br /><br /> 如果是零 （和 EnableNonUTF8 為非零）`http.sys`嘗試將它解碼為 ANSI 或 DBCS; 如果不成功，它嘗試 utf-8 轉換。|  
  
 當<xref:System.Net.HttpListener>收到要求時，它會使用轉換的 URI，從`http.sys`來作為輸入<xref:System.Net.HttpListenerRequest.Url%2A>屬性。  
  
 沒有需要支援在 Uri 中的字元和數字以外的字元。 舉例來說，下列 URI，用來擷取客戶的客戶資訊數字"1/3812 」:  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 請注意百分比編碼中的斜線的 Uri (%2f)。 這是必要的因為在此情況下的斜線字元代表的資料，不是路徑分隔符號。  
  
 將字串傳遞至 Uri 建構函式會導致下列 URI:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 將路徑分割成其區段，會導致下列項目：  
  
 `Customer('1`  
  
 `3812')`  
  
 這不是要求的寄件者的意圖。  
  
 如果**unescapeRequestUrl**屬性設為**false**，然後當<xref:System.Net.HttpListener>收到要求時，它會使用原始 URI，而不是從轉換的 URI`http.sys`做為輸入<xref:System.Net.HttpListenerRequest.Url%2A>屬性。  
  
 預設值**unescapeRequestUrl**屬性是 **，則為 true**。  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>屬性可用來取得目前的值**unescapeRequestUrl**適用的組態檔中的屬性。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定<xref:System.Net.HttpListener>類別，在它收到要求時使用的原始 URI，而不是從轉換的 URI`http.sys`來作為輸入<xref:System.Net.HttpListenerRequest.Url%2A>屬性。  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a>項目資訊  
  
|||
|-|-|  
|命名空間|System.Net|  
|結構描述名稱||  
|驗證檔||  
|可以是空白||  
  
## <a name="see-also"></a>另請參閱  
- <xref:System.Net.Configuration.HttpListenerElement>  
- <xref:System.Net.HttpListener>  
- <xref:System.Net.HttpListenerRequest.Url%2A>  
- [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
