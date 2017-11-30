---
title: "恢復功能和 microservices 的高可用性"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |恢復功能和 microservices 的高可用性"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 149e28ac7bd7383e4e960ed8a226943e2b9bdaa1
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="resiliency-and-high-availability-in-microservices"></a>恢復功能和 microservices 的高可用性

處理未預期的錯誤是其中一個最困難的問題，若要解決，尤其是在分散式系統。 大部分的開發人員撰寫的程式碼牽涉到例外狀況處理、 和，這也在測試所花費最多時間。 問題會比撰寫程式碼以處理失敗更為複雜。 微服務執行所在的電腦失敗時，會發生什麼事？ 不只需要偵測此微服務失敗 （本身困難的問題），但您也需要某個動作，重新啟動您的微服務。

微服務需要處理失敗的彈性，並要能重新啟動通常可用性的另一部電腦上。 此復原也都是在向下微服務可以復原此狀態，以及是否可以成功地重新啟動的微服務微服務，代表儲存的狀態。 換句話說，需要具備中 （在任何時間，可以重新啟動處理程序） 的計算能力的恢復功能以及更有恢復狀態或資料 （無資料遺失和資料則維持一致）。

恢復功能的問題是複合性的其他案例，例如當應用程式在升級期間發生失敗期間。 微服務，使用與部署系統，您必須判斷是否可以繼續向前移到較新版本，或改為復原回先前的版本，以維護一致的狀態。 是否有可向前移動的保留足夠的電腦以及如何復原先前版本的微服務的問題需要考量。 這需要發出健康情況資訊，以便在整體的應用程式與 orchestrator 進行這些決定微服務。

