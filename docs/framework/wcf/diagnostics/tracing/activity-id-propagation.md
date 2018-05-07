---
title: 活動識別碼傳播
ms.date: 03/30/2017
ms.assetid: cd1c1ae5-cc8a-4f51-90c9-f7b476bcfe70
ms.openlocfilehash: e51970f693d9ca2d2f81bf4efc97969896de4828
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="activity-id-propagation"></a>活動識別碼傳播
傳播會在 ServiceModel 活動追蹤啟用 (ServiceModel 傳播) 或停用 (使用者對使用者活動傳播) 時發生。  
  
## <a name="servicemodel-activity-tracing-is-enabled"></a>已啟用 ServiceModel 活動追蹤  
 如果已啟用 ServiceModel ActivityTracing，則傳播會在 ProcessAction 活動之間發生。  
  
### <a name="server"></a>伺服器  
 當`propagateActivity`屬性設為`true`同時在用戶端和伺服器上，識別碼`ProcessAction`伺服器中的活動等同於中傳播的識別碼`ActivityId`訊息標頭。  
  
 若未`ActivityId`標頭已存在訊息中 (也就是`propagateActivity` = `false`用戶端上)，或當`propagateActivity` = `false`在伺服器上，伺服器會產生新的活動識別碼。  
  
### <a name="client"></a>用戶端  
 如果用戶端為同步單一執行緒，則用戶端會忽略用戶端或伺服器的任何 `propagateActivity` 設定， 所以回應會改而在要求活動中處理。 如果用戶端為非同步或同步多執行緒、 `propagateActivity` = `true`中用戶端和伺服器所傳送的訊息中沒有的活動識別碼標頭，用戶端從訊息擷取活動識別碼，並傳輸至處理動作 」 活動包含傳播的活動識別碼。 否則，用戶端會從「處理訊息」活動傳輸至新的「處理動作」活動。 傳輸至新的「處理動作」活動是為了求得一致性才進行的額外動作。 在這個活動內，用戶端會從本機執行緒內容中擷取 BeginCall 活動的活動識別碼，同時執行緒也會配置用來處理回應訊息。 然後，用戶端會傳輸至初始「處理動作」活動。  
  
 如果用戶端為雙工，則可當做伺服器接收訊息。  
  
### <a name="propagation-in-fault-messages"></a>錯誤訊息中的傳播  
 處理有效和錯誤訊息之間並無差異。 如果`propagateActivity` = `true`，活動識別碼新增至 SOAP 錯誤訊息標頭等同於環境的活動。  
  
## <a name="servicemodel-activity-tracing-is-disabled"></a>已停用 ServiceModel 活動追蹤  
 如果已停用 ServiceModel ActivityTracing，則傳播會直接在使用者程式碼活動之間發生，而不會經過 ServiceModel 活動。 使用者定義的活動識別碼也會透過訊息活動識別碼標頭進行傳播。  
  
 如果`propagateActivity` = `true`和`ActivityTracing` = `off` （不論是否已啟用 ServiceModel 追蹤） ServiceModel 追蹤接聽程式，會發生下列事項用戶端或伺服器上：  
  
-   在作業要求或傳送回應時，TLS 中的活動識別碼會傳播至使用者程式碼外，直到形成訊息為止。 傳送活動識別碼標頭之前，也會將該標頭插入訊息。  
  
-   在接收要求或接收回應時，只要一建立收到的訊息物件，就會從訊息標頭擷取活動識別碼。 只要訊息一從範圍內消失，就會傳播 TLS 中的活動識別碼，直到到達使用者程式碼為止。  
  
 這些動作可確保只要開啟傳播，相同的活動中就會出使用者追蹤。 不過，ServiceModel 追蹤則不一定如此。 只有在設定使用者程式碼活動的相同執行緒上處理 ServiceModel 追蹤時，這些追蹤才會發生在使用者程式碼活動中。  
  
 一般來說，ServiceModel 追蹤會出現在下列位置：  
  
-   如果已停用 ServiceModel 追蹤，則所有發出的追蹤都會出現在使用者活動中。 如果已在伺服器和用戶端上啟用傳播，這些追蹤就會位於相同活動中。  
  
-   如果已啟用 ServiceModel 追蹤但停用 ActivityTracing，則在兩端皆啟用傳播時，使用者追蹤會出現在相同的活動中。 ServiceModel 追蹤會出現在預設的 0000 活動中，除非這些追蹤是發生在與使用者程式碼處理過程相同的執行緒中，而活動一開始會在這個過程中設定。  
  
-   如果已同時啟用 ServiceModel 追蹤和 ActivityTracing，則使用者追蹤會出現在使用者定義的活動中，而 ServiceModel 追蹤則會出現在 ServiceModel 定義的活動中。 傳播會發生在 ServiceModel 層級。
