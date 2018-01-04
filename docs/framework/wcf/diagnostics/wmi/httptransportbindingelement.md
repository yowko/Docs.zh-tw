---
title: HttpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6370284dbd9c680b29f315c791ea76356e7b36f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="httptransportbindingelement"></a>HttpTransportBindingElement
HttpTransportBindingElement  
  
## <a name="syntax"></a>語法  
  
```  
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a>方法  
 HttpTransportBindingElement 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  
 HttpTransportBindingElement 類別具有下列屬性：  
  
### <a name="allowcookies"></a>AllowCookies  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 表示用戶端是否接受 Cookie 並在未來的要求傳播 Cookie 的值。  
  
### <a name="authenticationscheme"></a>AuthenticationScheme  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用於驗證由 HTTP 接聽項處理之用戶端要求的驗證配置。  
  
### <a name="bypassproxyonlocal"></a>BypassProxyOnLocal  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表是否針對本機位址略過 Proxy 的值。  
  
### <a name="hostnamecomparisonmode"></a>HostNameComparisonMode  
 資料型別：字串  
  
 存取類型：唯讀  
  
 代表主機名稱是否用於連線到服務的值 (當符合 URI 時)。  
  
### <a name="keepaliveenabled"></a>KeepAliveEnabled  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 啟用時，不論活動等級為何，HTTP 連線會維持開啟。  
  
### <a name="maxbuffersize"></a>MaxBufferSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 緩衝集區的大小上限。  
  
### <a name="proxyaddress"></a>ProxyAddress  
 資料型別：字串  
  
 存取類型：唯讀  
  
 包含用於 HTTP 要求之 Proxy 位址的 URI。  
  
### <a name="proxyauthenticationscheme"></a>ProxyAuthenticationScheme  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用於驗證由 HTTP Proxy 處理之用戶端要求的驗證配置。  
  
### <a name="realm"></a>Realm  
 資料型別：字串  
  
 存取類型：唯讀  
  
 驗證領域。  
  
### <a name="transfermode"></a>TransferMode  
 資料型別：字串  
  
 存取類型：唯讀  
  
 代表訊息是經過緩衝處理或資料流處理，或為要求或回應的值。  
  
### <a name="unsafeconnectionntlmauthentication"></a>UnsafeConnectionNtlmAuthentication  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表是否已在伺服器啟用「不安全的連線共用」的值。  
  
### <a name="usedefaultwebproxy"></a>UseDefaultWebProxy  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表是否使用全機器追蹤 Proxy 設定，而非使用者特定設定的值。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
