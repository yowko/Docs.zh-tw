---
title: 動態地啟用分析的追蹤
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 22d122f802e82c2aa04d72a996cb872e06fcaeaa
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674949"
---
# <a name="dynamically-enabling-analytic-tracing"></a>動態地啟用分析的追蹤
使用隨附於 Windows 作業系統的工具，您可以使用 Windows 事件追蹤 (ETW) 來動態啟用或停用追蹤。 對於所有[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]Windows 通信基礎 （WCF） 服務，無需修改應用程式的 Web.config 檔或重新開機服務，即可動態啟用和禁用分析跟蹤。 這樣可讓發出追蹤事件的應用程式維持不變。  
  
 WCF 跟蹤選項可以以類似方式配置。 例如，您可以將嚴重性層級從 **Error** 變更為 **Information** ，無須干擾應用程式。 使用下列工具即可達到這個目的：  
  
- **Logman** – 命令列工具，用來設定、控制和查詢追蹤資料。 有關詳細資訊，請參閱[日誌創建跟蹤](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc788036(v=ws.10))和[日誌人更新跟蹤](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc788128(v=ws.10))。  
  
- **EventViewer** - Windows 圖形管理工具，用來檢視追蹤結果。 有關詳細資訊，請參閱[Windows 和事件檢視器的 WCF 服務和事件跟蹤](../../samples/wcf-services-and-event-tracing-for-windows.md)。 [Event Viewer](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766042(v=ws.11))  
  
- **Perfmon** – Windows 圖形管理工具，使用計數器來監事追蹤計數器和對於效能的追蹤效果。 有關詳細資訊，請參閱[手動創建資料收集器集](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766404(v=ws.11))。  
  
### <a name="keywords"></a>關鍵字  
 使用 <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> 類別時，.NET Framework 追蹤訊息一般會由嚴重性層級加以篩選 (例如，[錯誤]、[警告] 和 [資訊])。 ETW 支援嚴重性層級的概念，不過會使用關鍵字引入全新、有彈性的篩選機制。 關鍵字是任意的文字值，可讓追蹤事件提供額外的內容，說明該事件的意義。  
  
 對於 WCF 分析跟蹤，每個跟蹤事件有兩種類型的關鍵字。 第一，每個事件會有一個或多個案例關鍵字。 這些關鍵字會向案例表示，此事件提供支援。 有三組案例關鍵字，每組都是為特定目的而設計，如下表所示。 使用關鍵字進行篩選可以動態更改，而不會干擾 WCF 服務。 這代表您可以動態變更目前的追蹤案例和蒐集的追蹤資訊數量。 例如，您可以將 `HealthMonitoring` 變更為 `Troubleshooting` 並增加追蹤事件細微性。  
  
|關鍵字|描述|  
|-------------|-----------------|  
|`HealthMonitoring`|非常輕微、有限度的追蹤，讓您監視服務的活動。|  
|`EndToEndMonitoring`|用來支援訊息流動追蹤的事件。|  
|`Troubleshooting`|圍繞 WCF 擴充點發生的更精細的事件。|  
  
 第二組關鍵字定義 .NET 框架的哪個元件發出事件。  
  
|關鍵字|描述|  
|-------------|-----------------|  
|`UserEvents`|使用者代碼而不是 .NET 框架發出的事件。|  
|`ServiceModel`|WCF 運行時發出的事件。|  
|`ServiceHost`|由服務主機所發出的事件。|  
|`WCFMessageLogging`|WCF 消息日誌記錄事件。|  
  
## <a name="see-also"></a>另請參閱

- [WCF Services and Event Tracing for Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
