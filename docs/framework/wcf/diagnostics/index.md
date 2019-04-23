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
ms.openlocfilehash: 351d133215343e07e849ad1045eba601dd8cce56
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092276"
---
# <a name="administration-and-diagnostics"></a>管理與診斷
Windows Communication Foundation (WCF) 提供一組豐富的功能，可協助您監視應用程式的生命週期的不同階段。 例如，您可以使用組態在部署時設定服務與用戶端。 WCF 包含大量的效能計數器，可協助您測量應用程式的效能。 WCF 也會公開服務，以在透過 WCF Windows Management Instrumentation (WMI) 提供者的執行階段檢查的資料。 當應用程式遭遇失敗或開始發生異常行為時，您可以使用事件日誌檢查是否發生任何顯著的事件。 您也可以使用訊息記錄與追蹤檢查在應用程式中端對端之間發生的事件。 這些功能可協助開發人員和 IT 專業人員疑難排解 WCF 應用程式，當它的行為不正確。  
  
> [!NOTE]
>  如果您收到錯誤，但沒有特定的詳細資訊，您應該啟用`includeExceptionDetailInFaults`的屬性[ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)組態項目。 這會指示 WCF 將例外狀況詳細資料傳送至用戶端，可讓您偵測許多常見問題，而不需要更進階的診斷。 如需詳細資訊，請參閱 < [Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md)。  
  
## <a name="diagnostics-features-provided-by-wcf"></a>WCF 提供的診斷功能  
 WCF 會提供下列診斷功能：  
  
-   端對端追蹤可以在不使用偵錯工具的情況下，提供疑難排解應用程式的檢測資料。 WCF 輸出追蹤處理序里程碑，以及錯誤訊息。 這可以包含開啟通道處理站，或是由服務主機傳送與接收訊息。 您可以針對執行中的應用程式啟用追蹤以監視其進度。 如需詳細資訊，請參閱 <<c0> [ 追蹤](../../../../docs/framework/wcf/diagnostics/tracing/index.md)主題。 若要了解您可以使用追蹤來偵錯您的應用程式，請參閱[使用疑難排解您的應用程式追蹤](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)主題。  
  
-   訊息記錄可以讓您檢查訊息在傳輸前後的內容。 如需詳細資訊，請參閱 <<c0> [ 訊息記錄](../../../../docs/framework/wcf/diagnostics/message-logging.md)主題。  
  
-   事件追蹤會在事件記錄中寫入任何主要問題的事件。 然後可以使用事件檢視器檢查任何異常狀況。 如需詳細資訊，請參閱 <<c0> [ 事件記錄](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)主題。  
  
-   透過效能監視器公開的效能計數器，能夠讓您監視應用程式與系統的健康狀態。 如需詳細資訊，請參閱 <<c0> [ 效能計數器](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)主題。  
  
-   <xref:System.ServiceModel.Configuration> 命名空間可以讓您載入組態檔然後設定服務或用戶端端點。 當更新必須部署至許多電腦上時，您可以使用物件模型將對許多應用程式的變更寫入指令碼。 或者，您可以使用[組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)編輯經由 GUI 精靈的組態設定。 如需詳細資訊，請參閱 <<c0> [ 設定您的應用程式](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)主題。  
  
-   WMI 能夠讓您找出正在機器上接聽的服務，以及正在使用中的繫結。 如需詳細資訊，請參閱 <<c0> [ 使用 Windows Management Instrumentation 進行診斷](../../../../docs/framework/wcf/diagnostics/wmi/index.md)主題。  
  
 WCF 也提供許多可讓您更輕鬆地建立、 部署和管理 WCF 應用程式 GUI 和命令列工具。 如需詳細資訊，請參閱 < [Windows Communication Foundation 工具](../../../../docs/framework/wcf/tools.md)。 例如，您可以使用[組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)來建立和編輯 WCF 組態設定，使用精靈，而不直接編輯 XML。 您也可以使用[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)若要檢視、 分組和篩選追蹤訊息，以便您可以診斷、 修復，並確認與 WCF 服務的問題。  
  
## <a name="see-also"></a>另請參閱

- [設定應用程式](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
- [部署服務](../../../../docs/framework/wcf/diagnostics/deploying-services.md)
- [例外狀況參考](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)
- [事件記錄](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [訊息記錄](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [設定編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [ServiceModel 註冊工具](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)
- [追蹤](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [使用 Windows Management Instrumentation 進行診斷](../../../../docs/framework/wcf/diagnostics/wmi/index.md)
- [效能計數器](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
- [Windows Communication Foundation 工具](../../../../docs/framework/wcf/tools.md)
