---
title: 分析追蹤的概觀
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: b519156faba68c769f4c1380a11706aebaab7e7c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559053"
---
# <a name="analytic-tracing-overview"></a>分析追蹤總覽

[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] 中的分析追蹤是一項高效能、低詳細等級的追蹤功能，設定於 Windows 事件追蹤 (ETW) 之上。 ETW 是在核心層級執行，可大幅降低追蹤作業的負荷。 它能有效率地緩衝使用者和核心模式的事件，並且允許動態啟用記錄，而不需重新啟動服務。 事件發出和接收之後，即可在事件記錄檔中使用追蹤資料。

如需 ETW 的詳細資訊，請參閱 [使用 Etw 改善偵錯工具和效能微調](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)。

 除了使用 Windows 系統、安全性和應用程式事件記錄檔來分析應用程式之外，Windows Vista 和 Windows Server 2008 也在 [應用程式和服務記錄檔] 最上層節點下引進了額外的記錄檔。 這些新記錄檔的目的在於儲存特定應用程式或特定元件的事件，而非影響整個系統的全域事件 (例如安全性事件記錄檔可能會記錄的事件類型)。 [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] 將 WCF 追蹤事件、WCF 訊息記錄和追蹤記錄的記錄合併並相互關聯 [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] 至應用程式和服務記錄檔。

下列各節涵蓋適用于 WCF 分析追蹤的概念和功能。

## <a name="enable-wcf-diagnostics-settings"></a>啟用 WCF 診斷設定

WCF 診斷會在 [設定] 區段內啟用 `<system.serviceModel><diagnostics>` 。

```xml
<system.serviceModel>
  <diagnostics>
```

Web 主控之 IIS 虛擬應用程式的 WCF 診斷設定會在其 *Web.config* 檔案中啟用。 另一個選項是在應用程式內的子目錄中建立 *Web.config* 檔案。 此選項會將設定套用至子目錄內的所有服務。 為確保針對應用程式內的所有服務，以一致的方式初始化診斷設定，這些設定應該在應用程式目錄的 *Web.config* 檔案中，而不是在應用程式內的其中一個個別子目錄中。

## <a name="channels"></a>通道

ETW 允許軟體元件使用通道將追蹤事件導向特定對象。 例如，您可以將系統管理員的事件傳送給應用程式開發人員在意另一個通道的一個通道和事件。 通道會命名並向 Windows 註冊，讓取用者可以使用事件檢視器來查看通道的事件。

 WCF 的分析追蹤功能 [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] 寫入至 Microsoft-Windows 應用程式-應用程式通道。 此通道是針對想要在生產環境中監視 WCF 服務健康情況的使用者而設計。 它會定義一組小型的事件，可用於許多狀況監控和疑難排解案例中。

 若要啟用 Windows 事件追蹤資訊清單，以便在事件記錄檔中正確解碼訊息，請依照下列方式，在命令列上使用 ServiceModelReg 工具：

 `ServiceModelReg.exe -i -c:etw`

## <a name="dynamic-configuration"></a>動態組態

ETW 基礎結構可讓您使用標準 Windows 工具，以動態方式啟用和設定追蹤。 如需詳細資訊，請參閱 [動態啟用分析追蹤](dynamically-enabling-analytic-tracing.md)。

## <a name="message-flow-tracing"></a>訊息流程追蹤

如需如何啟用訊息流程追蹤的詳細資訊，請參閱設定 [訊息流程追蹤](configuring-message-flow-tracing.md)。

## <a name="keywords"></a>關鍵字

關鍵字用來篩選追蹤訊息，以及定義 .NET Framework 發出事件的元件。 如需詳細資訊，請參閱 [動態啟用分析追蹤](dynamically-enabling-analytic-tracing.md)。
