---
title: 前端用戶端通訊
description: 瞭解前端用戶端如何與雲端本機系統通訊
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: af26873381509df7807db6ecb37a7d73669adb37
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989073"
---
# <a name="front-end-client-communication"></a>前端用戶端通訊

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在雲端本機系統中,前端用戶端(行動、Web和桌面應用程式)需要通訊通道才能與獨立的後端微服務進行互動。  

有哪些選擇?

為了簡單化,前端用戶端可以直接與後端微服務*通信*,如圖 4-2 所示。

![將用戶端直接連線到服務通訊](./media/direct-client-to-service-communication.png)

**圖 4-2。** 將用戶端直接連線到服務通訊

使用此方法,每個微服務都有一個公共終結點,前端用戶端可以訪問該終結點。 在生產環境中,您將負載均衡器放在微服務前面,按比例路由流量。

雖然易於實現,但直接用戶端通信僅對簡單的微服務應用程式是可以接受的。 這種模式緊密耦合前端客戶的核心後端服務,為許多問題打開了大門,包括:

- 用戶端對後端服務重構的易感性。
- 核心後端服務會直接暴露出更大的攻擊面。
- 重複每個微服務之間的交叉問題。
- 過於複雜的客戶端代碼 - 客戶端必須跟蹤多個終結點,並以彈性方式處理故障。

相反,一個被廣泛接受的雲端設計模式是在前端應用程式和後端服務之間實現[API 閘道服務](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)。 圖案如圖 4-3 所示。

![API 閘道模式](./media/api-gateway-pattern.png)

**圖 4-3。** API 閘道模式

在上圖中,請注意 API 閘道服務如何抽象後端核心微服務。 作為 Web API 實現,它充當*反向代理*,將傳入的流量路由到內部微服務。

閘道將客戶端與內部服務分區和重構隔離。 如果更改後端服務,則可以在不中斷客戶端的情況下將其用於閘道。 這也是您處理交叉問題(如身份、緩存、彈性、計量和限制)的第一道防線。 其中許多交叉問題可以從後端核心服務卸載到網關,從而簡化了後端服務。

必須注意保持 API 閘道簡單快捷。 通常,業務邏輯會遠離閘道。 複雜的閘道有可能成為瓶頸,最終成為一個整體。 較大的系統通常公開按用戶端類型(移動、Web、桌面)或後端功能劃分的多個 API 閘道。 [前端後端](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends)模式為實現多個閘道提供了方向。 圖案如圖 4-4 所示。

![API 閘道模式](./media/backend-for-frontend-pattern.png)

**圖 4-4。** 前端圖案的後端介面

請注意,在上圖中,如何根據用戶端類型(Web、移動或桌面應用)將傳入流量發送到特定 API 閘道。 此方法有意義,因為每個設備的功能因外形、性能和顯示限制而異。 通常,與瀏覽器或桌面應用程式相比,移動應用程式公開的功能較少。 每個閘道都可以進行優化,以匹配相應設備的功能和功能。

首先,您可以構建自己的 API 閘道服務。 快速搜索 GitHub 將提供許多範例。 但是,有幾個框架和商業閘道產品可用。

## <a name="ocelot-gateway"></a>Ocelot 閘道

