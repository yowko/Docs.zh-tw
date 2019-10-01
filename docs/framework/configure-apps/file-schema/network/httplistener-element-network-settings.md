---
title: <httpListener> 項目 (網路設定)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 3f75096681ab07dd6d4788fbded5ca5c4a024aef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698187"
---
# <a name="httplistener-element-network-settings"></a>@no__t 0HTTPListener > 元素（網路設定）
自訂 <xref:System.Net.HttpListener> 類別所使用的參數。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<HTTPListener >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>Type  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|unescapeRequestUrl|布林值，指出 <xref:System.Net.HttpListener> 實例是否使用未經處理的非轉義 URI，而不是轉換後的 URI。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[設置](settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  
 **UnescapeRequestUrl**屬性會指出 <xref:System.Net.HttpListener> 是否使用未經處理的非轉義 uri，而不是轉換後的 uri，其中會轉換任何百分比編碼的值，並採用其他正規化步驟。  
  
 當 <xref:System.Net.HttpListener> 實例透過 @no__t 1 服務收到要求時，它會建立 `http.sys` 所提供之 URI 字串的實例，並將它公開為 <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> 屬性。  
  
 @No__t-0 服務會公開兩個要求 URI 字串：  
  
- 原始 URI  
  
- 已轉換 URI  
  
 原始 URI 是 HTTP 要求的要求行中提供的 <xref:System.Uri?displayProperty=nameWithType>：  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 針對上述要求，`http.sys` 所提供的原始 URI 是 "/path/"。 這代表在透過網路傳送的 HTTP 動詞命令之後的字串。  
  
 @No__t-0 服務會從要求中提供的資訊建立已轉換的 URI，方法是使用 HTTP 要求行中提供的 URI 和主機標頭來判斷要求應轉送至的源伺服器。 這是藉由比較要求中的資訊與一組已註冊的 URI 前置詞來完成。 HTTP 伺服器 SDK 檔是指此轉換後的 URI 做為 HTTP_COOKED_URL 結構。  
  
 為了能夠比較要求與已註冊的 URI 前置詞，需要對要求進行一些正規化。 針對上述範例，轉換後的 URI 如下所示：  
  
 `http://www.contoso.com/path/`  
  
 @No__t-0 服務會將 @no__t 1 屬性值和要求行中的字串結合，以建立已轉換的 URI。 此外，`http.sys` 和 @no__t 1 類別也會執行下列動作：  
  
- 取消轉義所有百分比編碼的值。  
  
- 將百分比編碼的非 ASCII 字元轉換成 UTF-16 字元標記法。 請注意，支援 UTF-8 和 ANSI/DBCS 字元，以及 Unicode 字元（使用% uXXXX 格式的 Unicode 編碼）。  
  
- 執行其他正規化步驟，例如路徑壓縮。  
  
 由於要求並未包含用於百分比編碼值之編碼的任何相關資訊，因此您可能無法藉由剖析百分比編碼的值來判斷正確的編碼方式。  
  
 因此 `http.sys` 提供兩個登錄機碼來修改進程：  
  
|登錄機碼|Default Value|描述|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|如果為零，`http.sys` 只接受 UTF-8 編碼的 Url。<br /><br /> 如果不是零，`http.sys` 也會接受要求中的 ANSI 編碼或 DBCS 編碼的 Url。|  
|FavorUTF8|1|如果不是零，`http.sys` 一律會先嘗試將 URL 解碼為 UTF-8。如果該轉換失敗且 EnableNonUTF8 為非零，則 Http.sys 會嘗試將它解碼為 ANSI 或 DBCS。<br /><br /> 如果為零（且 EnableNonUTF8 為非零），`http.sys` 會嘗試將它解碼為 ANSI 或 DBCS;如果不成功，它會嘗試 UTF-8 轉換。|  
  
 當 <xref:System.Net.HttpListener> 收到要求時，會使用來自 `http.sys` 的已轉換 URI 做為 <xref:System.Net.HttpListenerRequest.Url%2A> 屬性的輸入。  
  
 除了 Uri 中的字元和數位以外，還需要支援字元。 範例是下列 URI，用來抓取客戶編碼 "1/3812" 的客戶資訊：  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 請注意 Uri 中的百分比編碼斜線（% 2F）。 這是必要的，因為在此情況下，斜線字元代表資料，而不是路徑分隔符號。  
  
 將字串傳遞至 Uri 的函式會導致下列 URI：  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 將路徑分割成其區段會產生下列元素：  
  
 `Customer('1`  
  
 `3812')`  
  
 這不是要求寄件者的意圖。  
  
 如果**unescapeRequestUrl**屬性設定為**false**，則當 <xref:System.Net.HttpListener> 收到要求時，它會使用原始 URI，而不是從 `http.sys` 的轉換 uri，做為 <xref:System.Net.HttpListenerRequest.Url%2A> 屬性的輸入。  
  
 **UnescapeRequestUrl**屬性的預設值為**true**。  
  
 @No__t-0 屬性可以用來從適用的設定檔中取得**unescapeRequestUrl**屬性的目前值。  
  
## <a name="example"></a>範例  
 下列範例會示範如何設定 <xref:System.Net.HttpListener> 類別（當它收到使用原始 URI 的要求，而不是從 `http.sys` 轉換後的 URI 做為 <xref:System.Net.HttpListenerRequest.Url%2A> 屬性的輸入）。  
  
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
