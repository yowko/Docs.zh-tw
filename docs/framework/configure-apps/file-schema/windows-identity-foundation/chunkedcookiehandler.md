---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: a321c10e04eca2c1a5204929966a1725e918cbdf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158522"
---
# \<chunkedCookieHandler>

設定 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。 只有當專案的 `mode` 屬性 `<cookieHandler>` 是 "Default" 或 "區塊" 時，才會出現這個元素。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|chunkSize|任何一個 HTTP cookie 的 HTTP cookie 資料大小上限（以字元為單位）。 調整區塊大小時，您必須特別小心。 網頁瀏覽器對於 cookie 大小和每個網域允許的數目有不同的限制。 例如，原始的 Netscape 規格會約定這些限制：300個 cookie 總計、4096個位元組的每個 cookie 標頭 (包括中繼資料，而不只是) 的 cookie 值，以及每個網域20個 cookie。 預設值為 2000。 必要。|  
  
### <a name="child-elements"></a>子元素  

 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|設定 <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 用來讀取和寫入 cookie 的。|  
  
## <a name="remarks"></a>備註  

 當您將專案的 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 屬性設定 `mode` 為「預設」或「區塊」時 `<cookieHandler>` ，可以指定 cookie 處理常式用來讀取和寫入 cookie 的區塊大小，方法是包含 `<chunkedCookieHandler>` 子項目並設定其 `chunkSize` 屬性。 如果專案 `<chunkedCookieHandler>` 不存在，則會使用預設的區塊大小2000個位元組。 當 `mode` 屬性設定為 "Custom" 時，不能指定這個元素。  
  
 `<chunkedCookieHandler>`元素是由 <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> 類別表示。  
  
## <a name="example"></a>範例  

 下列範例會設定區塊 cookie 處理常式，以3000個位元組的區塊寫入 cookie。  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
