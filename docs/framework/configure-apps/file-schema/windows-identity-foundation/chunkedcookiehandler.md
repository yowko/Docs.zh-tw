---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: d9c81d5de7bea343f0d67fa00037763fbae7b8c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120779"
---
# <a name="chunkedcookiehandler"></a>\<chunkedCookieHandler>
設定<xref:System.IdentityModel.Services.ChunkedCookieHandler>。 這個項目只會出現如果`mode`屬性的`<cookieHandler>`項目是 「 預設 」 或 「 區塊 」。  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<cookieHandler>  
\<chunkedCookieHandler>  
  
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
|chunkSize|最大的大小，以字元為單位的任何一個的 HTTP cookie 的 HTTP cookie 資料。 您必須小心調整區塊大小。 網頁瀏覽器 cookie 和每一個網域允許的數字的大小有不同的限制。 例如，原始的 Netscape 規格約定這些限制：4096 個位元組，每個 cookie 標頭 （包括中繼資料，不只是 cookie 值），以及每個網域的 20 cookie 總 300 的 cookie。 預設值是 2000年。 必要項。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<cookieHandler>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|會設定<xref:System.IdentityModel.Services.CookieHandler>， <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 會使用來讀取和寫入 cookie。|  
  
## <a name="remarks"></a>備註  
 當您指定<xref:System.IdentityModel.Services.ChunkedCookieHandler>splittunneling`mode`屬性`<cookieHandler>`"Default"或"Chunked"的項目，您可以指定區塊大小的 cookie 處理常式用來讀取和寫入 cookie 包括`<chunkedCookieHandler>`子項目和設定其`chunkSize`屬性。 如果`<chunkedCookieHandler>`項目不存在，使用 2000 個位元組的預設區塊大小。 此元素不能指定何時`mode`屬性設為"Custom"。  
  
 `<chunkedCookieHandler>`項目由<xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>類別。  
  
## <a name="example"></a>範例  
 下列範例會設定區塊的 cookie 處理常式會將 cookie 寫入以 3000 位元組的區塊。  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
