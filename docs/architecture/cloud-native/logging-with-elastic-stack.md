---
title: 使用彈性堆疊記錄
description: 使用彈性堆疊、Logstash 和 Kibana 的記錄
ms.date: 05/13/2020
ms.openlocfilehash: 32d9d0dae175d8d45d48b56d17f133b4cc432363
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811167"
---
# <a name="logging-with-elastic-stack"></a>使用彈性堆疊記錄

有許多良好的集中式記錄工具，其成本會因免費的開放原始碼工具而異，而且成本更高。 在許多情況下，免費的工具都優於或優於付費供應專案。 其中一種工具是三個開放原始碼元件的組合：彈性搜尋、Logstash 和 Kibana。

這些工具統稱為彈性堆疊或 ELK 堆疊。

## <a name="elastic-stack"></a>彈性堆疊

彈性堆疊是從 Kubernetes 叢集收集資訊的強大選項。 Kubernetes 支援將記錄傳送至 Elasticsearch 端點，在大部分的 [情況](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)下，您必須先設定環境變數，如圖7-5 所示：

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

**圖 7-5**. Kubernetes 的設定變數

這會在叢集上安裝 Elasticsearch，並將所有叢集記錄檔傳送給它。

![Kibana 儀表板的範例，其中顯示針對內嵌自 Kubernetes ](./media/kibana-dashboard.png)
 **圖 7-6**的記錄進行查詢的結果。 Kibana 儀表板的範例，顯示從 Kubernetes 內嵌的記錄查詢結果

## <a name="what-are-the-advantages-of-elastic-stack"></a>彈性堆疊的優點為何？

彈性堆疊以低成本、可調整的雲端易用方式提供集中式記錄。 其使用者介面可簡化資料分析，讓您可以花時間搜集資料，而不需要使用相當笨拙介面。 它支援各種不同的輸入，因此當您的分散式應用程式跨越更多和不同種類的服務時，您可以預期能夠繼續將記錄和計量資料送入系統中。 彈性堆疊也支援快速搜尋（甚至是跨大型資料集），因此甚至是大型應用程式可能會記錄詳細資料，而且仍然能夠以效能提升的方式來查看。

## <a name="logstash"></a>Logstash

第一個元件是 [Logstash](https://www.elastic.co/products/logstash)。 這項工具是用來收集來自各種不同來源的記錄資訊。 比方說，Logstash 可以從磁片讀取記錄，也可以接收來自記錄程式庫（例如 [Serilog](https://serilog.net/)）的訊息。 Logstash 可以對記錄檔進行一些基本的篩選和擴充。 比方說，如果您的記錄包含 IP 位址，則可以將 Logstash 設定為進行地理查閱，並取得該訊息的國家或甚至是來源城市。

Serilog 是適用于 .NET 語言的記錄程式庫，可讓您進行參數化記錄。 參數不會產生內嵌欄位的文字記錄訊息，而是會分開保存。 這可讓您進行更聰明的篩選和搜尋。 [圖 7-7] 顯示寫入 Logstash 的範例 Serilog 設定。

```csharp
var log = new LoggerConfiguration()
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

**圖 7-7**。 透過 HTTP 將記錄資訊直接寫入至 logstash 的 Serilog 設定

Logstash 會使用如圖7-8 中所示的設定。

```
input {
    http {
        #default host 0.0.0.0:8080
        codec => json
    }
}

output {
    elasticsearch {
        hosts => "elasticsearch:9200"
        index=>"sales-%{+xxxx.ww}"
    }
}
```

**圖 7-8**。 從 Serilog 取用記錄的 Logstash 設定

在不需要大量記錄操作的情況下，有一個 Logstash 稱為 [節拍](https://www.elastic.co/products/beats)的替代方案。 「勝過」是一系列的工具，可從記錄收集各種不同的資料，以及網路資料和執行時間資訊。 許多應用程式會使用 Logstash 和節拍。

一旦 Logstash 收集記錄之後，就需要在某處放置記錄。 雖然 Logstash 支援許多不同的輸出，但其中一個較令人興奮的輸出是彈性搜尋。

## <a name="elastic-search"></a>彈性搜尋

彈性搜尋是功能強大的搜尋引擎，可在記錄抵達時編制索引。 它會讓針對記錄檔執行查詢變得更快速。 彈性搜尋可以處理大量的記錄，而且在極端的情況下，可以在多個節點之間相應放大。

您可以直接查詢已針對包含參數或透過 Logstash 處理來分割參數的記錄訊息，因為 Elasticsearch 會保留這種資訊。

[圖 7-9] 中的查詢會搜尋所造訪的前10個頁面 `jill@example.com` 。

```json
"query": {
    "match": {
      "user": "jill@example.com"
    }
  },
  "aggregations": {
    "top_10_pages": {
      "terms": {
        "field": "page",
        "size": 10
      }
    }
  }
```

**圖 7-9**。 用來尋找使用者所造訪前10個頁面的 Elasticsearch 查詢

## <a name="visualizing-information-with-kibana-web-dashboards"></a>使用 Kibana web 儀表板將資訊視覺化

堆疊的最後一個元件是 Kibana。 此工具是用來在 web 儀表板中提供互動式視覺效果。 即使是非技術性的使用者，也可以製作儀表板。 大部分位於 Elasticsearch 索引中的資料都可以包含在 Kibana 儀表板中。 個別使用者可能會有不同的儀表板，Kibana 可透過允許使用者特定的儀表板，來啟用此自訂。

## <a name="installing-elastic-stack-on-azure"></a>在 Azure 上安裝彈性堆疊

您可以透過數種方式在 Azure 上安裝彈性堆疊。 同樣地，您可以布建 [虛擬機器，並直接在其上安裝彈性堆疊](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)。 某些有經驗的使用者偏好此選項，因為它提供最高的自訂能力。 在基礎結構即服務上部署，會帶來大量的管理負擔，進而強制採用該路徑的人取得與基礎結構即服務相關聯之所有工作的擁有權，例如保護機器的安全，以及保持最新的修補程式。

較少額外負荷的選項，是使用已設定彈性堆疊的許多 Docker 容器之一。 這些容器可以放入現有的 Kubernetes 叢集中，並與應用程式程式碼一起執行。 [Sebp/elk](https://elk-docker.readthedocs.io/)容器是記錄完善且經過測試的彈性堆疊容器。

另一個選項是 [最近宣佈的 ELK 即服務](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/)供應專案。

## <a name="references"></a>參考資料

- [在 Azure 上安裝彈性堆疊](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
>[上一個](observability-patterns.md) 
>[下一步](monitoring-azure-kubernetes.md)
