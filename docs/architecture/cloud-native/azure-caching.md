---
title: 在雲端原生應用程式中快取
description: 瞭解雲端原生應用程式中的快取策略。
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 2da61a01fc53233d1934df813fcba3b91a495c43
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794965"
---
# <a name="caching-in-a-cloud-native-app"></a>在雲端原生應用程式中快取

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

快取的優點很清楚。 這項技術的運作方式是將經常存取的資料從後端資料存放區暫時複製到靠近應用程式的*快速儲存體*。 快取通常會實作為 。

- 資料會維持相對靜態。
- 資料存取速度很慢，特別是與快取的速度相比。
- 資料受限於高層級的爭用。

## <a name="why"></a>為什麼？

如 Microsoft 快取[指引](https://docs.microsoft.com/azure/architecture/best-practices/caching)中所述，快取可以提升個別微服務和整個系統的效能、擴充性和可用性。 它可減少對資料存放區處理大量並行要求的延遲和競爭。 隨著資料量和使用者數目的增加，快取的優點就愈大。

當用戶端重複讀取不可變或不常變更的資料時，快取最有效率。 範例包括參考資訊（例如產品和價格資訊），或許多耗用大量共用靜態資源的結構。

雖然微服務應該是無狀態的，但在絕對必要時，分散式快取可以支援平行存取會話狀態資料。

也請考慮快取以避免重複計算。 如果作業轉換資料或執行複雜的計算，請快取後續要求的結果。

## <a name="caching-architecture"></a>快取架構

雲端原生應用程式通常會執行分散式快取架構。 快取是以雲端為基礎的[支援服務](./definition.md#backing-services)來裝載，並與微服務分開。 圖5-20 顯示架構。

![在雲端原生應用程式中快取](media/caching-in-a-cloud-native-app.png)

**圖 5-19**：雲端原生應用程式中的快取

在上圖中，請注意快取是獨立的，並由微服務共用。 在此案例中， [API 閘道](./front-end-communication.md)會叫用快取。 如第4章所述，閘道可作為所有傳入要求的前端。 分散式快取會盡可能傳回快取的資料，以增加系統回應能力。 此外，將快取與服務分開，可讓快取獨立相應增加或相應放大，以滿足更多的流量需求。

此圖顯示常見的快取模式，稱為另行快取[模式](https://docs.microsoft.com/azure/architecture/patterns/cache-aside)。 針對連入要求，您必須先查詢快取（步驟 \#1）來取得回應。 如果找到，則會立即傳回資料。 如果資料不存在於快取中（稱為快取[遺漏](https://www.techopedia.com/definition/6308/cache-miss)），則會從下游服務中的本機資料庫抓取（步驟 \#2）。 然後會將它寫入快取以供未來的要求（步驟 \#3），並傳回給呼叫者。 請小心定期收回快取的資料，讓系統維持及時且一致的狀態。

當共用快取增加時，將其資料分割到多個節點上可能會有好處。 這麼做可協助將爭用降到最低，並改善擴充性。 許多快取服務都支援動態新增和移除節點，以及跨分割區重新平衡資料的功能。 這種方法通常牽涉到叢集。 叢集會將同盟節點的集合公開為順暢的單一快取。 不過，在內部，資料會在節點間散佈，並遵循預先定義的散發策略來平均平衡負載。

## <a name="azure-cache-for-redis"></a>Azure Cache for Redis

[Azure Cache For Redis](https://azure.microsoft.com/services/cache/)是安全的資料快取和訊息代理程式服務，完全由 Microsoft 管理。 以「平臺即服務」（PaaS）供應專案的形式取用，可提供高輸送量和低延遲的資料存取。 服務可供 Azure 內部或外部的任何應用程式存取。

Azure Cache for Redis 服務會管理跨 Azure 資料中心裝載之開放原始碼 Redis 伺服器的存取權。 此服務的作用是提供管理、存取控制和安全性的外觀。 服務原本就支援一組豐富的資料結構，包括字串、雜湊、清單和集合。 如果您的應用程式已使用 Redis，它會與 Azure Cache for Redis 一起正常搭配使用。

Azure Cache for Redis 不只是簡單的快取伺服器。 它可以支援數種案例來增強微服務架構：

- 記憶體中的資料存放區
- 分散式非關係資料庫
- 訊息代理程式
- 設定或探索伺服器
  
在 advanced 案例中，快取資料的複本可以[保存到磁片](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-how-to-premium-persistence)中。 如果嚴重事件同時停用主要和複本快取，則會從最新的快照集重建快取。

Azure Redis 快取適用于多個預先定義的設定和定價層。  進階層提供許多企業層級[的功能，](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-premium-tier-intro)例如叢集、資料持續性、異地複寫和虛擬網路隔離。

>[!div class="step-by-step"]
>[上一頁](relational-vs-nosql-data.md)
>[下一頁](elastic-search-in-azure.md)
