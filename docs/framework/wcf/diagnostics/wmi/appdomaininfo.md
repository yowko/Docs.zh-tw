---
title: "AppDomainInfo | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# AppDomainInfo
應用程式定義域資訊  
  
## 語法  
  
```  
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## 方法  
 AppDomainInfo 類別並未定義任何方法。  
  
## 屬性  
 AppDomainInfo 類別具有以下屬性：  
  
### AppDomainId  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 appdomain 的識別碼。  
  
### IsDefault  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指出 appdomain 是否為預設的 appdomain。  
  
### LogMalformedMessages  
 資料型別：布林值  
  
 存取類型：讀取\/寫入  
  
 值，指定是否記錄了格式錯誤的訊息。  
  
### LogMessagesAtServiceLevel  
 資料型別：布林值  
  
 存取類型：讀取\/寫入  
  
 值，指定是否在服務層級追蹤訊息 \(在加密和傳輸相關轉換之前\)。  
  
### LogMessagesAtTransportLevel  
 資料型別：布林值  
  
 存取類型：讀取\/寫入  
  
 值，指定是否在傳輸層級追蹤訊息。  
  
### MessageLoggingTraceListeners  
 資料型別：TraceListener 陣列  
  
 存取類型：唯讀  
  
 接聽 System.Wmi.MessageLogging 追蹤來源的集合追蹤接聽項。  
  
### 名稱  
 資料型別：字串  
  
 存取類型：唯讀  
  
 appdomain 的名稱。  
  
### PerformanceCounters  
 資料型別：字串  
  
 存取類型：唯讀  
  
 appdomain 中作用中效能計數器的範圍。  
  
### ProcessId  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 處理序識別碼。  
  
### ServiceConfigPath  
 資料型別：字串  
  
 存取類型：唯讀  
  
 服務組態的路徑。  
  
### TraceLevel  
 資料型別：字串  
  
 存取類型：讀取\/寫入  
  
 System.Wmi 追蹤來源的追蹤層級。  
  
### ServiceModelTraceListeners  
 資料型別：TraceListener 陣列  
  
 存取類型：唯讀  
  
 來自 System.ServiceModel 追蹤來源的接聽項集合。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|