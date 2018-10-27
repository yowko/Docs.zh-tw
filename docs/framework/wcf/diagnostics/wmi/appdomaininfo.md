---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 0b7f8aadbd9a9dfcdd33fc65be3a5a41ea95f5be
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50170220"
---
# <a name="appdomaininfo"></a>AppDomainInfo
應用程式定義域資訊  
  
## <a name="syntax"></a>語法  
  
```csharp
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
  
## <a name="methods"></a>方法  
 AppDomainInfo 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  
 AppDomainInfo 類別具有以下屬性：  
  
### <a name="appdomainid"></a>AppDomainId  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 appdomain 的識別碼。  
  
### <a name="isdefault"></a>IsDefault  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指出 appdomain 是否為預設的 appdomain。  
  
### <a name="logmalformedmessages"></a>LogMalformedMessages  
 資料型別：布林值  
  
 存取類型：讀取/寫入  
  
 值，指定是否記錄了格式錯誤的訊息。  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  
 資料型別：布林值  
  
 存取類型：讀取/寫入  
  
 值，指定是否在服務層級追蹤訊息 (在加密和傳輸相關轉換之前)。  
  
### <a name="logmessagesattransportlevel"></a>LogMessagesAtTransportLevel  
 資料型別：布林值  
  
 存取類型：讀取/寫入  
  
 值，指定是否在傳輸層級追蹤訊息。  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  
 資料型別：TraceListener 陣列  
  
 存取類型：唯讀  
  
 接聽 System.Wmi.MessageLogging 追蹤來源的集合追蹤接聽項。  
  
### <a name="name"></a>名稱  
 資料型別：字串  
  
 存取類型：唯讀  
  
 appdomain 的名稱。  
  
### <a name="performancecounters"></a>PerformanceCounters  
 資料型別：字串  
  
 存取類型：唯讀  
  
 appdomain 中作用中效能計數器的範圍。  
  
### <a name="processid"></a>ProcessId  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 處理序識別碼。  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  
 資料型別：字串  
  
 存取類型：唯讀  
  
 服務組態的路徑。  
  
### <a name="tracelevel"></a>TraceLevel  
 資料型別：字串  
  
 存取類型：讀取/寫入  
  
 System.Wmi 追蹤來源的追蹤層級。  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  
 資料型別：TraceListener 陣列  
  
 存取類型：唯讀  
  
 來自 System.ServiceModel 追蹤來源的接聽項集合。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|
