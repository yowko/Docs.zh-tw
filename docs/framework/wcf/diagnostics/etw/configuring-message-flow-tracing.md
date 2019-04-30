---
title: 設定訊息流程追蹤
ms.date: 03/30/2017
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
ms.openlocfilehash: 02c43b152cb1aef1684185e56eb7f172036ac46b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999514"
---
# <a name="configuring-message-flow-tracing"></a>設定訊息流程追蹤
啟用 Windows Communication Foundation (WCF) 的活動追蹤時，整個 WCF 堆疊中的邏輯活動指派端對端活動識別碼。 現在，[!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] 針對這項功能提供了具備更高效能且可搭配 Windows 事件追蹤 (ETW) 使用的版本，也就是所謂的訊息流程追蹤。 啟用之後，就會取得傳入訊息的端對端活動識別碼 (若是空的則會指派)，並且傳播給在通道將訊息解碼之後發出的所有追蹤事件。 在解碼之後，客戶可以使用這項功能，利用來自不同服務的追蹤記錄重新建構訊息流程。  
  
 偵測到應用程式的問題之後，可以啟用追蹤，等到問題解決再停用追蹤。  
  
## <a name="enabling-tracing"></a>啟用追蹤  
 若要啟用訊息流程追蹤，請將 .NET Framework 4 `messageFlowTracing` 組態項目設定為 `true`，如以下範例所示。  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
>  由於 `endToEndTracing` 組態項目位於 Web.config 檔案中，所以不能像 ETW 那樣利用動態方式設定。 應用程式必須先進行回收，`endToEndTracing` 組態項目才會生效。  
  
 活動會透過交換識別碼 (稱為活動識別碼) 建立相互關聯。 這個識別碼是 GUID，由 System.Diagnostics.CorrelationManager 類別所產生。 如果您要操作 System.Diagnostics.Trace.CorrelationManager.ActivityID，請確定此值在執行控制權傳回給 WCF 程式碼時設定為原始值。  此外，如果您要使用非同步 WCF 程式撰寫模型，請確定 System.Diagnostics.Trace.CorrelationManager.ActivityID 會在執行緒之間傳輸。  
  
## <a name="message-flow-tracing-and-rest-services"></a>訊息流程追蹤和 REST 服務  
 訊息流程追蹤可讓您端對端地追蹤要求。  透過 SOAP 服務，在 SOAP 訊息標頭中傳送活動 ID。 REST 要求不包含此標頭，因此會改用特殊 HTTP 事件標頭。 下列程式碼片段顯示如何以程式設計方式擷取活動 ID 值：  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 您可以使用下列程式碼，以程式設計方式加入標頭：  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
