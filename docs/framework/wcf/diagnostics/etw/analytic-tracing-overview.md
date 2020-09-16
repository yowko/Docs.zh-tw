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
# <a name="analytic-tracing-overview"></a><span data-ttu-id="42727-102">分析追蹤總覽</span><span class="sxs-lookup"><span data-stu-id="42727-102">Analytic tracing overview</span></span>

<span data-ttu-id="42727-103">[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] 中的分析追蹤是一項高效能、低詳細等級的追蹤功能，設定於 Windows 事件追蹤 (ETW) 之上。</span><span class="sxs-lookup"><span data-stu-id="42727-103">Analytic tracing in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] is a high performance and low verbosity tracing feature set on top of Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="42727-104">ETW 是在核心層級執行，可大幅降低追蹤作業的負荷。</span><span class="sxs-lookup"><span data-stu-id="42727-104">ETW runs at the kernel-level to greatly reduce the overhead of tracing operations.</span></span> <span data-ttu-id="42727-105">它能有效率地緩衝使用者和核心模式的事件，並且允許動態啟用記錄，而不需重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="42727-105">It efficiently buffers user- and kernel-mode events, and allows dynamic enabling of logging without requiring service restarts.</span></span> <span data-ttu-id="42727-106">事件發出和接收之後，即可在事件記錄檔中使用追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="42727-106">The tracing data is available in the event logs after it has been emitted and received.</span></span>

<span data-ttu-id="42727-107">如需 ETW 的詳細資訊，請參閱 [使用 Etw 改善偵錯工具和效能微調](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)。</span><span class="sxs-lookup"><span data-stu-id="42727-107">For more information about ETW, see [Improve Debugging and Performance Tuning with ETW](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw).</span></span>

 <span data-ttu-id="42727-108">除了使用 Windows 系統、安全性和應用程式事件記錄檔來分析應用程式之外，Windows Vista 和 Windows Server 2008 也在 [應用程式和服務記錄檔] 最上層節點下引進了額外的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="42727-108">In addition to using the Windows System, Security, and Application event logs to analyze application, Windows Vista and Windows Server 2008 introduced additional logs under the Applications and Services Logs top-level node.</span></span> <span data-ttu-id="42727-109">這些新記錄檔的目的在於儲存特定應用程式或特定元件的事件，而非影響整個系統的全域事件 (例如安全性事件記錄檔可能會記錄的事件類型)。</span><span class="sxs-lookup"><span data-stu-id="42727-109">The purpose of these new logs is to store events for a particular application or specific component instead of global events that have a system-wide impact (such as the type of events that the Security event log might record).</span></span> [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] <span data-ttu-id="42727-110">將 WCF 追蹤事件、WCF 訊息記錄和追蹤記錄的記錄合併並相互關聯 [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] 至應用程式和服務記錄檔。</span><span class="sxs-lookup"><span data-stu-id="42727-110">unifies and correlates the logging of WCF Trace Events, WCF Message Logs, and [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] Tracking records to the Applications and Services Logs.</span></span>

<span data-ttu-id="42727-111">下列各節涵蓋適用于 WCF 分析追蹤的概念和功能。</span><span class="sxs-lookup"><span data-stu-id="42727-111">The following sections cover concepts and capabilities that apply to WCF analytic tracing.</span></span>

## <a name="enable-wcf-diagnostics-settings"></a><span data-ttu-id="42727-112">啟用 WCF 診斷設定</span><span class="sxs-lookup"><span data-stu-id="42727-112">Enable WCF Diagnostics Settings</span></span>

<span data-ttu-id="42727-113">WCF 診斷會在 [設定] 區段內啟用 `<system.serviceModel><diagnostics>` 。</span><span class="sxs-lookup"><span data-stu-id="42727-113">WCF diagnostics are enabled within the `<system.serviceModel><diagnostics>` configuration section.</span></span>

```xml
<system.serviceModel>
  <diagnostics>
```

<span data-ttu-id="42727-114">Web 主控之 IIS 虛擬應用程式的 WCF 診斷設定會在其 *Web.config* 檔案中啟用。</span><span class="sxs-lookup"><span data-stu-id="42727-114">WCF diagnostic settings for a Web-hosted IIS virtual application are enabled in its *Web.config* file.</span></span> <span data-ttu-id="42727-115">另一個選項是在應用程式內的子目錄中建立 *Web.config* 檔案。</span><span class="sxs-lookup"><span data-stu-id="42727-115">Another option is to create a *Web.config* file in a subdirectory within the application.</span></span> <span data-ttu-id="42727-116">此選項會將設定套用至子目錄內的所有服務。</span><span class="sxs-lookup"><span data-stu-id="42727-116">This choice applies the settings to all of the services within a subdirectory.</span></span> <span data-ttu-id="42727-117">為確保針對應用程式內的所有服務，以一致的方式初始化診斷設定，這些設定應該在應用程式目錄的 *Web.config* 檔案中，而不是在應用程式內的其中一個個別子目錄中。</span><span class="sxs-lookup"><span data-stu-id="42727-117">To ensure that the diagnostics settings are initialized consistently for all services within the application, the settings should be within the *Web.config* file in the application directory and not in one of the individual subdirectories within the application.</span></span>

