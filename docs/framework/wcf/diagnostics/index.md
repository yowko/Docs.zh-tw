---
title: 管理與診斷
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d26386a0669c92b1b21559474c8f5f61862e6de7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="administration-and-diagnostics"></a>管理與診斷
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 提供豐富的功能，這些功能可協助您監視應用程式的各生命階段。 例如，您可以使用組態在部署時設定服務與用戶端。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 包含大量的效能計數器，可協助您測量應用程式的效能。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 亦會透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Windows Management Instrumentation (WMI) 提供者，在執行階段公開服務的檢查資料。 當應用程式遭遇失敗或開始發生異常行為時，您可以使用事件日誌檢查是否發生任何顯著的事件。 您也可以使用訊息記錄與追蹤檢查在應用程式中端對端之間發生的事件。 這些功能可以同時協助程式開發人員與 IT 專業人員，在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式發生錯誤行為時進行疑難排解。  
  
> [!NOTE]
>  如果您收到錯誤，而不特定的詳細資訊，您應該啟用`includeExceptionDetailInFaults`屬性[ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)組態項目。 這會指示 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 將例外狀況詳細資訊傳送至用戶端，以便讓您能夠偵測許多常見問題，而不需要更進階的診斷。 如需詳細資訊，請參閱[傳送和接收錯誤](../../../../docs/framework/wcf/sending-and-receiving-faults.md)。  
  
## <a name="diagnostics-features-provided-by-wcf"></a>WCF 提供的診斷功能  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供下列診斷功能：  
  
-   端對端追蹤可以在不使用偵錯工具的情況下，提供疑難排解應用程式的檢測資料。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會輸出處理序里程碑的追蹤以及錯誤訊息。 這可以包含開啟通道處理站，或是由服務主機傳送與接收訊息。 您可以針對執行中的應用程式啟用追蹤以監視其進度。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][追蹤](../../../../docs/framework/wcf/diagnostics/tracing/index.md)主題。 若要了解您可以使用追蹤以偵錯應用程式，請參閱[使用追蹤疑難排解您的應用程式](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)主題。  
  
-   訊息記錄可以讓您檢查訊息在傳輸前後的內容。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][訊息記錄](../../../../docs/framework/wcf/diagnostics/message-logging.md)主題。  
  
-   事件追蹤會在事件記錄中寫入任何主要問題的事件。 然後可以使用事件檢視器檢查任何異常狀況。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][事件記錄](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)主題。  
  
-   透過效能監視器公開的效能計數器，能夠讓您監視應用程式與系統的健康狀態。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][效能計數器](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)主題。  
  
-   <xref:System.ServiceModel.Configuration> 命名空間可以讓您載入組態檔然後設定服務或用戶端端點。 當更新必須部署至許多電腦上時，您可以使用物件模型將對許多應用程式的變更寫入指令碼。 或者，您可以使用[組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)編輯使用 GUI 精靈的組態設定。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][設定您的應用程式](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)主題。  
  
-   WMI 能夠讓您找出正在機器上接聽的服務，以及正在使用中的繫結。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][使用 Windows Management Instrumentation 進行診斷](../../../../docs/framework/wcf/diagnostics/wmi/index.md)主題。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也提供幾種 GUI 與命令列工具，讓您輕鬆建立、部署與管理 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Windows Communication Foundation 工具](../../../../docs/framework/wcf/tools.md)。 例如，您可以使用[組態編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)建立和編輯[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]使用精靈，而不直接編輯 XML 的組態設定。 您也可以使用[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)若要檢視、 分組和篩選追蹤訊息，以便您可以診斷、 修復，並確認問題[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務。  
  
## <a name="see-also"></a>請參閱  
 [設定應用程式](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)  
 [部署服務](../../../../docs/framework/wcf/diagnostics/deploying-services.md)  
 [例外狀況參考](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)  
 [事件記錄](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [訊息記錄](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [設定編輯器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [ServiceModel 註冊工具](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)  
 [追蹤](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [使用 Windows Management Instrumentation 進行診斷](../../../../docs/framework/wcf/diagnostics/wmi/index.md)  
 [效能計數器](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)  
 [Windows Communication Foundation 工具](../../../../docs/framework/wcf/tools.md)