此外，相關恢復功能如何以雲端為基礎的系統必須行為。 如前所述，以雲端為基礎的系統也必須不怕失敗，並必須嘗試自動修復它們。 比方說，在網路或容器失敗，用戶端應用程式或用戶端服務必須重試傳送訊息，或重試要求，因為在許多情況下，在雲端中的失敗是部分的策略。 [實作具有恢復功能的應用程式](#implementing_resilient_apps)> 一節中本指南說明如何處理部分失敗。 它說明使用類似的程式庫的技術，如使用指數型輪詢或.NET 核心中的斷路器模式的重試[Polly](https://github.com/App-vNext/Polly)，其中提供各種處理這個主體的原則。

## <a name="health-management-and-diagnostics-in-microservices"></a>健康情況管理和診斷 microservices 中

很明顯，常被忽略，而微服務必須在其健康情況及診斷報告。 否則，會從作業觀點來看很少深入解析。 一組獨立的服務之間的關聯的診斷事件和處理電腦時鐘偏差的事件順序的意義是一項挑戰。 互動的微服務透過同意通訊協定和資料格式的相同方式，就需要來記錄健全狀況和最終都會進行查詢和檢視事件存放區中的診斷事件的方式標準化。 在 microservices 方法中，它是索引鍵不同小組同意在單一記錄格式。 需要一致的方法來檢視應用程式中的診斷事件。

### <a name="health-checks"></a>健康情況檢查

健全狀況是不同的診斷。 健全狀況是關於報告其目前的狀態，以採取適當的動作微服務。 使用良好的範例，當做維護可用性的升級與部署機制。 雖然服務目前可能處於狀況不良的狀態，因為處理序當機或電腦重新開機，服務可能依然可運作。 最後您需要為這個較差執行升級。 最好的方法是先進行調查或允許提供時間讓復原微服務。 從微服務的健全狀況事件，幫助我們做出明智的決策和作用中，幫助您建立自我修復服務。

中實作健康情況檢查在 ASP.NET Core services 區段的本指南中，我們將說明如何使用新的 ASP.NET HealthChecks 文件庫中您 microservices，好讓它們可以報告其狀態至監視的服務，以採取適當的動作。

### <a name="using-diagnostics-and-logs-event-streams"></a>使用診斷和記錄檔的事件資料流

記錄檔會提供如何應用程式或服務正在執行，包括例外狀況、 警告和簡單的參考用訊息的相關資訊。 通常，每個記錄檔為文字格式，其中每個事件，一行雖然例外狀況通常也會顯示堆疊追蹤跨多行。

整合伺服器型應用程式中，可以只是將記錄寫入磁碟 （記錄檔） 上的檔案，並使用任何工具分析。 因為應用程式執行時限制為固定的伺服器或 VM，通常不太複雜，無法分析的事件流程。 不過，在 orchestrator 叢集中許多節點之間執行多個服務的分散式應用程式，能夠將分散式的事件相互關聯是一項挑戰。

微服務為基礎的應用程式應該不會嘗試儲存記錄檔或事件的輸出資料流本身，並管理路由至中央位置的事件甚至不能再一次。 它應該是透明的這表示每個處理序，應該只要撰寫其事件資料流至標準輸出的下方將會收集執行環境的基礎結構會由其執行位置。 舉例來說，這些事件資料流路由器是[Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow)，其中多個來源收集事件資料流，並將其輸出系統發佈。 這些可以包括簡單的標準輸出的開發環境，或是想要的雲端系統[Application Insights](https://azure.microsoft.com/services/application-insights/)， [OMS](https://github.com/Azure/diagnostics-eventflow#oms-operations-management-suite) （適用於內部部署應用程式），和[Azure 診斷](https://docs.microsoft.com/azure/monitoring-and-diagnostics/azure-diagnostics). 也有良好的協力廠商記錄分析平台和工具，可以搜尋警示、 報表和監視記錄檔，即使在即時喜歡[Splunk](http://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA)。

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Orchestrators 管理健康情況和診斷資訊

當您建立微服務為基礎的應用程式時，您需要處理複雜度。 當然，單一的微服務相當簡單，處理，但是數十份或數百個型別和無數 microservices 的執行個體是複雜的問題。 它就不會只建置您的微服務架構，您也需要高可用性、 可定址性、 復原、 健全狀況及診斷如果您想要擁有穩定且一致的系統。

![](./media/image22.png)

**圖 4-22**。 微服務平台為基礎的應用程式的健康情況管理

顯示在圖 4-22 中複雜的問題是很難將自行解決。 開發團隊應該專注於解決商務問題及建置自訂的應用程式的微服務為基礎的方法。 它們不應該專注於解決複雜的基礎結構發生問題;如果有，任何微服務為基礎的應用程式的成本是很大。 因此，有微服務導向的平台，稱為 orchestrators 」 或 「 微服務叢集，嘗試解決艱難問題的建置和執行服務和有效率地使用基礎結構資源。 這會減少建立使用 microservices 方法的應用程式的複雜性。

不同 orchestrators 聽起來可能類似，不同的診斷和每個所提供的健康情況檢查功能和到期日，有時會根據作業系統平台的狀態下一節中所述。

## <a name="additional-resources"></a>其他資源

-   **12 個因素應用程式。XI。記錄檔： 將記錄視為事件資料流**
    [*https://12factor.net/logs*](https://12factor.net/logs)

-   **Microsoft 診斷 EventFlow 程式庫。** GitHub 儲存機制。

    [*https://github.com/Azure/diagnostics-eventflow*](https://github.com/Azure/diagnostics-eventflow)

-   **什麼是 Azure 診斷**
    [*https://docs.microsoft.com/azure/azure-diagnostics*](https://docs.microsoft.com/azure/azure-diagnostics)

-   **Windows 電腦連線到 Azure 中的記錄分析服務**
    [*https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents*](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents)

-   **記錄您平均： 使用語意記錄應用程式區塊**
    [*https://msdn.microsoft.com/library/dn440729 (v=pandp.60).aspx*](https://msdn.microsoft.com/library/dn440729(v=pandp.60).aspx)

-   **Splunk。** 官方網站。
    [*http://www.splunk.com*](http://www.splunk.com)

-   **EventSource 類別**。 追蹤 Windows (ETW) 事件的應用程式開發介面[ *https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource*](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource)




>[!div class="step-by-step"]
[上一個](microservice-based-composite-ui-shape-layout.md) [下一步] (scalable-available-multi-container-microservice-applications.md)
