---
title: WCF 的事件記錄
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: 2dd4f82e8a100074850b21d298e91dc5dc15c59d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175275"
---
# <a name="event-logging-in-wcf"></a>WCF 的事件記錄
Windows Communication Foundation (WCF) 追蹤 Windows 事件記錄檔中的內部事件。  
  
## <a name="viewing-event-logs"></a>檢視事件記錄檔  
 根據預設會自動啟用事件記錄，且沒有機制可停用它。 可以使用 事件檢視器來檢視由 WCF 所記錄的事件。 若要啟動此工具，請按一下**開始**，按一下**控制台**，按兩下**系統管理工具**，然後按兩下**事件檢視器**.  
  
### <a name="application-event-log"></a>應用程式事件記錄檔  
 **應用程式事件記錄檔**包含大部分的 WCF 所產生的事件。 大部分的項目都指出應用程式的特定功能無法啟動。 範例包括：  
  
-   訊息記錄/追蹤：追蹤和訊息記錄失敗時，WCF 會將事件寫入事件記錄檔。 然而，並不是每次追蹤失敗都會觸發事件。 若要避免事件記錄檔全部填滿追蹤失敗，WCF 會實作 10 分鐘的停機期間，這類事件。 這表示，如果 WCF 追蹤失敗寫入事件記錄檔時，都不會同樣至少 10 分鐘的時間。  
  
-   共用接聽項：WCF TCP Port Sharing Service 會記錄事件時無法啟動。  
  
-   [!INCLUDE[infocard](../../../../../includes/infocard-md.md)]：當服務無法啟動的事件記錄。  
  
-   嚴重和錯誤事件，例如啟動失敗或當機  
  
-   開啟訊息記錄：開啟訊息記錄時的事件記錄。 這是要通知系統管理員，訊息標頭和本文中可能記錄了機密、應用程式特定的資訊。  
  
-   當設定 `enableLoggingKnownPII` 檔案之 `machineSettings` 項目中的 `machine.config` 屬性時，就會記錄事件。 這個屬性會指定是否允許任何在電腦上執行的應用程式記錄已知的個人可識別資訊 (PII)。  
  
-   如果 `logKnownPii` 或 `app.config` 檔案中的 `web.config` 屬性設定為 `true`，以便讓特定應用程式開啟 PII 記錄，但是 `enableLoggingKnownPII` 檔案之 `machineSettings` 項目中的 `machine.config` 屬性設定為 `false`，便會記錄事件。 此外，如果 `logKnownPii` 和 `enableLoggingKnownPII` 都設定為 `true`，便會記錄事件。 如需有關這些組態設定的詳細資訊，請參閱下的 [安全性] 區段[設定訊息記錄](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)主題。  
  
### <a name="security-event-log"></a>安全性事件記錄檔  
 **安全性事件記錄檔**包含由 WCF 記錄的安全性稽核事件。  
  
### <a name="system-event-log"></a>系統事件記錄檔  
 WCF 不會記錄任何項目**系統事件記錄檔**。  
  
### <a name="event-log-entries"></a>事件記錄檔項目  
 **來源**事件是產生記錄項目之組件的名稱。  
  
 事件記錄檔項目的型別是用於指出事件的嚴重性。 每個事件必須是單一型別，應用程式會在報告事件時指出。 事件檢視器會使用這個型別判斷要在記錄檔的清單檢視中顯示哪個圖示。 如需有關事件記錄檔項目的不同事件型別，請參閱 <xref:System.Diagnostics.EventLogEntryType>。  
  
 當您按一下 [詳細資訊] 時在事件檢視器中檢視事件，事件檢視器可能會透過網際網路傳送資訊。 如需詳細資訊，請參閱「事件檢視器」的說明。  
  
## <a name="see-also"></a>另請參閱

- [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
- [事件一般參考](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
