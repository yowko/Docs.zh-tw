---
title: "&lt;chunkedCookieHandler&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;chunkedCookieHandler&gt;
設定<xref:System.IdentityModel.Services.ChunkedCookieHandler>。  這個項目可能只會顯示如果`mode`屬性的`<cookieHandler>`項目為 「 預設 」 或 「 區塊 」。  
  
## 語法  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|chunkSize|以字元為單位，任何一個 HTTP cookie 的 HTTP cookie 資料的最大大小。  您必須調整區塊大小時請特別小心。  網頁瀏覽器 cookie 和每個網域所允許的數字的大小有所限制。  比方說，原始的 Netscape 規格 stipulated 這些限制： 加總 300 的 cookie，4096 個位元組，每個 cookie 標頭 \(包括中繼資料，而不只是 cookie 值\) 和 20 的 cookie，每個網域。  預設值為 2000。  必要項。|  
  
### 子項目  
 None  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<cookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|設定<xref:System.IdentityModel.Services.CookieHandler> ， <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\) 用來讀取和寫入 cookie。|  
  
## 備註  
 當您指定<xref:System.IdentityModel.Services.ChunkedCookieHandler>藉由設定`mode`屬性的`<cookieHandler>` "預設"或"區塊 」 的項目，您可以指定區塊大小 cookie 處理常式用來讀取和寫入 cookie，藉以`<chunkedCookieHandler>`子項目，並設定其`chunkSize`屬性。  如果`<chunkedCookieHandler>`項目不存在，會使用預設的區塊大小的 2000 位元組。  這個項目不能指定何時`mode`屬性設定為 \[自訂\]。  
  
 `<chunkedCookieHandler>`項目會以<xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>類別。  
  
## 範例  
 下列範例會設定將 cookie 寫入至 3000 位元組的區塊中的區塊的 cookie 處理常式。  
  
```  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## 請參閱  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>