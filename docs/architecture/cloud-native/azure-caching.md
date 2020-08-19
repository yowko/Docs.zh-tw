---
title: 在雲端原生應用程式中快取
description: 瞭解雲端原生應用程式中的快取策略。
author: robvet
ms.date: 05/17/2020
ms.openlocfilehash: a33f143499b5f9545493bc4bc757cc3d152f7aa9
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557512"
---
# <a name="caching-in-a-cloud-native-app"></a>在雲端原生應用程式中快取

快取的優點很容易理解。 這項技術的運作方式是暫時將經常存取的資料從後端資料存放區複製到靠近應用程式的 *快速儲存體* 。 快取通常會實作為

- 資料保持相對靜態。
- 資料存取速度很慢，特別是與快取的速度比較。
- 資料受限於高度的爭用層級。

## <a name="why"></a>原因為何？

如 Microsoft 快取 [指引](https://docs.microsoft.com/azure/architecture/best-practices/caching)中所述，快取可以提高個別微服務和系統整體的效能、擴充性和可用性。 它可減少處理大量並行要求至資料存放區的延遲和競爭情形。 當資料量和使用者數目增加時，快取的優點就愈大。

當用戶端重複讀取不可變或不常變更的資料時，快取最有效。 範例包括參考資訊，例如產品和價格資訊，或結構昂貴的共用靜態資源。

雖然微服務應該是無狀態的，但在絕對必要時，分散式快取可以支援平行存取會話狀態資料。

也請考慮快取以避免重複計算。 如果作業轉換資料或執行複雜的計算，請快取後續要求的結果。

## <a name="caching-architecture"></a>快取架構

雲端原生應用程式通常會執行分散式快取架構。 快取是以雲端式 [支援服務](./definition.md#backing-services)的形式裝載，與微服務分開。 圖5-15 顯示架構。

![雲端原生應用程式中的快取](media/caching-in-a-cloud-native-app.png)

**圖 5-15**：雲端原生應用程式中的快取

在上圖中，請注意快取與微服務無關，且由其共用。 在此案例中，會由 [API 閘道](./front-end-communication.md)叫用快取。 如第4章所述，閘道是所有連入要求的前端。 分散式快取會盡可能傳回快取的資料，以提高系統回應速度。 此外，將快取與服務分開，可讓快取獨立相應增加或相應放大，以滿足增加的流量需求。

上圖呈現常見的快取模式，稱為「另行快取」 [模式](https://docs.microsoft.com/azure/architecture/patterns/cache-aside)。 針對連入要求，您必須先查詢快取 (步驟 \# 1) 以取得回應。 如果找到，則會立即傳回資料。 如果資料不存在於快取中 (稱為「快取 [遺漏](https://www.techopedia.com/definition/6308/cache-miss) 」) ，則會從下游服務 (步驟 2) 中的本機資料庫中取出資料 \# 。 然後將它寫入快取中，以供未來要求 (步驟 \# 3) ，並傳回給呼叫者。 務必小心地收回快取的資料，讓系統維持及時且一致。

當共用快取成長時，將其資料分割至多個節點可能會有所説明。 這麼做有助於將爭用降至最低，並改善擴充性。 許多快取服務都支援動態新增和移除節點，以及重新平衡資料分割之間資料的能力。 這種方法通常牽涉到叢集。 叢集會將一組同盟節點公開為無縫的單一快取。 不過，在內部，資料會依照預先定義的分佈策略（可平均平衡負載）分散到各個節點。

## <a name="azure-cache-for-redis"></a>Azure Cache for Redis

[Azure Cache for Redis](https://azure.microsoft.com/services/cache/) 是安全的資料快取和訊息代理程式服務，完全由 Microsoft 管理。 作為「平臺即服務」 (PaaS) 供應專案使用，可提供高輸送量和低延遲的資料存取權。 Azure 內部或外部的任何應用程式都可以存取此服務。

Azure Cache for Redis 服務可管理跨 Azure 資料中心裝載的開放原始碼 Redis 伺服器的存取權。 服務可做為提供管理、存取控制和安全性的外觀。 服務原本就支援一組豐富的資料結構，包括字串、雜湊、清單和集合。 如果您的應用程式已使用 Redis，則它會依 Azure Cache for Redis 運作。

Azure Cache for Redis 是一部簡單的快取伺服器。 它可支援許多案例以增強微服務架構：

- 記憶體中的資料存放區
- 分散式非關係資料庫
- 訊息代理程式
- 設定或探索伺服器
  
針對先進的案例，快取資料的複本可 [保存到磁片](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-how-to-premium-persistence)中。 如果災難性事件同時停用主要和複本快取，則會從最新的快照集重建快取。

Azure Redis 快取適用于數個預先定義的設定和定價層。 進 [階層具有許多企業級功能，](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-overview#service-tiers) 例如叢集、資料持續性、異地複寫和虛擬網路隔離。

>[!div class="step-by-step"]
>[上一個](relational-vs-nosql-data.md) 
>[下一步](elastic-search-in-azure.md)
