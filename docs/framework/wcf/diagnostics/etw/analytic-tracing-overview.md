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
# <a name="analytic-tracing-overview"></a><span data-ttu-id="0a6a3-102">分析追蹤的概觀</span><span class="sxs-lookup"><span data-stu-id="0a6a3-102">Analytic Tracing Overview</span></span>
<span data-ttu-id="0a6a3-103">[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] 中的分析追蹤是一項高效能、低詳細等級的追蹤功能，設定於 Windows 事件追蹤 (ETW) 之上。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-103">Analytic tracing in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] is a high performance and low verbosity tracing feature set on top of Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="0a6a3-104">ETW 是在核心層級執行，可大幅降低追蹤作業的負荷。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-104">ETW runs at the kernel-level to greatly reduce the overhead of tracing operations.</span></span> <span data-ttu-id="0a6a3-105">它能有效率地緩衝使用者和核心模式的事件，並且允許動態啟用記錄，而不需重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-105">It efficiently buffers user- and kernel-mode events, and allows dynamic enabling of logging without requiring service restarts.</span></span> <span data-ttu-id="0a6a3-106">事件發出和接收之後，即可在事件記錄檔中使用追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-106">The tracing data is available in the event logs after it has been emitted and received.</span></span>  
  
 <span data-ttu-id="0a6a3-107">如需 ETW 的詳細資訊，請參閱[使用 Etw 改善偵錯工具和效能微調](https://go.microsoft.com/fwlink/?LinkId=164781)。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-107">For more information about ETW, see [Improve Debugging and Performance Tuning with ETW](https://go.microsoft.com/fwlink/?LinkId=164781).</span></span>  
  
 <span data-ttu-id="0a6a3-108">除了使用 Windows 系統、安全性和應用程式事件記錄檔分析應用程式之外， [!INCLUDE[wv](../../../../../includes/wv-md.md)] 和 [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] 也在應用程式和服務記錄檔最上層節點下引進了額外的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-108">In addition to using the Windows System, Security, and Application event logs to analyze application, [!INCLUDE[wv](../../../../../includes/wv-md.md)] and [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] introduced additional logs under the Applications and Services Logs top-level node.</span></span> <span data-ttu-id="0a6a3-109">這些新記錄檔的目的在於儲存特定應用程式或特定元件的事件，而非影響整個系統的全域事件 (例如安全性事件記錄檔可能會記錄的事件類型)。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-109">The purpose of these new logs is to store events for a particular application or specific component instead of global events that have a system-wide impact (such as the type of events that the Security event log might record).</span></span> [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]<span data-ttu-id="0a6a3-110">將 wcf 追蹤事件、wcf 訊息記錄和[!INCLUDE[wf1](../../../../../includes/wf1-md.md)]追蹤記錄的記錄，統一併相互關聯至應用程式和服務記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-110">unifies and correlates the logging of WCF Trace Events, WCF Message Logs, and [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] Tracking records to the Applications and Services Logs.</span></span>  
  
## <a name="concepts-and-capabilities"></a><span data-ttu-id="0a6a3-111">概念和功能</span><span class="sxs-lookup"><span data-stu-id="0a6a3-111">Concepts and Capabilities</span></span>  
 <span data-ttu-id="0a6a3-112">下列概念和功能適用于 WCF 分析追蹤。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-112">The following concepts and capabilities apply to WCF Analytic Tracing.</span></span>  
  
### <a name="enabling-wcf-diagnostics-settings"></a><span data-ttu-id="0a6a3-113">啟用 WCF 診斷設定</span><span class="sxs-lookup"><span data-stu-id="0a6a3-113">Enabling WCF Diagnostics Settings</span></span>  
 <span data-ttu-id="0a6a3-114">\<系統會在 system.servicemodel >\<diagnostics > 設定 區段內啟用 WCF 診斷。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-114">WCF diagnostics are enabled within the \<system.serviceModel>\<diagnostics> configuration section.</span></span>  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 <span data-ttu-id="0a6a3-115">Web 裝載 IIS 虛擬應用程式的 WCF 診斷設定是在本身的 Web.config 檔案中啟用。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-115">WCF diagnostic settings for a Web-hosted IIS virtual application are enabled in its’ Web.config file.</span></span> <span data-ttu-id="0a6a3-116">另一個選擇是在應用程式內的子目錄中建立 Web.config。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-116">Another option is to create a Web.config in a sub-directory within the application.</span></span>  <span data-ttu-id="0a6a3-117">這個選擇會將設定套用至子目錄內的所有服務。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-117">This choice applies the settings to all of the services within a sub-directory.</span></span>  <span data-ttu-id="0a6a3-118">為確保針對應用程式內的所有服務一致初始化診斷設定，這些設定應該在應用程式目錄的 Web.config 內，而不是在應用程式內的其中一個個別子目錄中。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-118">To ensure that the diagnostics settings are initialized consistently for all services within the application, the settings should be within the Web.config in the application directory and not in one of the individual sub-directories within the application.</span></span>  
  
### <a name="channels"></a><span data-ttu-id="0a6a3-119">通道</span><span class="sxs-lookup"><span data-stu-id="0a6a3-119">Channels</span></span>  
 <span data-ttu-id="0a6a3-120">ETW 允許軟體元件使用通道將追蹤事件導向特定對象。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-120">ETW allows software components to direct tracing events to a particular audience by use of channels.</span></span> <span data-ttu-id="0a6a3-121">例如，您可以將系統管理員的事件傳送至一個通道，以及將應用程式開發人員重視的事件傳送至另一個通道。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-121">For example, you can send events for system administrators to one channel, and events that application developers care about to another channel.</span></span> <span data-ttu-id="0a6a3-122">通道會加以命名並且註冊至 Windows，如此消費者就可以使用事件檢視器檢視通道的事件。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-122">Channels are named and registered with Windows so that consumers can view a channel’s events using the Event Viewer.</span></span>  
  
 <span data-ttu-id="0a6a3-123">WCF 在中[!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]的分析追蹤功能會寫入至 Microsoft Windows 應用程式-應用程式通道。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-123">The analytic tracing feature for WCF in [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] writes to the Microsoft-Windows-Application-Server-Applications channel.</span></span> <span data-ttu-id="0a6a3-124">此通道專為想要監視生產環境中 WCF 服務健全狀況的使用者而設計。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-124">This channel is specifically designed for users who want to monitor the health of WCF services in production.</span></span> <span data-ttu-id="0a6a3-125">它會定義一個小型事件集，可在許多健康狀況監控和疑難排解的情況中使用。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-125">It defines a small, set of events that can be used in many health monitoring and troubleshooting scenarios.</span></span>  
  
 <span data-ttu-id="0a6a3-126">若要啟用 Windows 事件追蹤資訊清單，以便在事件記錄檔中正確解碼訊息，請依照下列方式，在命令列上使用 ServiceModelReg 工具：</span><span class="sxs-lookup"><span data-stu-id="0a6a3-126">To enable the Event Tracing for Windows manifest so that messages are decoded properly in the event log, use the ServiceModelReg tool on the command line as follows:</span></span>  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a><span data-ttu-id="0a6a3-127">動態組態</span><span class="sxs-lookup"><span data-stu-id="0a6a3-127">Dynamic Configuration</span></span>  
 <span data-ttu-id="0a6a3-128">ETW 基礎結構可讓您使用標準 Windows 工具，以動態方式啟用和設定追蹤。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-128">The ETW infrastructure allows tracing to be enabled and configured dynamically using standard Windows tools.</span></span> <span data-ttu-id="0a6a3-129">如需詳細資訊，請參閱[動態啟用分析追蹤](dynamically-enabling-analytic-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-129">For more information, see [Dynamically Enabling Analytic Tracing](dynamically-enabling-analytic-tracing.md).</span></span>  
  
### <a name="message-flow-tracing"></a><span data-ttu-id="0a6a3-130">訊息流程追蹤</span><span class="sxs-lookup"><span data-stu-id="0a6a3-130">Message Flow Tracing</span></span>  
 <span data-ttu-id="0a6a3-131">如需如何啟用訊息流程追蹤的詳細資訊，請參閱設定[訊息流程追蹤](configuring-message-flow-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-131">For more information about how to enable message flow tracing, see [Configuring Message Flow Tracing](configuring-message-flow-tracing.md).</span></span>  
  
### <a name="keywords"></a><span data-ttu-id="0a6a3-132">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0a6a3-132">Keywords</span></span>  
 <span data-ttu-id="0a6a3-133">關鍵字是用來篩選追蹤訊息，並定義 .NET Framework 發出事件的元件。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-133">Keywords are used to filter trace messages and define which component of the .NET Framework emitted the event.</span></span> <span data-ttu-id="0a6a3-134">如需詳細資訊，請參閱[動態啟用分析追蹤](dynamically-enabling-analytic-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="0a6a3-134">For more information, see [Dynamically Enabling Analytic Tracing](dynamically-enabling-analytic-tracing.md).</span></span>
