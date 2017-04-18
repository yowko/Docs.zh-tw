---
title: "&lt;httpListener&gt; 項目 (網路設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# &lt;httpListener&gt; 項目 (網路設定)
自訂 <xref:System.Net.HttpListener> 類別所使用的參數。  
  
## 語法  
  
```  
  
      <httpListener  
  unescapeRequestUrl ="true|false"  
/>  
```  
  
## 類型  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|unescapeRequestUrl|布林值，指出 <xref:System.Net.HttpListener> 是否使用未經處理非逸出 URI 取代轉換的 URI。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## 備註  
 **unescapeRequestUrl** 屬性指出 <xref:System.Net.HttpListener> 是否會使用未經處理的未逸出的 URI，而不是已轉換的 URI，其中會轉換任何百分比編碼的值，並且採用其他正規化的步驟。  
  
 當 <xref:System.Net.HttpListener> 執行個體透過 `http.sys` 服務收到要求時，會建立 `http.sys` 所提供的 URI 字串的執行個體，並將它公開為 <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=fullName> 屬性。  
  
 `http.sys` 服務會公開兩個要求 URI 字串：  
  
-   未經處理的 URI  
  
-   已轉換的 URI  
  
 未經處理的 URI 是 HTTP 要求的要求行中提供的 <xref:System.Uri?displayProperty=fullName>：  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 上述要求之 `http.sys` 所提供的未經處理 URI 是 "\/path\/"。  這表示當 HTTP 動詞已透過網路傳送時其之後的字串。  
  
 `http.sys` 服務會從要求中提供的資訊建立轉換後的 URI \(藉由使用 HTTP 要求行中提供的 URI\)，並使用 Host 標頭來判斷要求轉送的原始伺服器。  這可藉由比對要求的資訊與一組已註冊的 URI 前置詞來完成。  HTTP 伺服器 SDK 文件是指轉換為 HTTP\_COOKED\_URL 結構的 URI。  
  
 若要能夠用已註冊的 URI 前置詞來比較要求，需要進行一些要求的正規化。  上述轉換 URI 的範例如下所示：  
  
 `http://www.contoso.com/path/`  
  
 `http.sys` 服務結合了 <xref:System.Uri.Host%2A?displayProperty=fullName> 屬性值及要求行中的字串來建立轉換後的 URI 字串。  此外，`http.sys` 和 <xref:System.Uri?displayProperty=fullName> 類別也可執行下列作業：  
  
-   取消逸出所有百分比編碼值。  
  
-   將百分比編碼的非 ASCII 字元轉換為 UTF\-16 字元表示。  請注意，對於 UTF\-8 和 ANSI\/DBCS 字元都有支援，Unicode 字元 \(Unicode 編碼方式使用 %uXXXX 格式\) 也不例外。  
  
-   執行其他正規化步驟，例如路徑壓縮。  
  
 由於要求不包含百分比編碼值使用之編碼方式的任何相關資訊，有可能無法藉由剖析百分比編碼值來決定正確的編碼方式。  
  
 因此 `http.sys` 提供兩個用於修改處理序的登錄機碼：  
  
|登錄機碼|預設值|說明|  
|----------|---------|--------|  
|EnableNonUTF8|1|如果零，`http.sys` 只接受 UTF\-8 編碼的 URL。<br /><br /> 如果非零，`http.sys` 也會接受要求中的 ANSI 編碼或 DBCS 編碼 URL。|  
|FavorUTF8|1|如果非零，`http.sys` 必定會先嘗試將 URL 解碼為 UTF\-8。如果該轉換失敗，而且 EnableNonUTF8 非零，Http.sys 接著便會嘗試將其解碼為 ANSI 或 DBCS。<br /><br /> 如果為零 \(而且 EnableNonUTF8 不是零\)，`http.sys` 會嘗試將它解碼為 ANSI 或 DBCS，如果不成功，則會嘗試 UTF\-8 轉換。|  
  
 <xref:System.Net.HttpListener> 收到要求時，會使用從 `http.sys` 轉換的 URI 做為 <xref:System.Net.HttpListenerRequest.Url%2A> 屬性的輸入。  
  
 除了 URI 中的字元和數字外，不需支援字元。  下列 URI 為範例之一，該 URI 用於擷取客戶編號 "1\/3812" 的客戶資訊：  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 請注意 URI \(%2F\) 中的百分比編碼斜線。  這是必要的，因為在這種情況下，斜線字元代表資料而非路徑分隔符號。  
  
 將字串傳遞至 URI 建構函式會引導至下列 URI：  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 將路徑分割為其區段會產生下列項目：  
  
 `Customer('1`  
  
 `3812')`  
  
 這不是要求寄件人的目的。  
  
 如果 **unescapeRequestUrl** 屬性設定為 **false**，則當 <xref:System.Net.HttpListener> 收到要求時，會使用未經處理的 URI，而不使用從 `http.sys` 轉換的 URI 做為輸入 <xref:System.Net.HttpListenerRequest.Url%2A> 屬性。  
  
 **unescapeRequestUrl** 屬性的預設值為 **true**。  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> 屬性可用來從適用的組態檔中取得 **unescapeRequestUrl** 屬性的目前值。  
  
## 範例  
 下列程式碼範例示範當 <xref:System.Net.HttpListener> 類別收到要求使用未經處理的 URI 取代從 <xref:System.Net.HttpListenerRequest.Url%2A> 屬性之 `http.sys` 輸入轉換的 URI 時，應如何設定此類別。  
  
```  
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
  
## 項目資訊  
  
|||  
|-|-|  
|命名空間|System.Net|  
|結構描述名稱||  
|驗證檔||  
|可以是空白||  
  
## 請參閱  
 <xref:System.Net.Configuration.HttpListenerElement>   
 <xref:System.Net.HttpListener>   
 <xref:System.Net.HttpListenerRequest.Url%2A>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)