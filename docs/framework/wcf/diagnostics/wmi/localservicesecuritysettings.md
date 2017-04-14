---
title: "LocalServiceSecuritySettings | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# LocalServiceSecuritySettings
LocalServiceSecuritySettings  
  
## 語法  
  
```  
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
  
## 方法  
 LocalServiceSecuritySettings 類別不會定義任何方法。  
  
## 屬性  
 LocalServiceSecuritySettings 類別具有下列屬性：  
  
### DetectReplays  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 布林值，這個值會指定是否會偵測及自動處理對通道所發出的重新執行攻擊。  
  
### InactivityTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 服務支援的暫止安全性工作階段數目上限。  
  
### IssuedCookieLifetime  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 TimeSpan 指定發出給所有新的安全性 Cookie 的存留期。  
  
### MaxCachedCookies  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 可以快取的 Cookie 數目上限。  
  
### MaxClockSkew  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 TimeSpan 指定通訊雙方之系統時鐘之間的最大時間差異。  
  
### MaxPendingSessions  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 服務上的最大暫止連線數目。  
  
### MaxStatefulNegotiations  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 可以同時為作用中的安全性交涉數目。  
  
### NegotiationTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 TimeSpan 指定伺服器和用戶端之間安全性交涉階段的最大持續期間。  
  
### ReconnectTransportOnFailure  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 布林值，指定使用 WS\-Reliable 訊息的連線是否會在傳輸失敗之後嘗試重新連線。  
  
### ReplayCacheSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 用於偵測重新執行的已快取 Nonce 數目。  
  
### ReplayWindow  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 TimeSpan 指定個別訊息 Nonce 有效的持續期間。  
  
### SessionKeyRenewalInterval  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 指定持續期間的 TimeSpan，啟動器將在這段期間過後更新安全性工作階段的金鑰。  
  
### SessionKeyRolloverInterval  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 TimeSpan，指定前一個工作階段金鑰在金鑰更新期間對傳入訊息屬有效的時間間隔。  
  
### TimestampValidityDuration  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 TimeSpan，指定時間戳記有效的持續期間。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>