## <a name="channels"></a><span data-ttu-id="42727-118">通道</span><span class="sxs-lookup"><span data-stu-id="42727-118">Channels</span></span>

<span data-ttu-id="42727-119">ETW 允許軟體元件使用通道將追蹤事件導向特定對象。</span><span class="sxs-lookup"><span data-stu-id="42727-119">ETW allows software components to direct tracing events to a particular audience by use of channels.</span></span> <span data-ttu-id="42727-120">例如，您可以將系統管理員的事件傳送給應用程式開發人員在意另一個通道的一個通道和事件。</span><span class="sxs-lookup"><span data-stu-id="42727-120">For example, you can send events for system administrators to one channel and events that application developers care about to another channel.</span></span> <span data-ttu-id="42727-121">通道會命名並向 Windows 註冊，讓取用者可以使用事件檢視器來查看通道的事件。</span><span class="sxs-lookup"><span data-stu-id="42727-121">Channels are named and registered with Windows so that consumers can view a channel's events using Event Viewer.</span></span>

 <span data-ttu-id="42727-122">WCF 的分析追蹤功能 [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] 寫入至 Microsoft-Windows 應用程式-應用程式通道。</span><span class="sxs-lookup"><span data-stu-id="42727-122">The analytic tracing feature for WCF in [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] writes to the Microsoft-Windows-Application-Server-Applications channel.</span></span> <span data-ttu-id="42727-123">此通道是針對想要在生產環境中監視 WCF 服務健康情況的使用者而設計。</span><span class="sxs-lookup"><span data-stu-id="42727-123">This channel is designed for users who want to monitor the health of WCF services in production.</span></span> <span data-ttu-id="42727-124">它會定義一組小型的事件，可用於許多狀況監控和疑難排解案例中。</span><span class="sxs-lookup"><span data-stu-id="42727-124">It defines a small set of events that can be used in many health monitoring and troubleshooting scenarios.</span></span>

 <span data-ttu-id="42727-125">若要啟用 Windows 事件追蹤資訊清單，以便在事件記錄檔中正確解碼訊息，請依照下列方式，在命令列上使用 ServiceModelReg 工具：</span><span class="sxs-lookup"><span data-stu-id="42727-125">To enable the Event Tracing for Windows manifest so that messages are decoded properly in the event log, use the ServiceModelReg tool on the command line as follows:</span></span>

 `ServiceModelReg.exe -i -c:etw`

## <a name="dynamic-configuration"></a><span data-ttu-id="42727-126">動態組態</span><span class="sxs-lookup"><span data-stu-id="42727-126">Dynamic Configuration</span></span>

<span data-ttu-id="42727-127">ETW 基礎結構可讓您使用標準 Windows 工具，以動態方式啟用和設定追蹤。</span><span class="sxs-lookup"><span data-stu-id="42727-127">The ETW infrastructure allows tracing to be enabled and configured dynamically using standard Windows tools.</span></span> <span data-ttu-id="42727-128">如需詳細資訊，請參閱 [動態啟用分析追蹤](dynamically-enabling-analytic-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="42727-128">For more information, see [Dynamically Enabling Analytic Tracing](dynamically-enabling-analytic-tracing.md).</span></span>

## <a name="message-flow-tracing"></a><span data-ttu-id="42727-129">訊息流程追蹤</span><span class="sxs-lookup"><span data-stu-id="42727-129">Message Flow Tracing</span></span>

<span data-ttu-id="42727-130">如需如何啟用訊息流程追蹤的詳細資訊，請參閱設定 [訊息流程追蹤](configuring-message-flow-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="42727-130">For more information about how to enable message flow tracing, see [Configuring Message Flow Tracing](configuring-message-flow-tracing.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="42727-131">關鍵字</span><span class="sxs-lookup"><span data-stu-id="42727-131">Keywords</span></span>

<span data-ttu-id="42727-132">關鍵字用來篩選追蹤訊息，以及定義 .NET Framework 發出事件的元件。</span><span class="sxs-lookup"><span data-stu-id="42727-132">Keywords are used to filter trace messages and define which component of the .NET Framework emitted the event.</span></span> <span data-ttu-id="42727-133">如需詳細資訊，請參閱 [動態啟用分析追蹤](dynamically-enabling-analytic-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="42727-133">For more information, see [Dynamically Enabling Analytic Tracing](dynamically-enabling-analytic-tracing.md).</span></span>
