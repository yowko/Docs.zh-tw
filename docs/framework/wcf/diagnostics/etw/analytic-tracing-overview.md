---
title: "分析追蹤的概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dd456401073d8c7f3c7bc9fbfbe5c11dbbd4e58
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="analytic-tracing-overview"></a><span data-ttu-id="eb61a-102">分析追蹤的概觀</span><span class="sxs-lookup"><span data-stu-id="eb61a-102">Analytic Tracing Overview</span></span>
<span data-ttu-id="eb61a-103">[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] 中的分析追蹤是一項高效能、低詳細等級的追蹤功能，設定於 Windows 事件追蹤 (ETW) 之上。</span><span class="sxs-lookup"><span data-stu-id="eb61a-103">Analytic tracing in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] is a high performance and low verbosity tracing feature set on top of Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="eb61a-104">ETW 是在核心層級執行，可大幅降低追蹤作業的負荷。</span><span class="sxs-lookup"><span data-stu-id="eb61a-104">ETW runs at the kernel-level to greatly reduce the overhead of tracing operations.</span></span> <span data-ttu-id="eb61a-105">它能有效率地緩衝使用者和核心模式的事件，並且允許動態啟用記錄，而不需重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="eb61a-105">It efficiently buffers user- and kernel-mode events, and allows dynamic enabling of logging without requiring service restarts.</span></span> <span data-ttu-id="eb61a-106">事件發出和接收之後，即可在事件記錄檔中使用追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="eb61a-106">The tracing data is available in the event logs after it has been emitted and received.</span></span>  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="eb61a-107"> ETW 的詳細資訊，請參閱 [使用 ETW 改善偵錯和效能調整](http://go.microsoft.com/fwlink/?LinkId=164781)。</span><span class="sxs-lookup"><span data-stu-id="eb61a-107"> ETW, see [Improve Debugging and Performance Tuning with ETW](http://go.microsoft.com/fwlink/?LinkId=164781).</span></span>  
  
 <span data-ttu-id="eb61a-108">除了使用 Windows 系統、安全性和應用程式事件記錄檔分析應用程式之外， [!INCLUDE[wv](../../../../../includes/wv-md.md)] 和 [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] 也在應用程式和服務記錄檔最上層節點下引進了額外的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="eb61a-108">In addition to using the Windows System, Security, and Application event logs to analyze application, [!INCLUDE[wv](../../../../../includes/wv-md.md)] and [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] introduced additional logs under the Applications and Services Logs top-level node.</span></span> <span data-ttu-id="eb61a-109">這些新記錄檔的目的在於儲存特定應用程式或特定元件的事件，而非影響整個系統的全域事件 (例如安全性事件記錄檔可能會記錄的事件類型)。</span><span class="sxs-lookup"><span data-stu-id="eb61a-109">The purpose of these new logs is to store events for a particular application or specific component instead of global events that have a system-wide impact (such as the type of events that the Security event log might record).</span></span> [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]<span data-ttu-id="eb61a-110"> 會統合並相互關聯以下項目的記錄檔： [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 追蹤事件、 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 訊息記錄和 [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] 應用程式和服務記錄檔的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="eb61a-110"> unifies and correlates the logging of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Trace Events, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Message Logs, and [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] Tracking records to the Applications and Services Logs.</span></span>  
  
## <a name="concepts-and-capabilities"></a><span data-ttu-id="eb61a-111">概念和功能</span><span class="sxs-lookup"><span data-stu-id="eb61a-111">Concepts and Capabilities</span></span>  
 <span data-ttu-id="eb61a-112">下列概念和功能適用於 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 分析追蹤。</span><span class="sxs-lookup"><span data-stu-id="eb61a-112">The following concepts and capabilities apply to [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Analytic Tracing.</span></span>  
  
### <a name="enabling-wcf-diagnostics-settings"></a><span data-ttu-id="eb61a-113">啟用 WCF 診斷設定</span><span class="sxs-lookup"><span data-stu-id="eb61a-113">Enabling WCF Diagnostics Settings</span></span>  
 <span data-ttu-id="eb61a-114">在中啟用 WCF 診斷\<system.serviceModel >\<診斷 > 組態區段。</span><span class="sxs-lookup"><span data-stu-id="eb61a-114">WCF diagnostics are enabled within the \<system.serviceModel>\<diagnostics> configuration section.</span></span>  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 <span data-ttu-id="eb61a-115">Web 裝載 IIS 虛擬應用程式的 WCF 診斷設定是在本身的 Web.config 檔案中啟用。</span><span class="sxs-lookup"><span data-stu-id="eb61a-115">WCF diagnostic settings for a Web-hosted IIS virtual application are enabled in its’ Web.config file.</span></span> <span data-ttu-id="eb61a-116">另一個選擇是在應用程式內的子目錄中建立 Web.config。</span><span class="sxs-lookup"><span data-stu-id="eb61a-116">Another option is to create a Web.config in a sub-directory within the application.</span></span>  <span data-ttu-id="eb61a-117">這個選擇會將設定套用至子目錄內的所有服務。</span><span class="sxs-lookup"><span data-stu-id="eb61a-117">This choice applies the settings to all of the services within a sub-directory.</span></span>  <span data-ttu-id="eb61a-118">為確保針對應用程式內的所有服務一致初始化診斷設定，這些設定應該在應用程式目錄的 Web.config 內，而不是在應用程式內的其中一個個別子目錄中。</span><span class="sxs-lookup"><span data-stu-id="eb61a-118">To ensure that the diagnostics settings are initialized consistently for all services within the application, the settings should be within the Web.config in the application directory and not in one of the individual sub-directories within the application.</span></span>  
  
### <a name="channels"></a><span data-ttu-id="eb61a-119">通道</span><span class="sxs-lookup"><span data-stu-id="eb61a-119">Channels</span></span>  
 <span data-ttu-id="eb61a-120">ETW 允許軟體元件使用通道將追蹤事件導向特定對象。</span><span class="sxs-lookup"><span data-stu-id="eb61a-120">ETW allows software components to direct tracing events to a particular audience by use of channels.</span></span> <span data-ttu-id="eb61a-121">例如，您可以將系統管理員的事件傳送至一個通道，以及將應用程式開發人員重視的事件傳送至另一個通道。</span><span class="sxs-lookup"><span data-stu-id="eb61a-121">For example, you can send events for system administrators to one channel, and events that application developers care about to another channel.</span></span> <span data-ttu-id="eb61a-122">通道會加以命名並且註冊至 Windows，如此消費者就可以使用事件檢視器檢視通道的事件。</span><span class="sxs-lookup"><span data-stu-id="eb61a-122">Channels are named and registered with Windows so that consumers can view a channel’s events using the Event Viewer.</span></span>  
  
 <span data-ttu-id="eb61a-123">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 中 [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] 的分析追蹤功能會寫入 Microsoft-Windows-Application-Server-Applications 通道。</span><span class="sxs-lookup"><span data-stu-id="eb61a-123">The analytic tracing feature for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] in [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] writes to the Microsoft-Windows-Application-Server-Applications channel.</span></span> <span data-ttu-id="eb61a-124">此通道是專為想要在實際執行時監控 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務健康狀況的使用者所設計。</span><span class="sxs-lookup"><span data-stu-id="eb61a-124">This channel is specifically designed for users who want to monitor the health of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services in production.</span></span> <span data-ttu-id="eb61a-125">它會定義一個小型事件集，可在許多健康狀況監控和疑難排解的情況中使用。</span><span class="sxs-lookup"><span data-stu-id="eb61a-125">It defines a small, set of events that can be used in many health monitoring and troubleshooting scenarios.</span></span>  
  
 <span data-ttu-id="eb61a-126">若要啟用 Windows 事件追蹤資訊清單，以便在事件記錄檔中正確解碼訊息，請依照下列方式，在命令列上使用 ServiceModelReg 工具：</span><span class="sxs-lookup"><span data-stu-id="eb61a-126">To enable the Event Tracing for Windows manifest so that messages are decoded properly in the event log, use the ServiceModelReg tool on the command line as follows:</span></span>  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a><span data-ttu-id="eb61a-127">動態組態</span><span class="sxs-lookup"><span data-stu-id="eb61a-127">Dynamic Configuration</span></span>  
 <span data-ttu-id="eb61a-128">ETW 基礎結構可讓您使用標準 Windows 工具，以動態方式啟用和設定追蹤。</span><span class="sxs-lookup"><span data-stu-id="eb61a-128">The ETW infrastructure allows tracing to be enabled and configured dynamically using standard Windows tools.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="eb61a-129"> [Dynamically Enabling Analytic Tracing](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="eb61a-129"> [Dynamically Enabling Analytic Tracing](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).</span></span>  
  
### <a name="message-flow-tracing"></a><span data-ttu-id="eb61a-130">訊息流程追蹤</span><span class="sxs-lookup"><span data-stu-id="eb61a-130">Message Flow Tracing</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="eb61a-131"> 如何啟用訊息流程追蹤的詳細資訊，請參閱 [Configuring Message Flow Tracing](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="eb61a-131"> how to enable message flow tracing, see [Configuring Message Flow Tracing](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md).</span></span>  
  
### <a name="keywords"></a><span data-ttu-id="eb61a-132">關鍵字</span><span class="sxs-lookup"><span data-stu-id="eb61a-132">Keywords</span></span>  
 <span data-ttu-id="eb61a-133">關鍵字可用來篩選追蹤訊息，以及定義發出事件的 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="eb61a-133">Keywords are used to filter trace messages and define which component of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] emitted the event.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="eb61a-134"> [Dynamically Enabling Analytic Tracing](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="eb61a-134"> [Dynamically Enabling Analytic Tracing](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).</span></span>
