---
title: "WCF 的事件記錄 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "事件記錄 [WCF]"
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
caps.latest.revision: 22
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 22
---
# WCF 的事件記錄
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 會追蹤 Windows 事件記錄檔中的內部事件。  
  
## 檢視事件記錄檔  
 根據預設會自動啟用事件記錄，且沒有機制可停用它。由 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 所記錄的事件可以使用事件檢視器來檢視。若要啟動這項工具，請依序按一下 \[**開始**\] 和 \[**控制台**\]，然後依序按兩下 \[**系統管理工具**\] 和 \[**事件檢視器**\]。  
  
### 應用程式事件記錄檔  
 \[**應用程式事件記錄檔**\] 包含了大部分由 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 所產生的事件。大部分的項目都指出應用程式的特定功能無法啟動。範例包括：  
  
-   訊息記錄\/追蹤：當追蹤和訊息記錄失敗時，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 會將事件寫入事件記錄檔中。然而，並不是每次追蹤失敗都會觸發事件。為防止事件記錄檔全部填滿追蹤失敗，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 會為此類事件實作 10 分鐘的關閉時間。這表示如果 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 將追蹤失敗寫入事件記錄檔，至少 10 分鐘不會再執行這項操作。  
  
-   共用接聽程式：WCF TCP Port Sharing Service 會在無法啟動時記錄事件。  
  
-   [!INCLUDE[infocard](../../../../../includes/infocard-md.md)]：在服務無法啟動時記錄事件。  
  
-   嚴重和錯誤事件，例如啟動失敗或當機  
  
-   訊息記錄已開啟：在訊息記錄已開啟時記錄事件。這是要通知系統管理員，訊息標頭和本文中可能記錄了機密、應用程式特定的資訊。  
  
-   當設定 `machine.config` 檔案之 `machineSettings` 項目中的 `enableLoggingKnownPII` 屬性時，就會記錄事件。這個屬性會指定是否允許任何在電腦上執行的應用程式記錄已知的個人可識別資訊 \(PII\)。  
  
-   如果 `app.config` 或 `web.config` 檔案中的 `logKnownPii` 屬性設定為 `true`，以便讓特定應用程式開啟 PII 記錄，但是 `machine.config` 檔案之 `machineSettings` 項目中的 `enableLoggingKnownPII` 屬性設定為 `false`，便會記錄事件。此外，如果 `logKnownPii` 和 `enableLoggingKnownPII` 都設定為 `true`，便會記錄事件。如需有關這些組態設定的詳細資訊，請參閱[設定訊息記錄](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)主題的＜安全性＞一節。  
  
### 安全性事件記錄檔  
 「**安全性事件記錄檔**」\(Security Event Log\) 包含由 WCF 記錄的安全性稽核事件。  
  
### 系統事件記錄檔  
 WCF 不會在「**系統事件記錄檔**」\(System Event Log\) 中記錄任何事件。  
  
### 事件記錄檔項目  
 事件的 \[**來源**\] 是產生記錄檔項目的組件名稱。  
  
 事件記錄檔項目的型別是用於指出事件的嚴重性。每個事件必須是單一型別，應用程式會在報告事件時指出。事件檢視器會使用這個型別判斷要在記錄檔的清單檢視中顯示哪個圖示。如需有關事件記錄檔項目的不同事件型別，請參閱 <xref:System.Diagnostics.EventLogEntryType>。  
  
 當您在事件檢視器中檢視事件並按一下 \[詳細資訊\] 時，事件檢視器可能會在網際網路上傳送資訊。如需詳細資訊，請參閱「事件檢視器」的說明。  
  
## 請參閱  
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)   
 [事件一般參考](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)