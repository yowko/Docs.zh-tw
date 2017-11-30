---
title: "&lt;httpListener&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 14a758f1d69da4db8ed58809de20d3522ea7e4e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lthttplistenergt-element-network-settings"></a>&lt;httpListener&gt;項目 （網路設定）
自訂所用參數<xref:System.Net.HttpListener>類別。  
  
 \<configuration>  
\<system.net >  
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
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|unescapeRequestUrl|布林值，指出如果<xref:System.Net.HttpListener>執行個體會使用原始的未逸出的 URI，而不是轉換後的 URI。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**說明**|  
|-----------------|---------------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  
 **UnescapeRequestUrl**屬性會指出如果<xref:System.Net.HttpListener>而不是轉換後的 URI 轉換百分比編碼的任何值，會採取其他的正規化步驟會使用原始的未逸出的 URI。  
  
 當<xref:System.Net.HttpListener>執行個體收到要求時透過`http.sys`服務，它會建立所提供的 URI 字串的執行個體`http.sys`，並公開其為<xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>屬性。  
  
 `http.sys`服務會公開兩個要求 URI 字串：  
  
-   未經處理的 URI  
  
-   已轉換的 URI  
  
 未經處理的 URI 是<xref:System.Uri?displayProperty=nameWithType>提供 HTTP 要求的要求行中：  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 所提供的原始 URI`http.sys`上面所提的要求是"/ 路徑 /"。 這表示它已透過網路傳送接下來的 HTTP 動詞命令的字串。  
  
 `http.sys`服務會使用 HTTP 要求行中所提供的 URI，在要求中所提供的資訊來建立已轉換的 URI 和主機標頭，以判斷原始伺服器的要求應該會轉送到。 這是藉由比較一組已註冊的 URI 前置詞的要求中的資訊。 HTTP 伺服器 SDK 文件指 HTTP_COOKED_URL 結構為此轉換的 URI。  
  
 為了要比較的要求已註冊的 URI 前置詞，需要執行某些要求的正規化。 轉換 URI 上述範例應如下：  
  
 `http://www.contoso.com/path/`  
  
 `http.sys`服務結合<xref:System.Uri.Host%2A?displayProperty=nameWithType>屬性值，並要求條線建立轉換的 URI 中的字串。 此外，`http.sys`和<xref:System.Uri?displayProperty=nameWithType>類別也會進行下列作業：  
  
-   取消-逸出所有百分比編碼值。  
  
-   轉換百分比編碼為 utf-16 字元表示法的非 ASCII 字元。 請注意，utf-8 與 ANSI/DBCS 字元支援以及 Unicode 字元 （Unicode 編碼使用 %uxxxx 格式）。  
  
-   執行其他的正規化步驟，例如路徑壓縮。  
  
 要求不包含任何百分比編碼值使用的編碼方式相關資訊，因為它可能無法判斷正確的編碼方式只是藉由剖析的百分比編碼值。  
  
 因此`http.sys`提供修改程序的兩個登錄機碼：  
  
|登錄機碼|預設值|描述|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|如果是零，`http.sys`接受只有 UTF 8 編碼的 Url。<br /><br /> 如果不是零，`http.sys`也接受 ANSI 編碼或 DBCS 編碼在要求中的 Url。|  
|FavorUTF8|1|如果不是零，`http.sys`一律會嘗試解碼 URL 為 utf-8 第一次。 如果該轉換失敗，而且 EnableNonUTF8 為非零，Http.sys，然後嘗試將它解碼為 ANSI 或依 DBCS。<br /><br /> 如果是零 （和 EnableNonUTF8 為非零），`http.sys`嘗試將它解碼為 ANSI 或依 DBCS; 如果不成功，它會嘗試 utf-8 轉換。|  
  
 當<xref:System.Net.HttpListener>收到要求時，它會使用轉換的 URI 從`http.sys`來作為輸入<xref:System.Net.HttpListenerRequest.Url%2A>屬性。  
  
 沒有需要支援在 Uri 中的字元和數字以外的字元。 範例是下列的 URI 用來擷取客戶的客戶資訊數字"1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 請注意百分比編碼中的斜線的 Uri (%2f)。 必須這樣做，因為在此情況下的斜線字元表示的資料，不是路徑分隔符號。  
  
 將字串傳遞至 Uri 建構函式會導致下列 URI:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 分割為其區段路徑會產生下列項目：  
  
 `Customer('1`  
  
 `3812')`  
  
 這不是寄件者要求的意圖。  
  
 如果**unescapeRequestUrl**屬性設為**false**，則當<xref:System.Net.HttpListener>收到要求時，它會使用原始 URI，而不是從轉換過的 URI`http.sys`做為輸入<xref:System.Net.HttpListenerRequest.Url%2A>屬性。  
  
 預設值為**unescapeRequestUrl**屬性是**true**。  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>屬性可以用來取得目前的值**unescapeRequestUrl**適用的組態檔中的屬性。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定<xref:System.Net.HttpListener>類別當它收到要求時使用原始 URI，而不是從轉換過的 URI`http.sys`來作為輸入<xref:System.Net.HttpListenerRequest.Url%2A>屬性。  
  
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
 <xref:System.Net.Configuration.HttpListenerElement>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpListenerRequest.Url%2A>  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
