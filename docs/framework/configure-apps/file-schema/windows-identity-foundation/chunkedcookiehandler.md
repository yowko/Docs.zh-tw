---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252112"
---
# <a name="chunkedcookiehandler"></a>\<chunkedCookieHandler>
<xref:System.IdentityModel.Services.ChunkedCookieHandler>設定。 只有當`mode` `<cookieHandler>`元素的屬性為「預設」或「區塊」時, 才會出現此元素。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<chunkedCookieHandler >**  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|chunkSize|任何一個 HTTP cookie 的 HTTP cookie 資料大小上限 (以字元為單位)。 調整區塊大小時, 您必須小心。 網頁瀏覽器對於 cookie 大小和每個網域允許的數目有不同的限制。 例如, 原始的 Netscape 規格會約定這些限制:300 cookies 總計、每個 cookie 標頭4096個位元組 (包括中繼資料, 而不只是 cookie 值) 和每個網域20個 cookie。 預設值為2000。 必要項。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<xref:System.IdentityModel.Services.CookieHandler> 設定(SAM)用來讀取<xref:System.IdentityModel.Services.SessionAuthenticationModule>和寫入 cookie 的。|  
  
## <a name="remarks"></a>備註  
 當您<xref:System.IdentityModel.Services.ChunkedCookieHandler>將專案的`mode`屬性`<cookieHandler>`設定為 [預設] 或 [區塊] 時, 您可以指定 cookie 處理常式用`<chunkedCookieHandler>`來讀取和寫入 cookie 的區塊大小, 方法是包含子項目和設定其`chunkSize`屬性。 `<chunkedCookieHandler>`如果元素不存在, 則會使用預設的區塊大小2000個位元組。 當屬性設定為 "Custom" `mode`時, 無法指定此元素。  
  
 `<chunkedCookieHandler>`元素是<xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>由類別表示。  
  
## <a name="example"></a>範例  
 下列範例會設定區塊 cookie 處理常式, 以3000個位元組的區塊寫入 cookie。  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
