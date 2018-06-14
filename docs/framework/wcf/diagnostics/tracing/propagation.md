---
title: 傳播
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: f4e92c6dec163d191c507dd80bb0d9dc129c6e96
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803233"
---
# <a name="propagation"></a>傳播
本主題說明 Windows Communication Foundation (WCF) 追蹤模型中的活動傳播。  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>使用傳播將端點上的活動相互關聯  
 傳播會針對應用程式端點間的相同處理單位 (例如，要求)，將錯誤追蹤的直接相互關聯提供給使用者。 在不同端點針對相同處理單位發出的錯誤會組成相同的活動群組，即使是跨應用程式定義域亦然。 這項工作是藉由傳播訊息標頭中的活動識別碼來達成。 因此，如果用戶端因為伺服器發生內部錯誤而逾時，則基於直接的相互關聯，這兩個錯誤都會出現在相同的活動中。  
  
 若要執行這項工作，請使用 `ActivityTracing` 設定，如前述範例所示。 此外，還要在所有端點上設定 `propagateActivity` 追蹤來源的 `System.ServiceModel` 屬性。  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 活動傳播是可設定的功能，讓 WCF 將標頭新增至傳出訊息，其中包含 TLS 上的活動識別碼。 將這個識別碼包含在對伺服器端的後續追蹤中，我們就可以將用戶端和伺服器活動相互關聯起來。  
  
## <a name="propagation-definition"></a>傳播定義  
 如果下列所有條件都成立，就會將活動 M 的 gAId 傳播至活動 N。  
  
-   N 是因為 M 而建立的  
  
-   N 知道 M 的 gAId  
  
-   N 的 gAId 等於 M 的 gAId。  
  
 gAId 是透過 ActivityId 訊息標頭所傳播，如下列 XML 結構描述所示。  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 下列是訊息標頭的範例。  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"     
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"   
  
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous  
          </a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a>傳播和活動界限  
 在端點之間傳播活動識別碼時，訊息接收者會將「開始」和「停止」追蹤與這個 (傳播) 活動識別碼一起發出。 因此，會有包含來自每個追蹤來源之 gAId 的「開始」和「停止」追蹤。 如果數個端點位於相同的處理序且使用相同的追蹤來源名稱，就會建立多個具有相同 lAId (相同 gAId、相同追蹤來源、相同處理序) 的「開始」和「停止」追蹤。  
  
## <a name="synchronization"></a>同步處理  
 若要在執行於不同電腦的端點之間同步處理事件，請將 CorrelationId 新增至訊息中所傳播的 ActivityId 標頭。 工具可以使用這個識別碼，在時鐘不一致的電腦之間同步處理事件。 具體來說，「服務追蹤檢視器」工具會使用這個識別碼來顯示端點之間的訊息流動。  
  
## <a name="see-also"></a>另請參閱  
 [設定追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [使用服務追蹤檢視器檢視相關追蹤並進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [端對端追蹤案例](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
