---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: 15304630eb8a14e01d4815ddddc84cd32796fdcf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133476"
---
# <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings
LocalServiceSecuritySettings  
  
## <a name="syntax"></a>語法  
  
```csharp
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a>方法  
 LocalServiceSecuritySettings 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 LocalServiceSecuritySettings 類別具有下列屬性：  
  
### <a name="detectreplays"></a>DetectReplays  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 布林值，這個值會指定是否會偵測及自動處理對通道所發出的重新執行攻擊。  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 服務支援的暫止安全性工作階段數目上限。  
  
### <a name="issuedcookielifetime"></a>IssuedCookieLifetime  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 TimeSpan 指定發出給所有新的安全性 Cookie 的存留期。  
  
### <a name="maxcachedcookies"></a>MaxCachedCookies  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 可以快取的 Cookie 數目上限。  
  
### <a name="maxclockskew"></a>MaxClockSkew  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 TimeSpan 指定通訊雙方之系統時鐘之間的最大時間差異。  
  
### <a name="maxpendingsessions"></a>MaxPendingSessions  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 服務上的最大暫止連線數目。  
  
### <a name="maxstatefulnegotiations"></a>MaxStatefulNegotiations  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 可以同時為作用中的安全性交涉數目。  
  
### <a name="negotiationtimeout"></a>NegotiationTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 TimeSpan 指定伺服器和用戶端之間安全性交涉階段的最大持續期間。  
  
### <a name="reconnecttransportonfailure"></a>ReconnectTransportOnFailure  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 布林值，指定使用 WS-Reliable 訊息的連線是否會在傳輸失敗之後嘗試重新連線。  
  
### <a name="replaycachesize"></a>ReplayCacheSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 用於偵測重新執行的已快取 Nonce 數目。  
  
### <a name="replaywindow"></a>ReplayWindow  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 TimeSpan 指定個別訊息 Nonce 有效的持續期間。  
  
### <a name="sessionkeyrenewalinterval"></a>SessionKeyRenewalInterval  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 指定持續期間的 TimeSpan，啟動器將在這段期間過後更新安全性工作階段的金鑰。  
  
### <a name="sessionkeyrolloverinterval"></a>SessionKeyRolloverInterval  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 TimeSpan，指定前一個工作階段金鑰在金鑰更新期間對傳入訊息屬有效的時間間隔。  
  
### <a name="timestampvalidityduration"></a>TimestampValidityDuration  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 TimeSpan，指定時間戳記有效的持續期間。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