對於簡單的 .NET 雲本機應用程式,您可以考慮[Ocelot 閘道](https://github.com/ThreeMammals/Ocelot)。 Ocelot 是為 .NET 微服務創建的開源 API 閘道,需要統一的入口點才能進入其系統。 它重量輕、速度快、可擴展。

與任何 API 閘道一樣,其主要功能是將傳入的 HTTP 請求轉發到下游服務。 此外,它還支援可在 .NET Core 中間件管道中配置的各種功能。 其功能集顯示在下表中。

|Ocelot 功能  | |
| :-------- | :-------- |
| 路由 | 驗證 |
| 要求集合模式 | 授權 |
| 服務發現(與領事和尤里卡) | 節流 |
| 負載平衡 | 記錄記錄、追蹤 |
| Caching | 標題/查詢字串轉換 |
| 關聯傳遞 | 自訂中間件 |
| 服務品質 | 重試原則 |

每個 Ocelot 閘道指定 JSON 設定檔中的上游和下游位址和可配置功能。 用戶端向 Ocelot 閘道發送 HTTP 請求。 收到后,Ocelot 會通過其管道將 HttpRequest 物件傳遞到其配置指定的狀態。 在導管結束時,Ocelot會創建一個新的 HTTPResponseObject 並將其傳遞到下游服務。 對於回應,Ocelot將反轉管道,將回應發送回用戶端。

Ocelot 可作為 NuGet 套件提供。 它針對 NET 標準 2.0,使其與 .NET Core 2.0+ 和 .NET 框架 4.6.1+ 執行時相容。 Ocelot 與任何講 HTTP 並在 .NET Core 支援的平台上運行的函數集成:Linux、macOS 和 Windows。 Ocelot 是可擴展的,支援許多現代平臺,包括 Docker 容器、Azure 庫伯奈斯服務或其他公共雲。  Ocelot 與開源套餐集成,如[領事](https://www.consul.io)[、GraphQL](https://graphql.org)和 Netflix 的[Eureka。](https://github.com/Netflix/eureka)

請考慮 Ocelot 的簡單雲原生應用程式,這些應用程式不需要商業 API 閘道的豐富功能集。

## <a name="azure-application-gateway"></a>Azure 應用程式閘道

對於簡單的閘道要求,可以考慮[Azure 應用程式閘道](https://docs.microsoft.com/azure/application-gateway/overview)。 它作為 Azure [PaaS 服務](https://azure.microsoft.com/overview/what-is-paas/)提供,它包括基本的閘道功能,如 URL 路由、SSL 終止和 Web 應用程式防火牆。 該服務支援[第 7 層負載平衡](https://www.nginx.com/resources/glossary/layer-7-load-balancing/)功能。 使用第 7 層,您可以基於 HTTP 消息的實際內容路由請求,而不僅僅是低級 TCP 網路數據包。

在這本書中,我們宣傳在[庫伯內斯](https://www.infoworld.com/article/3268073/what-is-kubernetes-your-next-application-platform.html)託管雲原生系統。 Kubernetes 是容器協調器,可自動處理容器化工作負載的部署、擴展和操作問題。 Azure 應用程式閘道可以配置為[Azure 庫伯奈斯服務群集的](https://azure.microsoft.com/services/kubernetes-service/)API 閘道。

應用程式[閘道閘道控制器](https://azure.github.io/application-gateway-kubernetes-ingress/)使 Azure 應用程式閘道能夠直接與[Azure 庫伯奈斯服務](https://azure.microsoft.com/services/kubernetes-service/)配合使用。 圖 4.5 顯示了體系結構。

![應用程式閘道輸入控制器](./media/application-gateway-ingress-controller.png)

**圖 4-5。** 應用程式閘道輸入控制器

Kubernets 包括一個內建功能,支援 HTTP (7 級) 負載平衡,稱為[入口](https://kubernetes.io/docs/concepts/services-networking/ingress/)。 入口定義了一組規則,用於如何將 AKS 內的微服務實例暴露給外部世界。 在上一個映射中,入口控制器解釋為群集配置的入口規則,並自動配置 Azure 應用程式閘道。 根據這些規則,應用程式閘道將流量路由到在 AKS 內運行的微服務。 入口控制器偵聽入口規則的更改,並相應更改 Azure 應用程式閘道。

## <a name="azure-api-management"></a>Azure API 管理

對於中度到大規模雲本機系統,可以考慮 Azure [API 管理](https://azure.microsoft.com/services/api-management/)。 它是一種基於雲的服務,不僅可滿足您的 API 閘道需求,而且還提供功能齊全的開發人員和管理體驗。 API 管理如圖 4-6 所示。

![Azure API 管理](./media/azure-api-management.png)

**圖 4-6。** Azure API 管理

首先,API 管理公開了允許基於可配置規則和策略對後端服務的受控訪問的閘道伺服器。 這些服務可以位於 Azure 雲、上置數據中心或其他公共雲中。 API 金鑰和 JWT 權杖確定誰可以執行哪些操作。 出於分析目的,記錄所有流量。

對於開發人員,API 管理提供了一個開發人員門戶,提供對用於調用服務、文檔和示例代碼的訪問。 開發人員可以使用 Swagger/Open API 來檢查服務終結點並分析它們的使用方式。 該服務適用於主要開發平臺:.NET、JAVA、Golang 等。

發佈者門戶公開管理儀錶板,管理員在儀錶板中公開 API 並管理其行為。 可以授予服務訪問許可權、監視服務運行狀況以及收集服務遙測。 管理員將*策略*應用於每個終結點以影響行為。 [策略](https://docs.microsoft.com/azure/api-management/api-management-howto-policies)是預先構建的語句,每個服務調用按順序執行。  策略配置為入站呼叫、出站呼叫或在錯誤時調用。 策略可以應用於不同的服務範圍,以便在組合策略時啟用確定性排序。 該產品附帶了大量預先建[構的策略](https://docs.microsoft.com/azure/api-management/api-management-policies)。

以下是策略如何影響雲原生服務的行為的範例:  

- 限制服務訪問。
- 強制實施身份驗證。  
- 如有必要,從單個源進行節流呼叫。
- 啟用快取。
- 阻止來自特定 IP 位址的呼叫。
- 控制服務流。
- 將請求從 SOAP 轉換為 REST 或在不同的資料格式(如從 XML 轉換為 JSON)之間。

Azure API 管理可以公開託管在雲或資料中心的任何地方的後端服務。 對於可能在雲端本機系統中公開的舊式服務,它同時支援 REST 和 SOAP API。 甚至其他 Azure 服務也可透過 API 管理公開。 您可以將託管 API 放在 Azure 支援服務(如[Azure 服務總線](https://azure.microsoft.com/services/service-bus/)或[Azure 邏輯應用](https://azure.microsoft.com/services/logic-apps/))之上。 Azure API 管理不包括內置負載平衡支援,應與負載平衡服務結合使用。

Azure API 管理會在[不同的層中](https://azure.microsoft.com/pricing/details/api-management/):

- 開發人員
- 基本
- 標準
- Premium

開發人員層用於非生產工作負載和評估。 其他層提供更高的功率、功能和更高的服務級別協定 (SL)。 進階層提供[Azure 虛擬網路和](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)[多區域支援](https://docs.microsoft.com/azure/api-management/api-management-howto-deploy-multi-region)。 所有層每小時都有固定價格。

最近,Microsoft 發佈了 Azure [API 管理的 API 管理無伺服器層](https://azure.microsoft.com/blog/announcing-azure-api-management-for-serverless-architectures/)。 該服務稱為*消耗定價層*,是圍繞無伺服器計算模型設計的 API 管理的變體。 與之前顯示的「預分配」定價層不同,消費層提供即時預配和按行動付費定價。

它為以下用例開啟 API 閘道功能:

- 使用無伺服器技術(如 Azure[函數](https://docs.microsoft.com/azure/azure-functions/functions-overview)和[Azure 邏輯應用](https://azure.microsoft.com/services/logic-apps/))實現的微服務。
- Azure 支援服務資源,如服務總線佇列和主題、Azure 存儲等。
- 微服務,其中流量偶爾有大峰值,但大部分時間仍然很低。

消耗層使用相同的基礎服務 API 管理元件,但使用基於動態分配的資源的完全不同的體系結構。 它與無伺服器計算模型完美一致:

- 沒有要管理的基礎結構。
- 無空閒容量。
- 高可用性。
- 自動縮放。
- 成本基於實際使用方式。
  
對於將無伺服器資源公開為 API 的雲原生系統而言,新的消費層是一個很好的選擇。

> 在編寫本文時,消費層處於 Azure 雲中的預覽狀態。

## <a name="real-time-communication"></a>即時通訊

即時通訊或推送通訊是前端應用程式通過 HTTP 與後端雲端雲端雲端原生系統通訊的另一個選項。 應用程式(如財務代碼、在線教育、遊戲和工作進度更新)需要後端的即時實時回應。 使用正常的 HTTP 通信,客戶端無法知道何時有新數據可用。 客戶端必須持續*輪詢*或向伺服器發送請求。 通過*即時*通訊,伺服器可以隨時將新數據推送到用戶端。

即時系統通常以高頻數據流和大量併發用戶端連接為特徵。 手動實現即時連接可能會很快變得複雜,需要非普通基礎架構來確保可伸縮性和向連接的用戶端發送可靠的消息。 您可以發現自己管理 Azure Redis Cache 的實例和一組負載均衡器,這些平衡器配置了用於用戶端相關性的粘性作業階段。

[Azure SignalR 服務](https://azure.microsoft.com/services/signalr-service/)是一種完全託管的 Azure 服務,可簡化雲原生應用程式的即時通信。 技術實現詳細資訊(如容量配置、擴展和持久連接)被抽象化。 他們處理你與99.9%的服務級別協定。 您專注於應用程式功能,而不是基礎結構管道。

啟用後,基於雲的 HTTP 服務可以直接將內容更新推送到連接的用戶端,包括瀏覽器、行動和桌面應用程式。 用戶端將更新,而無需輪詢伺服器。 Azure SignalR 抽象了創建即時連接的傳輸技術,包括 WebSocket、伺服器端事件和長期輪詢。 開發人員專注於向連接用戶端的所有或特定子集發送消息。

圖 4-7 顯示了一組 HTTP 客戶端,這些用戶端連接到啟用了 Azure SignalR 的雲端本機應用程式。

![Azure SignalR](./media/azure-signalr-service.png)

**圖 4-7。** Azure SignalR

Azure SignalR 服務的另一個優勢是實現無伺服器雲本機服務。 也許您的代碼是按需使用 Azure 函數觸發器執行的。 這種情況可能比較棘手,因為代碼不會與用戶端保持長連接。 Azure SignalR 服務可以處理這種情況，因為該服務已經為您管理連線。

Azure SignalR 服務與其他 Azure 服務(如 Azure SQL 資料庫、服務總線或 Redis Cache)緊密整合,為雲端本機應用程式開闢了許多可能性。

>[!div class="step-by-step"]
>[前一個](communication-patterns.md)
>[下一個](service-to-service-communication.md)
