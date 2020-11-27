---
title: 管理與診斷
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
ms.openlocfilehash: 703724c3040f2508f011e002c22fa45dd3197884
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285560"
---
# <a name="administration-and-diagnostics"></a>管理與診斷

Windows Communication Foundation (WCF) 提供一組豐富的功能，可協助您監視應用程式生命週期的不同階段。 例如，您可以使用組態在部署時設定服務與用戶端。 WCF 包含一組大量的效能計數器，可協助您測量應用程式的效能。 WCF 也會透過 WCF Windows Management Instrumentation (WMI) 提供者，在執行時間公開服務的檢查資料。 當應用程式遭遇失敗或開始發生異常行為時，您可以使用事件日誌檢查是否發生任何顯著的事件。 您也可以使用訊息記錄與追蹤檢查在應用程式中端對端之間發生的事件。 這些功能可協助開發人員和 IT 專業人員在 WCF 應用程式未正確運作時進行疑難排解。  
  
> [!NOTE]
> 如果您收到的錯誤沒有特定的詳細資訊，您應該啟用 configuration 專案的 `includeExceptionDetailInFaults` 屬性 [\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md) 。 這會指示 WCF 傳送例外狀況詳細資料給用戶端，讓您在不需要更先進的診斷的情況下，偵測到許多常見問題。 如需詳細資訊，請參閱傳送 [和接收錯誤](../sending-and-receiving-faults.md)。  
  
## <a name="diagnostics-features-provided-by-wcf"></a>WCF 提供的診斷功能  

 WCF 提供下列診斷功能：  
  
- 端對端追蹤可以在不使用偵錯工具的情況下，提供疑難排解應用程式的檢測資料。 WCF 會輸出進程里程碑的追蹤以及錯誤訊息。 這可以包含開啟通道處理站，或是由服務主機傳送與接收訊息。 您可以針對執行中的應用程式啟用追蹤以監視其進度。 如需詳細資訊，請參閱 [追蹤](./tracing/index.md) 主題。 若要瞭解如何使用追蹤來對應用程式進行疑難排解，請參閱 [使用追蹤疑難排解您的應用程式](./tracing/using-tracing-to-troubleshoot-your-application.md) 主題。  
  
- 訊息記錄可以讓您檢查訊息在傳輸前後的內容。 如需詳細資訊，請參閱 [訊息記錄](message-logging.md) 主題。  
  
- 事件追蹤會在事件記錄中寫入任何主要問題的事件。 然後可以使用事件檢視器檢查任何異常狀況。 如需詳細資訊，請參閱 [事件記錄](./event-logging/index.md) 主題。  
  
- 透過效能監視器公開的效能計數器，能夠讓您監視應用程式與系統的健康狀態。 如需詳細資訊，請參閱 [效能計數器](./performance-counters/index.md) 主題。  
  
- <xref:System.ServiceModel.Configuration> 命名空間可以讓您載入組態檔然後設定服務或用戶端端點。 當更新必須部署至許多電腦上時，您可以使用物件模型將對許多應用程式的變更寫入指令碼。 或者，您可以使用 [設定 [編輯器] 工具 ( # A0) ](../configuration-editor-tool-svcconfigeditor-exe.md) 使用 GUI wizard 來編輯設定設定。 如需詳細資訊，請參閱設定 [您的應用程式](configuring-your-application.md) 主題。  
  
- WMI 能夠讓您找出正在機器上接聽的服務，以及正在使用中的繫結。 如需詳細資訊，請參閱 [使用 Windows Management Instrumentation 診斷](./wmi/index.md) 主題。  
  
 WCF 也提供數個 GUI 和命令列工具，讓您更輕鬆地建立、部署及管理 WCF 應用程式。 如需詳細資訊，請參閱 [Windows Communication Foundation 工具](../tools.md)。 例如，您可以使用設定 [編輯器工具 ( # A0) ](../configuration-editor-tool-svcconfigeditor-exe.md) 來建立和編輯使用 WIZARD 的 WCF 設定，而不是直接編輯 XML。 您也可以使用 [服務追蹤檢視器工具 ( # A0) ](../service-trace-viewer-tool-svctraceviewer-exe.md) 來查看、群組和篩選追蹤訊息，讓您可以診斷、修復和驗證 WCF 服務的問題。  
  
## <a name="see-also"></a>另請參閱

- [設定您的應用程式](configuring-your-application.md)
- [部署服務](deploying-services.md)
- [例外狀況參考](./exceptions-reference/index.md)
- [事件記錄](./event-logging/index.md)
- [訊息記錄](message-logging.md)
- [組態編輯器工具 (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)
- [服務追蹤檢視器工具 (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [ServiceModel 註冊工具](servicemodel-registration-tool.md)
- [追蹤](./tracing/index.md)
- [使用 Windows Management Instrumentation 進行診斷](./wmi/index.md)
- [效能計數器](./performance-counters/index.md)
- [Windows Communication Foundation 工具](../tools.md)
