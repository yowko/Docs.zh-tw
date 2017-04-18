---
title: "HttpTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HttpTransportBindingElement
HttpTransportBindingElement  
  
## 語法  
  
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
  
## 方法  
 HttpTransportBindingElement 類別並未定義任何方法。  
  
## 屬性  
 HttpTransportBindingElement 類別具有下列屬性：  
  
### AllowCookies  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表用戶端是否接受 Cookie 並在未來的要求傳播 Cookie 的值。  
  
### AuthenticationScheme  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用於驗證由 HTTP 接聽項處理之用戶端要求的驗證配置。  
  
### BypassProxyOnLocal  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表是否針對本機位址略過 Proxy 的值。  
  
### HostNameComparisonMode  
 資料型別：字串  
  
 存取類型：唯讀  
  
 代表主機名稱是否用於連線到服務的值 \(當符合 URI 時\)。  
  
### KeepAliveEnabled  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 啟用時，不論活動等級為何，HTTP 連線會維持開啟。  
  
### MaxBufferSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 緩衝集區的大小上限。  
  
### ProxyAddress  
 資料型別：字串  
  
 存取類型：唯讀  
  
 包含用於 HTTP 要求之 Proxy 位址的 URI。  
  
### ProxyAuthenticationScheme  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用於驗證由 HTTP Proxy 處理之用戶端要求的驗證配置。  
  
### Realm  
 資料型別：字串  
  
 存取類型：唯讀  
  
 驗證領域。  
  
### TransferMode  
 資料型別：字串  
  
 存取類型：唯讀  
  
 代表訊息是經過緩衝處理或資料流處理，或為要求或回應的值。  
  
### UnsafeConnectionNtlmAuthentication  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表是否已在伺服器啟用「不安全的連線共用」的值。  
  
### UseDefaultWebProxy  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表是否使用全機器追蹤 Proxy 設定，而非使用者特定設定的值。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>