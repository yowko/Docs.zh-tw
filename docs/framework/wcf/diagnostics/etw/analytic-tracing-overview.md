---
title: 分析追蹤的概觀
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: 6170accc01e837bba0afb446f67a6c6272e7dde7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798210"
---
# <a name="analytic-tracing-overview"></a>分析追蹤的概觀
[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] 中的分析追蹤是一項高效能、低詳細等級的追蹤功能，設定於 Windows 事件追蹤 (ETW) 之上。 ETW 是在核心層級執行，可大幅降低追蹤作業的負荷。 它能有效率地緩衝使用者和核心模式的事件，並且允許動態啟用記錄，而不需重新啟動服務。 事件發出和接收之後，即可在事件記錄檔中使用追蹤資料。  
  
 如需 ETW 的詳細資訊，請參閱[使用 Etw 改善偵錯工具和效能微調](https://go.microsoft.com/fwlink/?LinkId=164781)。  
  
 除了使用 Windows 系統、安全性和應用程式事件記錄檔分析應用程式之外， [!INCLUDE[wv](../../../../../includes/wv-md.md)] 和 [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] 也在應用程式和服務記錄檔最上層節點下引進了額外的記錄檔。 這些新記錄檔的目的在於儲存特定應用程式或特定元件的事件，而非影響整個系統的全域事件 (例如安全性事件記錄檔可能會記錄的事件類型)。 [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]將 wcf 追蹤事件、wcf 訊息記錄和[!INCLUDE[wf1](../../../../../includes/wf1-md.md)]追蹤記錄的記錄，統一併相互關聯至應用程式和服務記錄檔。  
  
## <a name="concepts-and-capabilities"></a>概念和功能  
 下列概念和功能適用于 WCF 分析追蹤。  
  
### <a name="enabling-wcf-diagnostics-settings"></a>啟用 WCF 診斷設定  
 \<系統會在 system.servicemodel >\<diagnostics > 設定 區段內啟用 WCF 診斷。  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 Web 裝載 IIS 虛擬應用程式的 WCF 診斷設定是在本身的 Web.config 檔案中啟用。 另一個選擇是在應用程式內的子目錄中建立 Web.config。  這個選擇會將設定套用至子目錄內的所有服務。  為確保針對應用程式內的所有服務一致初始化診斷設定，這些設定應該在應用程式目錄的 Web.config 內，而不是在應用程式內的其中一個個別子目錄中。  
  
### <a name="channels"></a>通道  
 ETW 允許軟體元件使用通道將追蹤事件導向特定對象。 例如，您可以將系統管理員的事件傳送至一個通道，以及將應用程式開發人員重視的事件傳送至另一個通道。 通道會加以命名並且註冊至 Windows，如此消費者就可以使用事件檢視器檢視通道的事件。  
  
 WCF 在中[!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]的分析追蹤功能會寫入至 Microsoft Windows 應用程式-應用程式通道。 此通道專為想要監視生產環境中 WCF 服務健全狀況的使用者而設計。 它會定義一個小型事件集，可在許多健康狀況監控和疑難排解的情況中使用。  
  
 若要啟用 Windows 事件追蹤資訊清單，以便在事件記錄檔中正確解碼訊息，請依照下列方式，在命令列上使用 ServiceModelReg 工具：  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>動態組態  
 ETW 基礎結構可讓您使用標準 Windows 工具，以動態方式啟用和設定追蹤。 如需詳細資訊，請參閱[動態啟用分析追蹤](dynamically-enabling-analytic-tracing.md)。  
  
### <a name="message-flow-tracing"></a>訊息流程追蹤  
 如需如何啟用訊息流程追蹤的詳細資訊，請參閱設定[訊息流程追蹤](configuring-message-flow-tracing.md)。  
  
### <a name="keywords"></a>關鍵字  
 關鍵字是用來篩選追蹤訊息，並定義 .NET Framework 發出事件的元件。 如需詳細資訊，請參閱[動態啟用分析追蹤](dynamically-enabling-analytic-tracing.md)。
