---
title: '&lt;chunkedCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 906a9e7cafca14dc4ee13dcb9eb9e59736464fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltchunkedcookiehandlergt"></a>&lt;chunkedCookieHandler&gt;
設定<xref:System.IdentityModel.Services.ChunkedCookieHandler>。 這個項目可能只會存在於如果`mode`屬性`<cookieHandler>`元素是 「 預設 」 或 「 區塊 」。  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<Requiressl >  
\<chunkedCookieHandler >  
  
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
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|chunkSize|大小上限，以字元為單位的任何一個 HTTP cookie 的 HTTP cookie 資料。 您必須小心時調整的區塊大小。 網頁瀏覽器的 cookie 和每個網域的允許數目大小有不同的限制。 例如，原始的 Netscape 規格約定這些限制： 300 cookie 加總，4096 個位元組，每個 cookie 標頭 （包括中繼資料，不只是 cookie 的值） 和每個網域的 20 cookie。 預設值是 2000年。 必要項。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<Requiressl >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|設定<xref:System.IdentityModel.Services.CookieHandler>， <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 用來讀取和寫入 cookie。|  
  
## <a name="remarks"></a>備註  
 當您指定<xref:System.IdentityModel.Services.ChunkedCookieHandler>藉由設定`mode`屬性`<cookieHandler>`"Default"或"Chunked"的項目，您可以指定區塊大小的 cookie 處理常式用來讀取和寫入，藉以 cookie`<chunkedCookieHandler>`子項目和設定其`chunkSize`屬性。 如果`<chunkedCookieHandler>`項目不存在，使用預設區塊大小為 2000 個位元組。 此元素不能指定何時`mode`屬性設為"Custom"。  
  
 `<chunkedCookieHandler>`項目由<xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>類別。  
  
## <a name="example"></a>範例  
 下列範例會設定會將 cookie 寫入 3000 位元組的區塊的區塊的 cookie 處理常式。  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
