---
title: <httpListener> 項目 (網路設定)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 78526559164939667eab8848bc5fd2af6749d474
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195437"
---
# <a name="httplistener-element-network-settings"></a>\<httpListener> 項目 (網路設定)

自訂類別使用的參數 <xref:System.Net.HttpListener> 。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**

## <a name="syntax"></a>Syntax  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>類型  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|unescapeRequestUrl|布林值，指出實例是否使用未經處理的 <xref:System.Net.HttpListener> 非轉義 uri，而不是已轉換的 uri。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[設定](settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  

 **UnescapeRequestUrl**屬性會指出是否使用未經處理的非 <xref:System.Net.HttpListener> 轉義 uri，而不是轉換過的 uri，其中任何百分比編碼值都會轉換，並採用其他正規化步驟。  
  
 當 <xref:System.Net.HttpListener> 實例透過服務收到要求時 `http.sys` ，它會建立所提供之 URI 字串的實例 `http.sys` ，並將它公開為 <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> 屬性。  
  
 `http.sys`服務會公開兩個要求 URI 字串：  
  
- 原始 URI  
  
- 已轉換的 URI  
  
 原始 URI 是 <xref:System.Uri?displayProperty=nameWithType> 在 HTTP 要求的要求行中提供的：  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 `http.sys`針對上面所述的要求所提供的原始 URI 是 "/path/"。 這代表透過網路傳送 HTTP 動詞命令之後的字串。  
  
 `http.sys`服務會使用 HTTP 要求行中提供的 uri 和主機標頭來判斷要求應該轉送至的源伺服器，藉此從要求中提供的資訊建立已轉換的 uri。 這是藉由使用一組已註冊的 URI 前置詞來比較要求中的資訊來完成。 HTTP Server SDK 檔將這個已轉換的 URI 參考為 HTTP_COOKED_URL 結構。  
  
 為了能夠將要求與已註冊的 URI 前置詞進行比較，需要完成一些對要求的正規化。 針對上述範例，已轉換的 URI 如下所示：  
  
 `http://www.contoso.com/path/`  
  
 服務會將 `http.sys` <xref:System.Uri.Host%2A?displayProperty=nameWithType> 屬性值和要求行中的字串結合，以建立已轉換的 URI。 此外， `http.sys` 此 <xref:System.Uri?displayProperty=nameWithType> 類別也會執行下列動作：  
  
- 取消轉義所有百分比編碼的值。  
  
- 將百分比編碼的非 ASCII 字元轉換成 UTF-16 字元標記法。 請注意，UTF-8 和 ANSI/DBCS 字元也支援 unicode 字元， (使用% uXXXX format) 的 Unicode 編碼。  
  
- 執行其他正規化步驟，例如路徑壓縮。  
  
 因為要求未包含用於百分比編碼值之編碼的任何資訊，所以可能無法藉由剖析百分比編碼值來判斷正確的編碼方式。  
  
 因此 `http.sys` ，提供兩個登錄機碼來修改進程：  
  
|登錄機碼|預設值|描述|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|如果為零，則 `http.sys` 只接受 utf-8 編碼的 url。<br /><br /> 如果非零， `http.sys` 也會在要求中接受 ANSI 編碼或 DBCS 編碼的 url。|  
|FavorUTF8|1|如果非零， `http.sys` 一律會嘗試將 URL 解碼為 utf-8; 如果轉換失敗，而且 EnableNonUTF8 不是零，Http.sys 接著會嘗試將它解碼為 ANSI 或 DBCS。<br /><br /> 如果零 (，且 EnableNonUTF8 為非零) ，則會 `http.sys` 嘗試將它解碼為 ANSI 或 DBCS; 如果不成功，則會嘗試 utf-8 轉換。|  
  
 當 <xref:System.Net.HttpListener> 收到要求時，它會使用已轉換的 URI `http.sys` 做為屬性的輸入 <xref:System.Net.HttpListenerRequest.Url%2A> 。  
  
 除了 Uri 中的字元和數位之外，還需要支援字元。 以下是用來抓取客戶編碼 "1/3812" 客戶資訊的 URI 範例：  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 請注意 Uri 中的百分比編碼斜線 (% 2F) 。 這是必要的，因為在此情況下，斜線字元代表資料，而不是路徑分隔符號。  
  
 將字串傳遞至 Uri 的函式會導致下列 URI：  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 將路徑分割成其區段會導致下列元素：  
  
 `Customer('1`  
  
 `3812')`  
  
 這不是要求寄件者的意圖。  
  
 如果 **unescapeRequestUrl** 屬性設定為 **false**，則當 <xref:System.Net.HttpListener> 收到要求時，它會使用未經處理的 uri，而不是做為屬性的 `http.sys` 輸入 <xref:System.Net.HttpListenerRequest.Url%2A> 。  
  
 **UnescapeRequestUrl**屬性的預設值為**true**。  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>屬性可以用來從適用的設定檔案取得**unescapeRequestUrl**屬性的目前值。  
  
## <a name="example"></a>範例  

 下列範例將示範如何 <xref:System.Net.HttpListener> 在收到使用原始 uri 的要求時設定類別，而不使用轉換的 uri `http.sys` 做為屬性的輸入 <xref:System.Net.HttpListenerRequest.Url%2A> 。  
  
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
|可以是空的||  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [網路設定結構描述](index.md)
