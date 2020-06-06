---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252112"
---
# \<chunkedCookieHandler>
設定 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。 只有當 `mode` 元素的屬性為「預設」或「區塊」時，才會出現此元素 `<cookieHandler>` 。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a>語法  
  
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
|chunkSize|任何一個 HTTP cookie 的 HTTP cookie 資料大小上限（以字元為單位）。 調整區塊大小時，您必須小心。 網頁瀏覽器對於 cookie 大小和每個網域允許的數目有不同的限制。 例如，原始的 Netscape 規格會約定這些限制： 300 cookies 總計、每個 cookie 標頭4096個位元組（包括中繼資料，而不只是 cookie 值）和每個網域20個 cookie。 預設值為 2000。 必要。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|設定 <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM）用來讀取和寫入 cookie 的。|  
  
## <a name="remarks"></a>備註  
 當您將專案 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 的屬性設定 `mode` `<cookieHandler>` 為 [預設] 或 [區塊] 時，可以指定 cookie 處理常式用來讀取和寫入 cookie 的區塊大小，方法是包含 `<chunkedCookieHandler>` 子項目並設定其 `chunkSize` 屬性。 如果 `<chunkedCookieHandler>` 元素不存在，則會使用預設的區塊大小2000個位元組。 當 `mode` 屬性設定為 "Custom" 時，無法指定此元素。  
  
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
