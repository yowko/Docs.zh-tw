---
title: 動態地啟用分析的追蹤
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 46dfba2cb148009ddfd0bbd40e3b7202d774e0b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dynamically-enabling-analytic-tracing"></a>動態地啟用分析的追蹤
使用隨附於 Windows 作業系統的工具，您可以使用 Windows 事件追蹤 (ETW) 來動態啟用或停用追蹤。 所有[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]Windows Communication Foundation (WCF) 服務的分析追蹤可以啟用和停用，而不需要修改應用程式的 Web.config 檔案，或重新啟動服務。 這樣可讓發出追蹤事件的應用程式維持不變。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 追蹤選項可以使用類似的方法來設定。 例如，您可以將嚴重性層級從 **Error** 變更為 **Information** ，無須干擾應用程式。 使用下列工具即可達到這個目的：  
  
-   **Logman** – 命令列工具，用來設定、控制和查詢追蹤資料。 如需詳細資訊，請參閱[Logman 建立追蹤](http://go.microsoft.com/fwlink/?LinkId=165426)和[Logman 更新追蹤](http://go.microsoft.com/fwlink/?LinkId=165427)。  
  
-   **EventViewer** - Windows 圖形管理工具，用來檢視追蹤結果。 如需詳細資訊，請參閱[WCF 服務和 Windows 事件追蹤](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)和[事件檢視器](http://go.microsoft.com/fwlink/?LinkId=165428)。  
  
-   **Perfmon** – Windows 圖形管理工具，使用計數器來監事追蹤計數器和對於效能的追蹤效果。 如需詳細資訊，請參閱[資料收集器設定手動建立](http://go.microsoft.com/fwlink/?LinkId=165429)。  
  
### <a name="keywords"></a>關鍵字  
 使用 <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> 類別時，.NET Framework 追蹤訊息一般會由嚴重性層級加以篩選 (例如，[錯誤]、[警告] 和 [資訊])。 ETW 支援嚴重性層級的概念，不過會使用關鍵字引入全新、有彈性的篩選機制。 關鍵字是任意的文字值，可讓追蹤事件提供額外的內容，說明該事件的意義。  
  
 若是 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 分析追蹤，每個追蹤事件都有兩種類型的關鍵字。 第一，每個事件會有一個或多個案例關鍵字。 這些關鍵字會向案例表示，此事件提供支援。 有三組案例關鍵字，每組都是為特定目的而設計，如下表所示。 使用關鍵字篩選可以不需要干擾 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務來動態變更。 這代表您可以動態變更目前的追蹤案例和蒐集的追蹤資訊數量。 例如，您可以將 `HealthMonitoring` 變更為 `Troubleshooting` 並增加追蹤事件細微性。  
  
|關鍵字|描述|  
|-------------|-----------------|  
|`HealthMonitoring`|非常輕微、有限度的追蹤，讓您監視服務的活動。|  
|`EndToEndMonitoring`|用來支援訊息流動追蹤的事件。|  
|`Troubleshooting`|更多細微性事件圍繞 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]的擴充性點。|  
  
 第二組關鍵字會定義哪個 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 元件發出事件。  
  
|關鍵字|描述|  
|-------------|-----------------|  
|`UserEvents`|由使用者程式碼而不是 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]所發出的事件。|  
|`ServiceModel`|由 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 執行階段所發出的事件。|  
|`ServiceHost`|由服務主機所發出的事件。|  
|`WCFMessageLogging`|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 訊息記錄事件。|  
  
## <a name="see-also"></a>另請參閱  
 [WCF 服務和 Windows 的事件追蹤](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
